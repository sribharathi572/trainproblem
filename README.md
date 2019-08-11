# trainproblem

# main.html
<html>
<div>
<h1>easy trains</h1>
</div>
<div><a href="signup.html"><button>signup</button></a></div></br>
<div><a href="hac.html"><button>login</button></a></div></br>
</html>

# signup.html
<html>
<body bgcolor="lightgrey">
<form name="my1" method="post" >
<table border="1" allign="left" cellpadding="2.7p" cellspacing="2.2p">
<tr><th><label>enter name</label></th>
      <td><input type="text" length="10" placeholder="name" name="u1name"></td></tr>
<tr><th><label>enter place</label></th>
      <td><input type="text" name="uplace"></td></tr>
<tr><th><label>enter password</label></th>
      <td><input type="password" name="upw"></td></tr>
<tr><th><label>confrim password</label></th>
      <td><input type="password" name="ucpw"></td></tr>
<tr><td colspan="2"><center><input type="button" name="b1" value="signup" onclick="train.html"></center></td></tr>
</table>
</form>
</body>
</html>

# train.html
<html>
<body bgcolor="lightgrey">
<form name="my2" method="post" >
<table border="1" allign="left" cellpadding="2.7p" cellspacing="2.2p">
<tr><th><label>enter train name</label></th>
      <td><input type="text" length="10" placeholder="name" name="tname"></td></tr>
<tr><th><label>enter train number</label></th>
      <td><input type="password" name="tno"></td></tr>
<tr><td colspan="2"><center><input type="button" name="b2" value="submit" onclick="signup.php" ></center></td></tr>
</table>
</form>
</body>
</html>

# signup.php
<?php
  $dbhost='localhost';
  $dbuser='root';
  $dbpass='';
  $dbname='user';
  $con=new mysqli_connect($dbhost,$dbuser,$dbpass,$dbname);
  if(!$con){
  	echo"error is".mysqli_connect_error();
  }
  else{
	echo"connection is established";
}
if(isset($_POST(b1))){
	$name=$_POST[u1name];
	$place=$_POST[uplace];
	$pwd=$_POST[upw];
	$ucpw=$_POST[ucpw];
	$tname=$_POST[tname];
	$tno=$_POST[tno];
	$q="create table user(uname,varchar(20),place,varchar(20),pwd,varchar(20),ucpw,varchar(20),tname,varchar(20),tno,varchar(20))";
	mysqli_query($con,$q);
	$q1="insert into user(uname,place,pwd,ucpw,tname,tno)
		value($name,$place,$pwd,$ucpw,$tname,$tno)";
	if(mysqli_query($con,$q1)){
		echo"registration successful";
	}
	else{
		echo"the error is".mysqli_error();
	}
	mysqli_close($con);
	?>
  
  # login.html
  <html>
<body bgcolor="lightgrey">
<form name="my" method="post" >
<table border="1" allign="left" cellpadding="2.7p" cellspacing="2.2p">
<tr><th><label>enter name</label></th>
      <td><input type="text" length="10" placeholder="name" name="uname"></td></tr>
<tr><th><label>enter password</label></th>
      <td><input type="password" name="pw"></td></tr>
<tr><td colspan="2"><center><input type="button" name="b1" value="login" onclick="login.php" ></center></td></tr>
</table>
</form>
</body>
</html>

# login.php
<?php
  $dbhost='localhost';
  $dbuser='root';
  $dbpass='';
  $dbname='user';
  $con=new mysqli_connect($dbhost,$dbuser,$dbpass,$dbname);
  if(!$con){
  	echo"error is".mysqli_connect_error();
  }
  else{
	echo"connection is established";
}
if(isset($_POST(b1))){
	$name=$_POST[uname];
	$pwd=$_POST[pw];
	$cpwd=$_POST[cpw];
	$q="select * from user where uid='$name'";
	$rs=mysqli_query($conn,$q);
	$num=$mysqli_fetch_array($rs);
	echo'<center>';
	echo'<table border=1>';
	echo'<tr>';
	echo'<th>UserName</th>';
	echo'<th>train no</th>';
	echo'<th>train name</th>';
	echo'<th>date</th>';
	for($i=0;$i<$num;$i++){ ?>
<html>
<body>
<?php
		<tr><td><?php echo $num[0]></td>
		      <td><?php echo $num[1]></td>
		      <td><?php echo $num[2]></td>
		      <td><?php echo $num[3]></td></tr>
		<?php
		}
		mysqli_close($con);
		?>
	

?>
</body>
</html> 
	

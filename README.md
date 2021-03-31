# learning-resource-recommendation-system
To recommand resource for the user using content based filtering algorithm based on their learning ability.
<?php      
    include('connection.php');  
    $id = $_POST['id']; 
    $year = $_POST['year'];
    $dept = $_POST['dept'];
    $pwd = $_POST['pwd'];  
      
        //to prevent from mysqli injection  
        $id = stripcslashes($id);  
        $year = stripcslashes($year);  
        $dept = stripcslashes($dept);  
        $pwd = stripcslashes($pwd);
        $id = mysqli_real_escape_string($con, $id);  
        $year = mysqli_real_escape_string($con, $year);  
        $dept = mysqli_real_escape_string($con, $dept);  
        $pwd = mysqli_real_escape_string($con, $pwd);  
        $sql = "select *from login where id = '$id' and year = '$year' and dept = '$dept' and pwd = '$pwd'";  
        $result = mysqli_query($con, $sql);  
        $row = mysqli_fetch_array($result, MYSQLI_ASSOC);  
        $count = mysqli_num_rows($result);  
          
        if($count == 1){  
          session_start();
                            
                            
            $_SESSION["loggedin"] = true;
            $_SESSION["id"] = $id;
            $_SESSION["username"] = $username;                            
                            
                            // Redirect user to welcome page
                            header("location: Hlp.html");
  
         
        }  
        else{  
            echo "<h1> Login failed. Invalid username or password.</h1>";  
        }     
?>  
<?php      
    $host = "localhost";  
    $user = "root";  
    $password = '';  
    $db_name = "login";  
      
    $con = mysqli_connect($host, $user, $password, $db_name);  
    if(mysqli_connect_errno()) {  
        die("Failed to connect with MySQL: ". mysqli_connect_error());  
        
    }  
?>
<!DOCTYPE html>
<html>
<head>
<title>HOMEPAGE</title>
<link rel = "stylesheet" type = "text/css" href = "style1.css">   
</head>
<style>
img {
  width: 100%;
  height: auto;
  background: cover;
}
</style>
<body>
<div class="container">
<h2 style="text-align:center"> LEARNING RESOURCE RECOMMENTATION</h2>
<h2 style="text-align:center">CSE DEPARTMENT</h2>
<div class="navigation">
<a class="button" href="index.html">
<div class="logout">LOGOUT</div>
</a>
</div>

<div class="box" style="width:200px;">
<form action="/action_page.php">

<div class="center">
<input list="semesters" name="semesters">
  <datalist id="semesters">
    <option value="Semester 1">
    <option value="Semester 2">
    <option value="Semester 3">
    <option value="Semester 4">
    <option value="Semester 5">
    <option value="Semester 6">
    <option value="Semester 7">
    <option value="Semester 8">
  </datalist>
</div> 
 <div class="center">
   <input type="submit">
 </div> 

</body>
</html>
<?php
// Initialize the session
session_start();
 
// Check if the user is already logged in, if yes then redirect him to welcome page
if(isset($_SESSION["loggedin"]) && $_SESSION["loggedin"] === true){
    header("location: welcome.php");
    exit;
}
body{
    margin:0;
    padding:0;
    font-family: sans-serif;
    background: #cc99ff;
    
    background-size: cover;
}
.box{
  width:300px;
  padding:30px;
  position: absolute;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
  background:#f2e6ff;
  text-align:center;

}
.box h1
{
    color: #6600cc;
    text-transform: uppercase;
    font-weight: 700;
    text-align:center;
}
.box input[type="text"],.box input[type="password"],.box input[type="number"]
{
border: 0;
background: none;
display: block;
margin: 20px auto;
text-align: center;
border:3px solid #6600cc;
padding:14px 10px;
width:220px;
outline: none;
color: black;
border-radius: 24px;
transition:0.25px;
}

.box input[type="text"]:focus,.box input[type="number"]:focus,.box input[type="password"]:focus{

width:270px;
border-color:  #26004d;

}
.box input[type="submit"]{


    border: 0;
background: none;
display: block;
margin: 20px auto;
text-align: center;
border:3px solid #6600cc;
padding:14px 35px;
outline: none;
color: black;
border-radius: 24px;
transition:0.25px;
cursor:pointer;
    
}
.box input[type="submit"]:hover{
    background: #6600cc;
}

 
<html>  
<head>  
    <title>PLORS</title>  
    
    <link rel = "stylesheet" type = "text/css" href = "style.css">   
</head>  
<body>  
    <div id = "frm">  
          
        <form name="f1" class ="box" action = "authentication.php" onsubmit = "return validation()" method = "POST">  
	<h1>Login</h1>            
	    <input type="text" name="id" id="id" placeholder="Enter User_ID" >
	    <input type="number" name="year" id="year" placeholder="Enter Year" >
	    <input type="text" name="dept" id="dept" placeholder="Enter Dept" >
	    <input type="password" name="pwd" id="pwd" placeholder="Enter Password" >
            <input type =  "submit" id = "btn" value = "Login" />  
             
        </form>  
    </div>  
    
    <script>  
            function validation()  
            {  
                var id=document.f1.user.value;  
                var ps=document.f1.pass.value;  
                if(id.length=="" && ps.length=="") {  
                    alert("User Name and Password fields are empty");  
                    return false;  
                }  
                else  
                {  
                    if(id.length=="") {  
                        alert("User Name is empty");  
                        return false;  
                    }   
                    if (ps.length=="") {  
                    alert("Password field is empty");  
                    return false;  
                    }  
                }                             
            }  
        </script>  
</body>     
</html>  
body{
    margin:0;
    padding:0;
    font-family: Georgia;
    background-color: #f7e6ff;
    background-size: cover;
  
}
h2 {
  top:20%;
  left:50%;
  background-color: none;
  color:black;
  text-shadow: 2px 2px 5px #f2e6ff;
  text_align:center;
}

.container{
  width:1000px;
  padding:30px;
  position: absolute;
  top:20%;
  left:50%;
  transform: translate(-50%,-50%);
  background: none;
  text-align:center;

}
.box{
  width:2000px;
  padding:30px;
  position: absolute;
  top:150%;
  left:50%;
  transform: translate(-50%,-50%);
  background: none;
  text-align:center;

}
div.center {
  display: flex;
  justify-content: center; 
}

div.center input[type="submit"]{
border: 0;
background:  #e6ccff;
display: block;
margin: 20px auto;
text-align: center;
border:3px solid #400080;
padding:14px 35px;
outline: none;
color: black;
border-radius: 24px;
transition:0.25px;
cursor:pointer;
}

div.center input[list="semesters"]{
border: 0;
background:  #e6ccff;
display: block;
margin: 20px auto;
text-align: center;
border:3px solid #400080;
padding:14px 35px;
outline: none;
color: black;
border-radius: 24px;
transition:0.25px;
cursor:pointer;
}

div.navigation {
  width:1000px;
  padding:30px;
  position: absolute;
  top:20%;
  left:150%;
  transform: translate(-50%,-50%);
  background: none;
  text-align:left;

}
<?php
	session_start();
	$sym = $_SERVER['QUERY_STRING'];
	$command = escapeshellcmd("sample.py $sym");
    $output = shell_exec($command);
	$_SESSION['output'] = $output;
?>
<!doctype html>
<html>
    <head></head>
    <body>
        <h1>Homepage <?php echo  $_SESSION['uid']; ?></h1>
        <div>
		<?php echo  $_SESSION['output']; ?>
		</div>
    </body>
</html>

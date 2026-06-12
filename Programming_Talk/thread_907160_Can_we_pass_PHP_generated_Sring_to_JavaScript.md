---
title: "Can we pass PHP generated Sring to JavaScript"
date: 2008-09-01
forum: Programming Talk
---

### Post by ivikas on 2008-09-01
Hello all,

         I am doing a registration form.In it, there is a "check availability" link near "username" field.Users are supposed to enter a "username(say john)" in the username text box and click on "check availability" link which will open a pop up window and username availability status is displayed there.

This  lines are in register.php


The opening of pop up window is done using the following javaScript

```

function popup(theURL,winName,features) 
{ 
 		mywindow=window.open(theURL,winName,features);
	        mywindow.moveTo(1000,150);
}

```
And after taking the content of text box(john) like

                ```
<?php $username=$_POST['username'];?>

It is passed as a parameter value to "available.php" like

<a href="#" onclick="popup('available.php?user=<?php echo $_POST['username'] ?>,'Availability Check','width=300,height=350')">Check Availability</a>


```
------------------------------------------------------------------------
available.php

available.php is used to process the username availability status,in this i try to get the value of username textbox of register.php(say john) like

```
echo "Value=".$_REQUEST['user'];

```
               
But iam getting a null value in "available.php" instead of "john" that is entered in the username textbox field of register.php.Iam trying all the ways, but in vain

Please give an idea to get around

Thanks in advance.

---

### Post by cszikszoy on 2008-09-01
I think I understand what you are explaining, but this is definitely possible.  I've done it many times.  Something must be wrong with your implementation.

Can you access any POST variables?  I'm not sure what the rest of your pages look like, but to access these, register.php must have a form, whith the action of whatever page you are trying to access the POST variables on and the method of POST.

Furthermore, the form items on your HTML form must include a name="asdf" tag, which is used to define the POST variables.

If this doesn't answer your question perhaps you can explain more, or create a small project that reproduces your problem and show me the code.

---

### Post by SeanHodges on 2008-09-02
It would be useful to see the full source to get a better idea of what might be going wrong, for instance I can't tell if you are actually submitting your form...

$_POST[] is populated after an HTML form is submitted, if you are entering "John" into a text field and then clicking on the hyperlink you have given, the text has not been posted and therefore $_POST will be empty.

---

### Post by ivikas on 2008-09-03
This is contained in register.php and the javascript popup code is also here

```

function popup(theURL,winName,features) 
{ 
  		mywindow=window.open(theURL,winName,features);
	        mywindow.moveTo(1000,150);
}
<?php $got=$_POST['username']; ?>
td colspan="4"><input type="text" name="username"/>&nbsp;<input type="submit" value="Check Availability" name="avBtn" onclick="return popup('available.php?user=<?php echo $got; ?>','Avaiability Check','width=300,height=350');"/>

```

And in available.php i try to print the value as

```

<?php
		
		echo "Value=".$_REQUEST['user']; ?>

```

Now iam getting value but in **double clicking **the check availability button

---

### Post by cszikszoy on 2008-09-03
ivikas:

We need to see some actual source to help you.  I can't even tell if you are submitting some form to get these values.  As another poster stated, $_POST[] is empty unless you have a html form that posts to some other php page with the method of POST.

Without any real source I can't begin to tell you what's wrong.

In the mean time, please read these pages and see if they don't answer your questions

[http://www.tizag.com/phpT/forms.php](http://www.tizag.com/phpT/forms.php)
- A great overview of HTML forms and php form processing using the post method

[http://www.tizag.com/phpT/postget.php](http://www.tizag.com/phpT/postget.php)
- an explanation of the difference between POST and GET

These pages should be able to answer your questions.

---

### Post by ivikas on 2008-09-04
Okay, actually the code is lengthy,so i refrained,sorry for it here's the code

register.php

```

<?php
include("includes/connect.php");
if(isset($_POST['regBtn']))
	{
			
			$username=$_POST['username'];
			$password=$_POST['password'];
			$firstname=$_POST['fname'];
			$lastname=$_POST['lname'];
			$gender=$_POST['gender'];
			$dob=$_POST['date']."/".$_POST['month']."/".$_POST['year'];
			$email=$_POST['email'];
			$country=$_POST['country'];
			 
$insertQuery="insert into user(username,password,isadmin,firstname,lastname,gender,dob,email,country) values('".$username."','".$password."',1,'".$firstname."','".$lastname."','".$gender."','".$dob."','".$email."','".$country."')";

			
			@mysql_query($insertQuery,$db);
			header("Location:register.php?msg=001");
	}
	
	?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>||  World  ||  A place for you to connect,share and grow ||</title>
<meta name="generator" content="WordPress 2.1.2" /> <!-- leave this for stats -->
<link rel="stylesheet" href="css/style.css" type="text/css" media="screen" />
<script language="javascript">
function validate(theForm)
{
	if(theForm.username.value=="")
		{
			alert("Please provide a username!!");
			theForm.username.focus();
			return false;
		}
		if(theForm.password.value=="")
		{
			alert("Please enter your password.");
			theForm.password.focus();
			return false;
		}
		
		if(theForm.pconfirm.value=="")
		{
				alert("Please enter again to confirm your password");
				theForm.pconfirm.focus();
				return false;
		}
	 if(theForm.password.value != theForm.pconfirm.value)
		{
			alert("Password Mismatch!! try again");
			theForm.pconfirm.focus();
			return false;
		}
	if(theForm.fname.value=="")
		{
			alert("Please enter your first name");
			theForm.fname.focus();
			return false;
		}
		if(theForm.lname.value=="")
		{
			alert("Please enter your last name");
			theForm.lname.focus();
			return false;
		}
		if(theForm.date.value=="")
		{
			alert("Please select a  date.");
			theForm.date.focus();
			return false;
		}
		if(theForm.month.value=="")
		{
			alert("Please select a  month.");
			theForm.month.focus();
			return false;
		}
	if(theForm.year.value=="")
		{
			alert("Please select a  year.");
			theForm.year.focus();
			return false;
		}
		if(theForm.email.value=="")
		{
				alert("Please enter your email id");
				theForm.email.focus();
				return false;
		}	
		if(!checkEmail(theForm.email.value))
		{
			  alert("Invalid e-mail address ! please re-enter.");
			  theForm.email.focus();
			  return false;
		}
		if(theForm.country.value=="")
		{
			alert("Please select your country.");
			theForm.country.focus();
			return false;
		}
	return true;
}
function checkEmail(theValue) 
{
	if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(theValue))
	{
		return (true)
	}
	return (false)
}	
function popup(theURL,winName,features) 
{ 
  		mywindow=window.open(theURL,winName,features);
		//alert(theURL);
		 mywindow.moveTo(1000,150);
}
</script>

<style type="text/css">
<!--
.style1 {
	font-size: 12px;
	font-weight: bold;
}
-->
</style>
</head>
<body>
<div id="wrapper2">
<div id="navigation">

		         	<h1><a href="">world </a></h1>
			        <div class="slogan">Connect,share and grow </div>
			        <div style="clear: both;"></div>
 <ul>
 <li class="page_item"><a href="">Home</a></li>
 </ul>
 </div>


<div id="wrapper">
<form id="register" name="register" method="post">
<table width="200" border="0" align="center" cellpadding="0" cellspacing="0">
  <tr>
    <td><img src="images/top.jpg" width="509" height="18" /></td>
    </tr>
  <tr>
    <td background="images/repeat.jpg"><table align="center" cellpadding="4" cellspacing="0">

<tr><td width="79"><span class="style1">Username</span></td>

	<?php $got=$_POST['username']; ?>
	
<td colspan="4"><input type="text" name="username"/>&nbsp;
  <input type="submit" value="Check Availability" name="avBtn" onclick="return popup('available.php?user=<?php echo $got; ?>','Avaiability Check','width=300,height=350');"/></td>
</tr>
<tr><td class="style1">Password</td>
<td colspan="4"><input type="password" name="password" /></td></tr>
<tr><td class="style1">Confirm</td>
<td colspan="4"><input name="pconfirm" type="password" id="pconfirm" /></td></tr>
<tr><td class="style1">First Name</td>
<td colspan="4"><input type="text" name="fname" /></td></tr>
<tr><td class="style1">Last Name</td>
<td colspan="4"><input type="text" name="lname" /></td></tr>
<tr>
  <td class="style1">Gender</td>
  <td width="23"> <input type="radio" name="gender" value="Male" checked="checked"/></td>
  <td width="43">Male&nbsp;&nbsp;&nbsp;</td>
  <td width="23"><input type="radio" name="gender" value="Female" /></td>
  <td width="193">Female</td>
</tr>
<tr>
  <td class="style1">Date of Birth</td>
  <td colspan="4"><select name="date"><option value="" selected="selected">Date</option><?php for($i=1;$i<=31;$i++) { ?> <option value=<?php echo $i;?>><?php echo $i."<br>" ?></option><?php } ?></select>&nbsp;&nbsp;&nbsp;
<select name="month">
<option value="" selected="selected" >Month</option>
<option value="January">January</option>
<option value="February">February</option>
<option value="March">March</option>
<option value="April">April</option>
<option value="May">May</option>
<option value="June" >June</option>
<option value="July">July</option>
<option value="August">August</option>
<option value="September">September</option>
<option value="October">October</option>
<option value="November">November</option>
<option value="December">December</option>
</select>&nbsp;&nbsp;&nbsp;
<select name="year"><option value="" selected="selected">Year</option><?php for($i=1947;$i<=2001;$i++) { ?> <option value=<?php echo $i;?>><?php echo $i."<br>" ?></option><?php } ?></select></td>
</tr>
<tr>
  <td class="style1">E-mail</td>
  <td colspan="4"><input type="text" name="email" /></td>
</tr>
<tr>
  <td class="style1">Country</td>
  <td colspan="4"><select  name="country">					
														  <option value="" selected="selected">country</option>
														  <option value="Afghanistan">Afghanistan</option>
                                                          <option value="Albania">Albania</option>
                                                          <option value="Algeria">Algeria</option>
                                                          <option value="American Samoa">American Samoa</option>
                                                          <option value="Andorra">Andorra</option>
                                                          <option value="Angola">Angola</option>
                                                          <option value="Anguilla">Anguilla</option>
                                                          <option value="Antarctica">Antarctica</option>
                                                          <option value="Argentina">Argentina</option>
                                                          <option value="Armenia">Armenia</option>
                                                          <option value="Aruba">Aruba</option>
                                                          <option value="Australia">Australia</option>
                                                          <option value="Austria">Austria</option>
                                                          <option value="Azerbaijan">Azerbaijan</option>
                                                          <option value="Bahamas">Bahamas</option>
                                                          <option value="Bahrain">Bahrain</option>
                                                          <option value="Bangladesh">Bangladesh</option>
                                                          <option value="Barbados">Barbados</option>
                                                          <option value="Belarus">Belarus</option>
                                                          <option value="Belgium">Belgium</option>
                                                          <option value="Belize">Belize</option>
                                                          <option value="Benin">Benin</option>
                                                          <option value="Bermuda">Bermuda</option>
                                                          <option value="Bhutan">Bhutan</option>
                                                          <option value="Bolivia">Bolivia</option>
                                                          <option value="Botswana">Botswana</option>
                                                          <option value="Bouvet Island">Bouvet Island</option>
                                                          <option value="Brazil">Brazil</option>
                                                          <option value="British Virgin Islands">British Virgin Islands</option>
                                                          <option value="Brunei">Brunei</option>
                                                          <option value="Bulgaria"> Bulgaria</option>
                                                          <option value="Burkina Faso">Burkina Faso</option>
                                                          <option value="Burundi">Burundi</option>
                                                          <option value="Cambodia">Cambodia</option>
                                                          <option value="Cameroon">Cameroon</option>
                                                          <option value="Canada">Canada</option>
                                                          <option value="Cape Verde">Cape Verde</option>
                                                          <option value="Cayman Islands">Cayman Islands</option>
                                                          <option value="Chad">Chad</option>
                                                          <option value="Chile">Chile</option>
                                                          <option value="China">China</option>
                                                          <option value="Christmas Island">Christmas Island</option>
                                                          <option value="Cocos Islands">Cocos Islands</option>
                                                          <option value="Colombia">Colombia</option>
                                                          <option value="Comoros">Comoros</option>
                                                          <option value="Congo">Congo</option>
                                                          <option value="Cook Islands">Cook Islands</option>
                                                          <option value="Costa Rica">Costa Rica</option>
                                                          <option value="Croatia">Croatia</option>
                                                          <option value="Cuba">Cuba</option>
                                                          <option value="Cyprus">Cyprus</option>
                                                          <option value="Czech Republic">Czech Republic</option>
                                                          <option value="Denmark">Denmark</option>
                                                          <option value="Djibouti">Djibouti</option>
                                                          <option value="Dominica">Dominica</option>
                                                          <option value="Dominican Republic">Dominican Republic</option>
                                                          <option value="East Timor">East Timor</option>
                                                          <option value="Ecuador">Ecuador</option>
                                                          <option value="Egypt">Egypt</option>
                                                          <option value="El Salvador">El Salvador</option>
                                                          <option value="Equatorial Guinea">Equatorial Guinea</option>
                                                          <option value="Eritrea">Eritrea</option>
                                                          <option value="Estonia">Estonia</option>
                                                          <option value="Ethiopia">Ethiopia</option>
                                                          <option value="Falkland Islands">Falkland Islands</option>
                                                          <option value="Faroe Islands">Faroe Islands</option>
                                                          <option value="Fiji">Fiji</option>
                                                          <option value="Finland">Finland</option>
                                                          <option value="France">France</option>
                                                          <option value="French Guiana">French Guiana</option>
                                                          <option value="French Polynesia">French Polynesia</option>
                                                          <option value="Gabon">Gabon</option>
                                                          <option value="Gambia">Gambia</option>
                                                          <option value="Georgia">Georgia</option>
                                                          <option value="Germany">Germany</option>
                                                          <option value="Ghana">Ghana</option>
                                                          <option value="Gibraltar">Gibraltar</option>
                                                          <option value="Greece">Greece</option>
                                                          <option value="Greenland">Greenland</option>
                                                          <option value="Grenada">Grenada</option>
                                                          <option value="Guadeloupe">Guadeloupe</option>
                                                          <option value="Guam">Guam</option>
                                                          <option value="Guatemala">Guatemala</option>
                                                          <option value="Guinea">Guinea</option>
                                                          <option value="Guinea-Bissau">Guinea-Bissau</option>
                                                          <option value="Guyana">Guyana</option>
                                                          <option value="Haiti">Haiti</option>
                                                          <option value="Honduras">Honduras</option>
                                                          <option value="Hong Kong">Hong Kong</option>
                                                          <option value="Hungary">Hungary</option>
                                                          <option value="Iceland">Iceland</option>
                                                          <option value="India">India</option>
                                                          <option value="Indonesia">Indonesia</option>
                                                          <option value="Iran">Iran</option>
                                                          <option value="Iraq">Iraq</option>
                                                          <option value="Ireland">Ireland</option>
                                                          <option value="Italy">Italy</option>
                                                          <option value="Ivory Coast">Ivory Coast</option>
                                                          <option value="Jamaica">Jamaica</option>
                                                          <option value="Japan">Japan</option>
                                                          <option value="Jordan">Jordan</option>
                                                          <option value="Kazakhstan">Kazakhstan</option>
                                                          <option value="Kenya">Kenya</option>
                                                          <option value="Kiribati">Kiribati</option>
                                                          <option value="Korea, North">Korea, North</option>
                                                          <option value="Korea, South">Korea, South</option>
                                                          <option value="Kuwait">Kuwait</option>
                                                          <option value="Kyrgyzstan">Kyrgyzstan</option>
                                                          <option value="Laos">Laos</option>
                                                          <option value="Latvia">Latvia</option>
                                                          <option value="Lebanon">Lebanon</option>
                                                          <option value="Lesotho">Lesotho</option>
                                                          <option value="Liberia">Liberia</option>
                                                          <option value="Libya">Libya</option>
                                                          <option value="Liechtenstein"> Liechtenstein</option>
                                                          <option value="Lithuania">Lithuania</option>
                                                          <option value="Luxembourg">Luxembourg</option>
                                                          <option value="Macau">Macau</option>
                                                          <option value="Madagascar">Madagascar</option>
                                                          <option value="Malawi">Malawi</option>
                                                          <option value="Malaysia">Malaysia</option>
                                                          <option value="Maldives">Maldives</option>
                                                          <option value="Mali">Mali</option>
                                                          <option value="Malta">Malta</option>
                                                          <option value="Marshall Islands">Marshall Islands</option>
                                                          <option value="Martinique">Martinique</option>
                                                          <option value="Mauritania">Mauritania</option>
                                                          <option value="Mauritius">Mauritius</option>
                                                          <option value="Mayotte">Mayotte</option>
                                                          <option value="Mexico">Mexico</option>
                                                          <option value="Moldova">Moldova</option>
                                                          <option value="Monaco">Monaco</option>
                                                          <option value="Mongolia">Mongolia</option>
                                                          <option value="Montserrat">Montserrat</option>
                                                          <option value="Morocco">Morocco</option>
                                                          <option value="Mozambique">Mozambique</option>
                                                          <option value="Myanmar">Myanmar</option>
                                                          <option value="Namibia">Namibia</option>
                                                          <option value="Nauru">Nauru</option>
                                                          <option value="Nepal">Nepal</option>
                                                          <option value="Netherlands">Netherlands</option>
                                                          <option value="New Caledonia">New Caledonia</option>
                                                          <option value="New Zealand">New Zealand</option>
                                                          <option value="Nicaragua">Nicaragua</option>
                                                          <option value="Niger">Niger</option>
                                                          <option value="Nigeria">Nigeria</option>
                                                          <option value="Niue">Niue</option>
                                                          <option value="Norfolk Island">Norfolk Island</option>
                                                          <option value="Norway">Norway</option>
                                                          <option value="Oman">Oman</option>
                                                          <option value="Pakistan">Pakistan</option>
                                                          <option value="Palau">Palau</option>
                                                          <option value="Palestine">Palestine</option>
                                                          <option value="Panama">Panama</option>
                                                          <option value="Papua New Guinea">Papua New Guinea</option>
                                                          <option value="Paraguay">Paraguay</option>
                                                          <option value="Peru">Peru</option>
                                                          <option value="Philippines">Philippines</option>
                                                          <option value="Pitcairn Island">Pitcairn Island</option>
                                                          <option value="Poland">Poland</option>
                                                          <option value="Portugal">Portugal</option>
                                                          <option value="Puerto Rico">Puerto Rico</option>
                                                          <option value="Qatar">Qatar</option>
                                                          <option value="Reunion">Reunion</option>
                                                          <option value="Romania">Romania</option>
                                                          <option value="Russia">Russia</option>
                                                          <option value="Rwanda">Rwanda</option>
                                                          <option value="Saint Lucia">Saint Lucia</option>
                                                          <option value="Samoa">Samoa</option>
                                                          <option value="San Marino">San Marino</option>
                                                          <option value="Saudi Arabia">Saudi Arabia</option>
                                                          <option value="Senegal">Senegal</option>
                                                          <option value="Seychelles">Seychelles</option>
                                                          <option value="Sierra Leone">Sierra Leone</option>
                                                          <option value="Singapore">Singapore</option>
                                                          <option value="Slovakia">Slovakia</option>
                                                          <option value="Slovenia">Slovenia</option>
                                                          <option value="Somalia">Somalia</option>
                                                          <option value="South Africa">South Africa</option>
                                                          <option value="Spain">Spain</option>
                                                          <option value="Sri Lanka">Sri Lanka</option>
                                                          <option value="St. Helena">St. Helena</option>
                                                          <option value="St. Pierre and Miquelon">St. Pierre and Miquelon</option>
                                                          <option value="Sudan">Sudan</option>
                                                          <option value="Suriname">Suriname</option>
                                                          <option value="Svalbard and Jan Mayen Islands">Svalbard and Jan Mayen Islands</option>
                                                          <option value="Swaziland">Swaziland</option>
                                                          <option value="Sweden">Sweden</option>
                                                          <option value="Switzerland">Switzerland</option>
                                                          <option value="Syria">Syria</option>
                                                          <option value="Taiwan">Taiwan</option>
                                                          <option value="Tajikistan">Tajikistan</option>
                                                          <option value="Tanzania">Tanzania</option>
                                                          <option value="Thailand">Thailand</option>
                                                          <option value="Togo">Togo</option>
                                                          <option value="Tokelau">Tokelau</option>
                                                          <option value="Tonga">Tonga</option>
                                                          <option value="Trinidad and Tobago">Trinidad and Tobago</option>
                                                          <option value="Tunisia">Tunisia</option>
                                                          <option value="Turkey">Turkey</option>
                                                          <option value="Turkmenistan">Turkmenistan</option>
                                                          <option value="Turks and Caicos Islands">Turks and Caicos Islands</option>
                                                          <option value="Tuvalu">Tuvalu</option>
                                                          <option value="U.S. Minor Outlying Islands">U.S. Minor Outlying Islands</option>
                                                          <option value="Uganda">Uganda</option>
                                                          <option value="Ukraine">Ukraine</option>
                                                          <option value="United Arab Emirates">United Arab Emirates</option>
                                                          <option value="United Kingdom">United Kingdom</option>
                                                          <option value="United States of America">United States of America</option>
                                                          <option value="Uruguay">Uruguay</option>
                                                          <option value="Uzbekistan">Uzbekistan</option>
                                                          <option value="Vanuatu">Vanuatu</option>
                                                          <option value="Vatican City">Vatican City</option>
                                                          <option value="Venezuela">Venezuela</option>
                                                          <option value="Vietnam">Vietnam</option>
                                                          <option value="Virgin Islands">Virgin Islands</option>
                                                          <option value="Wallis and Futuna Islands">Wallis and Futuna Islands</option>
                                                          <option value="Western Sahara">Western Sahara</option>
                                                          <option value="Yemen">Yemen</option>
                                                          <option value="Yugoslavia (Former)">Yugoslavia (Former)</option>
                                                          <option value="Zambia">Zambia</option>
                                                          <option value="Zimbabwe">Zimbabwe</option>
</select></td>
</tr>
<tr>
  <td class="style1">Upload Image </td>
  <td colspan="4"><input name="phototxt" type="file" id="phototxt" /></td>
</tr>
<tr>
  <td class="style1">&nbsp;</td>
  <td colspan="4"><span class="style1"><img src="CaptchaSecurityImages.php?width=100&height=40&characters=5" align="absmiddle" id="image"/></span></td>
</tr>
<tr>
  <td class="style1">&nbsp;</td>
  <td colspan="4"><label>
    <input type="text" name="textfield" />
  </label></td>
</tr>
<tr>
  <td height="28" class="style1">&nbsp;</td>
  <td colspan="4"><span class="style1"><a href="#" onclick="document.getElementById('image').src = 'CaptchaSecurityImages.php?sid=' + Math.random(); return false">Reload New Image</a></span></td>
</tr>
<tr>
  <td height="28" class="style1">&nbsp;</td>
  <td colspan="4"><span class="style1">
    <input type="checkbox" name="check"  />
  </span>I accept <a href="rules.php" >rules and regulations </a>&nbsp;&nbsp;&nbsp;</td>
</tr>
<tr>
  <td colspan="5" class="style1"><input type="submit" value="Register" name="regBtn"  id="regBtn"  onclick="return validate(document.register);" />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input name="reset" type="reset" value="Clear" /></td>
  </tr>
</table>
   </td>
    </tr>
  <tr>
    <td><img src="images/bottom.jpg" width="509" height="18" /></td>
    </tr>
</table>
</form>
<div id="footer">
<p align="center">&copy;  2007-08. </p> 
</div>
</div></div>
</body>
</html>

```

This is available.php that will recieve user entered string say "john" and process the availability status and print it out.Iam now just printing the value here.[COLOR="Red"]I do get value here but in double clicking on the checkavailability button on the register form.[/COLOR]

```

<?php
		
		echo "Value=".$_REQUEST['user'];
		if(isset($_REQUEST['userID']))
	 	{
		echo "hi";
			if($_REQUEST['userID']!="")
			{
			
				echo "iam inside";
				include("includes/connect.php"); 
				$query="select username from user where username=".$_REQUEST['user'];
				//$query="select username from user where username=".vikas;
				echo $query;
				//echo "request variable=".$_REQUEST['user'];
			$result=@mysql_query($query,$db);			
		
				if($got=mysql_fetch_array($result,$db))
				{
	 			//header("Location:available.php?msg=001");
				//echo "Username not available!!,Please try another.";
				}
				else
				{
					//header("Location:available.php?msg=001");
					//echo "Congratulations!! username available";
				}
		}
}
?>
<html>
<head><title>|| Checking Availability ||  ||</title>
<link rel="stylesheet" href="css/style.css" type="text/css" media="screen" />
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252"><style type="text/css">
<!--
body {
	margin-left: 0px;
	margin-right: 2px;
	margin-bottom: 0px;
}
-->
</style></head>
<body>
<table>
<table>
  <tr>
    <td><img src="images/oneworld.jpg" width="300" height="74" /></td>    
  </tr>
  <tr>
    <td colspan="3"><?php echo $_REQUEST['user'] ?></td>
  </tr>
  <tr>
    <td colspan="3">&nbsp;</td>
  </tr>
  <tr>
    <td colspan="3">
<?php 

 
 		if(isset($_REQUEST['msgcode'])) 
 		{ 
			echo "username notvailable!!"; 
		}
		else
		{
			echo "username available";
		}


 	/*if(isset($_REQUEST['msg']))
		{
			if($_REQUEST['msg']=="001")
			{
				echo "Username not available!!,Please try another.";
			}
			else if($_REQUEST['msg']=="002")
			{
				echo "Congratulations!! username available!!";				
			}
		}*/
?>	</td>
  </tr>
  <tr>
    <td colspan="3">&nbsp;</td>
  </tr>
  <tr>
    <td colspan="3">&nbsp;</td>
  </tr>
  <tr>
    <td colspan="3">&nbsp;</td>
  </tr>
  <tr>
    <td colspan="3">&nbsp;</td>
  </tr>
  <tr>
    <td colspan="3" bgcolor="#FCF8EC">&nbsp;</td>
  </tr>  
  <tr>
    <td colspan="3"><div id="div" class="active">	
      <p align="center" style="font-size:12px">&copy; </p>
    </div></td>
  </tr>
</table>
</body>
</html>

```

---

### Post by supirman on 2008-09-04
Change:

[PHP]	<?php $got=$_POST['username']; ?>
	
<td colspan="4"><input type="text" name="username"/>&nbsp;
  <input type="submit" value="Check Availability" name="avBtn" onclick="return popup('available.php?user=<?php echo $got; ?>','Avaiability Check','width=300,height=350');"/></td>
</tr>
[/PHP]

to this:

[PHP]<td colspan="4"><input type="text" name="username"/>&nbsp;
  <input type="button" value="Check Availability" name="avBtn" onclick="return popup('available.php?user=' + document.register.username.value ,'Avaiability Check','width=300,height=350');"/></td>
</tr>[/PHP]

Change "check availability" to a plain button instead of a submit type.  Also, you can access the username field via the DOM, as in document.formname.fieldname.value (or in your case: document.register.username.value).  Being a plain button, we won't cause a refresh of the page as your original was doing.

Hope that helps.

---

### Post by cszikszoy on 2008-09-04
ivikas:

Read those two links I posted earlier.  If you read them your problem should become apparent.  You aren't using POST correctly.  You *generally* cannot access POST variables on the same page as your actual form.  (Well, unless your form submits its self to the page it's on... but let's not go there.)

As I and others have stated, for POST to be populated, you have to have the following things:

[LIST]
[*]A form - You've got this, great start
[*]The form must use "method=post" - You also have this, good.
[*]The form must have "action=form_process.php" - As your code is right now, your form doesn't "post" anywhere!
[/LIST]
So what I'm trying to say is this.  On your "register.php" page, the POST variable is out of scope.  Therefore, it's completely meaningless to check if post isset.  Furthermore, anywhere you write $_POST[] will not return anything because post isn't populated!  Also, your form on this page should have ```
action="available.php"
``` inside the form declaration tag.
 
On your "available.php" page replace $_REQUEST with $_POST.

Again, read those two links that I posted and all will be clear.

---

### Post by ivikas on 2008-09-04
Hello supirman,

             gr8 it worked thanks

---


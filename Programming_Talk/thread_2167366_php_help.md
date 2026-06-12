---
title: "php help"
date: 2013-08-13
forum: Programming Talk
---

### Post by peter_brickles on 2013-08-13
hi guys heres hoping some one more knowledgable can help me i have altered a php script i found to email me completed web forms from my site. How ever if i change the following line in the code 

> $email_subject = "Contact form submission: $name";

specificly the string Contact form submission  the email is never recieved the whole code is below id be really grateful if any one could offer some advice on this ? 

thanks dunryc 

> 

<?php 

$errors = '';

date_default_timezone_set('Europe/London'); //set the time zone as server isnt in the uk or set to uk 

$date = date('d/m/Y H:i:s'); //date variable 
$ipaddress = $_SERVER["REMOTE_ADDR"]; //get the users ip address into a vairialbe 


$myemail = 'peter.brickles@gmail.com';//<-----Put Your email address here.
$title = $_POST['title'];
$loan_amount = $_POST['loan_amount'];
$loan_purpose = $_POST['purpose'];
$first_name = $_POST['first_name']; 
$surname = $_POST['surname']; 
$postcode = $_POST['postcode'];
$house_number = $_POST['house_number'];
$street = $_POST['street'];
$town = $_POST['town'];
$hometype = $_POST['hometype'];
$home_phone = $_POST['home_phone'];
$mobile = $_POST['mobile'];
$work_number = $_POST['work_number'];

$email_address = $_POST['email']; 





if (!preg_match(
"/^[_a-z0-9-]+(\.[_a-z0-9-]+)*@[a-z0-9-]+(\.[a-z0-9-]+)*(\.[a-z]{2,3})$/i", 
$email_address))
{
    $errors .= "\n Error: Invalid email address";
}

if( empty($errors))
{
    $to = $myemail; 
    $email_subject = "Contact form submission: $name";
    $email_body = "You have received a new loan application. ".
    " Here are the details:\n\n IP Address: $ipaddress  \n Time/Date:$date  \n\n Loan Amount: £$loan_amount\n Loan Purpose: $loan_purpose\n \n Title: $title \n Name: $first_name \n Surname: $surname \n\n Postcode: $postcode \n House Nymber\Name: $house_number \n Street: $street \n Town/City $town \n Home Type: $hometype \n Home Phone $home_phone \n Mobile: $mobile \n Work Number: $work_number \n Email: $email_address "; 
    
    $headers = "From: $myemail\n"; 
    $headers .= "Reply-To: $email_address";
    
    mail($to,$email_subject,$email_body,$headers);
    //redirect to the 'thank you' page
    header('Location: contact-form-thank-you.html');
} 
?>
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd"> 
<html>
<head>
    <title>Contact form handler</title>
</head>

<body>
<!-- This page is displayed only if there is some error -->
<?php
echo nl2br($errors);
?>


</body>
</html>



---

### Post by SeijiSensei on 2013-08-13
> **peter_brickles said:**
> specificly the string Contact form submission  the email is never recieved the whole code is below id be really grateful if any one could offer some advice on this ?thanks dunryc

Can you give a specific example of how you changed the string and the result that change produced?  Otherwise we'll all be shooting in the dark.

---

### Post by Crusty Old Fart on 2013-08-18
I see that you have assigned values to the php variables: $first_name and $surname 
But I don't see a statement anywhere in your code that assigns a value to the variable: $name

  I think you need to assign a value to the variable: $name before you can use it as part of: $email_subject = "Contact form submission: $name"

Right?

Perhaps you intended to have a line of code before you defined the $email_subject variable similar to this:
[php] $name = $first_name . ' ' . $surname; [/php]
This also works:
[php] $name = "$first_name $surname";[/php]

---

### Post by carl4926 on 2013-08-18
Here is a basic php mailer

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Untitled Document</title>
</head>


<body>
<?php 
if(isset($_POST['Submit'])) {
$youremail = 'info@youremail.co.uk';
$fromsubject = 'Enquiry';
$fname = $_POST['fname'];
$lname = $_POST['lname'];
$mail = $_POST['mail'];
$phone = $_POST['phone']; 
$message = $_POST['message']; 
	$to = $youremail; 
	$mailsubject = 'Masage recived from'.$fromsubject.' Contact Page';
	$body = $fromsubject.'
	
	The person that contacted you is '.$title.' '.$fname.' '.$lname.'
	 Phone Number: '.$phone.'
	 E-mail: '.$mail.'
	
	 Message: 
	 '.$message.'
	
	|---------END MESSAGE----------|'; 
echo "Thank you for contacting Linux Solutions . Your Email has been sent successfully.<br/>Go to <a href='/index.html'>Home Page</a>"; 
								mail($to, $subject, $body);
 } else { 
echo "You must write a message. </br> Please go to <a href='/contact.php'>Contact Page</a>"; 
}
?>  
</body>
</html>
```

---


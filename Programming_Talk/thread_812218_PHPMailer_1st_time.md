---
title: "PHPMailer 1st time"
date: 2008-05-29
forum: Programming Talk
---

### Post by Penteado on 2008-05-29
Hi everyone, i've been trying to use PHPMailer to send emails. But i keep getting an error, Ill post the code and the error , hope someone is willing to help me. Thank You in advance

```


<html>
<head>
<title>PHPMailer</title>
</head>
<body>
<?php
 if (!array_key_exists('Submitted',$_POST))
 {
?>
  <form method="post" action="PHPMailer.php">
  <input type="hidden" name="Submitted" value="true"/><br/>
  Mail Server: <input type="text" name="Host" size="25"/><br/>
  If authentication is required:<br/>
  Username: <input type="text" name="Username" size="25"/><br/>
  Password: <input type="password" name="Password" size="10"/>
  <hr/>
  To: <input type="text" name="To" size="25"/><br/>
  From Email: <input type="text" name="From" size="25"/><br/>
  From Name: <input type="text" name="FromName" size="25"/><br/>
  Subject: <input type="text" name="Subject" size="25"/><br/>
  <textarea name="Message" cols="50" rows="10"></textarea><br/>
  Using HTML: <input type="checkbox" name="HTML"/>
  <input type="submit" value="Send Email"/>
  </form>
<?php
 }
 else
 {
	
	require("./PHPMailer/language/phpmailer.lang-en.php");	
  require("./PHPMailer/class.phpmailer.php");
  $To = $_POST['To'];
  $From = $_POST['From'];
  $FromName = $_POST['FromName'];
  $Subject = $_POST['Subject'];
  $Message = $_POST['Message'];
  $Host = $_POST['Host'];
  
  if (array_key_exists('HTML',$_POST))
  {
   $HTML = true;
   $Mail->Username=$_POST['Username'];
   $Mail->Password=$_POST['Password'];
  }
  else
  {
   $HTML = false;
  }
  
  $Mail = new PHPMailer();
     
  $Mail->IsSMTP(); // send via SMTP
  $Mail->Host = $Host; //SMTP server
  
  if (array_key_exists('Username',$_POST))
  {
   $Mail->SMTPAuth=true;
  }
  else
  {
   $Mail->SMTPAuth=false;
  } 
  
  $Mail->From = $From;
  $Mail->FromName = $FromName;
  $Mail->AddAddress($To);
  $Mail->AddReplyTo($From);
  
  $Mail->WordWrap = 50; // set word wrap
  $Mail->IsHTML($HTML);
  
  $Mail->Subject  = $Subject;
  $Mail->Body = $Message;
  
  if($Mail->Send())
  {
   echo "Message Sent";
  }
  else
  {
    echo "Message Not Sent<br/>";
    echo "Mailer Error: " . $Mail->ErrorInfo;
  }
 }
?>
</body>
</html>



```

```


Message Not Sent
Mailer Error: Language string failed to load: connect_host


```

---

### Post by Lau_of_DK on 2008-05-29
Sure, 

Let me quote someone who knows what he's talking about:

> 
This error message -commonly associated with the use of phpMailer- can have different causes (sometimes platform related) and could be a bit hard to troubleshoot if you don't narrow it down.

This is an (incomplete) overview of causes mentioned in the forum and bug tracker:

* A configuration error of the phplist pageroot value in config.php
Ref: [http://forums.phplist.com/viewtopic.php?p=15761#15761](http://forums.phplist.com/viewtopic.php?p=15761#15761)

* An invalid email address in your user list.
Ref: [http://mantis.phplist.com/view.php?id=5385](http://mantis.phplist.com/view.php?id=5385)

* A bug in phpmailer/class.phpmailer.php, which presumably has been fixed by now (since ver. 2.10.3 I believe).
Ref: [http://mantis.tincan.co.uk/view.php?id=4756](http://mantis.tincan.co.uk/view.php?id=4756)

* Another bug discovered in class.phplistmailer.php, when using phpmailer in combination with SMTP. This bug is still valid for ver. 2.10.4 [EDIT: and version 2.10.5]
Ref: [http://mantis.phplist.com/view.php?id=8590](http://mantis.phplist.com/view.php?id=8590)
When using SMTP with a non-standard SMTP port, you may get this error message:
Quote:
Mailer Error: Language string failed to load: connect_host
In this case you might fix this by applying this mod: [http://mantis.phplist.com/view.php?id=11493](http://mantis.phplist.com/view.php?id=11493)
and adding a line similar to this in config.php: $phpmailer_smtpport = '587';

* An incompatibility between phpMailer and Windows/IIS, obviously only relevant if you are on a Windows/IIS platform.
Ref: [http://www.u-g-h.com/index.php/2007/04/27/phpmailer-issue-on-iis/](http://www.u-g-h.com/index.php/2007/04/27/phpmailer-issue-on-iis/)

Most of these reports include suggested fixes. There might be more though, try searching the forum for that error message.

A number of users mentioned that disabling phpmailer in config.php, solved the problem for them.


Hope you figure it out,
/Lau

---


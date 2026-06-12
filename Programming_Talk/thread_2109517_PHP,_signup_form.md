---
title: "PHP, signup form"
date: 2013-01-27
forum: Programming Talk
---

### Post by cesar98026 on 2013-01-27
Hello, I'm running a free public webmail service where users can sign up and login. My signup form is highly flawed, and always is abused by spam bots. I have no input validation, and no MySQL entry checker. I've added a math question, however it does not work properly. I'm fairly new to PHP and need some guidance!
Here is my form:
```
 
<form name="reg" action="code_exec.php" onsubmit="return validateForm()" method="post">
  <p><span style="font-family: Arial;">By clicking submit, you agree to EmailFriend's Terms &amp; Conditions</span> </p>
      <table align="center" border="0" cellpadding="2" cellspacing="0" width="274">
      <tbody><tr>
        <td colspan="2">
        <div align="center"><?php 
 
 $remarks=$_GET['remarks'];
 $num_one = rand() % 10;
 $num_two = rand() & 10;
 $final_num = $num_one + $num_two;
 $_SESSION['answer'] = $final_num;
 $user_answer = $_POST['answer'];
 $real_answer = $_SESSION['answer'];
 
  if ($remarks==null and $remarks=="")
  {echo 'Register Here';}
 
  if ($remarks=='success' and $user_answer = $real_answer)
  {echo 'You are now Registerered! Click Login above to login! :) :P xD -_-';   }
 
 
 
?>
        </div>
 
        <br>
        </td>
      </tr>
 
      <tr>
        <td style="font-family: Arial;">
        <div align="right">Full Name:</div>
        </td>
        <td><input name="lname" type="text"></td>
      </tr>
      <tr>
        <td style="font-family: Arial;">
        <div align="right">Password:</div>
        </td>
        <td><input name="address" type="password"></td>
      </tr>
      <tr>
        <td style="font-family: Arial;" width="95">
        <div align="right">Username:</div>
        </td>
        <td width="171"><input name="fname" type="text"></td>
        <td style="font-family: Arial;" width="95">
        <div align="right">@emailfd.com</div>
        </td>
 </tr>
 <tr>
        <td style="font-family: Arial;" width="95">
        <div align="right"><?php echo $num_one . ' + ' . $num_two . ' = '; ?></div>
        </td>
        <td width="171"><input name="answer" type="text"></td>
        <td style="font-family: Arial;" width="95">
 
        </td>
 </tr>
 
      <tr>
        <td> <br>
        </td>
        <td><input name="submit" value="Submit" type="submit"></td></tr>
    </tbody>
  </table>
</form>

```
 
And my code_exec:
```
 
<?php
session_start();
include('connection.php');
 
$fname=$_POST['fname'];
$lname=$_POST['lname'];
$address=$_POST['address'];
mysql_query("INSERT INTO users(id, name, maildir, crypt)VALUES('$fname@emailfd.com', '$lname', '$fname/', ENCRYPT('$address') );");
mysql_query("INSERT INTO aliases (mail,destination) VALUES
 ('$fname@emailfd.com','$fname@emailfd.com') );");
header("location: index.php?remarks=success");
mysql_close($con);
$to = "[EMAIL="$fname@emailfd.com"]$fname@emailfd.com[/EMAIL]";
 $subject = "Welcome!";
 $message = "blah blah (lots of html)
$headers = 'From: The EmailFriend Team <ask@emailfd.com>' . "\r\n";
 $headers .= 'MIME-Version: 1.0' . "\r\n";
 $headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";
 mail($to,$subject,$message,$headers);
 echo "Mail Sent.";
 
?>

```
 
I seriously need help with security measures :(
Thanks in advance!

---

### Post by lisati on 2013-01-28
I'm not sure what the problem is with your existing code.

For adding security against spambots, you might want to check out [Stop Forum Spam](www.stopforumspam.com), [http://www.block-disposable-email.com/tester_scriptexample.txt](http://www.block-disposable-email.com/tester_scriptexample.txt) and [http://guildwarsholland.nl/phphulp/testspambot.php](http://guildwarsholland.nl/phphulp/testspambot.php) for some ideas.

---

### Post by greenpeace on 2013-01-28
> **cesar98026 said:**
> ...I've added a math question, however it does not work properly...

Hey!

Could you be a little more specific about this part?  ie. What do you expect to happen...  what actually happens, etc :)

Cheers!

---

### Post by SeijiSensei on 2013-01-28
I would never offer a service like yours for exactly the problems you list.  

Unless you are willing to validate every single registration before allowing them to send mail, you'll never solve this problem.  That means having a human look at every registration request and only confirming ones that look legitimate.  I'd also impose some type of quota on the number of messages someone can send per day and a low limit on the number of target addresses per message.  A limit of five messages per day to a maximum of five addressees per message would help restrain serious spammers. But these are all kludges; the fundamental problem remains that a service like yours is inherently insecure without a lot of oversight on your part.

My guess is it won't be long until your SMTP server starts being added to blacklists if it hasn't happened already.

---

### Post by AstroLlama on 2013-01-29
how are the bots abusing the form? are they signing up and sending emails from your service?

---


---
title: "PHP Mail function Help"
date: 2010-09-09
forum: Programming Talk
---

### Post by JustChris21 on 2010-09-09
Hi guys, my php code is...

[PHP]<?php 
if (isset($_REQUEST['email'])) && $_REQUEST['email']!='0'{ 
    $to = "chrisathisemail"; 
    $subject = "Contact Form Enquiry"; 
    $message = $_REQUEST["message"]; 
    $from = $_REQUEST["email"]; 
    mail($to,$subject,$message,$from); 
    header('Location: thanks.php');} 
else{ 
header('Location: error.php');} 
exit(); 
?> 
 
?>[/PHP]

and my html is...

```
<form id="form" action="contactscript.php" method="post">
               <fieldset id="field">
                  <legend id="leg">Contact Form</legend>

                  <span class="formtext"><label for="fname">First Name:</label></span>    <input class="input" id="first" name="first" type="text" size="30" /><br /><br />
                  <span class="formtext"><label for="sname">Surname:</label></span>        <input class="input" id="surname" name="surname" type="text" size="30" /><br /><br />
                  <span class="formtext"><label for="email">Email:</label></span>        <input class="input" id="email" name="email" type="text" size="30" /><br /><br />
                  <span class="formtext"><label for="contac">Contact Number:</label></span>        <input class="input" id="contact" name="contact" type="text" size="30" /><br /><br />
                  <span class="formtext"><label for="message">Message:</label></span>     <textarea id="textarea" name="message" class="input" rows="10" cols="30" >Please Type Your Message Here</textarea><br /><br />
                                                          <input id="submit" class="input" type="submit" value="Send!"  />
                                                                          
               </fieldset>
            </form>
```


Now when I host the site locally through apache (127.0.0.1) it works fine but when its uploaded to my server which is a windows server when I click on the submit button it pops up with a dialogue box to download the file instead of executing the script in the browser.

Any help is really appreciated!

---

### Post by odinfromvalhalla on 2010-09-09
does your windows server has php support installed? if not, the HTTP server (be it apache or IIS) will not recognize the mime type and not interpret the file and will treat it as any other file, giving you option to downalod

---

### Post by JustChris21 on 2010-09-09
Yeah php is installed as my site is/was written using php "includes" which process fine.

---


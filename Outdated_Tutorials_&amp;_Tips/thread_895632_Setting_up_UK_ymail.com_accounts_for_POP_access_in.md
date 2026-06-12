---
title: "Setting up UK ymail.com accounts for POP access in Evolution"
date: 2008-08-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Grez on 2008-08-20
Don't believe that you need an enhanced, paid account to do this. I've had lots of trouble setting it up, however, so I thought I'd post it up here for the benefit of any others who are struggling. These settings work for me!

Assuming you've tried to set up the account already and are experiencing difficulties, do the following:

In Evolution, select

**Edit>Preferences**


In the dialog box select **Mail Accounts** and then select your **ymail.com** account on the right hand side. Click **Edit**

_Click the **Identity** tab_

Enter the name you want your account to be called in the **Name** space

Where it says **Full Name**, enter the outbound name you want to apear on your e-mails.

Enter your ymail.com e-mail address in the appropriate box.

_Click the **Receiving E-mail** tab_

Select **POP** as the** Server Type**

Under Configuration, the **Server** is **pop.mail.yahoo.com:995**
(note that this is .com and not .co.uk)

Enter your full ymail.com e-mail address as your **Username**

Select **SSL encryption** for **Use Secure Connection** and Authentication type is **Password**. Check the **Remember Password** box

_Click the **Sending E-mail** tab_

**Server Type** is **SMTP**

**-edit- Before doing the step below, read the UPDATE (post 2 of this thread). Thank you!**

**Server** is **smtp.mail.yahoo.co.uk** 
(Note this is .co.uk and NOT .com)






Check the **Server requires authentication** box

**Secure Connection** is **No encryption**

**Authentication type** is **PLAIN**

**Username** is your full ymail.com e-mail address

Check the **Remember Password** box.

You should now be able to send and receive e-mails with Evolution using your UK ymail account. 


You can fill in the appropriate settings using the New Account setup procedure if you'rer starting from scratch.

Have fun!

---

### Post by Grez on 2008-09-06
_**UPDATE 05/09/2008**_

Since posting the above item, the SMTP server with the .co.uk extension has refused to function, and you must now put a .com extension onto both server names in order to get the mail to work.

This seems strange as when I originally published the setup instructions, the .com extension didn't work with the SMTP server.

Curiouser and curiouser....

---


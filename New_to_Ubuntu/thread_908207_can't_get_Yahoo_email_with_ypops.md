---
title: "can't get Yahoo email with ypops"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-09-02
I followed all the instructions at [http://www.geocities.com/t_skariah/ypops/](http://www.geocities.com/t_skariah/ypops/) ,and I successfully installed Ypops! in my Ubuntu system. When I try to login to Evolution to get my Yahoo email, it says "please enter password on host smtp.mail.yahoo.com." I typed in the same password that I normally use on the Web version of Yahoo email, and my password is refused. It says "unable to authenticate to SMTP server..bad authentication response from server."

In my Evolution email preferences under Sending Email, I have "Server requires authentication" checked off. Is this correct?

What I should do to get Ypops and Evolution to work together, so that I can get my Yahoo email???

JBA2337

---

### Post by Victormd on 2008-09-02
You do need to have "server requires authentication" checked on. Also, the port is different 466 and your pop settings require a different port as well (996). See the attached image extracted from the yahoo site instructions... You can use these settings directly under evolution and it should work.

---

### Post by JBA2337 on 2008-09-02
Thanks for your suggestion. I am not sure where to insert these port numbers, etc. 

I used "sudo dpkg-reconfigure -fgnome ypops", and I reconfigured ypops to use port 996 for pop.mail.yahoo.com, and I reconfigured ypops to use port 466 for smtp.mail.yahoo.com.

When I tried to login and check my email, I have the same problem; when I put in my password, I am told that I am using an invalid password, but I know for sure that I AM NOT USING THE WRONG PASSWORD.

Here are the specific responses that I get:

I clicked on Send/Receive. Response:
"Please enter the SMTP password for smtp.mail.yahoo.com"
I entered the password. Response:
"Unable to connect to POP server pop.mail.yahoo.com
Error sending password: ERR (Auth) invalid user/password"

Next, Evolution tells me:

"Please enter the POP password for jadamsxx on host pop.mail.yahoo.com"
I entered the password. Response:
"unable to authenticate to SMTP server"
"Bad authentication response from server"

I guess I don't understand exactly where to I put in the information that is displayed in the attachment that you sent with your email.

Any other suggestions???

JBA2337

---

### Post by OrangeCrate on 2008-09-02
Yahoo may be blocking access. I think I read something about that recently, but I can't remember where (*).

Unless their policies have changed, I think they still require you to get Yahoo Mail Plus, to get POP access. It's $19.95 per year.

If YPOPs doesn't work, and your still interested in POP access, see here for details:

[http://mailplus.mail.yahoo.com/](http://mailplus.mail.yahoo.com/)

Edit:

(*) Though I can't find the article I read, regarding Yahoo possibly blocking YPOPS, there is mention of it on the YPOPS Home page:

> I've started working on YPOPs! 0.9.6 to address the numerous bugs plaguing YPOPs! currently. Most of these have been introduced thanks to the changes introduced by Yahoo! over the last few weeks.

[http://ypopsemail.com/](http://ypopsemail.com/)

I would guess, that regardless of what the authors say, from Yahoo's perspective, it's an illegal product.

Anyway, good luck getting it to work.

---

### Post by JBA2337 on 2008-09-02
I finally gave up on using ypops to get my Yahoo email. 

JBA2337

---

### Post by Victormd on 2008-09-02
> **JBA2337 said:**
> I finally gave up on using ypops to get my Yahoo email. 

JBA2337

Did you enable pop support in your yahoo mail? Now you can, and you don't need ypop to access it...

---

### Post by killer_d76 on 2008-11-13
hhmmm mine seems to be working fine, so i created a thread on "How To" right here: 

> [http://ubuntuforums.org/showthread.php?t=980330](http://ubuntuforums.org/showthread.php?t=980330)

---


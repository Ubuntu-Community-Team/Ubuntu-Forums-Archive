---
title: "Ecommerce"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by mregister on 2008-08-27
hello all,

i am new to ubuntu/linux and was just hired as a tech guy for a small company. they are putting their catalog online and are putting an ecommerce site together. they have hired a consulting firm to build the site and it is going to run on an ubuntu/lamp box which i am going to adminstrate. Yikes!! I have for the last couple of weeks built a test sever and installed ubuntu 8.04 with the lamp configuration and added openssh, ssl, and have played around and have become somewhat familiar with navagating around ubuntu and various config files and such. i have setup and then broken openssh, public/private keys, etc. anyway, when i build this thing for production what areas do i need to pay specific attention to? what advice can you guys give me? i have no help except you guys here and i am not even sure what questions to ask. any advice is much appreciated.

thanks to all

---

### Post by tuxulin on 2008-08-27
> . 
i have setup and then broken openssh, public/private keys, etc. anyway, 
when i build this thing for production what areas do i need to pay specific attention to? 
what advice can you guys give me?

with a question like that there are many answers that you can get and probably most would not even relate to your situation. your question is too vague.

good luck
Tuxulin

---

### Post by Thelasko on 2008-08-27
This sounds like a question for [AskSlashdot]("http://ask.slashdot.org/").

---

### Post by ilrudie on 2008-08-27
Do not give anyone who is not an admin root access, especially not developers/testers,  Do not install an x windows environment on a server so developers can use their familiar gui.  Learn how visudo works so you can tightly control elevated access.  Do not give application accounts passwords.  [COLOR=Red]_**ALWAYS**_[/COLOR] have a working copy of the media in case you need to boot from it.  Also don't just auto patch the box.  Once you get a stable working environment patching becomes one of the things that can cause major problems.  Read what every patch does and determine if you absolutely need to run it.  A few times a year schedule time to bulk patch and only do necessary emergency (e.g. major security) patches outside those scheduled times.  Use a promote to productions scheme (test->dev->qa->prod) so you have a good idea if a patch is or isn't going to break the server before you try to apply it to the money maker.  Keep good backups.

These are just good things to do regardless of distro/OS.

---

### Post by mregister on 2008-08-27
thank you ilrudie. i know i have a lot to learn and i look forward to it. i look forward to posting and helping others when i get to where i can.

---

### Post by Zappa12321 on 2008-08-27
As one who just went through this I would recommend the following.

1) Build 2 similar setups One will be your test bed/backup server and the other one will be your live server.

2) Get in the habit of backing up your systems.  (I use rsync and cron to do it.)  

3) When deploying changes to the e-commerce site send it first to the test server and then if everything works correctly then move it over to the live server.  Also only update the live server when you know you have time to fix issues.  Nothing is worse than updating the server when you have no time to fix issues that crop up as it seems that no matter how careful you are that is the time that something unexpectedly breaks.

---

### Post by ilrudie on 2008-08-27
No Problem.  I try to help.

---


---
title: "Very frustrated!!"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by jd66921 on 2008-07-27
Hi,

  I am new to Ubunto.  Now I have decided to experiment with Ubunto as mental stimulation and with the idea that I might switch to it full time.

  Installation was very simple, I overwrote an XP system.  It came up easily, the network works, etc.  So, I tried some of the applications.

  First thing was that I could not see a Windows XP share.  The program seemed to imply that the shared disk should just show up, but it didn't.  I am using the Network File Browser.  I can see the other system but not the shares.  The shares are not passworded.  How do I do that??

  Next was email.  I tried the bundled "Evolution Email".  I filled in the information as best I could.  However, I cannot receive any email.  Worse, the error display window (I assume) disappears before I can read it.  How do you find out what went wrong?  Also, I found no place to set the port numbers required by my ISP (I tried adding them as ":465, etc" after the server name, no luck).  I also never saw a place to enter a password for my account??

  I also tried to run "ekiga".  I assume it is similar to MSN Messenger.  I tried to enter the appropriate infomation, and tried to register my username, with no(?) luck.  One question was for video, but only offered /dev/video or something that was not acceptable to the program.  What now?  NOW, the program says is is already running, but also says registration failed.  It says to enter commands as if I hada terminal open?? 

Overall, I am very frustrated trying this out.  I can browse the internet, and that is all.    Is there any source that can help me through these issues in an understandable fashion?  So far I am not impressed....

Thanks, 

Jeff

---

### Post by RuleMaker on 2008-07-27
> First thing was that I could not see a Windows XP share. The program seemed to imply that the shared disk should just show up, but it didn't. I am using the Network File Browser. I can see the other system but not the shares. The shares are not passworded. How do I do that??
Its called ssh, read [this]("https://help.ubuntu.com/community/SSHHowto").

> Next was email. I tried the bundled "Evolution Email". I filled in the information as best I could. However, I cannot receive any email. Worse, the error display window (I assume) disappears before I can read it. How do you find out what went wrong? Also, I found no place to **set the port numbers** required by my ISP (I tried adding them as ":465, etc" after the server name, no luck). I also never saw a **place to enter a password** for my account??
1) this is how:
pop.someserver.com:port_number
2) you'll be prompted to enter it if evolution successfully connects to the server.

Try pidgin instead of ekiga.

---

### Post by scragar on 2008-07-27
pidgin(or for old versions Gaim) is the MSN messenger replacement.

you can edit far more of evolutions info than it first display's by editing the settings once it's set up(even if it's not set up right, it should say so, or offer the advanced options earlier, but nothing I can do about it.)

---

### Post by stevoo on 2008-07-27
You should be able to see Windows normally.
Try clicking Places -> My computer
On of those should be your win installation and you can go into it. But you cannot change anything in the windows folder.

Know for Evolution Emai , most probably you are filling something wrong. But still i reccomend that you try Thunderbird. I believe it is simpler.

Ekiga, is more like skype for calling. As said above use Pidgin. That is a lot more like msn, and you can include almost all communications there(yahoo, msn, gtalk) 

All of this can be installed from the Synaptic Package manager :)

The dev/video part i didnt understood :)

P.s  - It is Ubuntu , not ubunto :)

---

### Post by sdowney717 on 2008-07-27
use aMSN for a windows MSN messenger clone. aMSN actually has a lot more features

read this for setting up windows network shares, you use samba

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

well actually I just tried this and all I had to do was
click places - connect to server

type in the IP of the machine I want to connect to

a screen comes up and I put in my ubuntu password.

This was connecting to root folder of c on an XP machine with no password required on the XP machine.

---


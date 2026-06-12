---
title: "Ubuntu Login Issues"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by spinozakantnietzsche on 2013-03-28
Let me start off by saying that I wanted to love Linux/Ubuntu. While I primarily run Windows, we have Linux servers at work and I've come to both appreciate and love the usefullness of bash,sed, gre, awk, etc. 

My problems with Ubuntu started not too long after installation. Currently, I am dual booting both Windows 7 and Ubuntu on my laptop. My first few times logging in to Ubuntu were smooth sailing, but now after I select Ubuntu in the boot loader it leads directly to a black screen with a cursor. Ctrl Alt F1-F6 will bring me to tty's but they won't accept my credentials. Ctrl Alt F7 is a black screen and Ctrl Alt F8 leads to a blinking line. Consequently, I am forced to reboot and go to recovery and then to root shell. Here I type 'passwd <my unsername>' and instead of prompting me to type a new password, I am just prompted with a list of printed arguments (-d,-- delete all, -f...,etc) that ostenstibly do nothing when I follow the directions, such as  'passwd -d <username>'. 

I then go back to 'resume' which then brings me to the the login prompt--rather than the black screen! Usually, at this stage my password is rejected. I either have to reboot and go through the same invovled process or type it ten or so times before it finally accepts my credentials--I can type and I am not mentally handicapped so I'm sure that I'm providing the same input every time.

So far this is my life with Ubuntu.

I fear that my situation is ultra specific, but if anyone has experienced anything like this before or has advice it would be much appreciated. Thanks!

Also, I did not perform any updates between when Ubuntu was seemingly working and when I started to experience these issues.

---

### Post by arpanaut on 2013-03-28
This will help get the password thing fixed up:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Do you have the correct graphics driver installed for your system?

---

### Post by spinozakantnietzsche on 2013-03-29
Thanks for the reply arpanaut! While the pyschocats instructions did not work, ' -mount -rw -o remount /' did, allowing me to change my password using 'passwd'. However, booting regularly still results in a flicker and then a black screen and when I try to log in via a tty my (very simple and impossible to mistype) password is rejected. Moreover, logging in via recovery and then resuming boot brings me to the regular login GUI, except instead of requiring a password all I have to do is click on the username and it logs in automatically. Frustrating. I reboot like I regularly would and then black screen again. Repeat.

---


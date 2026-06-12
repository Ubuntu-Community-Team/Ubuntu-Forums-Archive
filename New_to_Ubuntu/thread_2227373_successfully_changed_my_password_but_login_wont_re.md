---
title: "successfully changed my password but login wont recognize it"
date: 2014-06-01
forum: New to Ubuntu
---

### Post by joe110 on 2014-06-01
i realize this has been talked about before but the solution i found on here isn't working.

here's my problem. i was changing my  password in 14.04 LTE. i changed it successfully, apparently, once. i went to change  it again because i didn't like the password. i must have accidentally hit enter in  the middle of changing it and saved a password i immediately forgot.


i can't remember my password but i keep trying to re-enter it. i keep getting:


[B]passwd: Authentication token manipulation error
[/B]
**passwd: unchanged**


so i go to recovery mode on the GRUB and get root. i type:


[B]mount -rw -o remount /
[/B]
**passwd <username>**


then i change my password and it says password successfully updated. i then enter:


[B]sync
[/B]
**reboot -f**


 i reboot to the ubuntu desktop login screen and enter my password. it won't let me enter  my account. the screen kind of flickers and it doesn't do anything. it doesn't even give me an error message as it just loops back to the original login screen.

any suggestions about different things to try to get access back? it keeps saying i've successfully updated my password but my password doesn't do anything. if I enter a wrong password it gives me an invalid login message. is this some difference between authentication and password?

---

### Post by Impavidus on 2014-06-01
Your graphical session crashes as soon as it starts, taking you back to  the login screen. There is no problem with the password. The usual  suspect would be the file **.Xauthority** in your home directory, which, through incorrect usage of sudo, may have become root-owned. **.ICEauthority**  sometimes causes the same problem. Both must be owned by you and have  permissions -rw------- (octal 0600). If you login in the console  (ctrl-alt-F2) or from a root shell (recovery mode), you can check and  fix if needed.

Besides, when you change the password you have to enter it twice, to eliminate errors due to accidental key presses. Still, something could go wrong

---

### Post by deadflowr on 2014-06-01
I don't think that's the right mount command
try 
```
mount -o rw,remount /
```
Of course, I have never tried it the other way, but the one I posted definitely works to remount the file system read/write.

---

### Post by joe110 on 2014-06-01
> **Impavidus said:**
> Your graphical session crashes as soon as it starts, taking you back to  the login screen. There is no problem with the password. The usual  suspect would be the file **.Xauthority** in your home directory, which, through incorrect usage of sudo, may have become root-owned. **.ICEauthority**  sometimes causes the same problem. Both must be owned by you and have  permissions -rw------- (octal 0600). If you login in the console  (ctrl-alt-F2) or from a root shell (recovery mode), you can check and  fix if needed.

Besides, when you change the password you have to enter it twice, to eliminate errors due to accidental key presses. Still, something could go wrong

 I tried **locate .Xauthority **and my home directory doesnt appear to have .Xauthority or .ICEauthority**. **My second user account has both of them in the home directory and their permissions are -rw-------. 

> I don't think that's the right mount command

Yeah, I tried the other version of the mount command too. It didn't work. I'll give it a try again in case I screwed something up.

---

### Post by Robel_Lakwe on 2014-06-01
Thank you this helps a lot !

---


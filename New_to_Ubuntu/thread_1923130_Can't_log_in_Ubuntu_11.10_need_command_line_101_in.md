---
title: "Can't log in Ubuntu 11.10 need command line 101 input"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by Deskjockey on 2012-02-10
While trying to fix my Firefox Sat. update problem I now can't log in. I have my personal files on a separate partition. I assume that I can't just reload Ubuntu and keep my email that is probably on the home directory. Can I copy stuff off the home directory and then re-install Ubuntu on the same partition without formatting and then add those files back in? 
 
 
Anyway, I assume that is too easy so can't be done. Folks give advice that requires going to the Home directory and run some command lines.
 
I made an ubuntu CD and booted and see the directories but can't get there. I tried "cd music" and "cd/music" to see if I could just move around on the CD operating system and can't. I did ls and music is one of the sub directories. How would I get over to the Hard Drive home directory to run the various commands folks suggest to free up my password again. 
 
Thanks
 
 
Deskjockey

---

### Post by Rodney9 on 2012-02-10
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Rodney

---

### Post by Deskjockey on 2012-02-10
Rodney, that looks awesome, the best thing I've seen, however it isn't working for me. It lets me type my new password twice but then I get a response;  Authentication token manipulation error,  followed by password: unchanged. 
 
I also tried the second method but even though I get full permission for the etc folder I don't for the shadow folder so I can't edit.
 
Do I have any options at this point.

---

### Post by Henkdroid on 2012-02-10
Is your home folder on a different partition to your install, e.g when installing, did you use partition 1 for / and another for /home ?

---

### Post by Deskjockey on 2012-02-10
> **Henkdroid said:**
> Is your home folder on a different partition to your install, e.g when installing, did you use partition 1 for / and another for /home ?
 
Yes it is. I used the first one for ubuntu and the second one for all my personal files. 
 
Here is an update and maybe taking this in another direction. When I come to the login page, on the top right I don't get the usual icons such as an envelope and arrow pointing up and down etc. I get time, speaker, and a new one, onscreen keyboard. When this started the first symptom was I couldn't turn off the computer and if memory serves me the reboot-cancel-close (or whatever page) didn't come up so I used the off button. 
 
The next time I couldn't log in and getting a passwd error each try. However doing Rodney's link yet again I lwas able to log in on the terminal and got this result. 
---------------------------
Last log in with time given: date and time given. 

Welcome to Ubuntu 11.10

[LIST]
[*]Documentation: [[COLOR=#0000ff]https://help.ubuntu.com/[/COLOR]]("https://help.ubuntu.com/")[/list]

xxxx@xxxx-System-Product &#8211;Name:~$ [1490.804045] [Hardware Error]: MCO_Status[over|-|-|AddrVICECC]:  Oxd4355c00000000136

I get a bunch of [1490. xxxxxx] hardware errors posted down the page. 

more higher number errors. 
 
Data Cache Error: during L1 linefill from LZ     

Instruction Cache error: copyback Parity/Victim error
Bus Unit error

And and others
---------------------
Now going back to the usual login page I log in and the screen then goes black and comes back with the same login page as it was doing but not with a password error anymore. So this is crashing post login now. I had deleted some applications a little earlier in the day and I suspect that may be the issue. I notice in the Recovery Menu, fsck, that I did yesterday and it said all files were fine. I notice "remount" and wonder what that will do?

Any thoughts welcomed and maybe I need to say this part is solved and repost with the new issue of crashing post log in.

---

### Post by Henkdroid on 2012-02-10
You should be able to reinstall Ubuntu onto the same partition and hes the other one as home, just use the same username, my ubuntu install was deleted once, but all I had to do was install again and choose the home partition as home and all of my settings and preferences were the same, so if it's something wrong with the install you can fix it.

---

### Post by Deskjockey on 2012-02-10
Seems scary. I wish there was a way I could copy my files somewhere incase something goes wrong. How would the first partition that gets wiped clean be able to keep settings and I suspect my email file if it gets wiped during installation? 
 
I was wondering if I set up a second hard drive using the identical ID and Passwords if I would be able to copy stuff from this hard drive or will I still be denied permission.

---

### Post by l0vot on 2012-02-10
You can simply reinstall ubuntu, and use your separate partition as your home directory, just choose "something else" instead of use entire disk, install alongside, or guided when asked by the installer. Also a surefire way to gain access to any unencrypted hard drive is sudo passwd root, and then log in as root (only if you are a sudoer though).

---

### Post by Deskjockey on 2012-02-10
IOvot
 
I'm not sure how I installed it. When I click the folder icon on the left panel the Home folder is the ubuntu folder and my partition that is also listed has all my personal files. I then click through that partition to get to my files.  I suspect I probably didn't call my second partition home because I didn't understand what to do when given a choice. Still not sure what I am suppose to call Home. This is why I suspect my email is probably in the root and not my partition. If I understand you are saying that I do a clean install in my ubuntu partition but somewhere in the process it asks what partition is home and I can select my partition as home and then it will be the main one listed on the left panel rather than me having to click it to get there?

---

### Post by Deskjockey on 2012-02-11
Using Rodney9's link I was able to use my CD and move some files to a stick. I then did a new install. I may have to start another thread to figure out where my emails and bookmards are in those copied files so I can copy it back in. 
 
Thanks for the help guys.

---


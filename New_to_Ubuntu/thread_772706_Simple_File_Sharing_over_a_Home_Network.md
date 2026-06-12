---
title: "Simple File Sharing over a Home Network"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by brucewagner on 2008-04-28
I tried (using Hardy Heron 8.04) simply right-clicking on the folder I want to Share, and there is a new automatic tool.

Right-click...  Then, "Sharing Options".

Unfortunately, I get an error on the "File Manager - Folder Sharing" window...

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Is this a bug?

---

### Post by bodhi.zazen on 2008-04-28
Sounds like a permissions error. What directory are you trying to share and do you own it?

---

### Post by brucewagner on 2008-04-28
I was just testing/experimenting with it...  So it was my own HOME folder I was attempting to Share.

HOWEVER, I tried again just now and I get the same exact error when I try to share my own DOCUMENTS folder inside my home folder.

Also, I get that same error whether I "Allow other people to write in this folder", or Not...

---

### Post by bodhi.zazen on 2008-04-28
There is a bug report here :

[https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/215810)

See the very last post first, basically open nautilus, right click on a folder, install samba server. They then say you will need to log out and back in or reboot and your share should work.

If that fails, read the other comments first, try some of the other solutions listed, and if that fails, add to the bug report.

I can not give better advice at the moment as samba worked for me out of the box :confused:

---

### Post by bodhi.zazen on 2008-04-29
Just a follow up : I just tried this, got the same error, and logging out and back in indeed is the solution.

---

### Post by hyper_ch on 2008-04-29
whom do you want to share with? Other Linux computers or accross different OSes?

---

### Post by Deeta on 2008-04-29
When you get it to work, take care not to check the 'other' people checkbox when you try to share your home folder;-)
What will happen is:

-Nautilus will ask you to change permissions
-next time you start X gdm disallows you to login as other people can 'write' to your home directory
-super newbie friendly recovery console happy time ensues.

I managed to lock myself out of gnome this way. And if it were not for a secondary computer where I asked for help in the forums it would have been the end of my fun with Ubuntu ;-)

---

### Post by MagicMoonLight on 2008-05-05
****:)Don't Worry Don't Worry I have an easy temporary solution until for the file permission denial on sending files until they fix Samba.

:KS If Cut/copy does not work to send a file to your network share(or a computer on your local area network) just use drag and drop it works like a charm.:lolflag:

Hint: In hardy when you access your network share(folder) it mounts on the desktop just drag your file you want to send over the folder on the desktop and drop it in.

Cut/copy to network share not working
Cut/copy from network share works correctly
Drag and Drop to network share works correctly
Drag and Drop from network share works correctly

:) Good luck to all you wonderful Linux users.

---

### Post by janmartin on 2008-07-24
Hi,

how to do this "log out and then login again" with a live CD? 
I cannot install on the PC.

Thanks.

---

### Post by janmartin on 2008-07-24
I wrote a short explanation how to copy files using openssh instead of samba.

[http://ubuntuforums.org/showthread.php?p=5448464#post5448464](http://ubuntuforums.org/showthread.php?p=5448464#post5448464)

Good Luck.

---

### Post by HwyXingFrog on 2008-08-29
What is the command line command to open my list of shared folders in ubuntu?

I don't remember what it is, but if you do sudo <whatever the command is to run shared folders> then you can add/remove any you want.

---

### Post by shjoity on 2008-09-21
> **Deeta said:**
> When you get it to work, take care not to check the 'other' people checkbox when you try to share your home folder;-)
What will happen is:

-Nautilus will ask you to change permissions
-next time you start X gdm disallows you to login as other people can 'write' to your home directory
-super newbie friendly recovery console happy time ensues.

I managed to lock myself out of gnome this way. And if it were not for a secondary computer where I asked for help in the forums it would have been the end of my fun with Ubuntu ;-)

you can change these security settings i believe(i have not tried) in admin-->login, the last tab

---

### Post by tigerg on 2012-02-04
I am pretty well fed-up with this error. I can't get Ubuntu to share the damn files throught Nautilus. I get the 255 error whenever I use the share tab on any disk or folder. What a useless thing it is to get a numeric error without a link to a help file or even a clue. I have searched these forums for help and it ain't helpin.

---

### Post by Morbius1 on 2012-02-04
> 'net usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.You talking about that error?

If you do a:
```
ls -dl /var/lib/samba/usershares
```You should find out:
> drwxrwx--T 2 [COLOR=Blue]root sambashare[/COLOR] 4096 2012-01-11 17:49 /var/lib/samba/usersharesNow run the following command:
```
id
```You should see that you either are or are not a member of the sambashare group.

If you are not then add yourself:
```
sudo gpasswd -a your-user-name sambashare
```Then logout ( not reboot ) and login again and then try to share a folder.

* Usershare has what I believe to be the very best error messages in all of software-dom.*

---


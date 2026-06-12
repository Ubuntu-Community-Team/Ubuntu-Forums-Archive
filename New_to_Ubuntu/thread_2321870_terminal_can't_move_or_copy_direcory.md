---
title: "terminal can't move or copy direcory"
date: 2016-04-25
forum: New to Ubuntu
---

### Post by liamcoded on 2016-04-25
Hi I am following directions I found at this forum but they don't work.
I am trying to move a directory from downloads folder to icons folder.
Drag and drop doesn't work, it says I have no permission. Also, copy/paste is grayed out.

I tried following command in terminal but it doesn't work.
sudo mv /Downloads/captiva-icon-theme-master /usr/share/icons

I get the following message.
mv: cannot stat '/Downloads/captiva-icon-theme-master': No such file or directory

Adresses for these directories when open with right click "open in Terminal"
/Downloads
/usr/share/icons

Could anyone help me?

---

### Post by deadflowr on 2016-04-25
/Downloads doesn't exist, or at least not normally.
You have a Downloads folder, but the address is /home/user/Downloads
try:
```
sudo mv ~/Downloads/captiva-icon-theme-master /usr/share/icons/
```
the tidle ~, represents the user's home directory in short form, so to speak.

---

### Post by haplorrhine on 2016-04-25
You probably can't move it via the file manager because of insufficient permissions, which can be changed via chmod.  One way to see permissions (rwxrwxrwx):

ls -l ~/Downloads/

ls -l ~/Downloads/ | grep captive-icon...

---

### Post by liamcoded on 2016-04-25
Thank you deadflowr, unfortunately that hasn't worked. I think haplotthine might be right about not having insufficient permissions.

---

### Post by liamcoded on 2016-04-25
Hi haplorrhine. thank you for your response. You might be right. Unfortunately, I am brand new to Terminal and Bash.
"ls -l ~/Downloads/" gives me:
drwxrwxr-x 3 liamcoded liamcoded    4096 Sep 20  2014 captiva-icon-theme-master

"ls -l ~/Downloads/ | grep captive-icon-theme-master" Does nothing. I assume, I am missing some part of that command.

If it's not too much trouble could you let me know how to change permissions issue, or at least where I could find more about this. I don't know even what to search for in Google. 

Also, it's my laptop, but I was playing around with having it encrypted so I am not sure if that might be it. I don't need any encryption, it's just something I am trying to learn about.

**Update**, full code as it is:

```
[INDENT]liamcoded@toshiba1604lts:~$ ls -l ~/Downloads/
total 11248
drwxrwxr-x 3 liamcoded liamcoded    4096 Sep 20  2014 captiva-icon-theme-master
-rw-rw-r-- 1 liamcoded liamcoded 9863388 Apr 25 00:24 captiva-icon-theme-master.zip
drwxr-xr-x 2 liamcoded liamcoded    4096 Mar 21 11:11 lplinux
-rw-rw-r-- 1 liamcoded liamcoded 1623477 Apr 25 13:24 lplinux.tar.bz2
[/INDENT]

```

I really appreciate your help.

---

### Post by liamcoded on 2016-04-25
I can't install anything. Well, at least, security works.:D
I can't install LastPass.

---

### Post by howefield on 2016-04-25
Just a little tip, it is often more helpful to copy the entire input and output of your terminal and paste it back here, placed between code tags, eg..

```
hugh@wily-laptop:~$ ls -l ~/Downloads/
total 20
-rw-rw-r-- 1 hugh hugh 8426 Apr 22 15:32 freshplayerplugin_0.3.5-1-webupd8-xenial-2_all.deb
drwxrwxr-x 2 hugh hugh 4096 Apr 12 10:21 Telegram
hugh@wily-laptop:~$ 
```

Makes it much easier for others to eliminate the obvious and or user errors :)

---

### Post by liamcoded on 2016-04-25
Thank you for the tip :)

```
[INDENT]liamcoded@toshiba1604lts:~$ ls -l ~/Downloads/
total 11248
drwxrwxr-x 3 liamcoded liamcoded    4096 Sep 20  2014 captiva-icon-theme-master
-rw-rw-r-- 1 liamcoded liamcoded 9863388 Apr 25 00:24 captiva-icon-theme-master.zip
drwxr-xr-x 2 liamcoded liamcoded    4096 Mar 21 11:11 lplinux
-rw-rw-r-- 1 liamcoded liamcoded 1623477 Apr 25 13:24 lplinux.tar.bz2
[/INDENT]

```

---

### Post by $yl9pAR%t on 2016-04-25
Check if you are in sudo group, give us the output of:

```
groups liamcoded
```

---

### Post by liamcoded on 2016-04-25
Here it be:

```
liamcoded : liamcoded adm cdrom sudo dip plugdev lpadmin sambashare
```

---

### Post by steeldriver on 2016-04-25
> **liamcoded said:**
> Thank you deadflowr, unfortunately **that hasn't worked.** 

Hasn't worked **how**, exactly? The command that deadflowr suggested should have either worked, or produced an error message - if that's the case, please post the message.

---

### Post by liamcoded on 2016-04-25
Hi steeldriver, this is what I type in and get.

```
[INDENT]liamcoded@toshiba1604lts:~$ sudo mv ~/Downloads/captiva-icon-theme-master /usr/share/icons/
[sudo] password for liamcoded: 
liamcoded@toshiba1604lts:~$
[/INDENT]

``` 

I assume theme should show in System Settings and Unity Tweak Tool, but they are not there. There are Ambiance, High Contrast, and Radiance themes. System Settings shows just those three and UTT shows those three and additional versions for Ambiance and Radiance.

edit: I do use the same password I set for login.

I tried repeating the command and the whole thing says.

```

liamcoded@toshiba1604lts:~$ sudo mv ~/Downloads/captiva-icon-theme-master /usr/share/icons/
[sudo] password for liamcoded: 
liamcoded@toshiba1604lts:~$ sudo mv ~/Downloads/captiva-icon-theme-master /usr/share/icons/
mv: cannot stat '/home/liamcoded/Downloads/captiva-icon-theme-master': No such file or directory
liamcoded@toshiba1604lts:~$ 

```

---

### Post by steeldriver on 2016-04-25
The first command didn't produce an error, so it **did **work - which is why the it didn't work the second time (the directory was already gone - to its new location)

if you are unable to load the icons that's a different problem from the original "terminal can't move or copy direcory"

---

### Post by $yl9pAR%t on 2016-04-25
After you have moved your directory "captiva-icon-theme-master" from your "Downloads" directory to another place, you cannot do it again, because it is not in "Downloads" anymore, is it? Check manually using file manager if is it in /usr/share/icons?

You can also do it in terminal using this command:

```
ls /usr/share/icons
```

---

### Post by CantankRus on 2016-04-26
Way too complicated.....you just moved the wrong folder.
Did you look at the **README.md** file after you extracted the downloaded zip file?
> unzip and place **Captiva** folder to
/home/user_name/.icons
or
/usr/share/icons
The theme folder "Captiva" is in the "captiva-icon-theme-master" folder.
[ATTACH=CONFIG]268641[/ATTACH]

As you appear to have moved the  "captiva-icon-theme-master" folder  using deadflowr's command in post#2,
this command should move the "**Captiva**" folder to **/usr/share/icons** 
```
sudo mv /usr/share/icons/captiva-icon-theme-master/Captiva /usr/share/icons
```
The theme should now be visible in your tweak tool.

---

### Post by liamcoded on 2016-04-26
You are right. I have no idea why it wasn't there yesterday. I probably just didn't see it.

---

### Post by liamcoded on 2016-04-26
Thank you for the replay, issue has been solved. 

Although, I couldn't find directory "/home/user_name/.icons". I made sure that hidden files are displayed but I can't find ".icons". I guess it doesn't matter anymore, It worked out at the end. Thank you.

---

### Post by liamcoded on 2016-04-26
Thank you all for responding and your help. Issue has been solved. 
I just got to see how to mark this thread solved.

---

### Post by CantankRus on 2016-04-26
> **liamcoded said:**
> Thank you for the replay, issue has been solved. 

Although, I couldn't find directory "/home/user_name/.icons". I made sure that hidden files are displayed but I can't find ".icons". I guess it doesn't matter anymore, It worked out at the end. Thank you.
The ~/.icons directory doesn't exist by default. ( "~" is short for /home/username ..eg for me it is  /home/glen ...for you  **/home/liamcoded**)

Moving  the icons into** /usr/share/icons** makes them available to all users.
In most cases you only need to move them into **~/.icons** after creating the directory.
The benefit of placing in  **~/.icons** is you don't need elevated permissions to move and the theme will be backed up when you back up your home folder.

---


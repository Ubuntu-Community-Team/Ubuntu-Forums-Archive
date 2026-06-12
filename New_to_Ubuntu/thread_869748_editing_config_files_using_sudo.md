---
title: "editing config files using sudo?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by timsmith on 2008-07-25
Hi, 

I want to try to use Mutt to view my gmail.  Trouble is I've not got a clue how to use the sudo commands except to say that they are for administrative purposes.  I've read through the wiki which says that anything can be done using sudo.  I need to add lines to /etc/ssmtp/ssmtp.conf  (as explained in [http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)) I have opened this file in text editor but I cannot save the file because I am not 'root' and cannot save to filesystem....  I think I need to use sudo somehow and I've searched the forums and used google but I'm still confused as to how to use the command line... 

Sorry, I think I've been windozed for far too long... :-(

Thanks in advance!

Tim

---

### Post by quibbler on 2008-07-25
Code:

gksudo gedit /etc/ssmtp/ssmtp.conf 


regards quibbler

---

### Post by SunnyRabbiera on 2008-07-25
sudo doesnt do much on its own, thus why people suggest typing in further commands.

---

### Post by iaculallad on 2008-07-25
> **quibbler said:**
> Code:

sudo gedit /etc/ssmtp/ssmtp.conf 


regards quibbler

Make it a practice to use gksudo when invoking GUI-based applications to perform changes w/c needs privileges.

```
gksudo gedit /etc/ssmtp/ssmtp.conf
```

And stick to sudo when using terminal commands w/c needs privilege.

```
sudo vi /etc/fstab
sudo nano /boot/grub/menu.lst
```

---

### Post by Iceni on 2008-07-25
> **timsmith said:**
> Hi, 

I want to try to use Mutt to view my gmail.  Trouble is I've not got a clue how to use the sudo commands except to say that they are for administrative purposes.  I've read through the wiki which says that anything can be done using sudo.  I need to add lines to /etc/ssmtp/ssmtp.conf  (as explained in [http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)) I have opened this file in text editor but I cannot save the file because I am not 'root' and cannot save to filesystem....  I think I need to use sudo somehow and I've searched the forums and used google but I'm still confused as to how to use the command line... 

Sorry, I think I've been windozed for far too long... :-(

Thanks in advance!

Tim

Let me try to explain. As I understand, you don't get the concept of sudo.

In windows (XP) you are usually administrator, and all the time full access and every right over your system.

However, in Ubuntu you are a user, lacking the right to make changes that could potentially harm your system. Basicly you are only allowed to change files in your /home/ directory and make safe system changes like changing wallpaper or similar harmless actions. 

Here is the brilliance of sudo. When you use "sudo" before a command and then type your password, you are the administrator for a short time (I belive 15 min). So to install programs, change files outside your /home/ or change potentially critical settings, you need to be root - use sudo.

I hope this helps:)

---

### Post by timsmith on 2008-07-25
Great, I think I'm starting to get it.  Thanks

The next issue I have is that I need to reset the file permissions for the file

~/.fetchmailrc

I'm using

chmod 600 ~/.fetchmailrc

however, i get the following error message:

chmod: changing permissions of `/home/administrator/.fetchmailrc': Operation not permitted

any ideas why this isn't permitted?

Thanks again!

---

### Post by aeiah on 2008-07-25
are you sure .fetchmailrc exists first? files beginning with a . are hidden. in nautilus you can see hidden files by hitting ctrl+h, or you could use the 'ls -a' command on the command line.

if it doesnt exist you'll have to create it first.
```
touch .fetchmailrc
```

im only saying it because from a google it seems to not exist and you have to create it first, then chmod 600.

additionally, you dont need to specify your home directory with ~/ if you're there already. by default in a terminal you start off in your home directory

---

### Post by t0p on 2008-07-25
> **timsmith said:**
> 
The next issue I have is that I need to reset the file permissions for the file

~/.fetchmailrc

I'm using

chmod 600 ~/.fetchmailrc

however, i get the following error message:

chmod: changing permissions of `/home/administrator/.fetchmailrc': Operation not permitted

any ideas why this isn't permitted?


When an operation is "not permitted", this is generally a time to use sudo. Files in your home directory generally belong to you, so I don't know why you can't edit ~/.fetchmailrc.  But still, try
```
sudo chmod 600 ~/.fetchmailrc
```

---

### Post by andrew.46 on 2008-10-23
Hi timsmith:

> **timsmith said:**
> The next issue I have is that I need to reset the file permissions for the file

~/.fetchmailrc

I'm using

```
chmod 600 ~/.fetchmailrc 
```

however, i get the following error message:

chmod: changing permissions of `/home/administrator/.fetchmailrc': Operation not permitted

any ideas why this isn't permitted?

I have altered this guide a little to give the command lines for creating and modifying these files. Sorry for leaving the instructions a little confusing :-).

If you have not already solved this, the results shuld be similar to this:

```
andrew@skamandros:~$  ls -l $HOME/.fetchmailrc
-rw------- 1 andrew andrew 746 2008-10-22 22:34 /home/andrew/.fetchmailrc

```

   Andrew

---


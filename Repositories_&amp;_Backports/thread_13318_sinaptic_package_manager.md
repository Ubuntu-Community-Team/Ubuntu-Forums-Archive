---
title: "sinaptic package manager"
date: 2005-01-30
forum: Repositories &amp; Backports
---

### Post by sanman_nor on 2005-01-30
the last few things I have tried to install have not worked all errors 
I get a errors were encountered wile prosesing samba

what should I do

---

### Post by az on 2005-01-30
Do you have broken symlinks in rc2.d or something like that?  This is a known bug involving the network administration tool and usb wireless devices.

Is this the case?

[https://bugzilla.ubuntu.com/show_bug.cgi?id=2492](https://bugzilla.ubuntu.com/show_bug.cgi?id=2492)

if so:
Quote:
 could now finally update my samba package.

I have removed the two broken links:
/etc/rc2.d/K09samba
/etc/rc3.d/K09samba

and then I have created two new links:
ln -s /etc/rc2.d/K09samba /etc/init.d/samba
ln -s /etc/rc3.d/K09samba /etc/init.d/samba

and then I went again to synaptic and make the update and it worked, but it has
done many operations, but now it seems all is OK, I know that this doesn't solve
the bug, but at least we can update samba without any problem and know the
package is no more broken.

---

### Post by sanman_nor on 2005-02-09
so how would I go about doing this I am new  to linux and very little about it,  (learning  slowly)

---

### Post by drasko on 2005-02-13
> I have removed the two broken links:
/etc/rc2.d/K09samba
/etc/rc3.d/K09samba
go to the console and go to the /etc/rc.2 directory with cd cmmand.
remove file with rm command (rm K09samba). Then make soft link with ln -s command, as explained. same for the other file...
That's soppose to be all...

Alaso, to do this operations you'll probbably have to be a root, so du it from the root console, or su to root with command su -

Drasko

---

### Post by sanman_nor on 2005-02-15
first thank you so much
by console do you mean termanal 
if not how do I get to it

---

### Post by drasko on 2005-02-16
Yes, console or terminal - that's the same thing... That;s a place where the most of admin activities are gonna happen...  :grin: 
To get to console find the option in Gnome saying Terminal. If you need superuser privilegies for the job write `sudo' before the command. Example:```
$sudo cp foo /boot/bar
```  or something similar...
Haveing no root or superprivileged use in Ubuntu is a security issue. Sudoers are listed in /etc/sudoers file, so you can read more about that in a man pages. In Debian you would become root with su - command or go directly to the root shell from Gnome. Here, sudo is a better solution.
    Anyway, with sudo in front of the command you shuld do this tasks of removing and linking.

One more thing - there are many virtual console (terminals) you can open simultaniously. Not only from Gnome - try pressing Alt+Ctrl+F2, F3, and so on... Alt+Ctrl+F1 is a console in which you are currently logged on - in which you booted the system (try and see), and to go back in Gnome press Alt+Ctrl+F7.

 You can do any of the admin jobs in any of the terminals - effects will be the same...

Drasko

---

### Post by sanman_nor on 2005-02-20
ok so I go to  the root terminal 
and I type 
sudo cd /etc/rc.2 
and it comes up with no such file or directory, what am I doing wrong 

i also tried this in the vertual console that opens up with ctrl alt F1 with the same resolts 
thank you again for your help it is much apresheated, it is helping me learn

---

### Post by drasko on 2005-02-20
not rc.2 but rc2.d

You can see what files and directories are in /etc folder by issuing a command ls. That will give you a list of files... So, ```
cd /etc
``` and then say: ls
So then you'll se those rc directories. To go to them just say cd <dir> -  for example cd rc2.d

Also, for changing the directories (cd) you really don't need to be superuser (no sudo needed). You need superuser privilegies only when you want to copy or delete or move etc.. various protected files (like those in rc2.d)... so no reason for sudo cd /etc, just cd /etc will do.

Drasko

---

### Post by sanman_nor on 2005-02-20
thanks now I have no errors when loading programs
you guys are awsome

---

### Post by drasko on 2005-02-20
Glad to help...
Since you are new to Ubuntu, I reccomend you to read Unofficial Ubuntu Starter Guide, URL: [http://ubuntuguide.org/](http://ubuntuguide.org/) 
there you will find a lot of useful information... After learning a few first steps I guess you'll be suprised what is the power of Ubuntu, GNU and Linux... And it's fun also  :wink: 

See you,
Drasko

---


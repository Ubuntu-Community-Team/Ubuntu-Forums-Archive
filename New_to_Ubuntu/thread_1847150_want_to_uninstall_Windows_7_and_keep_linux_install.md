---
title: "want to uninstall Windows 7 and keep linux installed"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by Salahuddin on 2011-09-20
Hi guys 
I had first installed ubuntu 11.04 three weeks ago , and still using windows 7 
When i open my laptop the system let me choose between linux and windows 7.
now i want to uninstall windows 7 and keep working on ubuntu

and there are some stuff i don't understand in ubuntu :

 * when opening any partition or folder there are some files i don't want to be shown like 
autorun.inf  --- pagefile.sys --- vydsma.pif 
i think that these are system files and i want them to be hidden as in windows 
 
*In ubuntu to open any partition i have to open my "home" folder then open my "computer" then choose the partition i want .. but in windows i just have to press Ctrl + E to open my computer directly without any "my computer" on my desktop .. is there any hot key in ubuntu to do that ?

thanks for help

---

### Post by sadaruwan12 on 2011-09-20
Welcome to the ubuntu world,

It seems like you're a beginner in this field do I recommend that you keep your windows a little bit longer.

So to remove your windows use Gparted and delete your windows partition but please backup before you do this just in case.

Now run
```
sudo update-grub
```

this'll update your grub menu appropriately.


And to your second question,

Well in windows when you open my computer you'll see your partitions and from there you can access your files.

But in Linux we don't have that what we have is mount points and they look like folders when they show up in you computer.

In windows even if you've access to the system you cant do anything and also you are allowed to store files any where but linux don't do that Linux gives a specified area know as home folder store all your personal stuff so there's no need to go to computer file system are unless you want to modify the system.

And also isolating your files from system keeps the system out of harms way and giving you all the space to play with your settings and file.

And the files you mentioned is windows system files and the Autorun.inf is a virus file that runs only on windows that enables a virus to be run when you double click on a USB or on a HDD partition.

Hope this helps.

---

### Post by smurphy_it on 2011-09-20
As for the "hiding of files", when you are viewing them in your file manager (probably nautilus) you could hit the combo Ctrl-h.  That toggles the view of hidden files (on or off).

---

### Post by Salahuddin on 2011-09-20
Thanks for your advice
although i had started using linux just three months ago , i like it too much and i want to uninstall windows 7 cause i don't use it at all . so what i have to do to unistall win7
In fact i don't know what is that "grub"  is  and how to delete the windows partition and if so will it be removed totally or there will be some files remained ??? please explain ?

thanks .

---

### Post by josephmills on 2011-09-20
to hid a file just put a dot in front of it say I had a folder called "top-secret.txt " And I wanted to his it I would just rename it to .top-secret.txt     and that will hide it for you. hope that this helps.

as far as deleting you doz partition open gparted and remove it 
[http://www.youtube.com/watch?v=5Uaa546TmTM](http://www.youtube.com/watch?v=5Uaa546TmTM)
[https://help.ubuntu.com/community/GParted](https://help.ubuntu.com/community/GParted)

---

### Post by josephmills on 2011-09-20
> **Salahuddin said:**
> Thanks for your advice
although i had started using linux just three months ago , i like it too much and i want to uninstall windows 7 cause i don't use it at all . so what i have to do to unistall win7
In fact i don't know what is that "grub"  is  and how to delete the windows partition and if so will it be removed totally or there will be some files remained ??? please explain ?

thanks .

if you would like some ubuntu lessons I am setting a website just for that. check it out [http://www.ourshare.tk](http://www.ourshare.tk)

---

### Post by Mark Phelps on 2011-09-20
> **Salahuddin said:**
> ... now i want to uninstall windows 7 and keep working on ubuntu

Do you remember HOW you installed Ubuntu, specifically, whether you used Wubi?  Because, if you did, then removing Win7 removes Ubuntu as well.

If you're not sure, in Ubuntu, open a terminal and enter "sudo fdisk -lu" (that's a Lowercase L, not a one).  That will list out the partitions on your drive.  If they are all Windows filesystems, then you installed via Wubi and can't just remove Win7.

---

### Post by Salahuddin on 2011-09-22
i typed the command and the output is in the attachments .. 
guys .. i don't want to remove the partition or resize it .. i want to uninstall windows 7 from roots not by removing the partition only.. i think if i just removed the partition there would be some small files in the other partitions .. am i right ?

thanks

---

### Post by westie457 on 2011-09-22
Hi, to help us to help you could you boot into your Ubuntu system or a Live Desktop from a CD then open Firefox and go to this [site]("http://bootinfoscript.sourceforge.net/") to download and run 'bootinfoscript'. Instructions for using and posting are given on the site.

We would like to see all the output of the script mainly because all of your partitions are NTFS and at the moment only you know which is which.

---

### Post by Salahuddin on 2011-09-22
How to install grub with terminal ???

---

### Post by Mark Phelps on 2011-09-22
Your screenshot shows you installed Ubuntu using Wubi -- which treats it like any other Windows app.  If you remove Win7, you will remove Ubuntu as well.  And since you have to use the Win7 loader to launch Ubuntu, you can't remove the Win7 system files, either.

So, ignore the advice of everyone telling you to use GParted to remove the Win7 partition.  They didn't bother to check with you first to see if this was a Wubi install.

You would have to FIRST, move the Ubuntu install out of Windows into its ownn partition.  The Wubi guide, linked below, has instructions on how to do that:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

See section 8.8.

---

### Post by JKyleOKC on 2011-09-22
+1 to Mark's advice. The "wubi" installation is meant to make it easier for Windows users to try Ubuntu, but although it looks completely separate to you, it's completely inside a single Windows file so if you remove Windows, your Ubuntu will disappear along with it!

You can copy your complete Ubuntu installation to a USB drive or external HD, then reinstall it from the Live CD to use the entire drive. This will get rid of everything that's now on your drive; you can then copy your original installation back. For details, see the link that Mark gave.

Welcome to the group!

---


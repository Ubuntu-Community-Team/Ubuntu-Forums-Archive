---
title: "HOWTO Double Click Install of .RPM Packages"
date: 2006-02-14
forum: Outdated Tutorials &amp; Tips
---

### Post by %hMa@?b&lt;C on 2006-02-14
This is mostly (ok, almonst word for word, but its for rpms:KS ) taken from here [http://ubuntuforums.org/showthread.php?p=637765#post637765](http://ubuntuforums.org/showthread.php?p=637765#post637765)
ok, here goes.
first you want the package alien
```
sudo apt-get install alien
```
this package will allow you to change rpms to debs and so on and so fourth.

next: Open Applications>System Tools>Applications Menu Editor
next: Click System Tools then New Entry
next:Create the Entry as Follows

```
Name: RPM Installer
Comment: (blank)
Command: sudo alien -i
Icon: No Icon (or choose one that you like, i like the picture of tux :))
Check the box that says run in terminal
```

then:Right Click on a .rpm file and select Properties (if you dont have one, download one here [http://www.grisoft.cz/softw/70/filedir/inst/lnx_lws_stf__7_1-23.dir/avglinux-7.1-23_avi0672.i386.rpm](http://www.grisoft.cz/softw/70/filedir/inst/lnx_lws_stf__7_1-23.dir/avglinux-7.1-23_avi0672.i386.rpm))

Click Open With then Add. Select RPM Installer from the menu and click add.

next Make sure that "Open With" now has RPM Installer selected (select it if it hasn't) then click close

Open Applications>System Tools>Applications Menu Editor again. Then System Tools. Uncheck the checkmark near RPM Installer (this will remove it from the visible menu while keeping the necessary .desktop file)

Test by double clicking the .rpm package. A terminal will open, ask for your password, then install the package.

Assuming it all went smoothly, you should be all set.

---

### Post by Cariboo1938 on 2007-01-30
> **jeffc313 said:**
>  .......Assuming it all went smoothly, you should be all set.Try to revive the thread!
Hi jeff, I wonder if your HOWTO would work with an Edgy-Ubuntu6.10-amd64 system too???

---

### Post by yopnono on 2007-01-30
Add -c to include scripts from the rpm as well, recommended.

---

### Post by Cariboo1938 on 2007-01-30
> **yopnono said:**
> Add -c to include scripts from the rpm as well, recommended.Thanks yopnono!
As I'm a bit slow and not really an Linux expert, I need to know where to add the -c. Maybe you find a minute to give me more details on that.

---

### Post by yopnono on 2007-01-30
> alien -ci 

If you like to know more about the different alien options just type > alien --help

---

### Post by Cariboo1938 on 2007-01-30
Thank you, yopnono!
So far so good, I installed 'alien' with some dependencies without error.
 Now I wanted to do the next step:
> **jeffc313 said:**
>  ....next: Open Applications>System Tools>Applications Menu Editor
next: Click System Tools then New Entry
next:Create the Entry as Follows
 
But I don't find *'Applications Menu Editor'* under -->Application -->SystemTools
What can I do to find it?

---

### Post by smartboyathome on 2007-04-29
I tried this on Feisty, but it didn't work. How do I do it?

---

### Post by %hMa@?b&lt;C on 2007-07-24
> **smartboyathome said:**
> I tried this on Feisty, but it didn't work. How do I do it?

what part didnt work. sorry I forget to check my tutorial.  If its about the menu editor, its now called alacarte.  Just type alacarte in terminal to launch it.

---


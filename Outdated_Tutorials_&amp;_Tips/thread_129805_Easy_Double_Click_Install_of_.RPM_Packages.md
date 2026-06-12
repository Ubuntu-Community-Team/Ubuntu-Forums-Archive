---
title: "Easy Double Click Install of .RPM Packages"
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


---
title: "VirtualBox"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by mlempenau on 2012-04-24
[COLOR=#000000][FONT=Lucida Grande]I'm not sure what form to use for this ...

I'm using ubuntu 11.04 with VB 404 running windowsxp. I have installed the extension pack but can not get windowsxp to recognized either the cd/dvd drive or two different .iso files. I installed xp from this same cd drive and since then can not get it to recognize anything. I have gone to devices and checked the appropriate device. I have opened the Virtual Media Manager and it shows up there. I have not tried to manually install guest additions. Is this the problem? It will not do it automatically. What am I missing???[/FONT][/COLOR]

[COLOR=#000000][FONT=Lucida Grande]The drive shows up in windows files explorer, but when you click on it a window pops up saying, "Please insert a disk into drive D". I have put several disks into this drive without success.

The cd/dvd drive always mounts automatically in ubuntu.  
[/FONT][/COLOR]

---

### Post by wildmanne39 on 2012-04-24
Hi, to install guest additions with vb open and running go to the top of the page and click on devices then install guest additions then in xp you should be able to double click on the cdrom icon and it should show and install the guest additions.

If you want to use the cdrom in xp you need to make your settings look like the screenshot.

Also make sure you are added to the birtuaqlbox user group.
Thanks

---

### Post by mlempenau on 2012-04-25
I have a different version of virtual box so it looks different from yours but I did many times everything you have said.  I check the box to activate the guestadditions iso.  Then I click on install guest additions ... and nothing happens.  

I have also put this on the virtualbox user group but they are quite busy so I have not gotten a response yet.

---

### Post by mlempenau on 2012-04-25
I used Virtual Clone Drive to mount the guest additions iso.  Then I was able to manually install.  Now everything works as it should except I still can't access the cd/dvd drive.  I can set it up to share in Ubuntu and then get access to the files from there.

---

### Post by mlempenau on 2012-04-26
I found that Virtual Clone Drive had to be disabled in Device Manager.  Then after several minutes windows automatically detected the cd/dvd drive.

---

### Post by wildmanne39 on 2012-04-26
Hi, glad you got it working.

---


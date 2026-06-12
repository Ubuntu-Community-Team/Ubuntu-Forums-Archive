---
title: "after 8.04 update can't boot"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Knacker on 2008-05-02
I updated from gutsy to hardy and, stupidly I know, decided not to change menu.lst and other files when asked by the update manager. I had immediate problems my nvidia drivers and so started fiddling. The only change I made to anything was to follow the advise of the #5 post on this thread: 
[http://ubuntuforums.org/showthread.php?t=760304](http://ubuntuforums.org/showthread.php?t=760304)
[basically use synaptic to remove remaining gutsy (2.6.22-14) stuff (I removed four files), edit menu.lst (for new 2.6.24-16 kernel) and reboot.]
Now, when I boot I get a grub menu and when I select either normal ubuntu or recovery mode, I get the same error: 
"Error 22: No such partition"

the command that shows on the grub menu is 
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=4fd87f34-6f09-4820-a3a3-ca52a20cbd1a ro quiet splash

the only command I know from the grub command line is: 
"find /boot/grub/stage1"
which gives me: 
" (hd0,0)"

Please please help. I'm starting to freak out a bit. 
Thanks in advance.

---

### Post by Tatty on 2008-05-02
The simplest thing for you to do would be to re-install grub:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by frup on 2008-05-02
Open ubuntu up in a liveCD. Mount your drive.

Compare your menu.lst with this part of mine

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=58c17a41-74af-4060-a2d3-79581943ffe5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

Make sure your kernel is there and that it is being pointed to correctly.

Maybe post your menu.lst contents here for everyone else to scrutinise. Remember that has to be from your mounted ubuntu /boot/grub/menu.lst and not the liveCD's own one.

I would check that your /boot/initrd.img-2.6.24-16-generic (or what ever your menu.lst points to) exists too.


If everything seems too complicated you might save a lot of effort by just mounting your drive and backing up all your data and doing a reformat too. You should try fix the problem though.

---


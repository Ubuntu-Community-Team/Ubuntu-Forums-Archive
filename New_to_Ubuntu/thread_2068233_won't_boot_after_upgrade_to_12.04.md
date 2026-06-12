---
title: "won't boot after upgrade to 12.04"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by cookie on 2012-10-08
I was on 11.10 and things worked pretty good. I had downloaded some nVidia drivers to get dual monitor support on my Dell D630 laptop. Got it to work, sort of - had to manually change between dual and single monitor before disconnecting by using nVidia application, but I got used to it.

Now after upgrading to 12.04, bootup only gets to the purplish Ubuntu screen with the dots at the bottom. The dots don't alternate colors, it just sits there forever - all dots orange, not hitting the HD at all.

I assume the problem is my video drivers. I did some searching and found:

[http://askubuntu.com/questions/134550/ubuntu-12-04-wont-boot-after-upgrade](http://askubuntu.com/questions/134550/ubuntu-12-04-wont-boot-after-upgrade)

and others that suggest fixing the video driver problem. But, none of them give good newbie instructions for fixing this at the command prompt. I can get to the prompt, but I don't what to do from there.

The post above says to:

remove the nvidia-current (whuch might be rather old) and keep only the nvidia-common. In the worst case remove nvidia-common and ubuntu-desktop and reinstall them (with necessary rebooting).

I don't how to do that. What's the best way to get some video working again?

---

### Post by ajgreeny on 2012-10-08
Boot to the grub menu (hold shift if you don't normally see the menu) and go to the line you want to boot to with cursor keys.  Now hit the "E" key and you will see the boot details of the ubuntu stanza.  Go to the line that ends **quiet splash** and delete those two words and try using **nomodeset** in their place.  With luck that will get you to a GUI from which you should be able to install the nvidia driver for your card by using the dash and search term "drivers".

---

### Post by cookie on 2012-10-08
I tried that but still no GUI.
I get console text now, but it stops after "* checking battery state...          [OK] "

---

### Post by cookie on 2012-10-08
If I choose Ubuntu, with Linux 3.0.0-26-generic-pae then I am presented with the following to edit:

setparams 'Ubuntu, with Linux 3.0.0-26-generic-pae'

recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root <some GUID>
linux /boot/vmlinuz-3.0.0-26-generic-pae root=<some GUID> ro   quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-26-generic-pae


I replaced "quiet splash" on next to last line with "nomodeset", but that only got me the console text.
If I also remove the "vt.handoff=7", then when it finishes I am left at a command prompt.

Not sure what my next step should be.

---


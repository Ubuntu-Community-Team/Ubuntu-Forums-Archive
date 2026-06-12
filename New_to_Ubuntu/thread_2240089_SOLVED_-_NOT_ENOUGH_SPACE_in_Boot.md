---
title: "SOLVED - NOT ENOUGH SPACE in Boot"
date: 2014-08-17
forum: New to Ubuntu
---

### Post by richramik on 2014-08-17
Had this problem when going from 13.10 to 14.04.  Just happened again.  I ran the following:
[INDENT]sudo apt-get autoremove[/INDENT]

That being said, I looked in boot and still foudn artifacts of previous versions, such as:

[INDENT]abi......generic
config.....generic
initrd.img.....generic
system.map.....generic
vmlinuz.....generic
vmlinuz.....generic.efi.signed[/INDENT]

Are they needed, if not, how do I remove them?

Thanks,
Rich Ramik

---

### Post by egeezer on 2014-08-17
If you look through Synaptic by searching linux-image, you may see a lot of old kernels still checked as present.  You can then Completely Remove them (that takes the congifuration files with them).  I usually go through from time to time and get rid of all but the last two or three such images - keeps things light!

---

### Post by egeezer on 2014-08-17
Oh, and  PS: At one point Ubuntu was not including Synaptic Package Manager by default.  Don't worry if it isn't there, just go to the terminal and type sudo apt-get install synaptic.

---

### Post by deadflowr on 2014-08-18
I use the commands from this
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)
works perfectly for me, everytime.
I would suggest running the dry-run command first and do a comparison of kernels it lists that will be remove.
It will also remove and corresponding linux-header packages as well, so that's a bonus.

---

### Post by richramik on 2014-09-17
Hey guys:

Sorry for the delay in responding.  Went to tuxtweaks.com and used the following command line

"dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge"

After running, I check boot again and it worked.  Now I know what to do in the furute.

Thanks again.

---


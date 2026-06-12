---
title: "Synaptic Local or Obsolete??"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by WacoJohn on 2013-12-10
I have a very small hard drive.  In trying to conserve space, I completely uninstall anything found in Risidual Config.  Today, there is nothing there but there are two items in Local or Obsolete.  I am wondering if I can safely completely remove them.  Thank you in advance.

[ATTACH=CONFIG]248488[/ATTACH]

---

### Post by jdeca57 on 2013-12-10
I wouldn't ever delete something called linux-kernel unless you're certain you're not using it...

---

### Post by WacoJohn on 2013-12-10
not to worry ... I would never delete anything I was using.  What I was driving at is that I understand RESIDUAL CONFIG can be safely disposed of .. just don't know about LOCAL/OBSOLETE.

---

### Post by ptn107 on 2013-12-10
You can paste this in a terminal to cleanup any orphaned package configurations
```
dpkg -l | grep -e ^rc | awk '{print $2}' | xargs sudo apt-get -y purge; sudo apt-get autoremove -y
```

---

### Post by WacoJohn on 2013-12-10
You gentlemen are very kind to give me your time.  I am sure you give good advice.  As a (relative) beginner, I have to rely on GUI rather than command line (though learning slowly).  No way I could remember:

```
[COLOR=#000000][FONT=Ubuntu Mono]dpkg -l | grep -e ^rc | awk '{print $2}' | xargs sudo apt-get -y purge; sudo apt-get autoremove -y[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]

regardless whether 'real men' use command line. 
 
Hence, have Synaptic set to show me RESIDUAL CONFIG status items which I have learned are safe to 'remove completely'.  Learned it from a tutorial right here in this forum in fact.  It works GREAT.

In this case, don't find anything THERE, but do find items in LOCAL OR OBSOLETE and I am trying to learn what to do with them.  I guess I was not clear in the first place.  So .. if anyone can tell me, . I will then go back to my GUI enjoyment of Linux.  I am fairly certain these items are left overs from an update .. but because they are not showing in Residual Config, or ORPHANS (another Synaptic configuration related to this whole thing within the same tutorial), I wanted to get expert answers ... to my question.  thank you both again .. sincerely.  [/FONT][/COLOR]

---

### Post by ajgreeny on 2013-12-10
Depending on what you have installed the LOCAL/OBSOLETE may include several applications or packages that you want to keep; only you will know, but I wouldn't just assume you can remove them all.

For example my list includes devede, mplayer-gui, mencoder, some icon themes  and audio-recorder all of which I want, and although the OS would run perfectly well without all of them, I would not be able to carry out some activities that I do now using them.

PS:
You can see the kernels you have installed by using terminal command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` then search with synaptic for the kernel versions you don't need any more and "completely remove" them, leaving only the most recent and the previous version.

---

### Post by Impavidus on 2013-12-10
Local or obsolete contains the installed packages that are not present in the repositories. They may be .deb files you downloaded yourself and manually installed, or they could be leftovers from a previous release of Ubuntu. They are for Linux kernel 3.8, which, I think, is Ubuntu 13.04. If you upgraded to 13.10 they may have remained on your system for some reason. These packages are present in the 13.04 repos, not in the 13.10 repos. If your 13.10 has been properly installed it should be safe to uninstall these kernel packages.

---

### Post by WacoJohn on 2013-12-10
> **ajgreeny said:**
> Depending on what you have installed the LOCAL/OBSOLETE may include several applications or packages that you want to keep; only you will know, but I wouldn't just assume you can remove them all.

For example my list includes devede, mplayer-gui, mencoder, some icon themes  and audio-recorder all of which I want, and although the OS would run perfectly well without all of them, I would not be able to carry out some activities that I do now using them.

You certainly do make a valid point.  I assumed some items there would be something to keep .. while other items were 'obsolete' and disposable.  Naturally, it would be my own responsibility to know which.  I got that much via intuition.  Like I said .. I believe the two items are leftovers from an update ... maybe not.  No one has mentioned how to find out.

Once I discern what they are ... 

I just found the answer (sort of) here (should have googled the question in the first place):

[http://askubuntu.com/questions/44930/what-does-local-or-obsolete-mean-in-synaptic](http://askubuntu.com/questions/44930/what-does-local-or-obsolete-mean-in-synaptic)     (obsolete does NOT mean disposable).

Since neither item is shown in Residual Config or Orphans, .. I'm leaving 'em alone (for now).

Thank you all again.  I am not sure this thread is 'solved' (since I still don't know with certainty what to do with these two items) ... so going to leave it open for others. Sorry for my rookieness.

---

### Post by WacoJohn on 2013-12-10
> **Impavidus said:**
> Local or obsolete contains the installed packages that are not present in the repositories. They may be .deb files you downloaded yourself and manually installed, or they could be leftovers from a previous release of Ubuntu. They are for Linux kernel 3.8, which, I think, is Ubuntu 13.04. If you upgraded to 13.10 they may have remained on your system for some reason. These packages are present in the 13.04 repos, not in the 13.10 repos. If your 13.10 has been properly installed it should be safe to uninstall these kernel packages.


THANK YOU!!  NOW, I can close this thread as solved.  Nice work.

---

### Post by vasa1 on 2013-12-11
> **ajgreeny said:**
> ...

PS:
You can see the kernels you have installed by using terminal command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` then search with synaptic for the kernel versions you don't need any more and "completely remove" them, leaving only the most recent and the previous version.
I just run *sudo apt-get autoremove* after a new kernel is installed. I'm then left with the current kernel and the immediately previous one:
```
[05:29 PM] ~ $ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnu
	menuentry 'Ubuntu, with Linux 3.11.0-14-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.11.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.11.0-13-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.11.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux -
	menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --cla
	menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux -
menuentry 'Memory test (memtest86+)' {
menuentry 'Memory test (memtest86+, serial console 115200)' {
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'ospro
```
and
```
[05:34 PM] ~ $ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic linux-image-3.11.0-12-generic linux-image-extra-3.11.0-12-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 258 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178331 files and directories currently installed.)
Removing linux-headers-3.11.0-12-generic ...
Removing linux-headers-3.11.0-12 ...
Removing linux-image-extra-3.11.0-12-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-3.11.0-12-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
[05:40 PM] ~ $
```

---

### Post by WacoJohn on 2013-12-11
Thank you for the education ... I need it.  Very kind of you.

---


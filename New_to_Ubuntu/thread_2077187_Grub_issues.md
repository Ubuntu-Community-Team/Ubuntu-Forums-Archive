---
title: "Grub issues"
date: 2012-10-27
forum: New to Ubuntu
---

### Post by 3v3rgr33n on 2012-10-27
Hi

I did something quite stupid. I normally dual boot Windows 7 and Ubuntu 12.04. I installed an older version of ubuntu, 10.10 to be exact on a seperate partition.

The problem is that when I boot, the grub that appears is the recent one. The one I got after installing 10.10. I want to delete the 10.10 partition but I fear I will not be able to boot into my computer.

How do I safely delete the partition without loosing grub

Enkosi
Adeeb

---

### Post by mardybear on 2012-10-28
Hello.

I believe Ubuntu 12.04 uses grub2.

Never had to try this myself, but boot-repair looks like what you should try. If you're booting from Ubuntu liveCD, i would think you should use your 12.04 disk if possible as i believe Ubuntu 10.04 uses an older/different version of grub.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hope this helps,

mardybear

---

### Post by 3v3rgr33n on 2012-10-28
Hi

The description of that piece of software says
> ...when you can't boot Ubuntu...


I can boot into Ubuntu. The problem is that I may not be able to when I delete the ubuntu 10.10 partition. Prevention is better than cure!

I just want to know how can I sorta like make grub2 active again. I thought that would be possible through an update or something but the command ```
grub-update
``` which I thought existed doesn't.

Enkosi
Adeeb

---

### Post by larrys4227 on 2012-10-28
So now, you have Win7, 12.04, and 10.10 all installed?

I run a multiboot computer as well, and when one of the distros requires a kernal upgrade (or in your case, another fresh install) the GRUB from that distro takes over.

Right now, grub from 10.10 has control of your boot process ...

What you need to do is run boot-repair (in the software center) from 12.04.  This will give control back to that distro, and you'll happily see grub2 back at boot up. 

I've used boot-repair quite often and never run into any problems.  Make sure you note down the log file address when it tells you to, just in case.

---

### Post by grahammechanical on 2012-10-28
You can boot into 12.04 and open a terminal and run these two commands:

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

The first command updates the Grub configuration files on the Ubuntu you are running it from. The second command puts the Grub of that Ubuntu into the MBR of the first sata hard disk. A second sata hard disk would be called sdb. And so on.

I run 12.04 and at the moment 3 x 12.10 which I shall be converting to development versions of 13.04. I have this issue all the time. I chose one Ubuntu to be my controlling Ubuntu and I run those two commands whenever I need to get my selected Ubuntu back into control.

Did you notice the mistake you made with update-grub? Did not use sudo. But that only updates the Grub configuration files. You need the other command to put the Grub you want back into the MBR.

Run these commands before and after you delete/format the 10.10 partition.

Regards.

---

### Post by kathrync on 2012-10-28
> **3v3rgr33n said:**
> Hi

I thought that would be possible through an update or something but the command ```
grub-update
``` which I thought existed doesn't.

Enkosi
Adeeb

I think that should be

```
update-grub
```

I don't know enough to know if that will solve your primary problem, mind you!

---

### Post by larrys4227 on 2012-10-28
> **grahammechanical said:**
> 

I run 12.04 and at the moment 3 x 12.10 which I shall be converting to development versions of 13.04. I have this issue all the time. I chose one Ubuntu to be my controlling Ubuntu and I run those two commands whenever I need to get my selected Ubuntu back into control.

Regards.

I learn something new everyday!  Sounds alot simpler and quicker than what I've been doing. I'll try this next time for sure!! :)

---

### Post by 3v3rgr33n on 2012-10-28
Thank you all for the responses.

It seems like I now have a bigger problem. I executed the commands ```
sudo update-grub
```and ```
sudo grub-install /dev/sda
```

The problem now is that grub has long list of ubuntu 12.04's and at the bottom it has "chainload into grub 2" and "ubuntu 12.04 memtest+"

I can no longer boot into the other OS's now.

Enkosi
Adeeb

---

### Post by 3v3rgr33n on 2012-11-01
I tried solving this using boot repair after days of googling, it didn't work.

I also generated boot info which may be useful. [http://paste.ubuntu.com/1325291/]("http://paste.ubuntu.com/1325291/")

Enkosi
Adeeb

---

### Post by mwl128340 on 2012-11-01
if you run a bootinfoscript you might get more accurate help. all your boot info will be in it. the readme will tell you what to do. [HTML]http://sourceforge.net/projects/bootinfoscript/[/HTML]

---

### Post by mwl128340 on 2012-11-01
my bad. i didnt see ur last post

---

### Post by mwl128340 on 2012-11-01
your info says you got ver. .97 which is grub legacy, the older version. 12.04 uses grub 2.

---

### Post by mwl128340 on 2012-11-01
try reinstalling grub from either 12.04 live cd again. you might need to purge and reinstall which is explained here. [HTML]https://help.ubuntu.com/community/Grub2/Installing[/HTML]

---

### Post by 3v3rgr33n on 2012-11-01
> **mwl128340 said:**
> if you run a bootinfoscript you might get more accurate help. all your boot info will be in it. the readme will tell you what to do. [HTML]http://sourceforge.net/projects/bootinfoscript/[/HTML]

Here are the results [http://paste.ubuntu.com/1325475/](http://paste.ubuntu.com/1325475/)

I really don't know what the problem now. BTW, the results are not different from the previous paste.

Thnx
Adeeb

---

### Post by oldfred on 2012-11-02
Bootinfoscript is run as part of Boot-Repair.

Boot-Repair suggest which is what you have to do, it the uninstall of grub, purge & reinstall. Boot-Repair will do that if you select it.

Or you can manually do it.

HOWTO: Purge and Reinstall Grub 2 from the Live CD 
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by 3v3rgr33n on 2012-11-02
Thank you very much for your help, all of you.

I fixed it.

I used the following commands
```
sudo grub-install --recheck /dev/sdX
```

and ```
sudo update-grub
```

> Replace the X value (sda, sdb, etc). This is normally the drive with the Ubuntu OS. This should be the drive the computer's BIOS boots. The command assumes the /boot folder is not on a separate partition. These commands should not be run from a Live CD.

Enkosi kakhulu!
Adeeb

---


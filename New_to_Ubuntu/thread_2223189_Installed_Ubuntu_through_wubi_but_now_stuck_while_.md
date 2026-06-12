---
title: "Installed Ubuntu through wubi but now stuck while checking for disk drive."
date: 2014-05-09
forum: New to Ubuntu
---

### Post by thom6 on 2014-05-09
I apologize, this is my first time ever trying something like this.

I downloaded Ubuntu and ran wubi.exe.
Next, I allocated 20GB for installation space.
Now I installed it and it loaded up to this screen saying "serious errors were found checking the disk drive for /."
I tried to ignore, but I ended up at the terminal(?) and it kept asking me for commands.
I just typed exit after logging in and reading help and being unable to get root.
On restarting I have the same error.

I apologize for format, I'm typing from a phone. Any and all advice is very much appreciated.

---

### Post by QIII on 2014-05-09
Hello!

Is this a Windows 8 computer?

What version of Ubuntu?

---

### Post by thom6 on 2014-05-09
Hi! 

I'm on Windows 7, and I think the latest version of Ubuntu available from Ubuntu.com

Edit

So 14.04 I guess.

Edit

I got a "No installer" message when starting and then it progressed to the same old purple Ubuntu screen

Edit

And i am getting disk drive for /tmp is not ready

---

### Post by thom6 on 2014-05-09
Please, I have no idea what to do next... It seems like it wants me to "mount" something or other... There doesn't seem to be any files when I run "ls" 

Thanks again.

---

### Post by thom6 on 2014-05-10
Please, anyone know what's going on?

---

### Post by oldfred on 2014-05-10
12.04 is the last officially supported version of wubi. 
It is on the newer installer, but it totally is up to you if you want to use it. That is somewhat opposite of what the original purpose of wubi  is. So only use 12.04 if you want wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)
[http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04](http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04)
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)
Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by thom6 on 2014-05-10
> **oldfred said:**
> 12.04 is the last officially supported version of wubi. 
It is on the newer installer, but it totally is up to you if you want to use it. That is somewhat opposite of what the original purpose of wubi  is. So only use 12.04 if you want wubi.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

wubi only installs as direct download in Windows, not from CD with 12.04
[http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows](http://askubuntu.com/questions/125015/can-i-install-12-04-inside-windows)
[http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04](http://askubuntu.com/questions/360616/why-was-wubi-removed-from-13-04)
Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)
[http://www.omgubuntu.co.uk/2013/04/wubi-advice](http://www.omgubuntu.co.uk/2013/04/wubi-advice)
Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

Thank you so much for everything. Sorry if I came off as rude earlier, I was really stressed about this whole thing...

I'm no longer using Wubi, but since I can't access my BIOS (lost password... X_X) I'm trying to run 14.04 on VMware.

Unfortunately, when I try that, I keep getting "sda1: WRITE SAME failed. Manually zeroing." after logging in correctly. I think this might be more of a VMware issue, but I'd be so happy if there was a fix for this...

If not, I will just install 12.04 using wubi and be on my way, but I'd really much rather have 14.04

Thanks so much for your time.

---

### Post by oldfred on 2014-05-11
I do not know vmware.
You can start a new thread in the Virtualisation sub forum.

Another option is an external hard drive or even a flash drive.
I have full installs on 16Gb & 32GB flash drives. Not speedy, but once something is loaded in RAM it is just as fast. So if you have a fair amount of RAM it works. Best to turn off some settings to reduce writes.

This is for a flash drive, but same procedure for any external device. And you can install with just UEFI or just BIOS if you like.
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---


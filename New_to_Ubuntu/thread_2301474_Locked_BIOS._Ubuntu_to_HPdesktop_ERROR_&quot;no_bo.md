---
title: "Locked BIOS. Ubuntu to HPdesktop ERROR &quot;no boot device has been detected...&quot;"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by Yoln1 on 2015-11-02
Hi everybody, and thanks in advance for helping me. 

I am totally new here, and I am currently trying to install Ubuntu server to an HP-Desktop computer (HP 110-209 nfm). After having succesfully ran the install, I receive the error message  *"no boot device has been detected or the disk has failed"*. I have read multiple threads regarding these issue and have taken care of the following:


[LIST]
[*]**Computer requirements** are way enough for Ubuntu. 
[/LIST]


[LIST]
[*]Even though my HDD is 1TO, I have **only allocated 25Go** for the Ubuntu server instal partition (since it appears to have sometimes issues related to big size partitions) 
[/LIST]


[LIST]
[*]Have tried any **BIOS **configuration. (Put Ubuntu first, Enable/disable "**Security-Boot**", En/dis "Quick-Boot", ...) always get the same error message. 
[/LIST]


[LIST]
[*]Unplugged and held start for 60 sec... (tried everything yeah...) 
[/LIST]


[LIST]
[*]Installed Ubuntu in a **brand new HDD**, everything went fine during install again, still the same Error (both HDD were working fine on another computer and were SMART ok). 
[/LIST]


[LIST]
[*]Ran a **Boot-Repair** that went just fine. Here is the output log : [URL="http://paste.ubuntu.com/13083191/"]http://paste.ubuntu.com/13083191/
[/URL] 
[/LIST]

Finally thought I had to **flash my BIOS**, so I tried, downloaded the new update and created a bootable FreeDOS, but here is the twist. I can't boot on FreeDOS either (even though I have tried the bootable USB on another computer and it worked). So apparently, HP is preventing me from both running Ubuntu AND flashing the BIOS in order to make Ubuntu run...

My question is : _Have you ever heard about any system preventing from running Ubuntu and/or FreeDOS ? Is there any way-arround that I could try ? _

Thanks a lot in advance, I'm totally desperate on that issue...
Best, 
Y.

P.S. : This is my only bootable partition, since I don't plan in running Windows on this computer anymore.

---

### Post by oldfred on 2015-11-02
You have to boot freeDOS in BIOS boot mode, not UEFI. And BIOS/CSM/Legacy can only be set with Secure boot off.

With Secure boot on, you may have to also change settings to allow boot from a flash drive. Some systems think allowing anything else to boot is not secure.

And HP violates UEFI standard. Standard specifically says not to use description as part of UEFI boot. And unless is sees a description saying Windows is will not boot. There are several work arounds.
If only booting Ubuntu, not dual booting you can just create a new UEFI boot entry that says "Windows" but really is the shimx64.efi boot file.

Various work arounds.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Also more details on specific commands in link in my signature below.

---

### Post by Yoln1 on 2015-11-04
Hi, Thanks a lot for your answer.

First, changing the name to  "Windows" actually did the trick. Then I reinstalled another version without UEIF and everything's going smoothly now. Problem solved. Thanks again.

---


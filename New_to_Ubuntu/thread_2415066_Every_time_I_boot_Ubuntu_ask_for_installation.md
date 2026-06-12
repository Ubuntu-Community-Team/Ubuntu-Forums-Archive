---
title: "Every time I boot Ubuntu ask for installation"
date: 2019-03-19
forum: New to Ubuntu
---

### Post by nertion on 2019-03-19
Hello:

I have installed ubuntu. Then after the message than a restart is needed, it shows me the installation process again. I have tried several times and all of them with the same result. I would be grateful if someone could help me.

Thank you

---

### Post by Autodave on 2019-03-19
When it asks you to restart, you have to remove the installation medium and then restart.  If you have already installed, just remove the medium and restart: you should be good to go then.

---

### Post by nertion on 2019-03-19
I tried and again the same thing... 

I went to the boot menu, and tried the option, starting with the first hard disk, if I do this, then it goes to my user. ¿Should I do this every time?

---

### Post by Autodave on 2019-03-19
are you attempting to install Ubuntu along side of Windows?

---

### Post by nertion on 2019-03-19
Yes

---

### Post by Autodave on 2019-03-19
OK.  IF the install went through, when it asked you to remove the install medium and reboot, did you do that?  You must remove the install medium.  When it rebooted, you should have been presented with a screen that asked you if you wanted to boot in Ubuntu or Windows.  Did/does that happen?  Can you boot into Ubuntu at all (without the installation medium) in the machine?

---

### Post by nertion on 2019-03-19
For remove the install medium I went to the home page, right Botton into more details, then I went to the "store", and there I removed it. It is like this ?
Thank you

---

### Post by Tobeus on 2019-03-19
When you download Ubuntu, how did you create the install media (burn ISO to CD/DVD, create install USB, mount image in virtual machine)?  What we need to know is what format was used to install Ubuntu?  Whatever this format, it is still in the machine and needs to be removed.  When the machine boots, it is choosing the install media first, not the installed hard drive.

You must either remove the installation USB, CD/DVD, or unmount the ISO image from your virtual machine software.

---

### Post by nertion on 2019-03-19
I crear a boot USB using Rufus. 

Thank you!

---

### Post by Tobeus on 2019-03-19
Is the USB still in the computer when you reboot?

---

### Post by nertion on 2019-03-19
Yes

thank you !

---

### Post by nertion on 2019-03-19
If I take away then pen, then the pc runs windows.

---

### Post by oldfred on 2019-03-19
What brand/model system?
UEFI or BIOS install?
What video card/chip?

To see what is installed where:
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nertion on 2019-03-19
I use the BIOS por booting. The things is that if I go to the boot menu and go through the option: "Boot from first hard disk" I can get into my user and my docs. If I don't go trough this option and just do a normal booting, is when the installation process appears. 

Thank you very much!

---

### Post by yancek on 2019-03-19
I don't think you will be able to get any help until you run boot repair, suggested and link posted in post 13 above.  There are too many possibilities and everyone will just be guessing without details.

---

### Post by nertion on 2019-03-19
Yes... I tried the boot repair, and said something like this: " For using the boot repair star the pc with the UEFI and not with the legacy. If I do that, doesn't even run ubuntu...
thank you!

---

### Post by oldfred on 2019-03-19
You have newer UEFI hardware.
And then it depends on whether installs are UEFI or BIOS on which way you should boot Ubuntu live installer & add Boot-Repair.
Did you run the report? That should not matter unless your installs are UEFI and then a UEFI report includes a bit more info.

---

### Post by nertion on 2019-03-20
Should I past here the link to the boot repair info page?
thank you!

---

### Post by oldfred on 2019-03-20
Please post link and in clickable format so we can just click on the link to see details of your configuration.

---

### Post by 1clue on 2019-03-20
To me it sounds like you put a livecd installer on the USB stick, and then clicked 'try Ubuntu' and are running from the USB stick.

Did you actually format your drive and install Ubuntu, or did you just click 'try Ubuntu?'

---

### Post by nertion on 2019-03-20
Here it is:

[http://paste.ubuntu.com/p/FhMswX77H2/](http://paste.ubuntu.com/p/FhMswX77H2/)

thank you!

---

### Post by oldfred on 2019-03-20
You have a mixed boot install.
Windows is installed in UEFI boot from gpt partitioned drive.
But then you installed Ubuntu in BIOS boot mode. You can reinstall Ubuntu in UEFI mode or from Boot-Repair if you add it to Ubuntu live installer in UEFI mode, run from advanced options the full uninstall/reinstall of grub. That uninstalls grub2's BIOS boot loader and installs grub2's UEFI boot loader.

How you boot install media from UEFI boot menu is then how it installs. Since Windows is UEFI, you always want to boot in UEFI boot mode.
Your UEFI boot menu should have two entries for installer, one UEFI:flash and other flash which is BIOS boot. Flash will be name or label of your flash drive. My system just calls is pmap, so I have UEFI:pmap or pmap as choices.

I believe this near bottom of report, just says you booted in Legacy mode which is BIOS/Legacy/CSM boot mode.
La sesión actual este en modo Legacy.

---

### Post by nertion on 2019-03-20
I tried that but it saids that I need to boot the session in UEFI, but if I do that, the pc just turns on, shows a error message, and turn off...
Thank you!

---

### Post by oldfred on 2019-03-20
Have you turned off fast start up. From Boot-Repair:
      ```
 Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
Windows is hibernated, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 


```

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    
   Did you ever say what brand/model system?
What video card/chip?
Some need boot parameters.

Often better to have UEFI Secure Boot off, but Ubuntu should work with it on.
Report says you have it off,but Windows updates may turn it back on.

---

### Post by oldos2er on 2019-03-20
> **nertion said:**
> I tried that but it saids that I need to boot the session in UEFI, but if I do that, the pc just turns on, shows a error message, and turn off...
Thank you!

What is the error message?

---

### Post by nertion on 2019-03-21
I think that I got the problem,... I still had the boot pen connected (the one which I download Ubuntu). When I take it away, it works perfectly, so, was that the problem I guess,...
Thanks to everyone!

---


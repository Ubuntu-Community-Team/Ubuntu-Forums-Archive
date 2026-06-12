---
title: "UEFI &amp; secure boot &amp; 12.10"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by DD4lifeusmc on 2012-12-25
Forced to buy new laptop.  Samsung with win 8.
Want to put Ubuntu on it. Been using Ubuntu on old laptop 4 yrs.
But during research got some conflicting info.
Most all new computers use UEFI with secure boot.
Must disable this in the old "bios" by hitting F2 (normally) during startup.
Then I read Ubuntu 12.10 was written to use the secure boot and does not need disabled.
Then read that it is not ready as Microsoft decided the code did not meet their requirements.
 
So for a 12.10 install do I need to disable secure boot or not?
 
Are there any other gotchas I need to be aware of?
Thanks

---

### Post by candtalan on 2012-12-25
Commiserations. I have no direct experience, and am not looking forward to it either, however I am aware of such as this:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
which seems up to date (?) and suggests I think that if you want to , and are able to, turn secure boot off, then a normal Ubuntu install is possible. But if EFI is essential, then Ubuntu 12.10 64 bit may be used.
Good luck. I would be really happy to hear of how you get on?  hth

---

### Post by DD4lifeusmc on 2012-12-25
> **candtalan said:**
> Commiserations. I have no direct experience, and am not looking forward to it either, however I am aware of such as this:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
which seems up to date (?) and suggests I think that if you want to , and are able to, turn secure boot off, then a normal Ubuntu install is possible. But if EFI is essential, then Ubuntu 12.10 64 bit may be used.
Good luck. I would be really happy to hear of how you get on? hth
 
Not sure if secure boot is needed or not.
However the last two months with 12.04 clam antivirus has been detecting some bad files / web pages. So I believe I was infected.
And Ubuntu pops up a warning of a system  problem.
If secure boot does what it claims it could be good.
I think Ubuntu / Linux does need more antivirus software that has more options of what and where to do it's job. Times have changed. Ubuntu / Kinux is becoming more popular so the hackers are more tempted to write the viruses etc.  I don't use the default predefined folders. I split HD and save there, just in case the boot section of Ubuntu can not be salvaged without a complete reinstall.
Same with firewall, more plain English descriptions of what and where / when.
And I did just read in Ubuntu that 12.04 64 bit can be installed with secure boot on or off.
So downloading the 64 bit. Did the 32 bit yesterday. But will install the 64 instead.
Hope I don't get a brick!

---

### Post by GrouchyGaijin on 2012-12-26
> **DD4lifeusmc said:**
> 
I think Ubuntu / Linux does need more antivirus software that has more options of what and where to do it's job. Times have changed. Ubuntu / Kinux is becoming more popular so the hackers are more tempted to write the viruses etc. 
It is my understanding that because everything is controlled via permissions, a malicious script or program can't run on Linux unless you expressly grant it permission to do so.

---

### Post by oldfred on 2012-12-26
Most systems seem to need secure boot off to be able to boot flash drive to install. And how you boot install media is how it installs, so you need to boot in UEFI mode not legacy/BIOS/AHCI or whatever.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

 [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

This Samsung had an SSD.
       
 Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by bodhi.zazen on 2012-12-26
> **GrouchyGaijin said:**
> It is my understanding that because everything is controlled via permissions, a malicious script or program can't run on Linux unless you expressly grant it permission to do so.

That is a common misconception and is completely false. If you have shell access you can source a file and it will "run".

```
source $HOME/file.txt
```

You can source such a file from ~/.bashrc ...

---

### Post by GrouchyGaijin on 2012-12-26
> **bodhi.zazen said:**
> That is a common misconception and is completely false. If you have shell access you can source a file and it will "run".

```
source $HOME/file.txt
```

You can source such a file from ~/.bashrc ...

Really?  This is the first I've heard that.  I don't really understand what you mean by source a file. I wonder why then, not more is mentioned about the need for anti-virus programs on Linux then?

---

### Post by bodhi.zazen on 2012-12-26
> **GrouchyGaijin said:**
> Really?  This is the first I've heard that.  I don't really understand what you mean by source a file. I wonder why then, not more is mentioned about the need for anti-virus programs on Linux then?

Anti virus programs are not needed, IMO, as there are no known active viruses for linux.

Linux handles security very differently, your system has been patched for all the known viruses long ago.

Using any text editor, make a file in home, call it file.txt

Put this in it

```
echo "It works"
```

Now open a shell, run

```
chmod 600 ~/file.txt

~/file.txt
```

You will get an error.

Now run

```
source ~/file.txt

. ~/file.txt

bash ~/file.txt
```

---


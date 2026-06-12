---
title: "Corrupted Grub Loader - with a twist!"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by CharmingNathan on 2012-10-26
Hello all,

The problem I have is, at first a fairly simple one, I had Ubuntu 9.10 the Kamic Koala, with a dual boot of Widows X.P. installed The latter became corrupted, so I re-installed which then over wrote the M.B.R., so I no longer had the option of booting into Ubuntu.

*Here comes the twist: *In an attempt to resolve the issue, I tried to re-install Ubuntu, realised it wouldn't work, but in the process managed to wipe the X.P. Partition completely.

Now, I have researched this issue, and carried out the standard fixes for this, but all I get is Grub loading and a lot of text that is meaningless to me! However, all of the fixes I have seen, seem to assume that X.P. is still in place. In my case, however, it is not!

I am no Ubuntu expert, so I am hoping there is a relatively easy step-by-step resolution to this, but if there isn't, is there anyway I can migrate E-Mail's Firefox favourites, etc., to a new installation of Ubuntu 9.10?

In advance, thanks for your help!

---

### Post by NikTh on 2012-10-26
Hi , 
are you trying to install Ubuntu 9.10 ? You have to know that [Ubuntu 9.10 is EOL](https://wiki.ubuntu.com/Releases) . Personally I cannot help you with Ubuntu 9.10 , I don't know even what grub uses (legacy ? ).

I can only suggest to download a newer supported version of Ubuntu and create a bootable USB and boot from there and try to install again. 

Ubuntu 12.04 LTS (support until April 2017) : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
Create bootable USB with Unetbootin : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Obviously you will need another PC if yours not even boot. 

Thanks and Good Luck.

---

### Post by grahammechanical on 2012-10-26
How far did you get in your attempt to re-install 9:10? Far enough to mess up the data on the 9.10  partition?

You may be lucky. You may only need to re-install Grub from a live CD. And it may be best to do it from the 9.10 CD.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

The principles are the same even if Windows is no longer present.

Regards.

---

### Post by CharmingNathan on 2012-10-26
> **grahammechanical said:**
> How far did you get in your attempt to re-install 9:10? Far enough to mess up the data on the 9.10  partition?

You may be lucky. You may only need to re-install Grub from a live CD. And it may be best to do it from the 9.10 CD.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The principles are the same even if Windows is no longer present.

Regards.

I tried to install Grub and it states it is loading, then just comes out with a screen full of meaningless (to me) text?

The installation of 9.10 was stopped just before I realised I was about to wipe everything on that partition as well, just after I had wiped the X.P. partition. 

As far as I can ascertain, the 9.10 installation is intact, but because the Grub loader is corrupted, I can no longer gain access to it.

---

### Post by black veils on 2012-10-26
just thought i should say, about installing a recent version of Ubuntu, your hardware might have issues with it, so best to go with Xubuntu (it will look familiar to you - and everything you see can be changed), or even Lubuntu.

---

### Post by oldfred on 2012-10-26
May be best to see what is where. I normally suggest this, but not sure if it will fully run on old version liveCD or you can download it as a full repairCD.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Or you can just download the bootinfoscript (which is run by Boot-Repair, but BootInfo includes some extra useful data).

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by PowerBarry43 on 2012-10-26
Hi 

you could always try downloading a supergrub cd to boot into into your actual install of ubuntu 9.10 and reinstall grub from there

Hope this helps

Barry

---

### Post by CharmingNathan on 2012-10-27
> **PowerBarry43 said:**
> Hi 

you could always try downloading a supergrub cd to boot into into your actual install of ubuntu 9.10 and reinstall grub from there

Hope this helps

Barry

Thanks to you all very much for your assistance.

These C.D.'s sound the right way to go, but I am guessing they have to be burnt to a C.D. using Ubuntu itself? I am a real Ubuntu novice here so I have to confess not knowing how to do this, or are any of the above mentioned disks burnable in Widows then usable in Ubuntu? No, I thought not! I really DO appreciate your help thus far though. Thanks.

[I]***Since posting this, I have managed to use the internal C.D. Burner in Ubuntu and created the Boot Rescue C.D. that has resolved the issue...just a corrrupt Boot Loader eh?! Oh dear, now how do I get back the Data I wiped from the Widows X.P. Partition needlessly? :-(

Seriously, thanks to you all for your help - a great and very helpful Forum.***
[/I]

---

### Post by oldfred on 2012-10-27
Did you overwrite all of XP or just boot loader. If you overwrote all of system STOP using it. The more you use it the more you overwrite.

From liveCD run BootInfo report from Boot-Repair to see if NTFS partition(s) are still there and how system is configured.

If you overwrote the entire XP, you have lost some data. But you may be able to recover some with testdisk or photorec type applications.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---


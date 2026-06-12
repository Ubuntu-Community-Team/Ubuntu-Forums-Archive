---
title: "New to Ubuntu"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Dave Moore on 2013-02-19
Hello.
I am having problems and dont know where to even start. I have never used the Ubuntu OS before so im lost on this whole thing. Ms step daughter was trying to upgrade to VS 11.10. About half way through it stopped responding so she let it set over night and in the morning it was the same. She then re started the system and it starts going through its command lines and then stops. I am trying to help her get it going but im a Windows user so that should tell you i could use all the help i can get.

I dont even know what to start asking so please be kind LOL.
Thanks 
Dave.

---

### Post by LiamOS on 2013-02-19
What exactly was she trying to do when it froze?

---

### Post by oldfred on 2013-02-19
Part completed upgrades can be a major issue. But it may depend on how far the upgrade went. 

Have you done good backups. If not use liveCD/DVD/Flash drive to backup all of /home at the minimum.

Do you even get a grub menu? or if just Ubuntu hold shift from BIOS until menu appears?

If you do not get grub menu it has not started to boot and this may tell us something. 

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 


If you do not have liveCD.
       
 Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Dave Moore on 2013-02-19
She says every day she would turn her computer on and the update manager would say that the new release was out and it wanted her to update. Her biological father, who was accustomed to using Linux systems, said that over a certain period of time the version needed to be updated. So she was trying to update the Ubuntu version. Well, she says there was a window that popped up saying that a package didn't download correctly, and she tried clicking on it to close it, but it wouldn't let her close it. Then another window appeared saying a different package didn't download correctly, and it wouldn't let her close it either, so basically, she was just trying to close all the windows that were appearing.

---

### Post by Dave Moore on 2013-02-19
yes the grub menu does come up but she has never done any system backups.

---

### Post by Sef on 2013-02-19
> I dont even know what to start asking so please be kind LOL.


If anyone is not polite to you, please click the report abuse button in the lower left hand corner. We will deal with them if a complaint exists and is verified.

---

### Post by csillva on 2013-02-19
> Ms step daughter was trying to upgrade to VS 11.10.

I would recommend installing a long-term-support version of Ubuntu so that these upgrade headaches don't happen as often.[1]

Right now that means downloading a 12.04 Ubuntu image and burning it to a disc. You should be able to do this on your windows computer. You can get a 32 bit version here [2]

> About half way through it stopped responding so she let it set over night and in the morning it was the same. She then re started the system and it starts going through its command lines and then stops. I am trying to help her get it going but im a Windows user so that should tell you i could use all the help i can get.

If you get a grub menu you can boot to rescue mode, bring up your Ethernet manually, do an apt-get -f install, then try to complete process with apt-get dist-upgrade. Of course, you'd want to check the /etc/apt/sources file first to see what repositories it is pointing at - I'd guess right now they are pointing at 11.10  (is that still supported?) if not you might have trouble finding a mirror that still hosts the packages. 

Of course, all of that is a lot harder than downloading the 12.04 disc and installing fresh. And the outcome is worse than downloading and installing fresh.  If I recall correctly, it should even give you the option of preserving your files and settings. 


[1] [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
[2] [http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=32&release=lts](http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=32&release=lts)

---

### Post by houseworkshy on 2013-02-19
This is an aside.  As you are new to Ubuntu you may find this free downloadable guide useful [http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by Dave Moore on 2013-02-19
Ok then maybe i should try a fresh install? will this lose any of her data? and can i install it over the top of the old OS or do i need to do an uninstall of the old OS first?

---

### Post by Thee on 2013-02-20
Yes, a fresh default install will erase all of the data. So don't do that yet.
You can boot Ubuntu from CD without installing it (just press Try when it boots up from the CD), copy all the important files from your computer to a USB stick or a network drive, and then you can go ahead with a fresh install. There is no need to uninstall the OS first.

---

### Post by Dave Moore on 2013-02-20
Thank you guys. i downloaded 12.4 last night and put it on a disk so i will give it a go today.

---

### Post by oldfred on 2013-02-20
It may be possible to repair upgrade, but it can be a lot of effort and difficult for a new user. 

But if you elect to do a new install you need to fully backup all of /home. 

If you have unique hardware, there may be some settings in /etc that were made. But new versions may not need those, sometimes they even conflict with a new version but sometimes you may need them. If not sure, it does not hurt to also back up /etc but not restore it.  Then, if necessary, restore one or two configuration files or review them.

If your hard drive has lots of room or unused space, you can put a new install in just 10 to 25GB and make sure it works with your system once installed (liveCD should give most of that), and see if you like Unity or want to change to a different Desktop Enviroment

---


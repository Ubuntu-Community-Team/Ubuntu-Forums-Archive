---
title: "Losing dual boot option for Windows"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by mlplatt on 2012-10-26
I have just updated from Ubuntu 12.04 to 12.10.

This seems to work well but has had the unfortunate side effect that I have lost the option of booting into Windows Vista. Previously on starting the computer I was presented with a choice as to which OS, Windows or Ubuntu, I wished to select.

Now I am landed straight into Ubuntu. There seems to be no way  of accessing Windows.

Originally the disk was partitioned using EasyBCD and in the past problems of this nature have been solved through this programme but alas it only runs through Windows so is inaccessible to me at the moment. 

Can anyone help please? 

Malcolm Platt

---

### Post by Bucky Ball on 2012-10-26
I think you hit shift after boot to get to the menu list. You should see all OSs there. The upgrade has changed the default behaviour by the looks.

---

### Post by grahammechanical on 2012-10-26
The upgrade from 12.04 to 12.10 also upgrades Grub from 1.99 to 2.0. So, Grub will be written to the MBR of the hard disk at the end of the upgrade.

If you was using some other boot manager, then it most likely has been replaced by Grub.

Do you get the Grub boot menu? You are not clear about this. Because Grub has been upgraded and written to MBR then the boot order has been changed with Ubuntu 12.10 being the default OS to boot when the time out expires. This is why you are landing straight into Ubuntu.

If you get a Grub menu, then press E. That will put the first entry into Edit mode. It also has the advantage of stopping the counter-down timer. You can now take your time to examine the boot menu.

Pressing Esc will back you out of that selection. By selecting an entry and pressing E and afterwards pressing Esc you can investigate the menu and note what description refers to which OS and may be find how Windows Vista is being described. Press F10 to boot the selected entry that is being examined.

Regards.

---

### Post by Bucky Ball on 2012-10-26
You can press any key to stop the timer. The down arrow is fine.

---

### Post by mlplatt on 2012-10-26
Thanks Bucky and Graham. I am not sure when and how I can intervene. When I turn the computer on, after the Dell logo and the invitation to press either F2 oe F12 for set up or boot menu,  it goes to a purple plain screen, briefly goes black and then purple again with the Ubuntu logo. 

Previously after the Dell logo etc. it went into a black screen giving me the choice of Windows or Linux. This no longer happens. I am led straight into Ubuntu. 

As I recall, and I can no longer confirm this as I can't access EasyBCD, the manager is Grub2. 

So I don't have any timer in which to make a choice. I am just shunted willy nilly into Ubuntu.

The Boot Menu and Set up seem to offer no means of rectifying which OS  is used.

You will gather I am woefully ignorant of computers and their workings. 

Regards,

Malcolm

---

### Post by oldfred on 2012-10-26
Grub2 reinstalled to the MBR, but should have found your Windows install.

Try this first:

sudo update-grub

If that does not find Windows, down load this & run BootInfo report.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Bucky Ball on 2012-10-26
oldfred, OP not getting to menu list at boot so can't select Windows even if it's there (which it quite possibly already is IMHO).

@ mplatt: when you get to the f12 for changing boot device screen start hitting shift. (They seem to change this a bit so if that doesn't work then try ESCAPE). That should get you to the list.

---

### Post by YannBuntu on 2012-10-26
hello

> **mlplatt said:**
> Now I am landed straight into Ubuntu. 

Please run [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") --> Advanced options --> GRUB options tab --> tick "Uncomment GFXMODE" --> Apply
Indicate the URL that will appear.
Reboot the pc, and tell us if the GRUB menu appears.

---

### Post by mlplatt on 2012-10-27
I tried hitting shift and escape at F12 Bucky but with no result. Nor did running sudo update grub get me anywhere. 

 I then downloaded Book Repair as the following script. But I must be doing something wrong! I can't find it. The instructions say that it should be in Dash or that i should be able to find it by typing 'boot-repair' in  a terminal. But the file remains elusive. Where will it be? It looks as if the download worked but ...

Regards,

Malcolm
                                 mlplatt@mlplatt-Inspiron-530s:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair &&sudo apt-get update [sudo] password for mlplatt:
  You are about to add the following PPA to your system:  Simple tool to repair frequent boot problems
.  Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair) 
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair) Press [ENTER] to continue or ctrl-c to cancel adding it sudo apt-get install -y boot-repair && boot-repair gpg: keyring `/tmp/tmp5ttn9l/secring.gpg' created gpg: keyring `/tmp/tmp5ttn9l/pubring.gpg' created gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com gpg: /tmp/tmp5ttn9l/trustdb.gpg: trustdb created gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported gpg: Total number processed: 1 gpg:               imported: 1  (RSA: 1) OK 

Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                  Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal InRelease                              Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]           Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                      Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                       Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates InRelease                      Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                           Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]             Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                    Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports InRelease                    Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                        Get:7 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                             Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release.gpg                            Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                               Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release.gpg [933 B]          Get:9 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,243 B]                  Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                         Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release.gpg                  Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release                                Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [933 B]                    Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release [49.6 kB]           Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [2,841 B]            Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [5,204 B]       Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [1,457 B]   Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [14 B]    Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [19.0 kB] Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_GB                     Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                        Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B] Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release                      Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                          Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [4,876 B] Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_GB                     Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Sources                           Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                             Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [14 B] Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                        Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Sources            Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Sources Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main i386 Packages Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted i386 Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe i386 Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse i386 Packages Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en_GB Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en_GB Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Sources [12.9 kB] Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Sources [14 B] Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Sources [3,218 B] Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Sources [14 B] Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main i386 Packages [45.1 kB] Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted i386 Packages [14 B] Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe i386 Packages [18.5 kB] Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [14 B] Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Sources Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main i386 Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted i386 Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe i386 Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse i386 Packages Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en_GB         Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB   Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en_GB   Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en_GB     Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en_GB       Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en_GB Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en_GB   Fetched 230 kB in 7s (31.2 kB/s)                                                Reading package lists... Done

---

### Post by oldfred on 2012-10-27
I tried adding code tags but you copied without line endings so that made it worse, so I undid code tags. Sometimes I just have to copy into gedit to get correct Linux line endings then paste into a message, rehighlight and click on # to add code tags.

I does look like it installed correctly.

Does this show anything?

whereis boot-repair

In Linux capitals matter.

---

### Post by Bucky Ball on 2012-10-27
Also:

 ```
sudo add-apt-repository ppa:yannubuntu/boot-repair &&sudo apt-get update 
```

... should be:

 ```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

---

### Post by YannBuntu on 2012-10-28
An alternative is to use a disk with pre-installed Boot-Repair: [https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#A1st_option_:_get_a_CD_including_Boot-Repair)

---

### Post by mlplatt on 2012-10-29
Thanks to you all I have managed to return things to normal. I entered oldfred's suggested lines in a terminal again but this time correcting the error spotted by Bucky Ball. This time it worked. I didn't have to search for the file it just openned.

When I restarted I wasn't taken straight away into the black Boot Up screen but a purple one which was obviously an Ubuntu one but which did give me the option of opening Windows Vista. In Windows Vista I went to EasyBCD and repaired the boot details from there. 

Things are now back to normal. 

My thanks to all who helped.

Regards,

Malcolm :)

---


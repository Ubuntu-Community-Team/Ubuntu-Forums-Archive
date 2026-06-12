---
title: "cant instal any linux, help please."
date: 2015-11-28
forum: New to Ubuntu
---

### Post by Dragsteur on 2015-11-28
[IMG]http://i.imgur.com/C7bDeVB.png[/IMG]Hi, i currently run on Windows server R2 SP1. i would like to pass on linux ubuntu whit a dektop for me server. i need to host 2 web site, file server, source server and minecraft server.

what ever the linux distribution that i chose it dont instal at all (only a white dot on the top left corner of the screen) or it instal and to the same dot when i try to boot it.

what can i do to instal a linux whit a dekstop that is also good to host thing. 

Thanks in advance.

---

### Post by yancek on 2015-11-28
Which of the three hard drives do you want to install on?  Is there any free/unallocated space on that drive or does windows take it all up?  Did you do an md5 checksum on any of the Linux iso files you downloaded?  Are you using a DVD?  Did you burn the iso file as an image or just copy it to the DVD?  If you copied it you wasted a DVD.  If you put it on a flash drive what software did you use to do that?  Have you had an opportunity to test the DVD or flash drive on another computer?

---

### Post by Dragsteur on 2015-11-28
Edit:

I instal via a USB key whit universal usb installer and i take the iso of ubuntu 15 that they give me the link.

I instal on the SSD drive the 2 other are for the servers. 

i will completly remove windows to run only linux on this computer.

---

### Post by grahammechanical on 2015-11-28
I am going to point to the video adapter as the problem. I do not think it is able to run Ubuntu with its Unity user interface that requires a video adapter that can do hardware accelerated 3D rendering. The video adapter gets its memory from system memory (RAM) up to a maximum of 384 MB. These kind of arrangements are not the most suitable for using Ubuntu.

[http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-4500MHD-GMA-X4500MHD.9883.0.html](http://www.notebookcheck.net/Intel-Graphics-Media-Accelerator-4500MHD-GMA-X4500MHD.9883.0.html)

You should try another member of the Ubuntu family of Linux distributions. We have Xubuntu, Lubuntu, Ubuntu Mate and they do not have the high requirements for video adapters that Ubuntu has.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by sandyd on 2015-11-28
If you want, all of the things you listed that you wanted to run on the server do not require a GUI to configure or run. You can use Ubuntu Server if you can live with having a text-only interface. There will be not much of a difference since most of the configuration will be done through the terminal anyways and you will save a bit of RAM and disk space.

If you are looking to use the server for long term, I advise using Ubuntu 14.04 LTS instead of Ubuntu 15.10. Ubuntu 15.10 will stop being supported in July 2016, while Ubuntu 14.04 is a LTS (Long Term Support) release, and will be supported until April 2019. When a version stops being supported, the repos are moved to a separate URL and package updates are no longer done.

---

### Post by Dragsteur on 2015-11-28
ok i'll stick to 14.4 but i whant a desktop. my workshop/server room is also my GYM so i use to go down there and put some music or video on that computer when i workout XD that why i want a GUI. also im not use to linux and command line at all lol.

---

### Post by jim_deadlock on 2015-11-29
Managing a server usually requires some command line work whether you like it or not...

---

### Post by Dragsteur on 2015-11-29
yhea i'll deal whit it when i arrive there but i whant a desktop for the secondary use of that pc. the problem is i cant instal it. 

1: when i try to boot from the usb stick i got only a white flashing dot  on the top left of the screen and the setup never start.

or

2: when the setup does start and run when i remove the stick to boot ubuntu i got the same dot flashing at the same place and it never boot.

it does that whit 10 different linux distribution even ubuntu server whit only command line.

---

### Post by mastablasta on 2015-11-30
> **Dragsteur said:**
> yhea i'll deal whit it when i arrive there but i whant a desktop for the secondary use of that pc. the problem is i cant instal it. 

1: when i try to boot from the usb stick i got only a white flashing dot  on the top left of the screen and the setup never start.

or

2: when the setup does start and run when i remove the stick to boot ubuntu i got the same dot flashing at the same place and it never boot.

it does that whit 10 different linux distribution even ubuntu server whit only command line.

even for music and movies you do not need a GUI.

anyway had a similar experience when trying to boot with certain USB combination inside ports. weird and I am still checking if it's maybe some USB driver that stops it. anyway check BIOS, make sure you are booting from the correct disk. also the chip should be fully supported but sometimes these Intels aren't. nomodeset might help as might some other boot options available: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) hard to say from the top what is wrong. you would need to somehow get in (maybe with a live session) and post a log (at least an older dmesg and then some kernel logs to see where it got stuck).

it is not advised to put a desktop to server opened to internet. it adds another attack vector. you will need things like fail2ban, unattended updates etc.
if you really must have a GUI check out the browser GUIs such as Zentyal, Ajenti etc. Zentyal by default also installs XFCE desktop. or you can install zentyal web interface to Ubuntu.

if you do not need a super nice GUI you can get away with something like a windows manager such as IceWM, jwm etc. many of them to choose from. here is a how to for minimal Ubutnu install. only in your case you would use server image and get some basic desktop with only a windows manager in the end: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

server is traditionaly configured via various configuration files. which is why often CLI is enough. but I like a nice interface where I can doo all that with mouse and keyboard, so I use Ajenti.

---

### Post by buzzingrobot on 2015-11-30
> **Dragsteur said:**
> yhea i'll deal whit it when i arrive there but i whant a desktop for the secondary use of that pc. the problem is i cant instal it. 

1: when i try to boot from the usb stick i got only a white flashing dot  on the top left of the screen and the setup never start.

or

2: when the setup does start and run when i remove the stick to boot ubuntu i got the same dot flashing at the same place and it never boot.



This is not clear.

The first statement indicated you can not install Linux, that the installer never starts.

But, the second statement says the installer does start, at least sometimes.  Does this mean you do, in fact, see the installer GUI and use it to successfully install Ubuntu and that when you close the installer, remove the USB stick, and reboot, that it then fails?

In a normal installation, the installer will prompt you to remove the USB stick when the installation is completed, before it reboots that system.  Removing the USB stick at any time before that will result in a failed installation.

---

### Post by MartyBuntu on 2015-11-30
You're going to host websites...
...from a residential connection...
...with an *Enterprise* version of Windows Server?


I sure hope all your receipts are in order...

---

### Post by Dragsteur on 2015-11-30
it do both. whit some ISO it wont boot at all i dont see the installer. whit some other distribution it will instal but not boot.

i just tried whit the version 14.04 LST that i took on this website and on me gamer PC it boot and instal perfectly. but if i take the same key on the server it dont event boot i dont see the instal GUI. only the white dot flashing on the top left corner.

---

### Post by buzzingrobot on 2015-11-30
> **Dragsteur said:**
> 

i just tried whit the version 14.04 LST that i took on this website and on me gamer PC it boot and instal perfectly. but if i take the same key on the server it dont event boot i dont see the instal GUI. only the white dot flashing on the top left corner.

As mentioned earlier, the video chip in the server may not support Linux, or at least not support it easily. A search on that specific chip might find something useful or informative.

Also, you can add a desktop GUI to a server install later.  Try burning and booting a server image and see if the same problem occurs. If the install is successful, you'll boot into a text-based console that's requesting a username and password.

The fact that the same problem has happened with multiple distributions, though, leaves the video chip in the machine as the constant factor.

---

### Post by Dragsteur on 2015-11-30
if i instal a PCI graphic card i got a old GTX 750 or an AMD something?


Update: I just tried whit a Asus Gee Force 750 and i got the same whit dot of death XD. im currently downloading the Ubuntu server version.

Update: Now it does boot and try to instal but it block stating that it cant detect the instalation disc. but i try to instal it via USB and i dont event ave a disk drive ont this machine. any clue?

---

### Post by mörgæs on 2015-12-01
It's helpful if you post the exact error messages you see.

An X4500 is a fine processor and in general Intel is one of the best to support Linux. Dragsteur, forget what has been posted about GPU problems.

---

### Post by kolumcaj-silvi on 2015-12-09
Download a new Ubuntu iso from the main site and try to make a bootable usb with Unetbootin (google it), and try to install Ubuntu from that usb. It always worked for me :)

---


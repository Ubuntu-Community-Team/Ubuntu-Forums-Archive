---
title: "Witts End with Installing on Unbutu 11.10"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by The Dee on 2012-02-18
I've spent the better pat of two days trying to follow other people's instruction in this command format and haven't gotten ANYTHING done because I keep getting error messages. I am extremely new to Ubuntu and Linux (yesterday was my first time interacting with it and I don't know what else to do. :confused:

I'm trying to get MagicJack working on this OS. I understand that it is not compatible, but everything I've found says that I need to use a VM (also brand new terminology) with XP as its guest OS and make the USB accessible through it. I tried several VM builders, qemu, vmware player, virt-manager, virtualbox... I've really tried to make it work and have consistently failed.

Can you tell me exactly what to download and then exactly which commands i need to put in to make something work? Most of these forums seem to only serve people who already know all about commands, installing, and troubleshooting these programs and like I said, I'm brand new to this... I learn fast, but not that fast.

I'm using Ubuntu 11.10. 36 (or, not 64)

Thanx in advance for ANY help you can give.

---

### Post by carl4926 on 2012-02-18
Virtual Box is virtual machine software like VMWare.
It allows you to create a Virtual HD (This will use space from your Ubuntu install, or you can define a location but lets just keep it simple)
Typically when you create a New Virtual Machine in Virtual Box it defaults to 8 or 10 GB I think. I always decide how big a HD I want and create it that size, rather than using an expanding size.
You then install XP to this Virtual HD to create a installation of XP. Virtual Box has full documentation on this that you can download.

Also check
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

But you need Virtual Box from here
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by anewguy on 2012-02-18
Go to the Oracle site and download the version of virtualbox there.  There should be instructions on installing it (try just double-clicking what you downloaded ;) ).  Once you have virtualbox installed, you need to start it and then have a Windows installation CD with valid key that can be authorized in order to install Windows.  First choose the new option to set up a virtual machine and just take the defaults for now - we can change the things that need to be updated later.  Once you have the maching set up, put the CD in the drive then just start the virtual machine you just created.  Everything dealing with USB, etc., can be set up later.

Be aware you need some decent hardware and some decent memory to really run a virtual machine.  It might be wise to post back your hardware configuration so we can see if it is worthwhile or not.

As you've alread found, MagicJack will not work natively in Linux.  At first they said a Linux driver and software was coming, but now they have removed that.  There are other tools for doing similar things in linux - you may want to do a yahoo/google/bing/whatever search for Linux voip and research what comes up.

Dave ;)

---

### Post by The Dee on 2012-02-18
> **anewguy said:**
> 
Be aware you need some decent hardware and some decent memory to really run a virtual machine.  It might be wise to post back your [SIZE=3]**hardware configuration**[/SIZE] so we can see if it is worthwhile or not.


[COLOR=Blue]Thanx Carl & Dave...
The problem isn't so much knowing what to download and where from, but  once I download it, clicking on the downloaded files in the only opens  "empty" .gedit files that won't close. i then go looking for help with  installing, and get a bunch of different "tutorials" just took me 4  hours to figure out were directions for command prompts (because I'm  supposed know that 20 mins after turning on a computer and realizing I'm  way out of my league).

Anyway, trying to go through everything I've tried over the last 27 hours is kinda useless. Where would I find the hardware config you mentioned?[/COLOR] [COLOR=Blue]

[COLOR=DarkOrchid]I know! I can show you some of the commands I'v[/COLOR][/COLOR][COLOR=DarkOrchid]e used (some in order)! I started saving them so I could compare from one site or program to the other...[/COLOR]



sudo sh filename VMware-VIX-1.11.1-528992.i386.bundle

1. sudo apt-get install build-essential
2. sudo apt-get install linux-headers-`uname -r`
3. cp /cdrom/*.gz /tmp/
4. cd /tmp
5. tar xvzf VM*.gz
6. cd vmware*
7. sudo ./vmware-install.pl
NO HELP
1. chmod 777 VMware-player-4.0.0-471780.i386.bundle
2. sudo ./VMware-Player-4.0.0-471780.i386.bundle

4.gksudo bash ./VMware-Player-4.0.0-471780.i386.bundle  3.1.5-491717.i386.bundle
gksudo bash ./VMware-Player-3.1.5-491717.i386.bundle

sudo apt-get install build-essential linux-headers-`uname -r`


1. sudo apt-get install build-essential linux-headers-$(uname -r)
2. chmod +x VMware-Player-4.0.1-528992.bundle   4.0.0-471780.i386.bundle  3.1.5-491717.i386.bundle
3. gksudo bash ./VMware-Player-3.1.5-491717.i386.bundle 4.0.0-471780.i386.bundle
____________________________________________________
To Start:  virt-manager

then: sudo apt-get install virt-manager

sudo /sbin/ip addr add 172.20.0.1/12 dev eth0

Then run:  git clone git://git.qemu.org/qemu.git


Create Virtual Disk: qemu-img create -f vmdk imagename.vmdk 4G

create -f vmdk M.JackOS.vmdk 4G Formating 'M.JackOS.vmdk', fmt=vmdk, size=4194304 kB

Create ISO (standard):  dd of=M.JackOS bs=512 seek=4194304 count=0

My vm: virt-manager -hda M.JackOS -cdrom supreme1906 A Phi A -m 192 -boot d

virt-install -hda M.JackOS -cdrom supreme1906 A Phi A -m 192 -boot d
____________________________________________________
kvm-ok
sudo /usr/sbin/kvm-ok (KVM is not supported)

sudo apt-get install kvm libvirt-bin

sudo adduser $USER libvirtd

virt-install:  sudo apt-get install virtinst

sudo virt-install -n web_devel -r 256 \
--disk path=/var/lib/libvirt/images/web_devel.img,bus=virtio,size=4 -c jeos.iso --accelerate \
--network network=default,model=virtio --connect=qemu:///system --vnc \
--noautoconsole -v

sudo virt-install -n M.JackOS -r 512 \--disk path=~/Desktop/M.JackOS.vmx,bus=virtio,size=4 --cdrom supreme1906 A Phi A-i386.iso -m 192 --accelerate \--network network=default,model=virtio --connect=qemu:///system --vnc \--noautoconsole -v

sudo virt-clone -o M.JackOS. -n database_devel -f /path/to/database_devel.img --connect=qemu:///system 


VirtualBox: 7B0F AB3A 13B9 0743 5925  D9C9 5442 2A4B 98AB 5139 <info@virtualbox.org>

sudo dpkg -i VirtualBox-4.1_4.1.8_Ubuntu~Oneiric_i386.deb

sudo apt-get update
sudo apt-get install virtualbox-4.0.14

sudo ./VirtualBox.run install


[COLOR=DarkOrchid]
Like I said, I really tried. Does that help any?[/COLOR]

---

### Post by Rodney9 on 2012-02-18
Go here _ [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Or for 11.10 32bit - [http://download.virtualbox.org/virtualbox/4.1.8/virtualbox-4.1_4.1.8-75467~Ubuntu~oneiric_i386.deb](http://download.virtualbox.org/virtualbox/4.1.8/virtualbox-4.1_4.1.8-75467~Ubuntu~oneiric_i386.deb)

Download the .deb file and double click that.

Rodney

---

### Post by 3rdalbum on 2012-02-18
Whoa whoa whoa... none of that command-line hacking is necessary.

This page: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

If using 32-bit Ubuntu, click on the "i386" link that corresponds with your version of Ubuntu. If using 64-bit Ubuntu, click on the corresponding "amd64" link.

When the download is finished, go to the file that downloaded and double-click it. The Software Center will pop up and show the package details. Click "Install" and then type your password when asked. One minute later, you'll have Virtualbox and you can start using it.

---

### Post by The Dee on 2012-02-18
> **3rdalbum said:**
> 
When the download is finished, go to the file that downloaded and double-click it. The Software Center will pop up and show the package details.

The Software Center popped up, but there's nothing in it. It's just a gray screen that says "Software Center" at the top.
[ATTACH]212931[/ATTACH]


Am I doing something wrong? You guys make it seem so easy, but this is what Ive been dealing with... This is why I'm at my "[COLOR=DarkRed]Witts End...[/COLOR]"

---

### Post by androssofer on 2012-02-18
> **The Dee said:**
> The Software Center popped up, but there's nothing in it. It's just a gray screen that says "Software Center" at the top.
[ATTACH]212931[/ATTACH]


Am I doing something wrong? You guys make it seem so easy, but this is what Ive been dealing with... This is why I'm at my "[COLOR=DarkRed]Witts End...[/COLOR]"

these guys are making a mountain out of a mole hill!

click the ubuntu logo on the top left of your screen. seach 'software center'. click it. open software center normally.  search for 'virtualbox'. ***ignore all that download lark.. it should already be listed in software center***

click install

when it installs. click ubuntu logo again, search for virtualbox. open it. 

hit new...

follow the wizard to create a new vm... 

once created, click on the vm in virtualbox and hit settings.

click storage,

then click 'ide controller' and check that it says: 'host drive bla bla bla' under it. if so:


insert your xp disk into your drive, and hit start on the vm...

it should start the vm and boot the xp installer... 

report back if you get this far.. or of any issues...

---

### Post by The Dee on 2012-02-18
> **androssofer said:**
> 

insert your xp disk into your drive, and hit start on the vm...

it should start the vm and boot the xp installer... 

report back if you get this far.. or of any issues...


[COLOR=Purple]Before I try anything...
I don't have an XP disk. I might be able to get one, but I don't have one right now. Is it necessary to get everything done? If not, are there any alternatives that I can take advantage of immediately?[/COLOR] If not, it might be a few days before anyone gets any updates on this thread :?

---

### Post by 3rdalbum on 2012-02-19
Any version of Windows will do. Virtualbox runs entire operating systems.

---

### Post by QIII on 2012-02-19
Unless something has changed recently, Virtualbox OSE, which is found in the repos, will be of little use if you need USB support unless you also install the Extension Pack from virtualbox.org.  That is:  attempting to reduce the "mountain" back to a molehill by installing from the Software Center will not get you what you need without another mole hill to negotiate.  The portions of the Virtualbox code that handle USB control have been closed source for a number of years and were not included in the OSE version in the repos for as long as I remember.

Again, that may have changed.

Even if you install from virtualbox.org, I think you still have to install the Extension Pack.  I think I had to.

Oracle maintains a .deb repository that you can add via instructions at virtualbox.org.  Using that will keep Virtualbox and the extension pack updated.  Just be aware that every time the Linux kernel is updated the Guest Additions will need to be reinstalled.

"Just install it from the Software Center" will probably not be enough for what you need.

---


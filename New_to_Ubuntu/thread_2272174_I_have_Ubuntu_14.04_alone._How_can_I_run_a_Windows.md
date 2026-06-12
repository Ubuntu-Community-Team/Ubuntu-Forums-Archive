---
title: "I have Ubuntu 14.04 alone. How can I run a Windows installation alongside?"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by Victor_Gilbert on 2015-04-04
I am unable to install my printer on a 64bit Ubuntu. An alternative would be to install in Windows - and use Windows only when I need to print (rarely now). 

How can I do that?

Victor

---

### Post by yancek on 2015-04-04
You would probably need to post more information such as how new the computer is with some minimum hardware specifications and which version of windows you want to install.  If you want to install windows 8, you will need to decide whether to use UEFI and if so, you will have to have installed Ubuntu in UEFI mode or you will have problems booting.

---

### Post by ajgreeny on 2015-04-04
Probably it will be easiest to use a virtual install in, for example, VirtualBox.

I have to run a WinXP VM very occasionally simply to update my TomTom satvav device which can not be done in any Linux distro.  It starts very quickly and updates the satnav without a problem, and it can also print to my USB attached HP printer, which is attached by USB to the host machine, though I believe you need VBox-guest-additions to use USB-2 devices; it is worth adding the guest-additions anyway for file sharing and clipboard bidirectional use between host and guest.

---

### Post by Vladlenin5000 on 2015-04-04
I always recommend VirtualBox too but that depends on the host computer. If I'm not mistaken, the computer is as old as the printer (~7yo) so really not the best candidate for running a Windows virtual machine (minimum 512MB of RAM should be reserved for Windows XP and, *I think*, one 1GB for Seven...).

Anyway, the last post here, from Sandy, seems very palatable to me as a solution for your printer: [http://ubuntuforums.org/showthread.php?t=2271791](http://ubuntuforums.org/showthread.php?t=2271791)
Yes, I know, a lot of work *even for me*. At one point I would have asked myself how valuable is my time and perhaps conclude it isn't worth saving $50 for a new low entry but plug&play printer or a better, slightly older second hand on eBay (where you can try to sell yours)...

---

### Post by Siddhartha_Kashyap on 2015-04-04
Yes you can. I have a dual core PC with 1 GB RAM and 160 GB HDD. I run Lubuntu 14.04.2 LTS alongside Windows XP. Both of them work flawlessly. I use Windows xp to play "age of empires" and lubuntu for internet. When you boot from the ubuntu CD, choose "I'll edit the partitions myself". Delete an unimportant drive to make it a free space. Create a ext4 partition from this free space and a swap of about 4GB. Install ubuntu on the ext4 partition. You can use lubuntu...its lighter than ubuntu

---

### Post by Vladlenin5000 on 2015-04-04
> **Siddhartha_Kashyap said:**
> Yes you can. I have a dual core PC with 1 GB RAM and 160 GB HDD. I run Lubuntu 14.04.2 LTS alongside Windows XP. Both of them work flawlessly. I use Windows xp to play "age of empires" and lubuntu for internet. When you boot from the ubuntu CD, choose "I'll edit the partitions myself". Delete an unimportant drive to make it a free space. Create a ext4 partition from this free space and a swap of about 4GB. Install ubuntu on the ext4 partition. You can use lubuntu...its lighter than ubuntu

You're dual-booting and we're talking about virtual machines. You can't run a Windows XP VM _inside_ your Lubuntu without bringing both host and guest to a crawl...

---

### Post by Victor_Gilbert on 2015-04-06
**I operate Ubuntu 14.04 on a ACER E210, AMD Athlon 4,200 MHz, 160 GB hard drive (using 18 GB), 3 GB RAM.  **

I want to install WinXp

  I downloaded the VirtualBox-4.3 from the website. It appeared as* virtualbox-4.3 Oracle VM VirtualBox *in the Software Centre and I installed it. However it only shows a reinstall button and not a Remove button. I found the image in Applications clicked it but failed to obtain an Open button.

How can I remove that application and install from the Software Centre?

Victor

---

### Post by Vladlenin5000 on 2015-04-06
(EDIT)

With 3GB of RAM and that CPU, running a Windows XP VM (give it 512MB) is viable.
If you already installed the Oracle's version then keep it. It's just slightly newer than the one in the repositories. I always install directly from the website, along with the extension pack (a must for you).
Now you just need to create a new VM in Virtualbox then install the OS you want or find a ready made VM (it's a file, only a file) ;)

But honestly... All that trouble for a printer???
Bringing back to life old hardware or insisting in using it until it breaks is commendable but there comes a time when obsolete IS obsolete. In this case it shouldn't be but the manufacturer stopped the support after a few years, like they almost always do... Again, I don't know about you, but my time worths a lot more than the $50 I would save by not buying a new printer.

---

### Post by Victor_Gilbert on 2015-04-10
Thanks Vladenin5000

Got a WinXp up and running in an Oracle Virtual Box with extension downloaded from Oracle

The Box still does not recognize my Memory stick & External Hard Drive?

                                                                                                   Victor

---

### Post by Ronco Pizatto on 2015-04-10
Disclaimer: I support open source as much as anyone but there comes a time when I also consider retail software. I also have no financial interest in the recommended product except how i can get money to purchase it.

There is another way if you can spend money. TurboPrint provides excellent and easy to install divers for 600 different printers. Try a demo version.

[http://www.turboprint.info/](http://www.turboprint.info/)

---

### Post by Victor_Gilbert on 2015-04-11
> Got a WinXp up and running in an Oracle Virtual Box with extension downloaded from Oracle

The Box still does not recognize my Memory stick & External Hard Drive?
Nor any device connected by a USB.

Help

Victor

---

### Post by Vladlenin5000 on 2015-04-11
There's a menu in the virtual machine window where you select which USB devices are to be disconnected from the host and used by the guest. Ubuntu and Windows XP, respectively, in your case.

---

### Post by Victor_Gilbert on 2015-04-11
> There's a menu in the virtual machine window where you select which USB  devices are to be disconnected from the host and used by the guest.  Ubuntu and Windows XP, respectively, in your case.                 

Thanks BUT in the menu ---- USB ..........          Enable USB Controller + Enable USB (E_H_CI) Controller + USB Device Filters *are all greyed out*.

At last I've taken your advice and ordered a new printer!

Victor

---

### Post by Vladlenin5000 on 2015-04-11
> **Victor_Gilbert said:**
> USB Device Filters *are all greyed out*.

Yeah, about that... A detail I often miss because the very few times I had to use virtualization + external USB devices I had done the required step by command line. Here's an "old" but still relevant tutorial: [http://www.dedoimedo.com/computers/virtualbox-usb.html](http://www.dedoimedo.com/computers/virtualbox-usb.html)

Steps 4-5 illustrate the same issue and solution. The solution points to a GUI tool to manage users' and groups' permissions, "Users and Groups", that's no longer installed by default in Ubuntu. Although you can do it from the cli, in order to follow the tutorial to the letter you can simply install it from the Ubuntu Software Center (search: gnome-system-tools). So, just open it (dash search: users...) and add the settings of the aforementioned step 5. That should do it.

---

### Post by Victor_Gilbert on 2015-04-12
> and add the settings of the aforementioned step 5. That should do it.                 

Unfortunately not. ALL I did was tick my name!
 
                            >  Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

Removed the tick from **Group 'vboxer' Properties** .... but when restarted still got the above message. Installed dkms package How to execute? :

> [COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

Can't wait for my Hp all in one to arrive.

vicsat

---

### Post by Victor_Gilbert on 2015-04-15
Thanks Vladenin5000

The Hp Inkjet is up and running

vicsat

---

### Post by bofe on 2015-04-15
maybe try to boot tiny windows xp from usb
note tiny windows is user created so its good practice to first scan it with AV because I think that most come with virus already placed inside the OS

---


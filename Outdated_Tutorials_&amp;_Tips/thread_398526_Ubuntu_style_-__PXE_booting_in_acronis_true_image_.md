---
title: "Ubuntu style -  PXE booting in acronis true image enterprise server 9.1 (all)"
date: 2007-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by db260179 on 2007-04-01
Hi People,

This is a quick howto get a product called 'Acronis True image Enterprise 9.1 server' PXE booting using Ubuntu OS as the PXE imager, tftp server.

Everyones setup will vary, but the setup I have in our school is as follows:

2x Windows 2003 domain controllers, 6x Ubuntu Dapper servers (doing varies tasks)

I would just like to share my experience of getting acronis true image server 9.1. **([http://www.acronis.com](http://www.acronis.com)) **running in this setup.

Scenario: School in uk, for quick imaging to pc's and servers incase of disk failure.
Don't want to mess around with CD's or floppys or any other silly removable media.

PXE is the quick solution. Trialed out the acronis product, worked satisfactory.

Then tried the pxe solution, EEK! refused to boot from any pc? Looked on acronis forum, a few people had the same problem. A few suggestions from people where posted, but no real solution to the issue. UNTIL NOW! Yipeee....

OK!, here's how i got it working - not perfect, but works really well.

First of all, the RIS on a windows server doesnt work. I had to use Ubuntu linux box to do all grunt work.

Here's the Steps:

1. This guy was the only one who seemed to get it to work **[http://www.wilderssecurity.com/showthread.php?t=146713&highlight=kernel.dat](http://www.wilderssecurity.com/showthread.php?t=146713&highlight=kernel.dat)**

A bit confusing, and not really telling you how to get it working?

After searching around the internet i found these two articles.

**How to setup G4L (Ghost4Linux)**

**[http://www.opensourcehowto.org/how-t...inux--g4l.html](http://www.opensourcehowto.org/how-t...inux--g4l.html)**
and this

**How to setup PXE booting on Ubuntu**

**[http://myy.helia.fi/~karte/ubuntu_pxe.html](http://myy.helia.fi/~karte/ubuntu_pxe.html)**

Ok, i thought i'll put this to good use. I followed the instructions (testing on a spare pc), using a ubuntu dapper server 32bit and 64bit. then...

2. On instruction number 11 (**How to setup G4L (Ghost4Linux**)
., i added this

[B]LABEL acronistrue
MENU LABEL ^W: Acronis True Image
kernel boot/kernel.dat
append initrd=images/ramdisk.dat vga=791 ramdisk_size=32768 acpi=off quiet noapic[/B]

To the Default and labeled it W (Reason being that the latest G4L is 0.22, and has changed the menu list, you'll see once you download g4l-0.22.iso)

Obviously created the necessary folders in the **/tftpboot folder = boot and images**, then copyed the **ramdisk.dat and kernel.dat** from a pre made recovery iso image within acronis.

3. I have two windows servers 2003 running the dhcp to the clients, so i had to add some entry's to the server options in the dhcp manager.

**Option 66 and 67**

[B]Option 66 is the tftp server address, so i entered 172.16.0.12 or the dns name
then option 67
Option 67 is filename for booting, i entered pxelinux.0[/B]

If you dont enter the above then it takes the clients twice as long to find you tftp server, and most likely will have a "**proxydhcp 40 error**" come up on the client trying to boot.

**_(NOTE: The 'How to setup PXE booting on Ubuntu' above tells you howto adjust DHCP for ubuntu.)_**


Thats it!

So now i have Acronis true image pxe booting and G4L (Ghost4Linux), Cool!!!

If you are still a bit confused, send me a message or email me on [email]db260179@hotmail.com[/email] for config files etc.
:KS

---

### Post by copilot on 2007-11-20
Thanks, your post was very useful. I'm currently working on getting a catch-all pxe server going. I've got PING and G4L going, and as soon as I can get my hands on an updated kernel module I'll have acronis as well.  Now all that's left is a couple versions of ghost and I'll be covered. Thanks again!

---

### Post by db260179 on 2007-12-13
No problem, hope this comes in use to you and other people

---


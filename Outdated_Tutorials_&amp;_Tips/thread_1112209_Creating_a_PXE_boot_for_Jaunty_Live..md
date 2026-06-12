---
title: "Creating a PXE boot for Jaunty Live."
date: 2009-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by chrismyers on 2009-03-31
Requires:[INDENT]Ubuntu server for PXE environment (tested on Jaunty 9.04 server).
Wired network.
PXE boot capable network card on target machine.
[/INDENT]On the Ubuntu server:

Login as root or sudo su -

Create the following directory structure:[INDENT]/pxe

/pxe/images

/pxe/images/ubuntu

/pxe/pxelinux.cfg
[/INDENT]Download syslinux-xxx.zip from here:

[http://www.kernel.org/pub/linux/utils/boot/syslinux/](http://www.kernel.org/pub/linux/utils/boot/syslinux/)

Extract the files.

Find menu.c32 & pxelinux.0 & copy them to the /pxe directory.

*The other syslinux files & zip are no longer needed and can be deleted.*

create a file /pxe/pxelinux.cfg/default & paste in the following:[INDENT]DEFAULT menu.c32
PROMPT 0
NOESCAPE 0
ALLOWOPTIONS 0
TIMEOUT 600
 
MENU TITLE PXE Boot Menu

LABEL Ubuntu Jaunty Live Desktop
kernel images/ubuntu/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=192.168.1.101:/pxe/images/ubuntu initrd=images/ubuntu/casper/initrd.gz -- splash

LABEL Ubuntu Jaunty Live Install
kernel images/ubuntu/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=192.168.1.101:/pxe/images/ubuntu initrd=images/ubuntu/casper/initrd.gz -- splash only-ubiquity
[/INDENT]Copy the contents of the Ubuntu live CD into /pxe/images/ubuntu

Now install dnsmasq & nfs-kernel-server[INDENT]apt-get install dnsmasq nfs-kernel-server
[/INDENT]edit /etc/dnsmasq.conf & replace all text with:[INDENT]no-hosts
server=/localnet/192.168.1.1
dhcp-range=192.168.1.40,192.168.1.50,2h
dhcp-boot=pxelinux.0
enable-tftp
tftp-root=/pxe
resolv-file=/etc/nameservers
dhcp-option=3,192.168.1.1
[/INDENT]***Make sure you replace the ip addresses, netmasks etc with ones suitable for your network.***

edit /etc/exports & replace all text with:[INDENT]/pxe/images *(ro,sync,subtree_check)

[/INDENT]Add your DNS nameservers by creating the new file (this example is for opendns):

nano /etc/nameservers[INDENT]nameserver 208.67.222.222
nameserver 208.67.220.220
[/INDENT]Reboot your server (or restart dnsmasq & nfs-kernel-server).


You should now be able to boot your target client machine to Ubuntu if it has a pxeboot enabled network card (usually accessed by pressing F12 at boot).

This worked for me. I hope this helps.

---

### Post by FrozenCow on 2009-04-04
Thanks for the tutorial! It worked great for me under VirtualBox (both PXE server and client). Though, it took a long time to boot and the performance isn't great, but it works :D.
EDIT: Just tried Xubuntu, which I setup the same way. It runs much faster.

---

### Post by chrismyers on 2009-04-05
No problems.

Now you have done that, you can add other live images, such as clonezilla - for making clone images of any machine (Linux/Windows).

:-)

---

### Post by chrismyers on 2009-04-05
> **FrozenCow said:**
> Thanks for the tutorial! It worked great for me under VirtualBox (both PXE server and client). Though, it took a long time to boot and the performance isn't great, but it works :D.
EDIT: Just tried Xubuntu, which I setup the same way. It runs much faster.

Out of interest. Does your machine take a long time to boot, or is it slow when booted?

If it's slow to boot it could be because its running under VM (or slow network). If it's running slow, this could mean that your client has less than 384 megs of ram.

---

### Post by mbeierl on 2009-05-26
Hmmm... things worked but only up to a point: it "hangs" right after the squashfs message, with no further activity in the pxe client at all.

On the server I see this:
May 26 16:08:08 bootserver mountd[4469]: authenticated mount request from 192.168.0.122:1016 for /pxe/images/ubuntu (/pxe/images)

I have verified that the nfs mount is there and it looks fine from a secondary machine, but I have no idea how to debug the PXE client.

---

### Post by mbeierl on 2009-05-26
Urrrg... Hitting ctrl-c let something go and it booted.  I am baffled at this point...

---

### Post by senile2 on 2009-06-01
I guess I'll use this as a place to stop... I have gone cross eyed reading all the material on how to build a PXE server in Ubuntu, and so far none of them have worked or are missing parts or don't explain well enough how to do it.

Since your thread is dependent on PXE, I have to assume that you have one set up.  Do you know of a good "how-to" document that will help setting one up?  Currently have a system set up with Ubuntu 9.04 server and gnome gui, DHCP3, samba, tftfd, SSH, .... can't remember all the other packages I have installed at the direction of one doc or another.

I am part of a club that takes old computers and refurbs them then gives them to needy kids.  Lots of fun, but after about 500 os installs (manually), there has got to be a better way.

Thanks in advance....

---

### Post by chrismyers on 2009-06-02
Hi Senile2,

Adding other boot images, such as Clonezilla (Ubuntu version) is relatively simple.

First, add the following into /pxe/pxelinux.cfg/default

```
LABEL Clonezilla 
kernel images/clonezilla/live/vmlinuz1 
append boot=live initrd=images/clonezilla/live/initrd1.img boot=live union=aufs netboot=nfs nfsroot=192.168.1.xxx:/pxe/images/clonezilla
```*Note: Change the IP to match that of your server.* 

Create a directoy:

/pxe/images/clonezilla

Download Clonezilla, burn the CD & copy the entire contents of the cd to the clonezilla directory (You no longer need the CD).

Try booting from PXE. You should now have a Clonezilla option.

Cheers.

---

### Post by Davie In Dubai on 2009-06-07
Interesting, but would I be right in guessing that any existing DHCP server on his LAN would stop this from working?

---

### Post by deanhopkins on 2009-07-02
Im having a problem with this whereas the ubuntu installer is telling me that 'No common CD-ROM drive was detected', as my laptop cd rom is broken. 

Obviously, the files that are needed are stored on my ubuntu install on my desktop, and the laptop needs to read from them instead of looking for the CD.

any ideas?

thanks

---

### Post by morphix on 2009-08-03
> **mbeierl said:**
> Hmmm... things worked but only up to a point: it "hangs" right after the squashfs message, with no further activity in the pxe client at all.

On the server I see this:
May 26 16:08:08 bootserver mountd[4469]: authenticated mount request from 192.168.0.122:1016 for /pxe/images/ubuntu (/pxe/images)

I have verified that the nfs mount is there and it looks fine from a secondary machine, but I have no idea how to debug the PXE client.

I receive the same thing and when i check casper.log on the pxe client machine i see:
"mount call failed - server replied: Permission denied." then 
"Unable to find a live file system on the network".

Can someone please help me?

---

### Post by Cyphic on 2009-08-03
Interesting. Always been wondering how to use PXE (I'm a bit bored with Unetbootin and USB-sticks by now..), I'll try this one out tomorrow.

---

### Post by chrismyers on 2009-08-31
> **Davie In Dubai said:**
> Interesting, but would I be right in guessing that any existing DHCP server on his LAN would stop this from working?

Hi Dave.  Yes, you're right. Two dhcp servers could end up handing out the same ip address if dnsmasq.conf is not set up correctly.

Take a look at the following line:

dhcp-range=192.168.1.40,192.168.1.50,2h

This can only hand out only 11 ip addresses:

192.168.1.40-50

To prevent conflicts from happening, make sure that your existing dhcp server (or home router) is not handing out conflicting addresses & you will be OK - For instance: a dhcp server offering address ranges of 192.168.1.2-39 or 192.168.1.51-254 would not conflict with the the above dnsmasq settings.

Cheers.

O:)

---

### Post by neilsanner on 2009-09-04
Hi,

Thank you so much for this tutorial!!! It's the first live cd I've ever managed to boot from the network!:D

Live Ubuntu desktop is not really operational though from my laptop (really slow). I was hoping to use xubuntu instead but, I don't know why, I cannot go past the initial PXE menu. I select xubuntu in the menu and press enter, and it stays there. I've put all the content of the Xubuntu cd in this folder : "/pxe/images/xubuntu"

Here's my "default" file :

```
DEFAULT menu.c32
PROMPT 0
NOESCAPE 0
ALLOWOPTIONS 0
TIMEOUT 600

MENU TITLE PXE Boot Menu

LABEL Ubuntu 9.04 Live Desktop
kernel images/ubuntu/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=192.168.1.101:/pxe/images/ubuntu initrd=images/ubuntu/casper/initrd.gz -- splash

LABEL Xubuntu 9.04 Live Desktop
kernel images/xubuntu/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=192.168.1.101:/pxe/images/xubuntu initrd=images/xubuntu/casper/initrd.gz -- splash

LABEL Ubuntu 9.04 Live Install
kernel images/ubuntu/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=192.168.1.101:/pxe/images/ubuntu initrd=images/ubuntu/casper/initrd.gz -- splash only-ubiquity


```

Any ideas why it doesn't work? It's really strange...

---

### Post by chrismyers on 2009-09-05
> **neilsanner said:**
> Hi,

Thank you so much for this tutorial!!! It's the first live cd I've ever managed to boot from the network!:D

Here's my "default" file :

LABEL Xubuntu 9.04 Live Desktop
kernel images/xubuntu/casper/vmlinuz
append boot=casper netboot=nfs nfsroot=[COLOR=Red]192.168.1.101[/COLOR]:/pxe/images/xubuntu initrd=images/xubuntu/casper/initrd.gz -- splash

[/code]Any ideas why it doesn't work? It's really strange...

Hi Neil,


If you are getting the boot menu, you are 95% there! keep going. :D

Is your pxe server on 192.168.1.101?

You need to make sure that the ip addresses used match your server IP (& netmask)


Cheers.

---

### Post by neilsanner on 2009-09-05
> **chrismyers said:**
> 
Is your pxe server on 192.168.1.101?

You need to make sure that the ip addresses used match your server IP (& netmask)

Hi Chris,

Yes the pxe server is on 192.168.1.101 as specified in the "default" file. I find it weird that Ubuntu boots, but not Xubuntu...:-k As you could see in the default file, I've just cut and paste the ubuntu part, and changed Ubuntu by Xubuntu. And I've copied the whole Xubuntu CD to /pxe/images/xubuntu. If Ubuntu boots, that means that the networking is working and there's probably something else broken somewhere. I've already checked the case of the files names.

Do you have any other ideas why Xubuntu wouldn't boot?

---

### Post by chrismyers on 2009-09-06
Hi Neilsanner,

OK..  Right..

I don't ***know*** the correct answer, but maybe I can help a little.

The basic options for Ubuntu were taken from:

/pxe/images/ubuntu/isolinux/text.cfg

Take a look at the equivalent file in Xubuntu. I may give a clue what you need to set in your 'default' file.

Let me know if this helps O:)

---

### Post by deanhopkins on 2009-09-08
Hi guys, does anyone know if it is necessary to have Ubuntu Jaunty Server edition installed to be able to do this? Will it work from my Ubuntu Jaunty Desktop setup?

If not, will I be able to do it using ubuntu server installed on a vBox inside ubuntu desktop? Thanks

---

### Post by Hazardr on 2009-09-09
Hi

Thanks for this tutorial, it really helped me a lot. I got this to work on Virtual boxes and a lot of laptops but for some reason, some desktop machines hangs at running /Scripts/casper -premount. The only things these desktop machines have in common is that they are all P4 ( 478 ) processors with Via Rhine III onboard ethernet cards

Has anyone ever tried PXE booting into Januty Live with Via Rhine III Onboard NIC?

---

### Post by chrismyers on 2009-09-13
> **deanhopkins said:**
> Hi guys, does anyone know if it is necessary to have Ubuntu Jaunty Server edition installed to be able to do this? Will it work from my Ubuntu Jaunty Desktop setup?

If not, will I be able to do it using ubuntu server installed on a vBox inside ubuntu desktop? Thanks

Hi Dean,

Yes, it's possible to set this up on any Ubuntu server or even desktop.

I specified Ubuntu Jaunty server so that we were all working from the same base.

Minor changes between the Ubuntu versions ***may*** mean that there are small differences that you may need to overcome to get it working properly.

You are free to use any flavour of Ubuntu or any other distro if you wish. :-)

Cheers.

---

### Post by Belac_K on 2009-09-25
I've been successfully PXE booting Jaunty Live for a few weeks now, but it's extremely unpredictable how long it takes.  It seems to hang right after a network link is established ("eth0 link is ready" or some message like that), then sometimes 30 seconds, sometimes two minutes, sometimes an HOUR later it shows that TCP and UDP have been registered and continues booting.  Anyone else have this issue?

---

### Post by Dedors on 2009-10-25
> **Belac_K said:**
> I've been successfully PXE booting Jaunty Live for a few weeks now, but it's extremely unpredictable how long it takes.  It seems to hang right after a network link is established ("eth0 link is ready" or some message like that), then sometimes 30 seconds, sometimes two minutes, sometimes an HOUR later it shows that TCP and UDP have been registered and continues booting.  Anyone else have this issue?

i have the same problem, did you found a solution?

---

### Post by oddbodbloke on 2009-10-26
Hi,

I have had some success in getting this to work.

I have used dnsmasq as was suggested (rather than dhcpd3) which seems to be serving out the relevant files over tftp. The client and the dhcp server seem to be working well, as the PXE menu comes up, the kernel and initrd.gz is downloaded, but it hangs during a call to ipconfig.

I found this out by unpacking the initrd.gz and placing various messages that appear during boot.

The boot hangs during a call to configure_networking() (in /scripts/functions in initrd.gz) specifically on the line 

ipconfig -t 60 ${DEVICE}.

DEVICE is eth0 which is correct. (I tried eth1, but apparently this doesn't exist)

I should also mention that the kernel seems to be loading the correct module for the hardware (sky2).


IPOPTS is empty initially, but when I modify it to "on" in the functions file (so that I may execute a custom ipconfig command) nothing happens then either.

The kernel is still active when it appears it is doing nothing, as  (udev?) messages appear when usb devices etc are plugged in / out. 

I suppose my question would be, what is the ipconfig command to get this to work.

As far as I can tell, the ipconfig command belongs to klibc, and it seems that there is (was) some kind of problem with dhcp relays, but it looks as though this was fixed in 8.10. Could this be persistent in the Jaunty live cd? 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1593256.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1593256.html)

I'm not entirely sure what an dhcp relay is, but it's possible that my set up contains one as the client is connected via a router.

---


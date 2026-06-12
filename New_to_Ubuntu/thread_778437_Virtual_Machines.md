---
title: "Virtual Machines"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Jookia on 2008-05-02
Are there any good Virtual Machines out there that are easy to use? All I need is internet connection on a virtual machine. I have a help request for VirtualBox, so these will be my alternatives if that doesn't work out.

---

### Post by Xiong Chiamiov on 2008-05-02
Haven't used it in a while, and that was on Windows, but there is of course VMware.

---

### Post by seetho on 2008-05-02
I just tried VirtualBox on my XEON machine with Hardy.  Works like a charm - internet and all.  Very easy to setup and they have good documentation on their web-site.  You should give it a go.

---

### Post by drsox1899 on 2008-05-02
+1 for Virtual Box.  Much easier than VMWare.  Some tricky parts but there a lot of HowTo's and guides on this forum and the VB forums.  Very quick to run.

---

### Post by Jookia on 2008-05-02
I can't get it to run the internet. It doesn't show the connection.

---

### Post by iSplicer on 2008-05-02
+1 For virtualbox.

Just select bridged networking, should work fine.

---

### Post by seetho on 2008-05-02
I just use the default NAT.  It just works.  Didn't need to configure anything.

---

### Post by Jookia on 2008-05-02
> **iSplicer said:**
> +1 For virtualbox.

Just select bridged networking, should work fine.

How?

---

### Post by drsox1899 on 2008-05-02
I second the idea that all you need to do is run in NAT mode.  Bridge mode is for accessing other PCs etc on an internal network.

NAT setting in VB is setup when the VB is not running.  As part of the list of virtual devices is a networking section.  

Here's a section from the VB user's manual


Quote " ....


3.7.5 Network settings
The &#8220;Network&#8221; section in a virtual machine&#8217;s Settings window allows you to configure
how VirtualBox presents virtual network cards to your VM, and how they operate.
   VirtualBox can simulate up to four virtual network cards for a virtual machine. These
cards are presented as AMD PCNet cards, which most current operating systems (as
well as GNU GRUB) support out of the box, without needing extra drivers.
     Note: Unfortunately, Windows Vista has dropped support for this familly of
     network cards and requires manual driver installation; see chapter 4.2.4, Win-
     dows Vista networking, page 49.
   When you first create a virtual machine, VirtualBox by default enables one of these
four cards and selects &#8220;Network Address Translation&#8221; (NAT) for it. This way the the
guest can connect to the outside world using the host&#8217;s networking and the outside
world can connect to services on the guest which you choose to make visible outside
of the virtual machine.
   In most cases, the &#8220;NAT&#8221; setting will work fine for you. However, since VirtualBox
is extremely flexible in how it can virtualize networking, we have dedicated an entire
chapter of this manual to discussing networking configuration; please see chapter 6,
Virtual networking, page 59.


....  """ Unquote

You can get the manual (if you haven't got it) from here :

[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

There is usually a choice of three types of NIC cards.  Pick the middle one ( it's a 100mbps card ) and is enabled wrt drivers automatically.  If you try the 1000mbps card then you have to look for drivers on the Intel website.

PS  I'm assuming you want to run Windows in Ubuntu.

---

### Post by Jookia on 2008-05-02
I have it setup on defaults with a generated MAC address. No connection.

---

### Post by dokdoom on 2008-05-02
VMWare is very nice and easy to administor.

---

### Post by drsox1899 on 2008-05-02
> **Jookia said:**
> I have it setup on defaults with a generated MAC address. No connection.

Please give some more details about your Virtual Machine setup.  

Maybe take a screenshot of your setup page.

PS What version of Ubuntu are you running.  The VB repositories don't yet have 8.04.  PLUS I remember that VB works best when using the version direct from VB - not the version in the Ubuntu repositories

---

### Post by drsox1899 on 2008-05-02
Just to validate, I setup a WinXp in VB 1.5.6.  No problems at all.  VB Networking assigned an IP number and I got out to the Internet and also connected to one of my servers through its IP address.

---

### Post by drsox1899 on 2008-05-02
BREAKING NEWS !!!!


New version of Virtual Box now released :

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

Version 1.6

Supports Ubuntu 8.04 !!

---

### Post by riccaliolio on 2008-05-06
Hi All! I am new here in this forums but I am not really completely unfamiliar with Linux (been using it for some time now).

I am actually an MS XP user with a virtual machine running Ubuntu Hardy Heron. I was curious what Ubuntu users think is the best VM application, and I think 80% are using Virtual Box maybe because

[INDENT]- it works well with Linux, and[/INDENT]
[INDENT]- it is open-source! ^_^[/INDENT]

---

### Post by adrian.todireanu on 2008-12-22
I installed XP SP3 in VirtualBox OSE 2.0.4 but, instead of the four adapters that the manual claims should be available, there's only two, PCNET something and the "XPMachine" doesn't find any drivers for them, so no network, just an Ethernet Controller in Device Manager. What to do?

---

### Post by Zeedok on 2008-12-22
> **Jookia said:**
> I can't get it to run the internet. It doesn't show the connection.

Correct me if I'm wrong, but doesn't he/she need to add the vbox user group and give it permissions??

I remember doing that when I installed my VBox, and now whenever I install a new virtual machine everything 'just works'.

---


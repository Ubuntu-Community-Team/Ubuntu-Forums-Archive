---
title: "[HOWTO] Install VirtualBox in Ubutnu Intrepid Ibex 8.10"
date: 2009-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by lunatico on 2009-03-14
Hey!

This tutorial is intended for those of you interested on installing a virtual environment where you can install other operating systems, either to test them or because there is still that piece of software that will only run on windows on which you rely so much that your life is not complete without it. Or just to have fun.

I have used several virtualization applications and [VirtualBox]("http://www.virtualbox.org/") is my preferred choice. It is very easy to install, very stable, performance is great, CPU usage is not crazy and configuration is simple-click easy. Things "just work". After installing it a few times I found that there are a few tricks to have a perfect installation on which everything works, I'll share them here.

I have tested this on a Thinkpad T61 and a T60p running Ubuntu 8.10. This is not a technical tutorial, it's just an installation procedure. You can bring technical questions here but I don't promise I'll have the answers. VirtualBox has a great [forum]("http://forums.virtualbox.org/") for this.

Note 28/03/2010: This will also work on 9.04 and 9.10.

[FONT="Arial Black"]Let's start:[/FONT]

1. Download the PUEL version of VirtualBox. It's important that you get the PUEL version and not the OSE version from repositories as the OSE does not include RDP, USB, iSCSI and SATA support.

[INDENT]Download from these links VirtualBox for Ubuntu 8.10 ("Intrepid Ibex") [32-bit]("http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_i386.deb") | [64-bit]("http://download.virtualbox.org/virtualbox/2.1.4/virtualbox-2.1_2.1.4-42893_Ubuntu_intrepid_amd64.deb") | [All Linux downloads]("http://www.virtualbox.org/wiki/Linux_Downloads").[/INDENT]

Save the deb package to your desktop, we will use it twice.

2. Double click the deb package and install. At this point VirtualBox is installed and you can start using it and install an OS. But you might find problems using USB devices, for that you need some fixes.

3. Go to Systems -> Administration -> Users and Groups. Click 'Unlock', select your username and click 'Properties'. Go to the 'User Privileges' tab and tick the 'Use VirtualBox' option. (Now that you are there I would recommend ticking all options) Click OK.

4. Now click the 'Manage Groups' button and look for vboxusers, select it and click 'Properties'. Make sure your username is selected as a group member and take note of the Group ID, we will use it on the next step. Click OK, Close and Close.

5. Now on a terminal type:

```
gksudo gedit /etc/fstab
```

and at the end of the file add the following line

```
none /proc/bus/usb usbfs devgid=XXX,devmode=664 0 0
```

where XXX is the group ID for the group vboxusers. Save and close.

6. Restart you computer and then double click the deb package again and go through the installation again. This should fix some permission issues generated on the first installation which where causing the USB devices to be greyed out.


That's all.
:D
[FONT="Arial Black"]
Post installation tips[/FONT]

[LIST]
[*]Getting your mouse and keyboard back to the host:
[/LIST]
[INDENT]Hit the Right Ctrl key. This can be changed by going to File -> Preferences -> Input. But a much better option is to install the Guest Aditions.[/INDENT]

[LIST]
[*]Install Guest Aditions:
[/LIST]
[INDENT]Open VirtualBox, select your guest machine and start it. Once it's up click on Devices -> Install Guest Additions. Follow the installation wizard on the guest and reboot it.

Map a folder in your host machine as a network drive in your guest:
You need the Guest Aditions installed for this to work. Open VirtualBox, select your guest machine on the left and click Settings. Go to Shared Folders and click the + to Add Share. Browse to the folder you want to share on your host and give it a <sharename>. Click OK to both windows and start your guest virtual machine.
On the guest machine open a command line and type:

```
net use x: \\xboxsvr\<sharename>
```

This will map the folder you shared as drive X on the guest.[/INDENT]

[LIST]
[*]Fix choppy audio:
[/LIST]
[INDENT]Open VirtualBox, select your guest machine on the left and click Settings. Go to Audio and select PulseAudio as the Host Audio Driver. This for the hardware on which I wrote this tutorial, may change with other hardware.[/INDENT]

[LIST]
[*]Why does my Skype dies when I try to run it on my VirtualBox guest?
[/LIST]

[INDENT]I know there is a Skype version we can use on Ubuntu and it works very well, I use it. But there is one thing it lacks: sending SMS to mobile phones! So for that reason, having Skype on your guest machine is not a bad idea if you ever need to send SMS with it.

After I installed Skype it kept just dieing, without giving any errors, just a Windows error saying that the application had failed. Anyway... after Googleing for a while I found out that my guest system was not using my CPU's virtualization capabilities. So if you are suffering this problem you could try this.
I'll give a general explanation, no step-by-step instructions as this will be different on other hardware, but the idea is the same.
Reboot your computer and go into the BIOS, look for something related to virtualization support and enable it. It is usually under CPU or Processor settings. Then boot normally and open VirtualBox, select your virtual guest and click Settings -> General -> Advanced tab and tick the 'Enable VT-x/AMV-V' option.
Start your guest machine and start Skype, this may have fixed your problem.[/INDENT]


If you have any other tips or comments post them here and I'll update the tutorial.

---

### Post by quixote on 2009-05-08
I'm confused about one thing: why isn't it *sudo* apt-get install and-so-on?  It was the last couple of times I installed vbox (under Hardy, I think.  Maybe once under Gutsy, too).  But now both here and on the virtualbox site itself the instructions imply that one installs as an ordinary user.  That makes not much sense to me.  What am I missing?

---

### Post by lunatico on 2009-05-09
> **quixote said:**
> I'm confused about one thing: why isn't it *sudo* apt-get install and-so-on?  It was the last couple of times I installed vbox (under Hardy, I think.  Maybe once under Gutsy, too).  But now both here and on the virtualbox site itself the instructions imply that one installs as an ordinary user.  That makes not much sense to me.  What am I missing?

Well first if you run as sudo you are installing as super user root, probably it used to be like that before due to access permisions to certain resources or something like that. Then apt-get install and so on because it used to be included on the software sources, it had to be built speficicaly for each distro, but it looks like now the installer is better from vbox's side. People in virtualbox forums would know the answer.

---

### Post by quixote on 2009-05-09
Yeah.  I'd assume vbox needs that kind of access.  Strange.  I'll dig around on the virtualbox forums and see if anyone explains it . . . although for forums where people actually answer questions you have to come to ubuntu :-D !

---


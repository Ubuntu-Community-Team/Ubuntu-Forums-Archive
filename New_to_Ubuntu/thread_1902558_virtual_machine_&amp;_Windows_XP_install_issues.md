---
title: "virtual machine &amp; Windows XP install issues"
date: 2011-12-31
forum: New to Ubuntu
---

### Post by samikearns on 2011-12-31
Hiya,

I feel like a complete dunderhead here.  I've installed (and uninstalled) Virtualbox many times and tried to run/install Windows XP.  I've been able to create a virtual machine, but whenever I try and start it up and install from my CD, there's no progression at all and it seems to freeze, which means I need to do a force quit.  Then when I try again, I get this error.....
[COLOR=Red]Failed to open a session for the virtual machine Windows XP.

The device helper structure version has changed.

If you have upgraded VirtualBox recently, please make sure you have terminated all VMs and upgraded any extension packs. If this error persists, try re-installing VirtualBox. (VERR_PDM_DEVHLPR3_VERSION_MISMATCH).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}[/COLOR]

or sometimes I get the error telling me to install dkms (which i had done many times) and execute modprobe vboxdrv as root.

I've read a few threads on here to no avail.  What am I doing wrong???
I'm running 11.10 (64bit I think).

Any help to get this running would be gratefully received.
Cheers,
Sami.

---

### Post by Ms. Daisy on 2011-12-31
> **samikearns said:**
> ... but whenever I try and start it up and install from my CD, there's no progression at all and it seems to freeze, which means I need to do a force quit. 
Just a thought, how long did you let it go before you decided it had frozen?  When I installed XP on my machine (host), the installation took a long time. If you're in a VM, then it would probably take even longer.  I've put all kinds of stuff in VMs, and some of the installations seem to hang, but they do ultimately succeed if I let them go.

---

### Post by BC59 on 2011-12-31
You have to reinstall Virtualbox. If you install it through Software Center is easy. If not, run > sudo apt-get remove virtualbox and then download the latest .deb from [Virtualbox]("https://www.virtualbox.org/wiki/Linux_Downloads") site and double click to install it through Software Center.
And I hope you are not using a Windows XP 64bits!

---

### Post by Ms. Daisy on 2011-12-31
> **BC59 said:**
> You have to reinstall Virtualbox. If you install it through Software Center is easy. If not, run  and then download the latest .deb from [Virtualbox]("https://www.virtualbox.org/wiki/Linux_Downloads") site and double click to install it through Software Center.
And I hope you are not using a Windows XP 64bits!
The OP said>  I've installed (and uninstalled) Virtualbox many times  BC59, are you suggesting that he download the latest .deb this time?
And why do you hope he's not using Windows XP 64 bits?

---

### Post by Paqman on 2011-12-31
Have you done the opther things it suggested? Namely:

> **samikearns said:**
> please make sure you have terminated all VMs and upgraded any extension packs.
and:
> 
execute modprobe vboxdrv as root.


You could try creating a Linux VM and see if you get the same problem. I'm guessing you will, but it'll be useful to rule some variables out.

---

### Post by samikearns on 2011-12-31
Ms Daisy - thanks for your response.  I let it go for about an hour (yesterday) and it was still at 0%.  It was then I thought it probably wasn't doing anything.

BC59 - thanks also.  I did what you recommended (uninstalled virtualbox) and downloaded the latest from the virtualbox site.  I double clicked and now software centre is running very slowly and it's taken quite a few goes to get where I think is nowhere.  Now when I click on the virtualbox download and when software centre eventually opens, virtualbox 4.1 opens (with a green tick AND an 'install' button) with the description......
Breaks existing package'virtualbox-4.1' conflict virtualbox-4.1()

I seem to have gone backwards.  I've also restarted my laptop, hoping that would help.

Paqman - yes, I tried doing everything it asked me.  But when I tried executing modprobe vboxdrv as root, I got a fatal message that it couldn't find/recognise vboxdrv.

What now???  Any other suggestions?
Sami.

---

### Post by Paqman on 2011-12-31
> **samikearns said:**
> Paqman - yes, I tried doing everything it asked me.  But when I tried executing modprobe vboxdrv as root, I got a fatal message that it couldn't find/recognise vboxdrv.


You've not got the Virtualbox kernel module loaded then.

Start from scratch. Install Synaptic if you don't already have it and use it to "completely uninstall" Virtualbox, check that you've got dkms and your kernel headers installed, then add the Virtualbox repo (if you haven't already) and install Virtualbox. While it's installing click on the progress box to open the little window showing the output of the process and post it all here. That will show where the install process is going awry.

---

### Post by BC59 on 2011-12-31
And just ensure that all necessary packages are completely installed and configured-run
sudo dpkg --configure -a
sudo apt-get -f install

---

### Post by samikearns on 2011-12-31
OMG - Thank you Paqman and BC59 for your advice.

I've had Ubuntu for a few months, but I'm still quite new and a bit slow (sometimes) with computer literacy.

Any chance of clear English instructions for what you advised me to do in your last post?

How do I check if I have Synaptic?  And if I don't have it, where do I get it from?

Apologies for the bother, but thanks.

Sami.

---

### Post by BC59 on 2011-12-31
For Synaptic install it through Ubuntu Software Center. It's not installed by default in Ubuntu 11.10.

For the commands run them on a terminal. To open a terminal push CTRL+ALT+T, paste the commands with SHIFT+ALT+V and Enter. Then insert your password.

First run separately the following commands to ensure the packages are installed correctly:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

And then to restore Virtualbox:

```
sudo apt-get remove virtualbox-dkms
sudo apt-get install virtualbox-dkms
```

---

### Post by samikearns on 2011-12-31
Thanks BC59.  I've done all that.  

The software centre has synaptic package manager seems to be already installed (there's a green tick on it).  And below is the trail of what took place in the terminal.  btw, thanks for the shortcut.  I was just searching for the terminal each time in the dash home folder.

sami@sami-MSI-Notebook-VX600:~$ sudo dpkg --configure -a
[sudo] password for sami: 
sami@sami-MSI-Notebook-VX600:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
sami@sami-MSI-Notebook-VX600:~$ sudo apt-get remove virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
sami@sami-MSI-Notebook-VX600:~$ sudo apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
sami@sami-MSI-Notebook-VX600:~$ 

There remains a problem with the virtualbox installation/removal, it seems.  Have I done everything right?

Thanks,
Sami

---

### Post by Paqman on 2011-12-31
> **samikearns said:**
> There remains a problem with the virtualbox installation/removal, it seems.

```
sudo apt-get remove --purge virtualbox-4.1
```

Or open Synaptic and click on "remove completely" for that package.

---

### Post by samikearns on 2011-12-31
OK, thanks Paqman.  I ran the script first.  Below is what I got....

sami@sami-MSI-Notebook-VX600:~$ sudo apt-get remove --purge virtualbox-4.1
[sudo] password for sami: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
sami@sami-MSI-Notebook-VX600:~$ 


Then I went to the software centre to uninstall the synaptic package manager which contained three items...
'Install packages using the apt protocal-gtk+fontend' apturl;
'Gstreamer code installer' gnome-codec-install; and 
'Gnome application that manages apt updates' update-manager.  

I clicked 'remove all' and below is what I got almost immediately into the removal...

An unhandleable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the virtualbox-4.1 package. This might mean you need to manually fix this package.


I've clicked OK for this message.  I still seem to have the synaptic package manager.

Sami.

---

### Post by Paqman on 2011-12-31
Er, why are you trying to uninstall Synaptic? It's Virtualbox that's the problem, Synaptic is potentially part of the solution. Reinstall synaptic, apturl, update-manager and gnome-codec-install if they aren't still on your system.

---

### Post by samikearns on 2011-12-31
Because that's what I understood you asked me to do when you said to open synaptic and click on 'remove completely' for that package...Obviously, I misunderstood.

Err, what now???

Many thanks
Sami

---

### Post by Ms. Daisy on 2011-12-31
> **BC59 said:**
> For Synaptic install it through Ubuntu Software Center. It's not installed by default in Ubuntu 11.10.

For the commands run them on a terminal. To open a terminal push CTRL+ALT+T, paste the commands with SHIFT+ALT+V and Enter. Then insert your password.

First run separately the following commands to ensure the packages are installed correctly:

```
sudo dpkg --configure -a
``````
sudo apt-get -f install
```And then to restore Virtualbox:

```
sudo apt-get remove virtualbox-dkms
``````
sudo apt-get install virtualbox-dkms
```

samikearns, you'll get this sorted out.  Just slow down and read very carefully BC59's post (the one I re-posted here.)  I added a few code tags to make it more explicit.

Now for a little info for you so you understand what we're recommending and what it will do: Ubuntu has the [Ubuntu Software Center]("http://www.ubuntu.com/ubuntu/features/ubuntu-software-centre") where you can install and remove software specifically designed for Ubuntu. It takes care of all the separate packages and dependencies for each program. However, the Software Center sometimes does not completely remove all the packages.  The [Synaptic Package Manager]("https://help.ubuntu.com/community/SynapticHowto") is just that- you can see all the packages and dependencies for software. 

So what everyone is suggesting is that when you have uninstalled virtual box countless times, you didn't completely remove the entire program.  We want you to remove the whole thing through the Synaptic Package Manager.  Then when you reinstall it, hopefully any broken or missing packages/dependencies will be fixed.

---

### Post by Paqman on 2011-12-31
> **samikearns said:**
> Because that's what I understood you asked me to do when you said to open synaptic and click on 'remove completely' for that package...Obviously, I misunderstood.


I see. I was actually showing you the GUI way of achieving the same thing as the command line version, hence "OR open Synaptic and...". Don't worry though, no real damage done. Reinstalling things you've accidentally removed is harmless.

If you've reinstalled everything then the problem now becomes sorting your borken Virtualbox package. Open up Synaptic and see what kind of status the package virtualbox-4.1 is in. The command I gave should have removed it, but the command line output you posted didn't say whether it did or not. It's possible the package will be listed as "broken" in Synaptic.

I would suggest adding the Virtualbox repository. Instructions are on [this page]("https://www.virtualbox.org/wiki/Linux_Downloads"), under "Debian-based Linux distributions". With that repo enabled, hit "reload" in Synaptic and reinstall/install virtualbox-4.1

---

### Post by samikearns on 2011-12-31
Thanks Ms Daisy and Paqman.  

As in my previous post
> **samikearns said:**
> OK, I ran the script first.  Below is what I got....

sami@sami-MSI-Notebook-VX600:~$ sudo apt-get remove --purge virtualbox-4.1
[sudo] password for sami: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
sami@sami-MSI-Notebook-VX600:~$ 


I'm still getting the same messages.

And I tried to open synaptic, but after typing in my password got this error message....


An error occurred

The following details are provided:
E: The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

It's 3am here and I'm going to turn in for the night.  Hope to pick it up again tomorrow.
I really appreciate all the help.
Sami.

---

### Post by samikearns on 2012-01-01
Hi everyone,

Happy New Year.

I've also got an error notice sitting in my 'toolbar' on the top of my screen.  It says....

[COLOR=Red]An error occurred.  Please run Package Manager from the right click menu or run apt-get in a terminal to see what is wrong.  The error message was: 'Unknown error: '<type 'exceptions.SystemError'>' (E:The package virtualbox-4.1 needs to be reinstalled, but I can't find an archive for it)'.  This usually means that your installed packages have unmet dependencies.[/COLOR]

With the options: Show updates, Install all updates, Check for updates, Show notifications (ticked), and Preferences.  But apart from Preferences and Check for updates, I get a range of error messages (probably a derr moment???)

Install Updates provides the following error message...

[COLOR=Red]An unhandeable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install the software and to perform other package management related tasks
Details
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the virtualbox-4.1 package. This might mean you need to manually fix this package.[/COLOR]


Show Updates provides the following error message...

[COLOR=Red]Not all updates can be installed
Run a partial upgrade to install as many updates as possible.
This can be cause by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu[/COLOR]

with the options of [COLOR=Red]Partial Upgrade[/COLOR] or [COLOR=Red]Close[/COLOR] and when I click Close, another error message is provided... 

[COLOR=Red]Software index is broken
It is impossible to install or remove any software.  Please use the package manager "Synaptic" or run sudo apt-get install -f" in a terminal to fix this issue at first.[/COLOR]
Which I've done but again get the error that virtualbox needs to be reinstalled, but cant find an archive for it.

Your thoughts on this and my last post???

Thanks in advance.
Sami.

---

### Post by Paqman on 2012-01-01
> **samikearns said:**
> again get the error that virtualbox needs to be reinstalled, but cant find an archive for it.


Have you tried adding the archive for it?

---

### Post by samikearns on 2012-01-01
> **Paqman said:**
> Have you tried adding the archive for it?


No........ coz I don't know how :(

---

### Post by Paqman on 2012-01-01
> **samikearns said:**
> No........ coz I don't know how :(

No worries, [go here]("https://www.virtualbox.org/wiki/Linux_Downloads") and check the section "Debian-based Linux distributions".

Basically you want to:
```
gksudo gedit /etc/apt/sources.list
```
Add:
```
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib

```
Save the file then:
```

wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install --reinstall virtualbox-4.1

```

---

### Post by larrypg on 2012-01-01
Hello,

I installed VirtualBox OSE from the software center just a few days ago.  Granted it is version 4.04 but it worked with no problems installing Kubuntu 11.10 and Windows 8 in it.  That might be easier than trying to install it from an oracle deb.

---

### Post by Haneef Mubarak on 2012-01-01
Installing it from an Oracle deb is better, but anyways: What are your computer specs?

---

### Post by anewguy on 2012-01-01
I think I would try the following in a terminal window:

sudo apt-get purge -f virtualbox-4.1



I believe you will still get the error.  If not, then go into the package manager and remove it.


I don't believe the base package name used with apt is really virtualbox-4.1.  I think the base package is actually just called virtualbox.  I think these errors regarding virtualbox-4.1 are introduced because of a bad package name.  The base package name of virtualbox is what you should be using with apt.

I would first try:

sudo apt-get purge -f virtualbox

I *think* that should get around your problem, unless you installed virtualbox using a different method than either apt-get or synaptic package manager.  Even in the software center it lists the virtualbox package name as just virtualbox.

Once you get it all cleaned out, then I also highly recommend going to the oracle site and downloading virtualbox and the extension pack there.  I've never had any problems as long as I have done that.  Remember that to use USB devices you must be sure the controllers are enabled in the virtual machine setup, and be sure to add a USB filter - just add one with nothing in it, as this will default to being able to access all USB devices.

Dave ;)

---

### Post by samikearns on 2012-01-02
Thanks Paqman

I've done all that and have again tried to install the windows into the virtual machine.  It's been going about an hour, but again, its progress is still at 0%.  ???

Computer specs...
Umm, I've got an MSI laptop, 4GB memory, Intel® Pentium(R) Dual CPU T3400 @ 2.16GHz × 2 processor, ATI graphics, 250GBHDD

Thanks, Dave.  I haven't tried what you suggested yet.  

In light of above, should I give it a go Dave and Paqman?  Or is something else called for (and not throwing it out the window lol).

:confused:
Cheers,
Sami.

---

### Post by Ms. Daisy on 2012-01-02
When you're installing Windows in the virtual machine, how much drive space did you give the VM?  I wonder if the virtual drive is too small whether it will successfully install.

---

### Post by anewguy on 2012-01-02
As long as you actually have virtualbox running again, stick with paqman.  They've gotten you this far with success.

As far as the default virtual disk size in the vm, it seems like everytime I have created a vm the default virtual disk size is 8gb - enough to install XP - plus the disk is dynamic so virtualbox just grows the virtual disk as needed.

BTW - do you get through all of the initial screens for XP installation so it is hanging at 0% copied, or do you never see anything on the screen at all?

Is this an XP install disk, or an XP upgrade disk?

Dave ;)

---

### Post by Paqman on 2012-01-02
> **samikearns said:**
> I've done all that and have again tried to install the windows into the virtual machine.  It's been going about an hour, but again, its progress is still at 0%.  ???


Hmm,something is not right there, but it's hard to say what. Could be a lot of things. Make sure that you've given the VM enough resources. Double-check the amount of RAM you've given it. I tend to use dynamically-expanding drives for VMs, size won't be an issue with those as you can give them tons and they'll grow as required. In general I'd say don't mess with the settings for things like network adaptors.

Do you know for sure that your install media is good?

You could try installing Linux into a VM and see what happens.

---

### Post by anewguy on 2012-01-02
+1   Remember that XP takes a minimum of 512mb of memory.  I would give it more.  Are you using the actual CD or an ISO?


Also - perhaps you could start virtualbox from the command line - something like "virtualbox" or maybe "virtualbox-qt".  That may show some errors in the terminal window you aren't seeing otherwise.

Also, the /var/log/syslog may contain more information as well.   You could just look at it in an editor or there are other tools to see only that last "x" entries, etc..  If you think you need one of those post back and we'll help you.  You should pay attention to anything that says "virtualbox" in someway.

Also, as I asked before, does it get past the initial XP install screens and hangs in the "Copying files needed for installation" or the "Copying files"?  Or is it hanging before XP boots?

Dave ;)

---

### Post by samikearns on 2012-01-02
Thanks everyone for your posts.

I'll try and answer all your questions (in order and) as best I can.....

I was giving the VM 512 and fixed disk size of 10G, but tried it again with 750 and dynamically expanding as suggested by Paqman.  I get to the 'First Run Wizard' where I guess I'm trying to install Windows and it's the window '[COLOR=Red]Windows XP: Starting VM[/COLOR]' that gets stuck on 0%.  The message inside that window is...[COLOR=Red] Creating processes for virtual machine Windows XP (GUI/QT) 1/2
[COLOR=Black]
Dave, sorry, I have NO idea what you're talking about re /var/log/syslog etc.  I'm a bit of a numpty when it comes to computer language.  I know more than the average joe, but not a lot more.  sorry.  ](*,)Do you feel like this?

My laptop had Vista (which sux big time and I couldn't reload anyway coz it was on my MSI recovery disks, of which, disk 2 wasn't working) and a friend of mine had a spare XP and registration, so he copied it for me.  That's what I'm trying to boot from; a writable CD with all the docs, files and setup copied to it.

BTW, what's an ISO???  And when I read people loading virtualbox OSE (as opposed to plain old virtualbox), what does that mean?:-k

Have I answered everything?

Thanks,
Sami.


[/COLOR][/COLOR]

---

### Post by mediajunkie on 2012-01-03
hi,

I run 11.10-64bit on Hpdv7, and I had the same message, but got it under control now. 

the only thing I did was remove the extension that are needed for USB support in VB. After I removed that in VB, and un-flagged usb devices in the setup, my virtual winxp started. So this message must be related to a wrong version of extensions installed for the version of VB. 

maybe you could try that. 

note: the package installer is at version 4.1.2  oracle is at 4.1.8. They seem not to have extension packs for 4.1.2, only for 4.1.8. So I guess we will be uninstalling and reinstalling the whole thing from the oracle site. (last time that failed though)

---

### Post by anewguy on 2012-01-03
This is also why we have been saying we would prefer you delete your current virtualbox installation, download virtualbox and the matching extension from Oracle's site, then install that virtualbox, and once running install the extensions.  Right now it sounds like you aren't even getting virtualbox to boot the vm, so it can't even install XP.  Need to get virtualbox to boot to the vm first, then move on to XP. Once you've done that you know things will match, and USB should be fine (you'll still need the empty filter).

---

### Post by Ms. Daisy on 2012-01-03
> **samikearns said:**
> I was giving the VM 512 and fixed disk size of 10G, but tried it again with 750 and dynamically expanding as suggested by Paqman.  I get to the 'First Run Wizard' where I guess I'm trying to install Windows and it's the window '[COLOR=Red]Windows XP: Starting VM[/COLOR]' that gets stuck on 0%.  The message inside that window is...[COLOR=Red] Creating processes for virtual machine Windows XP (GUI/QT) 1/2
[COLOR=Black]

BTW, what's an ISO???  And when I read people loading virtualbox OSE (as opposed to plain old virtualbox), what does that mean?:-k[/COLOR][/COLOR]
[virtual box OSE]("https://www.virtualbox.org/wiki/Editions") stands for open source edition, but it doesnt' apply to versions above 4.0.

An ISO is what you use to install a Linux distribution like Ubuntu.  You download it from [here]("http://www.ubuntu.com/download/ubuntu/download"). Someone suggested earlier that you create a new virtual machine & install Ubuntu on it.  You will download the ISO onto your computer, then you will point the VM to the ISO to use that as the installation of the OS.  Here's the [manual for virtual box]("https://www.virtualbox.org/manual/") if you haven't seen it already. A lot of it is intuitive, but some you will have to read about.

So if you can install ubuntu in a virtual box, then we know that nothing's wrong with virtual box, but something's wrong with your windows installation cd (I'm thinking that's the problem now based on your description of the installation CD).  If you can't install ubuntu, then something's wrong with virtual box. In that case, you should install virtual box from oracle's website.  I thought you had already done that. Have you?

---

### Post by samikearns on 2012-01-03
> **anewguy said:**
> This is also why we have been saying we would prefer you delete your current virtualbox installation, download virtualbox and the matching extension from Oracle's site, then install that virtualbox, and once running install the extensions. .

As I understood it, that's what I did.  I ran the install, uninstall, purge etc commands in a terminal window (just like I was advised) and then downloaded 4.1.8 from virtualbox.org.  However, not sure if I did the extension, did I?


thanks for the explanations, Ms Daisy.  Much appreciated.

Ok, how about I try and do a Linux distro into a vm and see how that goes?????  I'll have a read through the Ubuntu download site and get back to you.

Wish me luck!!!! :)

Cheers,
Sami.

---

### Post by samikearns on 2012-01-03
OK, I've done something else wrong....#-o

I downloaded Ubuntu 10.4 for the VM, which worked great :biggrin: until it tried to run:frown:.  It loaded etc fine.  But when the guest OS (10.4) tried to run I got the following message in a terminal window...
[COLOR=Red]This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.[/COLOR]

What have I done wrong this time, guys??:?

And, what should I be asking my friend re the Windows XP cd?

Cheers,
Sami.

---

### Post by allenh on 2012-01-04
Hi I'm new to Ubuntu after having got rid of Vista and have had similar but not the same problems when trying to load Windows XP, which I like, within Ubuntu 11.10. When I loaded the extension pack, Virtualbox came back and told me it had been altered and then I could not access my XP which I had managed to successfully load. So I went right back to start reloading Ubuntu, Virtualbox then Windows XP and it is now working.  But my main problem has always been that the USB connections have not and do not work within Windows nor have I managed to sort out how I can transfer a file from Ubuntu to XP. 

I'll watch this space to see if Sami is confronted with these problems once he has XP.

I am also finding the Ubuntu jargon hard to get my head around. Even reading the help manual, I can't figure out where I can find vboxusers. And I have just learned from following these threads how you open a Terminal window with CTRL+ALT+T, not that I dare try any of the commands. :)

A big thanks for helping me understand.

---

### Post by anewguy on 2012-01-04
To get USB devices working, go to settings for the VM on the VirtualBox window, look for USB and add a filter - leave everything blank in it (I can't remember if you have to give it a name).  This allows all USB devices to be visible in the virtual machine.

Dave ;)

---

### Post by anewguy on 2012-01-04
> **samikearns said:**
> OK, I've done something else wrong....#-o

I downloaded Ubuntu 10.4 for the VM, which worked great :biggrin: until it tried to run:frown:.  It loaded etc fine.  But when the guest OS (10.4) tried to run I got the following message in a terminal window...
[COLOR=Red]This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.[/COLOR]

What have I done wrong this time, guys??:?

And, what should I be asking my friend re the Windows XP cd?

Cheers,
Sami.

I'm a little off due to an epidural in a nerve root in my lower lumbar spine so forgive me if I'm wrong, but I think you're trying to install a 64-bit version of the guest OS on a 32-bit machine.  If the system you are installing on is 64-bit and if the host OS is 64-bit, then you need to get the 64-bit version of virtualbox.  If the host OS is NOT 64-bit, regardless of the hardware, then you need the 32-bit VirtualBox and the 32-bit version of the guest you  are trying to install.  On the Oracle site they are differentiated if I remember correctly.  Also, you must download the separate extension pack that matches the release and type (32 or 64 bit) of the VirtualBox package you downloaded - the extension pack is a separate download.

Also - if the problem is your VirtulBox install itself (the 32/64 thing) - be sure to use the "Remove" function in the VirtualBox window and remove any vm defs that might be there, since nothing has worked.  Then remove all of the virtualbox you installed before installing VirtualBox itself again.
Dave ;)

---

### Post by samikearns on 2012-01-04
Dave, I hope you're doing ok now.

My host OS is 11.10 64 bit.  Have no idea what version of virtualbox I downloaded (32 or 64).  And like I mentioned previously, I'm not sure I downloaded the extension pack.

Also, I don't know which version of XP I have.  I'll ask my friend.

Cheers,
Sami.

---

### Post by Paqman on 2012-01-07
> **samikearns said:**
> My host OS is 11.10 64 bit.  Have no idea what version of virtualbox I downloaded (32 or 64).

You'll have the 64-bit. However, when you set up a VM, you have to tell Virtualbox whether you want to emulate a 32- or 64-bit machine. If you choose to emulate a 32-bit machine, you'll get the error you reported if you try to install a 64-bit OS.

---

### Post by samikearns on 2012-01-16
Thanks for all your help, guys.  But it's still not working for me.

I'm just gonna give up and install XP alongside Ubuntu and dual boot my machine.

Apologies for the bother.

Cheers,
Sami.

:(

---

### Post by corevalue on 2012-01-16
I'm having similar problems. I've been using Vbox 4.1.6 under kubuntu 11.04 with an XP guest for ages, with USB, until today I needed USB 2.0 support, and duly downloaded and ran the extension pack. That it seems was 4.1.8. I now get the same "device helper..." message telling me about a version mismatch when I try to run the guest. I really do not want to re-install Vbox if it can be helped - I've got too much installed on the Virtual machine.

Is there anyway to recover apart from a re-install?

---

### Post by Haneef Mubarak on 2012-02-21
[LIST=1]
[*]ReinstallingVirtualbox doesn't mean you lose your guests, they are stored in you home folder under VirtualBox VMs.
[*]I am having this problem too, there might be a serious bug in this case...
[/LIST]

---


---
title: "[SOLVED] there is only one app thats keeping from killing windows forever"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by trestamanos on 2008-09-20
Im running Virtualbox (Windows) on Ubuntu 8.04.  For some reason i cant get Windoes (runnng on Virtualbox) to recognize USB.  please help-thanks

Thanks in advance-

tres

---

### Post by k33bz on 2008-09-20
Instead of trying to get Quicken to work on Linux. You can try one of the many accounting programs available to Linux. Most of which will import all your Quicken Book data.

---

### Post by neurostu on 2008-09-20
If Quickbooks 2003 works in wine then try that... if you absolutely need Quickbooks to work you can run it in VirtualBox, VMWare or Visualbox.

I would advise against using wine with any software that is mission critical. Wine is a great product that can open up a lot of possabilities for running programs in linux, but it can still have problems...  I'm guessing what I'm saying is be careful with wine.

Also have you ever considered dual booting?

---

### Post by jcwmoore on 2008-09-20
have you looked at GNUCash as an alternative to quickbooks?

back to your question, i would recommend VirtalBox and use a Windows XP VM (vista is resource hungry and probably would run poorly in a VM)  for those windows only apps you need.  I really like the ability to save a snapshot of your virtual hard drive and restore your VM if things get messed up

---

### Post by Therion on 2008-09-20
IMO, Virtual Box is a snap to install and use.

Download the latest version [HERE](http://www.virtualbox.org/wiki/Downloads) then use [this tutorial](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html) to install it.  
Don't use the download on the first page of the tutorial; go straight to the Installation section.

Post back or PM if you need help getting it set up.  I just helped someone else install it earlier this morning.

---

### Post by bpalone on 2008-09-20
What Therion said.  

I use VirtualBox because I have about three (actually eight) apps that I need that are not available in Linux.  I use QuickBooks Pro 2007 and so far it appears to work fine in the virtual machine.  I did, however, have to put my data files in the virtual hard drive.  It did not like them being out on the real HD, complained about not being a network version.

As always, KEEP GOOD BACK UPS.  I learned the painful way a few years ago when I had to redo a whole years books when a HD failed.  Gained a bit of religion after that.

You may also want to consider keeping a dual boot system around.  Some of my apps just perform better when that OTHER OS has the whole system.  If you are going to need a Windows OS, you can still get 2000 professional from some places.  I personally think it was M$'s best os and it is the last one without the NT Call Home.

Good luck and enjoy both Linux and Virtual Machines (which ever flavor of that you decide on).

---

### Post by Therion on 2008-09-20
> **bpalone said:**
> ... I did, however, have to put my data files in the virtual hard drive.  It did not like them being out on the real HD, complained about not being a network version.
Hmmm... Did you install Guest Additions and such?  Might also be the case if you're using the version of VB from the Repo.
You should be able to map any folder on your 'buntu partition that you want (like Home, for instance) and share it between the virtual install and 'buntu.

---

### Post by bpalone on 2008-09-20
It was not VirtualBox complaining. It was QuickBooks Pro 2007.  All my other apps read ans save just fine out on the real HDs.  My point was to inform that QuickBooks might complain and that keeping my data files for it on the Virtual Hard Drive was my solution.  Trying to answer a possible problem before it was one.

---

### Post by trestamanos on 2008-09-20
Q: How do I import my data from Quickbooks(TM)?

    A: At this time there is no way to import from Quickbooks, and there are no plans to add that functionality. The Quickbooks QBW data format is a proprietary, non-documented file format. So until someone documents the file format or donates a QBW file parser your best bet for importing your QB data into GnuCash would be to output your data in a CSV format and either import the CSV data directly or convert the CSV to QIF and use the QIF importer. 

Source - [http://wiki.gnucash.org/wiki/FAQ#Q:_How_do_I_import_my_data_from_Quickbooks.28TM.29.3F](http://wiki.gnucash.org/wiki/FAQ#Q:_How_do_I_import_my_data_from_Quickbooks.28TM.29.3F)

-----

And this is why i want to leave proprietary software all together.
It looks for now Virtualbox is my only solution.  Unfortunately, I have to use Quickbooks because it is the accounting tool of our business.  This is a corporation and what I have seen from GNU Cash is not as robust nor does it have all of the features Quickbooks has.

Thank you all for your input.

From  what Ive read the only con of Vbox is speed....i guess ill have to put up with it until Linux can come up with something a bit more powerful.

---

### Post by Therion on 2008-09-20
> **trestamanos said:**
> From  what Ive read the only con of Vbox is speed...
I'm not saying VB is the be-all-end-all, but neither have I ever complained about it's speed.  

Of course YMMV, but I've never heard anyone complain it was slow either.  Try it; I think you'll be pleasantly surprised.

---

### Post by trestamanos on 2008-09-20
I wanted to thank you for your input.  
For those trying to install Vbox on Ubuntu....dont be afraid!.....i consider myself a n00b and just finished installing it. 

Now the real test (after i figure how can i install it from the Windows VM  :lolflag:........

I have the Quickbooks software on an external disk via USB but darn Windows is not picking it up.  

I tried from Ubuntu but dont know my way around??....can anybody help?

Thanks

tres

PS-Win on Vbox doenst seem slow at all.....havent noticed it.

---

### Post by bpalone on 2008-09-20
There is a thread around here somewhere that tells you what .conf file you have to modify and what to modify within it.  It is really pretty simple, just un-comment a line or two.  Do a search on VirtualBox USB that may turn it up.  Then you  have to enlighten your virtual machine as to its availability.  Go down to USB on the right panel in VirtualBox window and click on it.  It is pretty self explanatory from there.  Some USB items don't work through VirtualBox, so don't be to upset if doesn't read it.  I am guessing that it probably will.

If it doesn't read it, you can move the files you need from external drive into the internal drive.  Then using the shared folders, access it from there. 

While I was typing this, it came to mind that it may of been on the VirtualBox forums that found the instructions for making USB work in Ubuntu.  If you need a link to them let me know and I'll post it.

Hope this helps you.

edit addition: Just re-read your post.  In Ubuntu it will probably appear in media/whateveryourdeviceis. To look open places HOme, then click on File System, then scroll down to find the folder Media and double click it.

---

### Post by trestamanos on 2008-09-22
bpalone,

I'll take you up on any link that can help me figure it out.  (Trying to get Win on virtualbox to recognize USB)

i did do some research but no luck.

i did find the file you referred to and put the Quickbooks.exe in the media file (Ubuntu).....but cant find it in Windows.

Theres got to be a way where one can put the .exe in a specific place in Ubuntu and then find it in the Vbox Windows?

thanks

---

### Post by trestamanos on 2008-09-22
> **bpalone said:**
>  

While I was typing this, it came to mind that it may of been on the VirtualBox forums that found the instructions for making USB work in Ubuntu.  If you need a link to them let me know and I'll post it.

Hope this helps you.




just for clarification-Ubuntu recognizes USB just fine,  I was referring to Windows (on Virtualbox)....it doesnt pick up the USB.  Oddly enough, it does recognizes CD/DVD drive.  I guess i can burn the programs to a CD and do it that way.  

Theres gotta be a way to do it without burning a CD

---

### Post by bpalone on 2008-09-22
I will have to dig around here and find the info for making the USB work with VB and Ubuntu.  Then I'll post back.

I don't think you can just move the .exe file over have it work.  Most programs write some things to Windows registry that allows them to run. I would just use the install disk/CD to install it in the Virtual Machine. Then get your data files to where it can read them and you are back in business.

I hope you installed the Free but not Open Source from the Sun Microsystems web site.  It would be version 2.x.x right now.  You need to install Guest Additions which makes things easier to do, including resizing the virtual machines window and its display.

You said you had found your USB drive from Ubuntu.  To see it from within your virtual machine, you need to Share the Folder.  You can either do this before you launch your Windows virtual machine in the Settings or Details in the Shared Folders.  Once you have it open it pretty self explanatory.  Or with your Windows virtual machine running you can click on Devices and then Shared Folders and share it from there.

That is assuming that your Virtual Box is communicating with the USB device.  I will find the info for that post it, along with a link to the VirtualBox Forums here in a little while.

---

### Post by bumanie on 2008-09-22
To get us support, you need the vbox (free for home use) proprietary version. Then [follow this]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") - the thread is a bit old, but I think it still works oK.

---

### Post by bpalone on 2008-09-22
OK, had to look in the third of three machines to find it, but here it is.

Link to setting up VirtualBox with USB in Ubuntu:

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)...

Go down to the USB portion and follow the directions.

Here is the link to the VirtualBox Forums:

[http://forums.virtualbox.org/](http://forums.virtualbox.org/)

Another source of information when trying to figure something out with VirtualBox.

The poster above this one is steering you correctly also.  I didn't read the link he posted for installing, but did glance at it.  Doesn't hurt to get more than one source.  One may make more sense than another, to you.

Hope all this helps you out.

---

### Post by angelsguitar on 2008-09-22
> **trestamanos said:**
> Im running Virtualbox (Windows) on Ubuntu 8.04.  For some reason i cant get Windoes (runnng on Virtualbox) to recognize USB.  please help-thanks

Thanks in advance-

tres

Hi.  I'm kind of lost here; the replies to the original post do not match the original question.  Did you change the original question on post #1? If that was the case, next time start a new thread to avoid confusion.

Now, back to your question, the free version of VirtualBox does not include USB support, but follow this instructions to activate it:

[http://ubuntuforums.org/showthread.php?t=828927]("http://ubuntuforums.org/showthread.php?t=828927")

---

### Post by trestamanos on 2008-09-22
bumanie,

:lolflag:
Could not load the settings file '/home/administrator/.VirtualBox/VirtualBox.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Attribute 'version' has a value, '1.3-linux', that does not match its #FIXED value, '1.2-linux'
Location: '/home/administrator/.VirtualBox/VirtualBox.xml', line 3, column 83.


Result Code: 
0x80004005
Component: 
VirtualBox
Interface: 
IVirtualBox {76b25f3c-15d4-4785-a9d3-adc6a462beec}


OUCH!!

no biggie....i know what to do next-i think.

---

### Post by trestamanos on 2008-09-22
Angel,

Whats up.....yo soy Mayaguezano.  I too play :guitar:

-------

Thanks for the info-was not aware that the free version didnt support USB, etc.

Before I try your suggestion....Does it cost money to activate it?

I know i can burn it into a CD and be done with it,
------
Just trying to learn from you pros-:lolflag:

thanks

tres

---

### Post by bpalone on 2008-09-22
The free version we are talking about is available here:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Their interpretation of the Personal Use is very liberal.  Doesn't cost a thing.

---

### Post by angelsguitar on 2008-09-22
> **trestamanos said:**
> Angel,

Whats up.....yo soy Mayaguezano.  I too play :guitar:

-------

Thanks for the info-was not aware that the free version didnt support USB, etc.

Before I try your suggestion....Does it cost money to activate it?

I know i can burn it into a CD and be done with it,
------
Just trying to learn from you pros-:lolflag:

thanks

tres

No, as stated in the previous post, it doesn't cost anything.

By the way, soy de Arecibo.  Saludos Ubuntero!!!

---

### Post by trestamanos on 2008-09-22
I couldn't get the USB to work with Vbox Windows....no big deal.  I installed via CD-RW and it installed fine.
  
Took a little longer but don't want to spend too much time since I am installing Windows on Vbox for one app (Quickbooks-GNU Cash- while a great software....is not there yet IMO....).

I am all set!

I am really excited about switching to Linux.
I want to thank everyone in the community.  Everyone here was really nice and patient.  I hope I can repay the favor as I learn more.
Thanks

tres

---

### Post by TriSwords on 2008-09-22
I got my USB working yesterday but cannot find the page I used to enable it.

Maybe some people here can help out if I missed anything, but here is what I did:

1) In the terminal type 

```
sudo gedit /etc/init.d/mountdevsubfs.sh 
```

2) Make the section after # Magic to make /proc/bus/usb work uncommented.
Should look like
```

# Magic to make /proc/bus/usb work
	
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

```
(its 4 lines, total)

Close the file and save it

3) Make sure you enable USB in VirtualBox (I also enabled USB 2.0)

4) Type in the terminal

```
sudo gedit /etc/group
```

and find the line like

```
vboxusers:x:125:michael
```

except michael will be whatever your user name is. Remember the number before it (in my case 125).

5) Close that out, make sure you made NO changes.

6) Now in the terminal type in 

```
sudo gedit /etc/fstab
```

Add this line to the bottom

```
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0
```

Replace 

```
devgid=125 with devgid=<whatever number was after vbox:x:>
```

Save and exit.

7) Next I typed in the terminal

```
sudo chown -R root:vboxusers /proc/bus/usb
```

8 ) Finally restarted my computer. After that the USB options in Virtualbox saw my flash drive I had plugged in. I just checked the box next to it to enable it. (Although I had to enable and disable it from the bottom of virtual box while XP was on to get it to install.)

---

### Post by angelsguitar on 2008-09-23
> **trestamanos said:**
> I couldn't get the USB to work with Vbox Windows....no big deal.  I installed via CD-RW and it installed fine.
  
Took a little longer but don't want to spend too much time since I am installing Windows on Vbox for one app (Quickbooks-GNU Cash- while a great software....is not there yet IMO....).

I am all set!

I am really excited about switching to Linux.
I want to thank everyone in the community.  Everyone here was really nice and patient.  I hope I can repay the favor as I learn more.
Thanks

tres

I have this other two tutorials on activating USB on VirtualBox.  Had them bookmarked a while ago, although I've never followed then to be honest.  Check them out; maybe they say something different that may help you:

[http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html]("http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html")

[http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")

---

### Post by trestamanos on 2008-09-23
Thanks Angel.

---


---
title: "NOKIA PC Suite"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by harsh_ on 2008-09-10
Well, i,ve completely gone bonkers over linux.... ubuntu rather.... for the degree of openness it provides, unlike the monopoly OS
Anyways, i had this query whether i can connect my Nokia N73 for transferring files??? (Not in mass storage mode). Also, N70 which does not have the mass storage mode; is a complete stranger with ubuntu....
Please help.... With this, the last doubt with ubuntu is killed....... FOREVER

---

### Post by philinux on 2008-09-10
I'm testing out wammu and gmobilemedia for my SE K810i. Both are in synaptic. They end up in the accessories menu.

---

### Post by ooobuntooo on 2008-09-10
Doesn't the icon just appear on the desktop like a removable disk.
It does with my Sony Ericsson K800i.
I don't require any software.

---

### Post by siddhuwarrier on 2008-09-13
Hi, I just spent a couple of hours getting it working on my Nokia N70. There are a few guides to get this right, but one of them has a few errors (probably because it refers to an older version of Ubuntu; Feisty Fawn), and the otehr does not tell you how to use the Java-based graphical frontend. So I've put both of these together.

BEFORE YOU DO ANY OF THIS, CONNECT YOUR NOKIA PHONE USING AN USB CABLE.

Step 1: Install obexftp.
Open a terminal and type: 
> sudo apt-get install obexftp openobex-apps

Step 2: Get the obexftp frontend.
>  wget [http://downloads.sourceforge.net/obexftpfrontend/obexftp-frontend-0.6.6.deb?modtime=1216323028&big_mirror=0](http://downloads.sourceforge.net/obexftpfrontend/obexftp-frontend-0.6.6.deb?modtime=1216323028&big_mirror=0)
sudo dpkg -i  obexftp-frontend-0.6.6.deb


Remove the .deb file using rm when you're done installing it using dpkg.

Step 3: Find the product ID and vendor ID of your Nokia phone.

In the terminal you have opened, type:
> 
lsusb | grep Nokia


You should get an output line that goes something like this:

**Bus 004 Device 020: ID 0421:043a Nokia Mobile Phones N70 USB Phone Parent**

I get Nokia N70 because my mobile phone is, well, a Nokia N70. ;)

In my case, 0421 is the vendor ID, and 043a is the product ID (obtained from the string 0421:043a).

Note: If you don't get anything from this, try typing 

> 
lsusb


and looking for a line with Nokia.

Step 4: Add permissions to udev, so that this device can be mounted using obexftp.

In the terminal, type:
> 
sudo gedit /etc/udev/rules.d/40-permissions.rules


Add the line to the end of this file:

BUS=="usb", SYSFS{idVendor}=="**VendorID**", SYSFS{idProduct}=="**ProductID**", GROUP="plugdev", USER="**yourUserName**"

Change VendorID and ProductID in this file to refer to the values you determined in step 3, and yourUserName to your user ID (in my case, siddhu)

Step 5: Now, let's run a quick test to make sure we've got it setup all right. In the terminal, type:

> 
obex_test -u


You should get output that looks something like this.

Interface 0: Nokia Nokia N70 SYNCML-SYNC
Interface 1: Nokia Nokia N70 PC Suite Services

Step 6: Let's get syncing!! In the terminal, type:

> 
obexftp-frontend &


This should open up to show you a configuration dialog. If it doesn't, click *Options->Configuration*.

Specify the ObexFTP path if it's not already been specified. It should be /usr/bin/obexftp if you followed the instructions described herein. If you want to find out what your ObexFTP path is, type in terminal:

> 
which obexftp


and copy the output into the textbox in the ObexFTP Front-end program.

In the ``Advanced Options'' group box, deselect ``Device Info Fetching''

Then, look below at the ``Device Information'' Group box. In the ``Connection type'' drop down box, select 'USB'. Enter 1 into the ``Connection line'' text box.

Click on the ``Test'' button. You should get a little dialog box that says ``Connection Established''.

YAY!!! :D

Click `OK'. The config dialog will disappear. Now, click on the ``Device'' menu and click ``Query root files'' (or alternately, press F5). You should see the folders on your phone.

YAY (again)!!! :D

---

### Post by dioltas on 2008-09-13
> **siddhuwarrier said:**
> Hi, I just spent a couple of hours getting it working on my Nokia N70. There are a few guides to get this right, but one of them has a few errors (probably because it refers to an older version of Ubuntu; Feisty Fawn), and the otehr does not tell you how to use the Java-based graphical frontend. So I've put both of these together.

BEFORE YOU DO ANY OF THIS, CONNECT YOUR NOKIA PHONE USING AN USB CABLE.

Step 1: Install obexftp.
Open a terminal and type: 


Step 2: Get the obexftp frontend.


Remove the .deb file using rm when you're done installing it using dpkg.

Step 3: Find the product ID and vendor ID of your Nokia phone.

In the terminal you have opened, type:


You should get an output line that goes something like this:

**Bus 004 Device 020: ID 0421:043a Nokia Mobile Phones N70 USB Phone Parent**

I get Nokia N70 because my mobile phone is, well, a Nokia N70. ;)

In my case, 0421 is the vendor ID, and 043a is the product ID (obtained from the string 0421:043a).

Note: If you don't get anything from this, try typing 



and looking for a line with Nokia.

Step 4: Add permissions to udev, so that this device can be mounted using obexftp.

In the terminal, type:


Add the line to the end of this file:

BUS=="usb", SYSFS{idVendor}=="**VendorID**", SYSFS{idProduct}=="**ProductID**", GROUP="plugdev", USER="**yourUserName**"

Change VendorID and ProductID in this file to refer to the values you determined in step 3, and yourUserName to your user ID (in my case, siddhu)

Step 5: Now, let's run a quick test to make sure we've got it setup all right. In the terminal, type:



You should get output that looks something like this.

Interface 0: Nokia Nokia N70 SYNCML-SYNC
Interface 1: Nokia Nokia N70 PC Suite Services

Step 6: Let's get syncing!! In the terminal, type:



This should open up to show you a configuration dialog. If it doesn't, click *Options->Configuration*.

Specify the ObexFTP path if it's not already been specified. It should be /usr/bin/obexftp if you followed the instructions described herein. If you want to find out what your ObexFTP path is, type in terminal:



and copy the output into the textbox in the ObexFTP Front-end program.

In the ``Advanced Options'' group box, deselect ``Device Info Fetching''

Then, look below at the ``Device Information'' Group box. In the ``Connection type'' drop down box, select 'USB'. Enter 1 into the ``Connection line'' text box.

Click on the ``Test'' button. You should get a little dialog box that says ``Connection Established''.

YAY!!! :D

Click `OK'. The config dialog will disappear. Now, click on the ``Device'' menu and click ``Query root files'' (or alternately, press F5). You should see the folders on your phone.

YAY (again)!!! :D


Does this allow you to install games/applications onto your phone? Or backup your phone book etc? Thanks, good guide. Im gonna try it with my nokia 6230i when i get a chance.

---

### Post by chris_j on 2008-09-24
siddhuwarrier you are absolutely fantastic :guitar:

It works perfectly =D>

---

### Post by Steve H on 2008-09-27
Thanks for that, worked beautifully!! :D I can browse all the files on my n70 and its memory card.

Now I've just got to find a way to sync the calendar...any ideas?

---

### Post by ben2talk on 2008-09-30
CONNECTION ERROR

YUUUY (not again)!!! :(([/QUOTE]

---

### Post by neilrizo on 2008-10-20
> **siddhuwarrier said:**
> 
Step 3: Find the product ID and vendor ID of your Nokia phone.

In the terminal you have opened, type:

lsusb | grep Nokia

You should get an output line that goes something like this:

**Bus 004 Device 020: ID 0421:043a Nokia Mobile Phones N70 USB Phone Parent**

I get Nokia N70 because my mobile phone is, well, a Nokia N70. ;)

In my case, 0421 is the vendor ID, and 043a is the product ID (obtained from the string 0421:043a).


I don't have a usb data cable for my Nokia E61i, all I have is a bluetooth dongle. In this case I cannot use the "lsusb" command. What terminal command should I use in order to get my phone's product and vendor ID?

---

### Post by toxicafunk on 2009-03-23
> **ben2talk said:**
> CONNECTION ERROR

YUUUY (not again)!!! :( 

I had the same problem until I realized I had to execute obexftp-frontend with root priviledges.

---

### Post by texadactyl on 2009-04-05
Still works in 2009.  Stood the test of time!  Good job.

Note that the `wget` step is no longer necessary.  It can be replaced with:

[INDENT]sudo apt-get install obextool[/INDENT]

if you don't mind using a TK based tool.  That way, the Ubuntu package maintainers will keep track of updates.

Also, Bluetooth in place of USB is quite simple to add to the above script.  The Gnome Bluetooth Applet whose ICON is normally at the top of the screen can be used to "setup a new device".  Just right-click on it and the rest is pretty simple.

However, I want to reliably sync my Symbian-based phone with my desktop (Gnome or KDE) -- just like I used to with my Palm hand-held and jpilot (Palm Desktop replacement for Linux).  Hopefully in the future, some energetic Symbian+Linux group will develop a _reliable and simple to use_ graphical user interface, similar to the Palm Desktop.

---

### Post by Whitsboy on 2009-05-01
Hello Siddhuwarrier'
I have been trying to follow your instructions to install nokia phones on ubuntu. When I get to the test I receive
 'Using USB transport, querying available interfaces
Use 'obex_test -u interface_number' to run interactive OBEX test client'
can you tell me what is happening

Cheers
:confused:

---

### Post by texadactyl on 2009-08-14
If you are willing to consider an alternative approach:
[http://ubuntuforums.org/showthread.php?p=7781356#post7781356]("http://ubuntuforums.org/showthread.php?p=7781356#post7781356")

---

### Post by texadactyl on 2009-08-19
I found some problems with Thunderbird filtering out certain types of data (E.g. the 3rd email address and the 2nd mobile phone).  However, Gnome Evolution seems to sync everything from Google Contacts and Calendar.  I also hear good things about the KDE equivalents (I am a Gnome user, currently).

So, my updated sync procedure is as follows, assuming that I make a change on my Nokia N95 while walking about:
1 - Sync Nokia N95 with Google.
2 - Sync Google to Evolution.

The Google / Evolution setup is straight-forward:
[http://linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps]("http://linux.com/news/software/applications/8226-how-to-sync-evolution-with-googles-pim-apps")

Note that it may not be a perfect sync.  I heard that some contact "note" fields got lost along the way for some users.

Sometimes I long for the days of my Palm Pilot and `jpilot`.

---

### Post by adilbhilai on 2009-08-31
Does wammu supports Nokia 6630

---

### Post by peterp77 on 2009-12-27
> **Whitsboy said:**
> Hello Siddhuwarrier'
I have been trying to follow your instructions to install nokia phones on ubuntu. When I get to the test I receive
 'Using USB transport, querying available interfaces
Use 'obex_test -u interface_number' to run interactive OBEX test client'
can you tell me what is happening

Cheers
:confused:

I have exactly the same problem. If anyone can shed some light on this that would be much appreciated..

---

### Post by Thalarse on 2010-02-02
Sorry about the necromancy, but does this (or any other) method allow you to update the firmware of the phone?

---

### Post by sandy8925 on 2010-06-14
@Thalarse - no it doesn't. the phone firmware is installed on a separate memory chip on the phone. and there all sorts of keys and filesums to verify that the firmware is nto tampered with. to get an idea of how difficult it is see here: n70linux.wordpress.com

---

### Post by LuHe on 2010-07-14
You could use [Series60-Remote]("http://series60-remote.sourceforge.net") for your S60-based mobile phone.

You can use this software suite to send and receive text messages.
It is also possible to create and edit contacts and to browse the file system of your mobile phone.

---

### Post by labinnsw on 2010-07-15
I am having a problem trying to use ObexFTP Front-end. [Please see post No. 7 of this link]("http://ubuntuforums.org/showthread.php?t=1528708")

---

### Post by peterp77 on 2010-07-20
> **LuHe said:**
> You could use [Series60-Remote]("http://series60-remote.sourceforge.net") for your S60-based mobile phone.

You can use this software suite to send and receive text messages.
It is also possible to create and edit contacts and to browse the file system of your mobile phone.
Thanks LuHe. I tried the Series 60 with my N73. It works very, very well.  I've been looking for something like this for a long time. I'd say it's even better than Nokia PC Suite. It even allows you to use SQL functionality to query messages and contacts.

---


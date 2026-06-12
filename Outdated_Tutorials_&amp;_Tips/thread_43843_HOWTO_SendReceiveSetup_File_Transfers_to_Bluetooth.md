---
title: "HOWTO: Send/Receive/Setup File Transfers to Bluetooth Phones using Gnome Scripts!"
date: 2005-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by derrick1985 on 2005-06-23
**Introduction** 

Hey all, if you are like me then you are kinda tired of having to go into your terminal to setup a Bluetooth connection, and even go there to send and receive files. What IF, there was a nicer, easier way to do it? I just may have the solution.

First of all, this is my first ever script, and this comes from reading the HOWTO on installing a deb via right clicking. So, please be patient with me while I perfect these. These do however, work so far for me.

First of all, if you don't already have a working Bluetooth Connection to your phone (or any other device, this should work for all Bluetooth devices) then read this excellent HOWTO: [http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth](http://ubuntuforums.org/showthread.php?t=34740&highlight=bluetooth)

It talks about Nokia phones, but this will work for any phone. It worked great for my Motorola V551.

After you have a working connection, we need to make some scripts. This is VERY easy to do with Gnome, and this will probably be the last time you will have to open up a terminal for anything Bluetooth again.

**Script Setup** 

Start off like this.

gedit ~/.gnome2/nautilus-scripts/Bluetooth\ Setup

If you read the howto, you will notice that after every reboot, we have to re-pair the devices and activate the proper Bluetooth modules. This script will do it all for us, just have to insert in out sudo password.

Enter this into your gedit window:

#!/bin/bash
modprobe l2cap
gksudo modprobe rfcomm
gksudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
gksudo rfcomm bind /dev/rfcomm0 YOUR_PHONE_ADDRESS 10
done

REMEMBER to change YOUR_PHONE_ADDRESS and put in your phones proper address. An example of a working script is this:

#!/bin/bash
modprobe l2cap
gksudo modprobe rfcomm
gksudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
gksudo rfcomm bind /dev/rfcomm0 00:12:8A:C9:5A:8B 10
done

Close and Save.

Next, we need to make a script to receive files from our phone. NOTE: All files are saved in your /tmp directory, so remember to copy and paste them where you want them. Also, you can currently with the Bluetooth utils, only send ONE FILE AT A TIME. So, that means this script will have to be used for every file sent. Sorry, I know it's a pain.

gedit ~/.gnome2/nautilus-scripts/Bluetooth\ Receive\ File

Copy and Paste

#!/bin/bash
obexserver
done

Save and Close

Next up, we are going to send files to phones. 

gedit ~/.gnome2/nautilus-scripts/Bluetooth\ Send\ File

Copy and Paste

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
gnome-obex-send $uri
done

Save and Close

Now, we have to make this script executable from our menu. Copy and paste the lines below one  at a time.

chmod +x ~/.gnome2/nautilus-scripts/Bluetooth\ Setup
chmod +x ~/.gnome2/nautilus-scripts/Bluetooth\ Receive\ File
chmod +x ~/.gnome2/nautilus-scripts/Bluetooth\ Send\ File

Now, on your Right click menu you will have another option called "Scripts". Here is what you do to get transferin' (this would be an example of what you would do after a reboot)

Right click---Scripts---Bluetooth Setup
(enter root password twice)
Right click---Scripts---Bluetooth Receive File
(obexserver is now started, send a file from your phone to your Linux box's /tmp folder)
Right click on a file---Scripts---Bluetooth Send File
(sends selected file(s) to bluetooth paired device)

**Closing** 

Again, these are my first scripts, so I don't expect them to work right away. Please post any comments you have and I will try my best to help everyone with their problem. Also note, this is assuming you have only ONE bluetooth device, so if you want to pair up with another device, you would change the lines in the first scirpt, Bluetooth Setup.

I hope someone finds this useful.

Good luck

---

### Post by oofnik on 2005-06-27
Very nice! I just added obexserver to the Bluetooth Setup script, as it seems a bit redundant to make a script to run one simple command. But anyway, thanks a lot for these scripts! :smile:
Eh.. actually the send script is not working for me, I have no idea why. hmm..

---

### Post by derrick1985 on 2005-06-27
[QUOTE=oofnik]Very nice! I just added obexserver to the Bluetooth Setup script, as it seems a bit redundant to make a script to run one simple command. But anyway, thanks a lot for these scripts! :smile:
Eh.. actually the send script is not working for me, I have no idea why. hmm..[/QUOTE]

Yeah, the reason obexserver isn't in the setup script is because obexserver has to be started up again for every file downloaded. So, if you have 10 files to transfer, you have to turn on obexserver 10 times (one after another after the file has downloaded)

And as for your send script, make sure that you can send files to your phone using the terminal. If you can, then check the scripts. I've included a tar.gz file of the scripts i'm using.

Hope that helped.

---

### Post by atlas95 on 2005-07-16
Hmm I have little problem, all is working but when I want to send a file to my sgh-d500 it ask me a password, for exemple i say 0000 but next computer must ask me the password too.But it isn't...so computer say me can't connect to phone or something like that ..
How to do?
Do you understand me?

Thanks :/

---

### Post by keltong on 2005-07-18
Hi! Thanks for this wonderful script. It works perfectly for me. Tried the terminal but this scripts are just so great. Thanks!!!

---

### Post by gammyhand on 2005-08-02
[QUOTE=keltong]Hi! Thanks for this wonderful script. It works perfectly for me. Tried the terminal but this scripts are just so great. Thanks!!![/QUOTE]
 I have no idea how to receive stuff on bluetooth which is annoying because I want to transfer my photos to my computer. Should I not be seeing my Samsung D500 in the filesystem? I can send files to it no problem at all.

---

### Post by gammyhand on 2005-08-03
anyone?

---

### Post by AndrewB on 2005-08-05
Thanks, the scripts are perfect. Works great with Motorola V3.

---

### Post by gammyhand on 2005-08-07
[QUOTE=AndrewB]Thanks, the scripts are perfect. Works great with Motorola V3.[/QUOTE]
 Anyone got any advice on my problem?

---

### Post by friviere01 on 2005-08-09
What about connecting to TWO phones? Could modify the script to use several phones? 
-----------
REMEMBER to change YOUR_PHONE_ADDRESS and put in your phones proper address. An example of a working script is this:

#!/bin/bash
modprobe l2cap
gksudo modprobe rfcomm
gksudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
gksudo rfcomm bind /dev/rfcomm0 00:12:8A:C9:5A:8B 10
done

Close and Save.
-----------

---

### Post by gasparov on 2005-08-29
[QUOTE=friviere01]What about connecting to TWO phones? Could modify the script to use several phones? 
-----------
REMEMBER to change YOUR_PHONE_ADDRESS and put in your phones proper address. An example of a working script is this:

#!/bin/bash
modprobe l2cap
gksudo modprobe rfcomm
gksudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
gksudo rfcomm bind /dev/rfcomm0 00:12:8A:C9:5A:8B 10
done

Close and Save.
-----------[/QUOTE]
 is it possbile to do all the sudo stuff by once or better without any pass being prompted?

---

### Post by pjbgravely on 2005-10-07
[QUOTE=friviere01]What about connecting to TWO phones? Could modify the script to use several phones? 
-----------
REMEMBER to change YOUR_PHONE_ADDRESS and put in your phones proper address. An example of a working script is this:

#!/bin/bash
modprobe l2cap
gksudo modprobe rfcomm
gksudo mknod /dev/rfcomm0 c 216 0
sdptool add --channel=10 OPUSH
gksudo rfcomm bind /dev/rfcomm0 00:12:8A:C9:5A:8B 10
done

Close and Save.
-----------[/QUOTE]
Yes add,
    gksudo rfcomm bind /dev/rfcomm1 ADDRESS_OF_SECOND_PHONE 10

When you go to send data you will be prompted for which phone.
 
Don't forget to add second phone to /etc/bluetooth/rfcomm.conf

Also it is easier to use gnome-bluetooth-manager to receive files than  obexserver.

Paul

---

### Post by twinprism on 2006-04-11
The bluetooth send script doesn't appear to work with spaces in filenames, any suggestions for a modification to fix that?

Thanks,
TP

---

### Post by pacmanman on 2006-09-06
Hello, how can I select the directory of download? (choose between /tmp and another). Thank you.

---

### Post by aitchsee on 2006-11-12
Thanks very much for this :) 

Now, please forgive me for my stupidity, ubuntu is the first linux flavour I've tried and I only installed it three days ago so I really am a **total** noob, but this works perfectly when I send files from the phone to the computer (which is, I guess the most important part) but when I try to send *from* the computer I get a pop-up box saying "choose bluetooth device" but there is nothing there to choose! 

I haven't a clue what to do now! ](*,) 

any help gratefully received and please overlook any idiocy/bad terminology! - it's a Nokia 6630 btw and I do have it set be "shown to all"
-H

---

### Post by #66 on 2006-12-27
> **twinprism said:**
> The bluetooth send script doesn't appear to work with spaces in filenames, any suggestions for a modification to fix that?

Thanks,
TP

Same prob here! Spaces in file name or folder wont work. Brilliant script however

CC

---

### Post by balaji.ramasubramanian on 2007-02-25
> **twinprism said:**
> The bluetooth send script doesn't appear to work with spaces in filenames, any suggestions for a modification to fix that?

Thanks,
TP

You will have to write a Perl code in place of the simple bash code given earlier. Here is an example. 

```

#!/usr/bin/perl -w

for $uri (split /\n/, $ENV{NAUTILUS_SCRIPT_SELECTED_FILE_PATHS}) {
	$uri =~ s/\s+/\\ /g;
	`gnome-obex-send $uri`;
}
```

Replace your bash script (or create another) with the above lines of code. Just as a note to those that are still struggling with this: I could get my OBEX server to send files directly without having to invoke the "Receive" or "Bluetooth Setup" scripts shown above. I am using Edgy Eft and find that when I send a file from the mobile to my laptop, I get it directly on my desktop. To get this I wrote a simple script and added it to the Session startup programs along with my other favorite ones. 

```

/usr/sbin/sdpd
sudo modprobe l2cap
sudo modprobe rfcomm
sudo mknod /dev/rfcomm0 c 216 0
sudo sdptool add --channel=10 OPUSH
sudo rfcomm bind /dev/rfcomm0 00:0E:6D:7F:06:63 10 ### Change this address to your own mobile phone's address which you can get from "hcitool scan". 
gnome-obex-server
```

In addition to this, you need not have edited your /etc/bluetooth/rfcomm.conf to configure your rfcomm0 device. The above lines of bash code do all that is actually mentioned there. In fact, I didn't need one. 

Check if this works for you. If it does not, revert to original instructions. Besides, these have been tested only on Edgy.

---

### Post by coolindian109 on 2008-12-04
you wont need so much configuration and all.
Just install Blueman bluetooth manager.
Use this instead of the default bluetooth-applet.
It has a nice UI where you can select a device, browse, and send files .
Also you can set up a obex ftp server so that you can send files from your mobile to your PC..

---

### Post by fantan on 2008-12-06
Hi,
And where to get Blueman bluetooth manager? It isn't in the repos.

fantan

---


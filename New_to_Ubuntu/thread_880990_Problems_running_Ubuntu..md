---
title: "Problems running Ubuntu."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Yotobari on 2008-08-05
EDIT: I had a quick search of the forums and couldn't find anything relating to my particular problem. My apologies if I overlooked this being answered somehere else.

I've been advised (forced) to switch from Windows to Ubuntu by a friend. I have downloaded the 8.04.1 ISO file and the Wubi 8.04.1 file. As instructed I ran the Wubi file, rebooted my computer and selected Ubuntu eventualy I was bought to a page mentioning something about Busyboxes and driver cache files (I can't quite recall the details) and it didn't move past this page for quite some time. I decided to give up after being told it probably meant incompatible hardware but am now unsure as to wether I simply didn't wait long enough.
Any advice would be greatly appreciated. Thank you.

---

### Post by y@w on 2008-08-05
Hi Yotobari, before we can help you we need to know what kind of state your machine is in. Does it boot to Windows now? Have you tried to run the installer again?

Also: welcome to the forums :)

---

### Post by Yotobari on 2008-08-05
Yes, I'm currently running in Windows and tried to use the installer again earlier and was again kept at the same page.

---

### Post by Achetar on 2008-08-05
Try using the normal installer (boot from the CD).

---

### Post by BGFG on 2008-08-05
Hi and welcome,

I don't know if your are running Vista or XP, but i'd suggest you partition your drive first(if it's possible) and then just boot into the Ubuntu live cd and install on your newly partitioned drive. Life is just easier that way. :)

---

### Post by dew5 on 2008-08-05
I had this same problem.

I wiped my hard disk using a program I acquired through apc mag in Australia the partitioned the drive to use the whole disk and it installed fine.

Are you getting stuck at the partition state during the install?

dew5

---

### Post by Yotobari on 2008-08-05
I'm running Vista and am considering installing to a CD and trying that approach, also I'm not exactly very techy (only recently found out how to change a file from a .png to .jpg) so if you could advise me on how to partition my drive that would also be greatly appreciated.

I'm not entirely sure what stages it's at as it installs. All I can clearly remember is the Ubuntu loading bar and then getting stuck on the Busybox page.

---

### Post by Bucky Ball on 2008-08-05
Hi Yotobari,

If you are switching to Ubuntu, try dual booting, as wubi inside Windoze is not quite switching.

If you have a spare drive or partition, do a full install of Hardy 8.04 and go the full experience (Like BGFG said - makes life easier). If you really are looking to switch, you will have Windoze there which you can ween off as your Linux knowledge grows (and you have your persuasive friend and the forum to help you through!).



Good luck :)

---

### Post by BGFG on 2008-08-05
> **Yotobari said:**
> I'm running Vista and am considering installing to a CD and trying that approach, also I'm not exactly very techy (only recently found out how to change a file from a .png to .jpg) so if you could advise me on how to partition my drive that would also be greatly appreciated.

I'm not entirely sure what stages it's at as it installs. All I can clearly remember is the Ubuntu loading bar and then getting stuck on the Busybox page.

HA HA! Vista!
Cool. administrative Tools>>Disk management. then:
Select your drive and shrink it.
Boot into the live cd, use the new space you just created and  install. For a really nice dualboot setup. Check out EasyBCD. With it you can keep both installations very separate and just add ubuntu to the Vista bootloader.

If i confuse just tell me and i'll be more detailed. :)

---

### Post by Bucky Ball on 2008-08-05
Partitioner is included in the installation cd. You will get to it as part of the install process. Just don't touch the partition which is NTFS (that is where Windoze is) and you should be fine. Select manual install (when you get to that bit) and follow your nose, pick your size etc ...

This might help you along,

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Go to the section on partitioning. There is lots of info out there.

Leaving you in the good hands of BGFG ... good luck :)

---

### Post by Yotobari on 2008-08-05
I found the Administrative Tools folder and it doesn't seem to contain a Disk management section, searching for it reveals it apparently doesn't exist. Yay.

---

### Post by BGFG on 2008-08-05
> **Yotobari said:**
> I found the Administrative Tools folder and it doesn't seem to contain a Disk management section, searching for it reveals it apparently doesn't exist. Yay.

This should help....

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by drinkpepsi on 2008-08-05
Are you running raid on your pc? I had the same error, and had to break the raid array, and set each drive up as an individual drive.

---

### Post by Yotobari on 2008-08-05
Ok, I attempted to burn the ISO to a disc with disaster (why do they say 700mb when they can actually only hold 500?) and as I'm having real trouble with Wubi would it be best to wait it out til I get a LiveCD in the post?

---

### Post by BGFG on 2008-08-05
> **Yotobari said:**
> Ok, I attempted to burn the ISO to a disc with disaster (why do they say 700mb when they can actually only hold 500?) and as I'm having real trouble with Wubi would it be best to wait it out til I get a LiveCD in the post?

What program did you use ?
A great program to handle ISO's is ISOburn. I've used it in Vista and i still use it in WINE in Ubuntu.
As for the 700. the do hold 700megs, but in the disaster something probably went wrong with the formatting and you lost some space.

---

### Post by Bucky Ball on 2008-08-06
Have you got a DVD, Yotobari? Work just as well ... :)

---

### Post by Yotobari on 2008-08-06
I completely forgot about trying DVDs, yay for my mother buying me about 100 blank ones years ago. Ok I'm going to download ISOburn and see where I can get with this.

---

### Post by Yotobari on 2008-08-06
I've tried to burn the disc in both Infrarecorder and ISOburn, neither are letting me burn the disc. Infrarecorder is just plain greying almost everything out and ISOburn is informing me that '" is not a valid floating point value.' I've now gotten myself completely stuck hehe. And may I say thank you for all your help so far, it's greatly appreciated.

---

### Post by Yotobari on 2008-08-06
Alright, good news. I am now running Ubuntu (well not right at this minute) but I have no internet connection. Also I didn't set up a Virtual Machine or whatever it's called so I could have Windows on it (It's something like that) and am unsure of wether I can add it now or I have to reinstall Ubuntu, I gave it a try on a whim after trying out something someone else had mentioned.

---

### Post by 0utlaw 0f Pk on 2008-08-06
Same problem I have, except i've been in ubuntu before.

---

### Post by y@w on 2008-08-06
> **Yotobari said:**
> Alright, good news. I am now running Ubuntu (well not right at this minute) but I have no internet connection. Also I didn't set up a Virtual Machine or whatever it's called so I could have Windows on it (It's something like that) and am unsure of wether I can add it now or I have to reinstall Ubuntu, I gave it a try on a whim after trying out something someone else had mentioned.

You don't need to reinstall Ubuntu to in order to get virtual machines running. You'll just need some software to run your virtual machines. I'd recommend either [VMware]("http://vmware.com/products/server/") or [VirtualBox]("http://virtualbox.org"). VirtualBox will come as a package, so that would probably be the way to go. 

What are the problems you're having with getting an internet connection? Are you able to get an IP address?

---

### Post by Yotobari on 2008-08-06
I honestly don't have a clue, I didn't have my friend to walk me through when I got it going, all I know is that it couldn't find a network connection (I have a perfect signal on Windows).

Also, what platform should I download the virtual machine for, I'm a little confused as I'm downloading in Windows but plan on using it in Ubuntu.

---

### Post by Bucky Ball on 2008-08-06
Yotobari, first you need to identify your card. Are you talking wireless? Run these commands in a terminal:

> sudo lshw

Find your hardware, and ...

> iwconfig

Can you find anything that relates to a network connection or configuration?

Also, if you go System->Administration->Network Tools you will get a little more detail. With Ubuntu, setting up internet can be 'out of the box' easy or 'rip my hair out' tricky. All depends on card and connection.

You may find this page of interest,

[https://wiki.ubuntu.com/HardwareIdentification](https://wiki.ubuntu.com/HardwareIdentification)

Good luck and let us know ... :)

ps: in case you didn't know 'sudo' = superuser do! Makes you root for that command only.

---

### Post by Yotobari on 2008-08-07
Ok my findings have concluded I either a) can't find my internet on the lshw one or b) didn't recognize it. iwconfig concludes I have no wireless extensions whatsoever and Network tools tells me I have an IP adress and the IPv thingys.

---

### Post by Bucky Ball on 2008-08-07
in a terminal type:
> 
lspci -v | less

You should be looking for something like this (my wireless card);

> 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

If you can't find, post the result here ...

I am presuming that you are talking laptop and wireless here?? Would be really helpful if you gave the details of your machine in your first post (sorry if I have missed these details in this thread) .. Here's mine;

HP dv6000 series laptop, amd64, 2 gig ram, broadcom etc etc and any other details you can think of ...

If you stick that in your opening post in future (or even your signature) we can get further faster ...

Let us know if you find your card and what it is exactly you are sitting in front of ... :)

---

### Post by Yotobari on 2008-08-07
Alright firstly desktop. HP Pavillon, 1.88gig ram, amd64, Lynksys Wireless-G. I'm off to have a look at this card thing now.

---

### Post by Bucky Ball on 2008-08-07
Cool, thanks.

Is it the one on this page?

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1150490054358&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5435839789B10](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1150490054358&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5435839789B10)

It looks like the Linksys needs to use ndiswrapper (at least in Gutsy). Have a look at this page;

[http://hehe2.net/linux/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/](http://hehe2.net/linux/howto-linksys-wmp54g-pci-wireless-adapter-on-ubuntu-gutsy/)

This should work for Hardy too. At the step where it says ...
> 
1-First of all grab the driver from here (XP not Vista)

Don't. Download it from the first page I gave you in this post (if that is your card that is). I'll keep looking but something to remember is that a few of the wireless card drivers are designed for Windows 64 bit and will not work with Ubuntu 64 (my card is a case in point). Therefore, you need to go for the 32 bit, older driver. This point will need further investigation ... :)

*UPDATE: I take that back! On further investigation, ndiswrapper may not be the case. Try this page;

[https://help.ubuntu.com/community/WifiDocs/LinksysWPC54G](https://help.ubuntu.com/community/WifiDocs/LinksysWPC54G)

I am presuming this is the card you are talking about. They recommend the b43-fwcutter method which works for me where the ndiswrapper didn't after much struggle. I should have added: you are running Hardy?

---

### Post by Yotobari on 2008-08-07
Yes I am running Hardy, the ispci didn't seem to work much at all, just gave me a list of other codes. I'm gonna try the b43 one now. I'm a little unsure as to where to put the file though as I'm obviously downloading off Windows and I'm assuming I need it running in Ubuntu.

---

### Post by Bucky Ball on 2008-08-07
In reference to your edit ...

 > I'm obviously downloading off Windows and I'm assuming I need it running in Ubuntu.Ah ha. The answer to that, at least in my case, is yes. I'm afraid I have little to no idea how you would achieve this without some major screwing around in Windoze. You could start by running this command using 'l' not 'i' -

> lspciThis will give you the exact model of the Linksys card. Then go here and see if you can find a match:

[http://linuxwireless.org/en/users/Drivers/b43/devices](http://linuxwireless.org/en/users/Drivers/b43/devices)

If you do, then boot back into Ubuntu and try:

> System-> Administration -> Hardware DriversIn there you will find the Broadcom b43 driver. Has it got a tick next to it??? We might get lucky cos if you match on the b43 page, switching this driver on may switch your card on. If you get a match, switch it on, if you don't get a match and it is on, switch it off. It may be preventing your card working 'out of the box'.  :)

---

### Post by Bucky Ball on 2008-08-07
Just out of interest, what driver is Windoze using to get this card up?

---

### Post by appi2012 on 2008-08-07
I also have a Hp Pavillion with a Linksys Wireless G Wireless card, that I set up. (Ubuntu is running perfectly!). I am assuming it is a usb card; that explains why it doesn't show up in "lspci" It should show up if you type:
```
lsusb
```
If you have a WUSB54GV2 card, then download the attached archive, and unzip it in Vista. If you don't, you can just skip this step.

Boot into ubuntu. Insert your ubuntu cd, and open a terminal. Type:
```
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common
```
That will install ndiswrapper, a utility that will run windows drivers in linux. 
If you used my file, then:
  Now, go to places -> [Your Vista Drive]
  Navigate to the folder place you unzipped my folder.
  Copy the folder to your home folder.
If you skipped the first step, then:
  Insert your wireless driver cd. Find the folder that has some .sys files and an .inf 
  file. Copy this folder to your home folder.

After getting the driver folders, in the terminal type:
```
cd [The folder's name]
```
```
ndiswrapper -l
```
(This should do nothing)
```
sudo ndiswrapper -i [Name of INF file]
```
```
sudo ndiswrapper -m
```
```
sudo modprobe ndiswrapper
```

That should do it! Wait a little bit, and then right click the network monitor on the top right. Make sure "Enable Wireless" is checked. Now, you can just click on the network monitor, and it will give you a list of wireless networks to connect to.

HOpe that helps

---

### Post by Bucky Ball on 2008-08-07
Great work appi2012. Let's hope that works ... ;)

BTW, how do you get your quote boxes labelled 'CODE' like that? Is it as simple as replacing the [quote] with ```
 when composing your post?

[code]hdajdfh
```Hey, yea! So it is! Answered my own question ... :)

---

### Post by Yotobari on 2008-08-07
I have absolutely no clue what driver Windows is using, it just worked hehe. I really should get a printer if I'm writing all this down, I'm about to attempt Operation: Connect to the internet :D

---

### Post by Yotobari on 2008-08-07
Hmm, do I need to download the ndiswrapper thing before I try and get the connection up? It would apppear just typing it in doesn't install it, heh.
Ok after downloading ndiswrapper and putting it into Ubuntu, it still can't find the file wich is definitely there.

---

### Post by appi2012 on 2008-08-07
You need to have the ubuntu cd in your drive when you install it. If it doesn't work, then go to System -> Administration -> Software Sources, and make sure the the CD is checked.

---

### Post by appi2012 on 2008-08-07
You could copy the folder onto a flash drive, which would make it easier to find.

---

### Post by Yotobari on 2008-08-07
That's what I did do. It's on my drive and in the home folder. And I'm using Wubi not the CD.

---

### Post by appi2012 on 2008-08-07
Then either burn a cd or, just download these debs to your flash drive, copy them to your home folder, and double click them to install:

[http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download]("http://packages.ubuntu.com/hardy/i386/ndiswrapper-utils-1.9/download")

[http://packages.ubuntu.com/hardy/i386/ndiswrapper-common/download]("http://packages.ubuntu.com/hardy/i386/ndiswrapper-common/download")

---

### Post by Yotobari on 2008-08-08
After many hours of fiddling around and more terminals than you can stake a stick at. I have the ndiswrapper downloaded and the Lynksys driver running. My internet cable is definitely plugged in, I havn't turned off any internet settings in Ubuntu and I still have no internet, if anyone has any last ditch attempts to get it running, short of buying another card, it would be greatly appreciated.

---

### Post by Bucky Ball on 2008-08-08
Do this;

System->Administration->Hardware Drivers

Make sure the Broadcom b43 wireless driver is switched off. You also need to make sure that it is blacklisted. This page shows you how;

[http://anomsuratno.wordpress.com/](http://anomsuratno.wordpress.com/)

Good luck and hang in there, you are getting pretty damn close by the sounds and learning a bit as you go ... :)

ps: ndiswrapper is notoriously tricky for those new to Ubuntu (unless you get lucky!) - I went through the exact same thing and never had success. That is why the new driver and setup in Hardy 8.04 for Broadcom cards is so good, mine worked almost straight away.

---

### Post by Yotobari on 2008-08-08
Was I meant to run a Broadcom driver? I'd used a Lynksys one, that might explain what went wrong.

---

### Post by appi2012 on 2008-08-08
what does:
```
lsusb
```
return?

---

### Post by Bucky Ball on 2008-08-08
No, I have a Broadcom card! You must make sure this driver for you in Hardy is switched off re my last post.

```
lsusb
```Means, basically, list USB devices. But I am imagining your card is in the box, not usb plug in type.

[HTML]http://www.ss64.com/bash/[/HTML]

A list of Linux bash commands to have a look at ... :)

---

### Post by Yotobari on 2008-08-08
Yeah the lusb is coming up with my net thing (It is usb) And so I switch off the driver then try and connect to the internet?

---

### Post by Bucky Ball on 2008-08-08
Yep. If the b43 driver is the problem and it is on, you might ... might get instant results in fact. Keep your eye on the wireless light. If not, do a reboot. But as I say, make sure b43 is also blacklisted (re the link on how to do this in my post back a bit) or it will crank up again at reboot.

Getting there ... hopefully! As I say, I had a long battle with ndiswrapper, but my particular card was always going to be problematic. Yours shouldn't be that bad. :)

---

### Post by Yotobari on 2008-08-08
Ok I tried to blacklist the lynksys driver and it kept telling me that it couldn't find it or something along the lines of that .

---

### Post by Bucky Ball on 2008-08-08
No no no! Follow the instructions here:

[http://anomsuratno.wordpress.com/](http://anomsuratno.wordpress.com/)

... and look at the very first part where it tells you how to blacklist the b43 driver.

> First before you start installing ndiswrapper you need to blacklist b43 modules by editing /etc/modprobe.d/blacklist
$ sudo gedit /etc/modprobe.d/blacklist
password:
 then add:
 blacklist b43 (you can put it under blacklist bcm43xx
 save and quit gedit.
Your problem might be that you really need to do this first and I am surprised, if it is not the case, you weren't told this first (left you with someone who had the same card I thought).

You will not have any luck if you blacklist your valid driver! You need to **blacklist the b43** **driver** ... and** switch it off in System->Administration->Hardware Drivers**! That way, when you boot it will* only* attempt to use the *Linksys* driver you want it to use. If the b43 driver is also on, you are going to get a conflict and that could be your problem. You *only* want the *Linksys *driver available ...

:)

---

### Post by Yotobari on 2008-08-08
If it has been blacklisted it should be in the gedit list when that's open right? Because it's in that list when I run the modprobe command.

---

### Post by Bucky Ball on 2008-08-08
```
sudo nano /etc/modprobe.d/blacklist
```Run that and if you don't find it there, it is not blacklisted. If you do find it there but it has a '#' next to it, remover the '#' and that will blacklist it.

ps: 'nano' is just a more basic terminal editor. You can replace that with gedit if you like, sorry ... ;)

---

### Post by Yotobari on 2008-08-08
This is what I get when I run that:

# replaced by b43 and ssb.
blacklist bcm43xx

---

### Post by Bucky Ball on 2008-08-08
> **Yotobari said:**
> This is what I get when I run that:

# replaced by b43 and ssb.
blacklist bcm43xx

As you may have figured, that hash '#' basically means don't run this command, which is why the comments have a hash in front. Thus;

```
# replaced by b43 and ssb
```... hash says 'ignore this'. The line under it is not ignored; no hash first.

Yep, that is good. Now, is it switched off in System->Administration->Hardware Drivers? Go there on the desktop. You should find that driver and an nvidia one. They either do or don't have a tick. If b43 has a tick, untick it. Leave the others as they are.

---

### Post by Yotobari on 2008-08-09
Hmm the only driver in there is a nvidia one, the lynksys driver is under windows wireless and the b43 one doesn't seem to exist at all.

---

### Post by Bucky Ball on 2008-08-09
> only driver in there is a nvidia one, 
the b43 one doesn't seem to exist at all.That is all the way it should be. I have no experience of your card and have just about exhausted what I know on this. I would advise you to post where you are at now with as much detail about your card as possible in the 'Networking and Wireless' forum here;

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

You may have more luck as no-one with experience of this card and Ubuntu seems to be forthcoming here. Another things to do is get the *exact* model of your card and google 'yourcardmodel ubuntu hardy' or something along those lines. Again, just remember when you post in 'Networking and Wireless' don't be vague; be as specific and detailed as possible. The more info you can give the better the help and faster the fix. Try to avoid people having to ask what it is you have got in there.

Good luck with it and sorry I couldn't help ya, but you are close ... ;(

* Update: [http://forums.linksys.com/linksys/board?board.id=Wireless_Adapters](http://forums.linksys.com/linksys/board?board.id=Wireless_Adapters)

Took me literally 3 minutes to find this and we are 6 pages old! Linksys forum about Linux and wireless adapters. Go there before doing anything else I would suggest, but identify your card exactly first. You can do this on their site also.

---

### Post by appi2012 on 2008-08-11
Look at the bottom of your usb wireless adapter. It should say what model number it is. What is it?

---

### Post by Yotobari on 2008-08-12
Appi, I'd hate to be a little ratty here but if you'd so much as skimmed through this topic you'd know that I'd mention the card numerous times and also that I've installed the driver for it already. WUSB54Gv2

---

### Post by appi2012 on 2008-08-13
Sorry about that. (Actually, a search reveals that you never mentioned the exact model number :))

That is the exact same one I have, so you shouldn't have to do anything but those instructions I gave you previously. No need to blacklist anything. Just make sure you use the driver I gave you (the xp one - not the vista one)

---

### Post by Bucky Ball on 2008-08-13
[quote=[appi2012]("http://ubuntuforums.org/member.php?u=613479")]
you shouldn't have to do anything but those instructions I gave you previously.
[/quote]

Exactly what I thought when you posted your post that started with this. It looked like that would work ... 

> I also have a Hp Pavillion with a Linksys Wireless G Wireless card
... :| ?

---


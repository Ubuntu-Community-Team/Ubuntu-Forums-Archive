---
title: "HOWTO - BT Voyager 105"
date: 2006-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by welsh_spud on 2006-03-05
[CENTER]**[SIZE="6"]HOWTO – Install BT Voyager modem drivers[/SIZE]**[/CENTER]

Anybody in the UK who has signed up for broadband from the big  ISP's (BT, AOL, etc) will find that their 'free' modem isn't technically a modem. These 'modems' are what we in the Linux world call Winmodems, because they require a software based driver to mess with all the 00101101's instead of using a hardware chip found in other modems.

These modems are usually fine for day-to-day work such as web browsing and e-mail. They plug into your computer using USB instead of Ethernet. Other than the fact they can sometimes have high ping times, they are perfect for large scale distribution.

The problems start when you want to start using your USB modem with Ubuntu. Companies like BT haven't released any drivers for Linux so the community has made a reverse-engineered driver.

In this HowTo, I will walk you through the installation of the eciadsl driver.

***[COLOR="Sienna"][SIZE="4"]Step 1) Get everything set up.[/SIZE][/COLOR]***

If this is your first dive into the Linux world, some of this tutorial may seem strange and archaic. Don't worry because I'm going to hold your hand all the way through and try my best to explain each step.

So then, before we really start, you will need to get hold of some physical things;
[LIST]
[*]A nice cool and refreshing drink
[*]A computer/partition/friend that has access to the Internet
[*]A blank floppy disk/zip drive/USB stick/CD-R/ or something to transfer media from one place to another.
[*]And a stockpile of patience
[*]Unplug the modem from the USB port[/LIST]

***[COLOR="Sienna"][SIZE="4"]Step 2) Acquiring the software[/SIZE][/COLOR]***

With your friends computer, download the file [http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb](http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb) and the file [http://archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.5-4ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.5-4ubuntu1_i386.deb) from the Internet.

Once those two files are download; burn them to a CD using your favourite CD burning program, or transfer them to a USB drive. The aim is to get this media somehow onto your Ubuntu install.

Log into your Ubuntu computer and go to Places > Home Folder. Now open the device the used to transfer the media. Simply drag and drop the files from the CD to the Home Folder. Those files are now safe on your Ubuntu installation.

***[COLOR="Sienna"][SIZE="4"]Step 3) Installing the buggers[/SIZE][/COLOR]***

Because this HowTo is sort of breaking away from the way programs are normally installed, we are going to have to whip out the trusty Terminal program. Fear not, the things you will be typing are probably the most basic commands in Linux.

Start off by going to Applications > Accessories > Terminal. This will bring up the Terminal program. The only text in the black window should be your username @ the name of your computer followed by a :~$ . This tells us that the command line is ready and waiting for orders. Start off by typing in 

```
ls
```

That is LS, but in lowercase; not an i. When you type that command in, you will see every file and folder that is inside your home folder. 

Next, we are going to install the files you took off the floppy disk. At the time of writing this the files were called:

**eciadsl-usermode_0.11-1_i386.deb**
and
**pppoe_3.5-4ubuntu1_i386.deb**

To install the files type in the Terminal window:

```
sudo dpkg -i pppoe_3.5-4ubuntu1_i386.deb
```

Let that install (few seconds) then type in:

```
sudo dpkg -i eciadsl-usermode_0.11-1_i386.deb
```

Like before, some text should come flying downwards.

Phew! OK that is probably the hardest bit gone now - take a nice sip of your cool refreshing drink that you got from *Step 1)*

We have now installed the drivers to the system, what is left now is configuring the driver.

***[COLOR="Sienna"][SIZE="4"]Step 4) Configuring the driver[/SIZE][/COLOR]***

In the Terminal type in:

```
sudo gedit /etc/hotplug/blacklist
```

This will bring up a text editor. In the file, add the word **dabusb** to the end. This will tell the system not to try and load up the USB modem when it boots (that is eciadsl's job from on). Save, exit and restart the computer.

Once you have rebooted and are logged in, open the terminal again and type in:

```
eciadsl-config-tk
```

This will bring up a very ugly configuration program. This is where the fun begins. In all the text boxes, fill them according to whatever they should be:-

user name: *You should have been given an e-mail user name when you signed up*
password: [I]Whatever[I]
provider: *British Telecom*
DNS1: *Accept default*
DNS2: *Accept default*
VPI: *0*
VCI: *38*
modem type: *BT Voyager 105*
VID1/PID1/VID2/PID2: *accept defaults*
modem chipset: *GS7470*
synch file: */etc/eciadsl/gs7470_synch03.bin*
PPP mode: *Accept default*
is DHCP used? *no*
is a static ip used? *no*
Once all that is filled in, check it again and click the green **[COLOR="YellowGreen"]Create Config[/COLOR]** button. Your done with that window. Now plug in your USB Modem and type in:-
```

/usr/bin/eciadsl-start
```

This should make the lights come on and flash about for a bit. If so, the Internet is now your oyster!

---

### Post by TheDoctor on 2006-04-19
Brilliant! I'm new to Linux and Ubuntu and I made this work. Thanks.

One question though: Do I have to perform the eciadsl-start everytime I need to dial-up?

---

### Post by PriceChild on 2006-04-19
Yup... i think it's possible to make it launch on start up, but i haven't managed it yet.

Remember if you dual boot with windows, you need to disconnect the modem to restart it every time you switch OS.

This method will work with many MANY more modems. (59 to be exact, plus 3 possibly)

Check here for the complete list:
[http://eciadsl.flashtux.org/modems.php](http://eciadsl.flashtux.org/modems.php)

---

### Post by AndyJC on 2006-07-05
All is well untill the **"gedit..."** command. The box that comes up is empty.
Where should **"dubusb"** be typed?

Also...after rebooting - when the command **"eciadsl-config-tk"** is entered... it says i need to be rooted??

Please help,

 Andy

---

### Post by AndyJC on 2006-07-06
Can anyone help?

---

### Post by shame on 2006-07-18
Just type it on the first line of the empty box but I've never needed to do the dabusb on ubuntu so you can probably forget that bit.
You need to run eciadsl-config-tk and in fact any "eciadsl-" command as root so do ```
sudo eciadsl-config-tk
```

---

### Post by AndyJC on 2006-07-20
Cheers for all your help guys, almost there - however, seemed to have stumbled at the last hurdle.

I've configured my  modem and typed in the /usr/bin/eciadsl-start command. - and am greeted with the following error:

[Eci Adsl 4/5] Connecting to provider
nice: cannot set niceness: permission denied.
ERROR: Failed to connect.



 Can anyone help! So close yet so far!!!


 Cheers!

---

### Post by welsh_spud on 2006-07-20
Try

```
sudo /usr/bin/eciadsl-start command
```

---

### Post by AndyJC on 2006-07-20
> **welsh_spud said:**
> Try

```
sudo /usr/bin/eciadsl-start command
```

Tried this... no error message displayed, however - "Connecting to server" is continuously displayed... giving me the impression that it cannot connect to server.

Now... I asked PlusNet (my broadband provider) for my connection password (I've lost mine!) and they replied saying it was the same as the password I use to log into the member centre on the PlusNet site. This doesnt seem right to me... do you think this could be the wrong password - hence not my connection issues?

P.S. EciAdsl 1/5, 2/5 and 3/5 complete successfully.

Any further help much appreciated.

 THanks.

---

### Post by chalkedup on 2006-07-20
hi andy it sounds like the same problem i have with my voyager 100 modem
i need to use the connect command twice to get online
first i use ```
sudo eciadsl-start
```
then wait a bit while it hangs on the ? 3rd stage then i press ctrl + c at the same time to stop it and then type in
```
sudo eciadsl-doctor
```
and then it connects up im not sure if this is the same for everyone but ive noticed a few others have to do the same

---

### Post by shame on 2006-07-20
I'm not sure about the niceness error but I would run sudo eciadsl-doctor before you do anything else and post back with any errors.
I'm having problems with eciadsl and certain kernels at the moment so that could be a factor.

Regarding the password, I'm also with plusnet and the password is indeed the same one you use to login to the site.

I should also mention there seems to have been a few problems connecting to plusnet for the last couple of days and since they have been doing line upgrades and various other changes this could also be a factor.

---

### Post by joe_tie on 2006-08-07
Newbie here (formally OS/2 and Windows).
Just wanted to say thanks for the USB info.
Got my BT Voyager Modem 100 up and running fairly easily.

---

### Post by SPr on 2006-12-03
Hi,

I've been following this excellent tutorial but I've found a couple of problems.

When it comes to:
```
sudo eciadsl-config-tk
```
I get this error:
```
sudo: unable to execute /usr/bin/eciadsl-config-tk: Permission denied
```

So I used:
```
sudo eciadsl-config-text
```
instead and now I get this error:
```
me@me-desktop:~$ sudo eciadsl-config-text
[: 26: ==: unexpected operator
[: 36: 0: unexpected operator
-e 
===== Welcome to the EciAdsl Linux driver configuration =====
...
etc
...
```

The unexpected operators also appear when entering and confirming my password:
```
Type in your password (given by your provider):
[: 905: ==: unexpected operator
Type in your password again (for verification): 
[: 905: ==: unexpected operator
-e ** passwords don't match, try again
```

So, basically, I'm stuck. ](*,) 

The text error looks like a character encoding problem to me. I looked in terminal>character encoding>add or remove but couldn't find a replacement to work.

Any ideas?

Please remember I'm a compete newb with Linux.

Edit:
I'm running Edgy Eft.

Just found the eciadsl faq. My answer looks as if it is there.

---

### Post by james2nd on 2006-12-31
hi (newbie)
 I have just installed dapper on my other computer and not understanding the internet connection process, iv`e just found this thread for the voyager 105, my ISP is PIPEX but the protocol is PPPoA so before I do anything wrong can somebody tell me if it is the same proceeder as PPPoE to setting up the connection. I am completely new to ubuntu but am trying very hard to get as much info as possible.
                            
                             thanks james2nd:confused:

---

### Post by herbertchirata on 2007-01-08
I get the error message when i run the command eciadsl-start 



/usr/bin/eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

ERROR eciadsl-synch SYNCHING: failed
ERROR eciadsl-synch: failed
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

using channel 19
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <magic 0x7e37f2fb>]
sent [LCP ConfReq id=0x1 <magic 0x7e37f2fb>]
Script /usr/bin/eciadsl-pppoeci -vpi 10 -vci 38 -vendor 0x1690 -product 0x0215 -mode LLC_RFC2364 finished (pid 7089), status = 0x0
Modem hangup
Connection terminated.


Please Help  !!!

Regards 
Herbert Chirata:confused:

---

### Post by j-mcalllister on 2007-02-12
hey i started to use the info on the 1st page but it asked for a password ne idea what it would be ?


many thanks 
james

---

### Post by jam'ez on 2007-02-13
> **j-mcalllister said:**
> hey i started to use the info on the 1st page but it asked for a password ne idea what it would be ?


many thanks 
james

The password that your ISP (internet service provider) gave you.

---

### Post by liamwithers on 2007-02-15
Hi, you are not the only one suffering problems with the password, I cannot get it to work, it says there is a 905 error?? =S

Please help somebody!

---

### Post by Pgi947 on 2007-02-16
> **liamwithers said:**
> Hi, you are not the only one suffering problems with the password, I cannot get it to work, it says there is a 905 error?? =S

Please help somebody!


Snap, pretty new to linux, seems straight forward though.

First problem, running gedit command, i just get a blank text document, where do i edit it? also there is no such dir. as /etc/hotplug/ on my set up:confused: 

So i skipped that as earlier suggested, managed to track down how to run eciadsl-config-tk by actually running eciadsl-config-text in terminal then selecting 'option 1' to configure.

I get as far as the second stage, after typing my user name (email address) given to me by my ISP, am then prompted to type my password (given by ISP) no matter what i do or type i get something along the same lines as Liam's post

905: unexpected operator after every password is typed
Then '-e passwords don't match'

Hope someone can help, im not sure what the problem could be, i typed the password identicle at least 10 times, same error :-(

---

### Post by drbenway on 2007-02-19
Hello... complete and utter newbie here, so apologies if I'm making a blindingly obvious mistake here..  I've installed xubuntu on an old laptop..

I downloaded and installed the drivers, but I 'm getting stuck when I get to this bit:

```
sudo gedit /etc/hotplug/blacklist
```

I just get:  

*sudo: gedit: command not found*

Is this because I'm using xubuntu (rather than ubuntu) ??  If so, what command should I be using instead? 

cheers for any help!

---

### Post by drbenway on 2007-02-19
> **drbenway said:**
> Hello... complete and utter newbie here, so apologies if I'm making a blindingly obvious mistake here..  I've installed xubuntu on an old laptop..

I downloaded and installed the drivers, but I 'm getting stuck when I get to this bit:

```
sudo gedit /etc/hotplug/blacklist
```

I just get:  

*sudo: gedit: command not found*

Is this because I'm using xubuntu (rather than ubuntu) ??  If so, what command should I be using instead? 

cheers for any help!

I posted a little prematurely.. oops...  so I understand gedit is the text editor (which doesnt seem to be on xubuntu)

I tried 

```
sudo mousepad /etc/hotplug/blacklist
```

instead, and that brought up a text editor.. I typed **dabusb** but when I try to save I get this error message popping up:

*Error: Can't open file to write*

Any suggestions?  Was trying mousepad a reeaaally stoopid idea?

---

### Post by teaker1s on 2007-02-20
either install gedit or when in text mode there is nano which isn't very nice but works

sudo nano /etc/hotplug/blacklist

---

### Post by Sidders on 2007-02-27
Hi guys,

I tried doing this last week and I encountered similar errors other people have reported above. I figured maybe it was because I was running Ubuntu off a live disc rather than having installed it to a hard drive. Anyway, now I've installed Ubuntu to my hard drive but now I'm getting a problem nobody has yet reported. When I got to the "sudo eciadsl-config-tk" command I got the following error:

$ bash /usr/bin/eciadsl-config-tk: /usr/bin/wish: Bad interpreter: No such file or directory

I can't figure what's causing this problem! Can anyone help? It's doing my head in because I would like to switch to Ubuntu completely, but the only thing stopping me is that I don't have any internet, so it would be useless!

---

### Post by Sidders on 2007-02-28
Ignore that, I've done it! Posting this from my ubuntu system as I speak. I needed to install the tk8.3 package for those interested. Also had to edit my shell scripts so they point to bash and not sh.

---

### Post by Strev_123 on 2007-03-24
Hi all, I've installed everything following the steps provided and all seems well until I get to "/usr/bin/eciadsl-start", then I get the following;
> darren@ubuntu:~$ /usr/bin/eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

/proc/bus/usb/001/004: Permission denied
/proc/bus/usb/001/003: Permission denied
/proc/bus/usb/001/002: Permission denied
/proc/bus/usb/001/001: Permission denied
ERROR can't find your GlobeSpan GS7470 USB ADSL WAN Modem
ERROR eciadsl-synch: failed 
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

nice: cannot set priority: Permission denied
ERROR: failed to connect

Please help as it's getting to be a pain having to reboot to post a query.

---

### Post by David McCaig on 2007-05-09
I am running Ubuntu 7.0.4 and basically have no idea about Ubunutu whatsoever.

I have followed the superb instructions at the top of this page, but have reached a couple of stumbling blocks.

When I attempt to enter the dabusb command I get a blank text box.

I also seem to have encountered the same problems as Sidders when I enter the eciadsl-config-tk command i.e. $ bash /usr/bin/eciadsl-config-tk: /usr/bin/wish: Bad interpreter: No such file or directory

As I have said above I am clueless about Ubuntu, so if someone could explain what I have to do in very simple steps I would be eternally grateful.

---

### Post by David McCaig on 2007-05-10
I have entered the eciadsl-config-text command and that has got me into the configuration tool.

It then lets me enter my user name without any problems, but as soon I try and enter my passport it comes up unexpected operator (905 error) and then when I verify my password it says they do not match.

Can anyone help - I seem to be so close to success.

---

### Post by David McCaig on 2007-05-10
I have now got my password recognised and entered the config tool but the options dont totally match those shown by Welsh Spud.

My ISP is AOL, please can someone help.

---

### Post by David McCaig on 2007-05-11
Gradually making progress, the one thing I cant do is transfer a downloaded synch bin file from my desktop to the /etc/eciadsl folder.

When I try using file manager it says I dont have permission and when I use terminal I dont have a clue what I am doing.

Surely there must be someone out there in Ubuntu land who can help!!!!!!!!!!!

---

### Post by hessiess on 2007-05-13
will this work for the bt voyager 1010 wiless adapter?

---

### Post by john_spiral on 2007-05-17
> **David McCaig said:**
> Gradually making progress, the one thing I cant do is transfer a downloaded synch bin file from my desktop to the /etc/eciadsl folder.

When I try using file manager it says I dont have permission and when I use terminal I dont have a clue what I am doing.

Surely there must be someone out there in Ubuntu land who can help!!!!!!!!!!!

Ubuntu icon  -> Accessories -> Terminal

type:

sudo cp /home/your_username/Desktop/gs7470_synch03.bin /etc/eciadsl/

enter your password.

---

### Post by john_spiral on 2007-05-17
> **Strev_123 said:**
> Hi all, I've installed everything following the steps provided and all seems well until I get to "/usr/bin/eciadsl-start", then I get the following......error......


Please help as it's getting to be a pain having to reboot to post a query.

you will need to type:

sudo /usr/bin/eciadsl-start

enter your password.

---

### Post by philipoflondon on 2007-05-28
Hi,

I've been following this excellent tutorial but I've found a couple of problems.

When it comes to:

Code:
sudo eciadsl-config-tkI get this error:

Code:
sudo: unable to execute /usr/bin/eciadsl-config-tk: So I used:

Code:
sudo eciadsl-config-textinstead and now I get this error:

Code:
me@me-desktop:~$ sudo eciadsl-config-text
[: 26: ==: unexpected operator
[: 36: 0: unexpected operator
-e 
===== Welcome to the EciAdsl Linux driver configuration =====
...
etc
...The unexpected operators also appear when entering and confirming my password:

Code:
Type in your password (given by your provider):
[: 905: ==: unexpected operator
Type in your password again (for verification): 
[: 905: ==: unexpected operator
-e ** passwords don't match, try again

Copied from another post. This is what I get as well can anyone help thanks

---

### Post by hessiess on 2007-05-30
will this work for the bt voyager 1010 wiless adapter?:popcorn:

---

### Post by .naVA on 2007-07-07
This is my 1st time using Linux, I'm running Ubuntu 7.04 Fiesty Fawn.
 When I get too "sudo gedit /etc/hotplug/blacklist" I type that in Terminal, then in the text editor I enter "dabusb" then click save, it says cannot save becuase of no such file, so I look in the /etc/ and there isn't a "hotplug" folder. Please help! :(

---

### Post by jessejazza on 2007-08-05
Very grateful for your excellent post. I have the latest BT Voyager 220V ADSL Voice Router.

I am shortly to install Ubuntu on a spare machine in preparation to saying bye to MS. This router is quite a clever thing and i was wondering how much of your instruction is similar?

It has a USB and ethernet connection and I am planning to set up my windoze machine on one and a m/c with ubuntu on the other. Give myself a year to get fully converted!

Would it be possible to retain the BT-talk phone line (the additional line) with ubuntu. I can only assume that the little remote box that one plugs a normal standard phone into is an encoder - i.e. saving a USB phone appliance... BUT the modem provides the automatic switching between the house number and BT-Talk number.

thx

---

### Post by intel17 on 2007-09-06
If this helps ECIADSL have a newer version 0.12 [http://eciadsl.flashtux.org/download/debian/etch/eciadsl-usermode_0.12-1_i386.deb](http://eciadsl.flashtux.org/download/debian/etch/eciadsl-usermode_0.12-1_i386.deb)

-Pete

---

### Post by jessejazza on 2007-09-08
Be very grateful if someone could advise on the 220. I am using an ethernet connection and thus not sure how much of the instruction i need to follow - some of that instruction was for USB drivers. ](*,)

This Voyager is new as of May.

In windoze i just set it up using the disk. I believe that it can be set up straight from Ubu. The voice part i've now gathered is not installed but part of the router electronics.

thx

---

### Post by jessejazza on 2007-09-09
Now discovered that go to System->Administration->Networking->Wired connection->Properties (set as DCHP)

That easy... AND check the connection is fully pushed home!

That easy - and i thought it was something else. Thought i'd mention in case anyone else has any difficulties.

---

### Post by little zen on 2007-09-21
@ .naVA

having exactly the same problem! found this in the community docs:

> Note: Hotplug is replaced

Note that in newer Ubunto releases, it seems that hotplug itself is not installed. If you try to apt-get install hotplug, you get this message:

Package hotplug is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  udev module-init-tools

udev is configured in /etc/udev

[https://help.ubuntu.com/community/BootHotPlugErrors?highlight=%28%2Fetc%2Fhotplug%2Fblacklist%29]("https://help.ubuntu.com/community/BootHotPlugErrors?highlight=%28%2Fetc%2Fhotplug%2Fblacklist%29")

---

### Post by little zen on 2007-09-22
Discovered you need to delete the dabusb module if there is no blacklist:

> Disable or delete dabusb module:
If /etc/hotplug/blacklist exists, edit it and add a line containing the word 'dabusb' (without the quotes) to it. Restart Linux.
Otherwise, type :
# modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a 

[http://eciadsl.flashtux.org/tutorial.php]("http://eciadsl.flashtux.org/tutorial.php")

"modprobe" didn't work for me but this did the trick:

```
sudo rm /lib/modules/2.6.20-15-generic/kernel/drivers/media/video/dabusb.ko
```

still can't connect though! eciadsl-start gets as far as stage 4/5 then the connection terminates :(

---

### Post by starship54 on 2007-11-14
> **little zen said:**
> still can't connect though! eciadsl-start gets as far as stage 4/5 then the connection terminates :(Same here. Does anyone know how to solve this problem? Thanks.

>  [EciAdsl 4 / 5] Connecting to providers ... 

LCP: timeout sending Config-Requests 
Connection terminated.  

---

### Post by Roy Radford on 2008-01-14
Hi, Everyone,

                      Just to add a little further confusion, I'm also new to Linux, running Ubuntustudio-7.10-alternate-i386 and struggling with Voyager105.

    I don't appear to have a 'hotplug' directory either!

  Great fun having all these slightly different versions to play with, isn't it!   :lolflag:

    Have fun,

      Roy.

---

### Post by geeforce on 2008-04-22
Hi there, I follow the instructions but I can't run eciasl-config-tk. although I've a green entry I can't run it. No such file or directory. There's something else missing (another directory).

What on earth is going wrong?

---

### Post by Hairyloon on 2008-05-15
Are there any drivers for the amd64 yet?
Or how can I make the i386 drivers work with my machine?

---

### Post by lorryt0 on 2008-07-27
Hi everyone I found this thread out of pure desperation I have just came across Ubuntu after building my first PC its nothing flash just built up out of old bits sourced from hear and there but im proud of my effort and excited at the thought of using Ubuntu as an OS but I have stalled on the getting online bit when I found this I thought brilliant so I followed the instructions about three times and failed then realised there was many pages of people with the same problem and the fist page was typed in 2006 so now I am none the wiser, is there anyone out there that can bring this up to date in dummy format please

Lorry

---

### Post by Roy Radford on 2008-07-27
Hi, Lorry,

          Join the club! There seem to be far more questions than answeres on this subject everywhere.

     Have fun,

       Roy.

---

### Post by geezerone on 2008-07-27
removed.

---

### Post by Damnsmalldan on 2008-08-23
Well, to add to the error list, basically, i have set it up(username etc), and when i try to start it up it says; 'Error:failed to get synchronization.' I try using the eciadsl-doctor and it says:'Failed to load  Globespan firmware.' 
Please help me!

---

### Post by Damnsmalldan on 2008-08-25
Ignore my last post, i found a tutorial on google and followed it. For those interested, it is here: [https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043536.html]("https://lists.ubuntu.com/archives/ubuntu-users/2005-July/043536.html").
The problem now however, is that it comes up with this: (note: in place of the smiley should be 364-im not sure what happened!!!)
[EciAdsl 4/5] Connecting to provider...

using channel 11
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <magic 0x7e37f2fb>]
sent [LCP ConfReq id=0x1 <magic 0x7e37f2fb>]
Script /usr/bin/eciadsl-pppoeci -vpi 10 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 12828), status = 0x0
Modem hangup
Connection terminated.

It then runs through various channels, but still will not connect! 
Is this a config error (e.g wrong password) or what? 
Please help!!!!

---

### Post by petelew48 on 2008-11-06
Hi, Im trying to connect to the internet via aol but no joy.
Get as far as 'gedit' but wont save file after entering 'debusb'.
After reboot on entering 'eciadsl-config-tk' I get the message 'bash: /usr/bin/eciadsl-config-tk: /usr/bin/wish: bad interpreter: No such file or directory.
Can anyone help please?

---

### Post by Costageriatrica on 2008-11-29
Can anyone help? I'm an absolute beginner. I was fine up to the configuration programme appearing. My user name went in fine but no typing appeared on screen when I entered my password, and when I entered it again for confirmation, I got the message that the passwords didn;t match. After about 20 tries, I gave up. Is this possibly a glitch in the system, or is it me?

---

### Post by Costageriatrica on 2008-11-29
I had this problem. Key sudo gedit /etc/hotplug/blacklist dabusb and  press enter. Text editor opens under two tags: blacklist and dabusb. Select dabusb and save, Exit and select close blacklist without saving. When you get to the next stage, enter eciadsl-config-text rather than -tk.

---

### Post by steelbloo on 2009-02-09
[FONT="Verdana"][SIZE="3"][COLOR="Indigo"]Hi - I am a complete novice to this and need a little help PLEASE....

I have completed the 'BLUE' section below, When I hit return after typing in the first code in "step 4" a window opens (like a page) I type in dabusb and it tells me /etc/hotplug/blacklist can't be found.  

What am I doing wrong ?????  Sorry, and thank you in advance for your help!

Steelbloo[/COLOR][/SIZE][/FONT]

[COLOR="Blue"]> **welsh_spud said:**
> [CENTER]**[SIZE="6"]HOWTO – Install BT Voyager modem drivers[/SIZE]**[/CENTER]

Anybody in the UK who has signed up for broadband from the big  ISP's (BT, AOL, etc) will find that their 'free' modem isn't technically a modem. These 'modems' are what we in the Linux world call Winmodems, because they require a software based driver to mess with all the 00101101's instead of using a hardware chip found in other modems.

These modems are usually fine for day-to-day work such as web browsing and e-mail. They plug into your computer using USB instead of Ethernet. Other than the fact they can sometimes have high ping times, they are perfect for large scale distribution.

The problems start when you want to start using your USB modem with Ubuntu. Companies like BT haven't released any drivers for Linux so the community has made a reverse-engineered driver.

In this HowTo, I will walk you through the installation of the eciadsl driver.

***[COLOR="Sienna"][SIZE="4"]Step 1) Get everything set up.[/SIZE][/COLOR]***

If this is your first dive into the Linux world, some of this tutorial may seem strange and archaic. Don't worry because I'm going to hold your hand all the way through and try my best to explain each step.

So then, before we really start, you will need to get hold of some physical things;
[LIST]
[*]A nice cool and refreshing drink
[*]A computer/partition/friend that has access to the Internet
[*]A blank floppy disk/zip drive/USB stick/CD-R/ or something to transfer media from one place to another.
[*]And a stockpile of patience
[*]Unplug the modem from the USB port[/LIST]

***[COLOR="Sienna"][SIZE="4"]Step 2) Acquiring the software[/SIZE][/COLOR]***

With your friends computer, download the file [http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb](http://eciadsl.flashtux.org/download/eciadsl-usermode_0.11-1_i386.deb) and the file [http://archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.5-4ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/r/rp-pppoe/pppoe_3.5-4ubuntu1_i386.deb) from the Internet.

Once those two files are download; burn them to a CD using your favourite CD burning program, or transfer them to a USB drive. The aim is to get this media somehow onto your Ubuntu install.

Log into your Ubuntu computer and go to Places > Home Folder. Now open the device the used to transfer the media. Simply drag and drop the files from the CD to the Home Folder. Those files are now safe on your Ubuntu installation.

***[COLOR="Sienna"][SIZE="4"]Step 3) Installing the buggers[/SIZE][/COLOR]***

Because this HowTo is sort of breaking away from the way programs are normally installed, we are going to have to whip out the trusty Terminal program. Fear not, the things you will be typing are probably the most basic commands in Linux.

Start off by going to Applications > Accessories > Terminal. This will bring up the Terminal program. The only text in the black window should be your username @ the name of your computer followed by a :~$ . This tells us that the command line is ready and waiting for orders. Start off by typing in 

```
ls
```

That is LS, but in lowercase; not an i. When you type that command in, you will see every file and folder that is inside your home folder. 

Next, we are going to install the files you took off the floppy disk. At the time of writing this the files were called:

**eciadsl-usermode_0.11-1_i386.deb**
and
**pppoe_3.5-4ubuntu1_i386.deb**

To install the files type in the Terminal window:

```
sudo dpkg -i pppoe_3.5-4ubuntu1_i386.deb
```

Let that install (few seconds) then type in:

```
sudo dpkg -i eciadsl-usermode_0.11-1_i386.deb
```

Like before, some text should come flying downwards.

Phew! OK that is probably the hardest bit gone now - take a nice sip of your cool refreshing drink that you got from *Step 1)*[/COLOR]

We have now installed the drivers to the system, what is left now is configuring the driver.

***[COLOR="Sienna"][SIZE="4"]Step 4) Configuring the driver[/SIZE][/COLOR]***

In the Terminal type in:

```
sudo gedit /etc/hotplug/blacklist
```

This will bring up a text editor. In the file, add the word **dabusb** to the end. This will tell the system not to try and load up the USB modem when it boots (that is eciadsl's job from on). Save, exit and restart the computer.

Once you have rebooted and are logged in, open the terminal again and type in:

```
eciadsl-config-tk
```

This will bring up a very ugly configuration program. This is where the fun begins. In all the text boxes, fill them according to whatever they should be:-

user name: *You should have been given an e-mail user name when you signed up*
password: [I]Whatever[I]
provider: *British Telecom*
DNS1: *Accept default*
DNS2: *Accept default*
VPI: *0*
VCI: *38*
modem type: *BT Voyager 105*
VID1/PID1/VID2/PID2: *accept defaults*
modem chipset: *GS7470*
synch file: */etc/eciadsl/gs7470_synch03.bin*
PPP mode: *Accept default*
is DHCP used? *no*
is a static ip used? *no*
Once all that is filled in, check it again and click the green **[COLOR="YellowGreen"]Create Config[/COLOR]** button. Your done with that window. Now plug in your USB Modem and type in:-
```

/usr/bin/eciadsl-start
```

This should make the lights come on and flash about for a bit. If so, the Internet is now your oyster!

---

### Post by dv3500ea on 2009-09-06
> 
using channel 11
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
sent [LCP ConfReq id=0x1 <magic 0x7e37f2fb>]
sent [LCP ConfReq id=0x1 <magic 0x7e37f2fb>]
Script /usr/bin/eciadsl-pppoeci -vpi 10 -vci 38 -vendor 0x1690 -product 0x0215 -mode VCM_RFC2364 finished (pid 12828), status = 0x0
Modem hangup
Connection terminated.

It then runs through various channels, but still will not connect! 
Is this a config error (e.g wrong password) or what? 
Please help!!!!

I have the same problem, can anyone help.

---


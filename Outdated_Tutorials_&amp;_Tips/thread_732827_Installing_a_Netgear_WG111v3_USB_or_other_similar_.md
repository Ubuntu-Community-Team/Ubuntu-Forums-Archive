---
title: "Installing a Netgear WG111v3 USB or other similar wireless"
date: 2008-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by stooshbunutu on 2008-03-23
**[COLOR="Red"]AS OF VERSION 9.10 THE ADAPTER WORKS ON A 'PLUG AND PLAY' BASIS.[/COLOR]**

**[COLOR="Red"]NOW WORKING FOR 9.04[/COLOR]**

I have done this successfully on numerous installations on numerous machines. So here is how it works:

**Step 1 - *Gathering the Drivers***

This code will gather and unzip the required files into your /home/your_user_name/ directory.
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar -xvjf compat-wireless-2.6.tar.bz2
```


**Step 2 - *Installing the drivers***

```
[COLOR="Blue"]sudo apt-get -y install build-essential debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc lib64stdc++6-4.3-dbg lib64mudflap0[/COLOR]
cd compat-wireless-[COLOR="Red"]yyyy-mm-dd[/COLOR]
make
[COLOR="Blue"]sudo make install[/COLOR]
[COLOR="Blue"]sudo make unload[/COLOR]
[COLOR="Blue"]sudo modprobe rtl8187[/COLOR]

```
[COLOR="Red"]Replace with todays date in the same format[/COLOR]
[COLOR="Blue"]Enter Your Password on prompt after a blue line[/COLOR]

**Step 3 - *Add the rtl8187 module to /etc/modules***

```
gksudo gedit /etc/modules
```

Add *rtl8187* at the end of the list

**Step 4 - *Setup the connection***

Click on the network icon in the system tray to show the connections. Click on "_C_onnect to Hidden Wireless Network..." and simply:
[LIST=1]
[*]Find your notes from when you had the router installed
[*]In the top box type in what you named your router (case sensitive)
[*]Then select from the drop down box what type of encryption your router has
[*]Now enter your router password (again case sensitive)
[/LIST]
Click on connect and you should be away

**Step 5 - *Using your connection***

It may be necessary for some to repeat Step 4.

When you use your USB adapter, 
for best connection have your wireless adapter inserted before switching on your computer.
Always connect to your router with the connect to hidden wireless network option and avoid using the Auto version as this is more likely to drop-out.

**To test your connection at any time:**

Type the following into terminal
```
ping -c1 google.com
```
If the output is *unknown host: google.com* then you have no connection. If the output shows an amount of time taken to connect with google.com then you have a connection.

For additional Ubuntu Support see my new help site - [helpbuntu.mstrutt.co.uk]("http://helpbuntu.mstrutt.co.uk/") - Happy surfing!

---

### Post by oduartix on 2008-04-03
Cheers,

This tutorial is working great, and looks foolproof even for a Linux noob like me, but I hit a wall at step 4.

The instruction
"Double-Click on the network icon in the system tray to bring up the Network Manager." is puzzling me.

The Network Manager (which I believe is that network icon that neighbours the master volume, and that hints "Wired network connection" when I hover it) does nothing on double-click!

Left clicking it shows 2 options:
Wired Network (select by default)
Manual Configuration

Right clicking it shows 1 check:
Enable Networking
and 2 info icons:
Connection Information
About

Am I missing something?
Thanks for all the help.

---

### Post by stooshbunutu on 2008-04-04
> **oduartix said:**
> Left clicking it shows 2 options:
Wired Network (select by default)
Manual Configuration

Manual Configuration is what it will be. It seems to change between the two on my system as to whether to double click or left click, manual configuration.

Sorry to confuse you

---

### Post by oduartix on 2008-04-04
> **stooshbunutu said:**
> Manual Configuration is what it will be. It seems to change between the two on my system as to whether to double click or left click, manual configuration.
Sorry to confuse you
No problem.
I've just realized that my problem is that on the connections tab, I shlud be seeing:
[B]Wireless connection
Wired connection
Modem connection[/B]
but I just see:
[B]Wired connection
Modem connection[/B]
I followed your steps (repeating step 2 and all) without the slightest error message, so I can't figure out why I can't get **wireless** on that list.
BTW, a friend has told me you can install **ndiswrapper** through Synaptic, and that would more than halve Step 1 & 2, besides being less error prone and much more friendly...
Have you tried that?

Damn! I just realized I didn't boot with the pen inserted.
Off to try that!
Will let you know.
Thanks a million so far!

---

### Post by oduartix on 2008-04-05
Well, sadly it's a no go...
I was about to post  apicture of the connections window but I got excited installing other stuff and my Ubuntu won't boot due to lack of disk space.
Will get back to this as soon as i solve the disk space issue...

---

### Post by oduartix on 2008-04-05
This is what I get when I click on Network Connections:

[IMG]http://farm3.static.flickr.com/2276/2390698353_6bafdc7063_o_d.png[/IMG]

Any guess why wireless isn't there?

Thanks.

---

### Post by stooshbunutu on 2008-04-06
Reboot with the wireless in, repeat step 2, and then go to system >> administration >> network tools, and see if wireless interface is on the drop down.

What usb device are you using? is it the WG111v3?

did you install ndiswrapper via the way I shown or via synaptic?

---

### Post by oduartix on 2008-04-07
> **stooshbunutu said:**
> Reboot with the wireless in, repeat step 2, and then go to system >> administration >> network tools, and see if wireless interface is on the drop down.

It's not.

> **stooshbunutu said:**
> What usb device are you using? is it the WG111v3?
Yes.

> **stooshbunutu said:**
> did you install ndiswrapper via the way I shown or via synaptic?
Well, both actually. I tried following your instructions and when I couldn't go further a friend advised me to install ndiswrapper via synaptic.

Perhaps it's time for me to either quit or take the pen back, because even though I can get it to connect to my wireless router on Windows, I can't get Internet through it either...

---

### Post by nick.ncs on 2008-04-08
Thanks a lot.... That helped me a lot...

---

### Post by stooshbunutu on 2008-04-08
> **nick.ncs said:**
> Thanks a lot.... That helped me a lot...

your welcome

---

### Post by stooshbunutu on 2008-04-08
[QUOTE=oduartix;4673909]Well, both actually. I tried following your instructions and when I couldn't go further a friend advised me to install ndiswrapper via synaptic.[QUOTE]

What part of it did you get stuck at when trying it via terminal?

---

### Post by thehuckle on 2008-04-12
Hi, I have exactly the same problems as oduartix, wondering if you could help. I follow your instructions to the letter. I am running Ubuntu 8.04 LTS. 

When it didn't work the first time, I tried repeating. I got errors about ndiswrapper-common in stage 2, ie that it was not installed (despite apt-get install build-essential). So, I installed through synaptic installer, and when I tried step 2 again. I was told that the driver was already installed. 

I am, therefore, confused as to why the wireless option does not show in Network Settings. Any ideas?

---

### Post by stooshbunutu on 2008-04-13
Firstly I have not upgraded to 8.04 yet and this was written for 7.10 so I don't know if that might make a difference.

The error you encountered about ndiswrapper-common not being installed doesn't matter. It is something that is sometimes installed so is removed if it is. You did not need to install it via synaptic, I suggest you remove it via synaptic and try again.

Other than this I am afraid I am not sure.

Regards,

---

### Post by liquidfunk on 2008-04-13
> **oduartix said:**
> It's not.


Yes.


Well, both actually. I tried following your instructions and when I couldn't go further a friend advised me to install ndiswrapper via synaptic.

Perhaps it's time for me to either quit or take the pen back, because even though I can get it to connect to my wireless router on Windows, I can't get Internet through it either...

 As for your problem, what I have done to get my card to work is, install all the NDISwrapper options from Synaptics, open the Windows Wireless drivers program. Then make a file within your home directory name is Wireless or WG111v3 or whatever. Put the following files in it:

[http://www.avengergear.com/upload/WG111v3.tar.bz2](http://www.avengergear.com/upload/WG111v3.tar.bz2)

 (Extracted of course) 

 Then select the .inf in the Windows wireless drivers program. Choose the name of your network in the Wireless Network folder. Reboot, and BANG!

---

### Post by thehuckle on 2008-04-13
Guessed as much, I was just fiddling =]

In the Windows Wireless Drivers GUI, in the list of drivers I've installed WG111v3 is now listed (wooo), and the comment is "Hardware Present: Yes" (double wooo). Unfortunately there is still no wireless option in Network Settings - so still unable to connect (even after reboot). Any ideas?

---

### Post by ccalgreen on 2008-04-16
Great tutorial - I followed it and got my WG111v3 to scan for and detect my local wireless network (matching with a WGR614v7 router).

I have a couple of problems, though. First is it's *extremely* slow to detect and stabilize (anywhere between 5-10 mins) - the connection keeps flickering on and off, and only shows a broadcast strength between 0% and 54%.  This doesn't happen with the same combination under Vista, so could this be a driver issue?

Second, every time I reboot my machine, the setup is lost.  I have to run through the full list of commands here to add and activate the wireless connection each time, even though the messages I receive says that everything had been installed before.

Any ideas?

(Note I am a complete newbie and this is my first post!)

---

### Post by stooshbunutu on 2008-04-16
> **ccalgreen said:**
> Great tutorial - I followed it and got my WG111v3 to scan for and detect my local wireless network (matching with a WGR614v7 router).

I have a couple of problems, though. First is it's *extremely* slow to detect and stabilize (anywhere between 5-10 mins) - the connection keeps flickering on and off, and only shows a broadcast strength between 0% and 54%.  This doesn't happen with the same combination under Vista, so could this be a driver issue?

Second, every time I reboot my machine, the setup is lost.  I have to run through the full list of commands here to add and activate the wireless connection each time, even though the messages I receive says that everything had been installed before.

Any ideas?

(Note I am a complete newbie and this is my first post!)

Are you just selecting your router from the drop down list or are you configuring manually like I suggest?

I have found that roaming mode (selecting from the dropdown) causes a bad connecting and doesn't save your configuration

PS what version of Ubuntu are you using?

---

### Post by morcs on 2008-04-17
Cheers, as a newcomer to Linux I've followed this through, got it working and documented the process I went through here:

[http://bigjumpjames.blogspot.com/2008/04/setting-up-netgear-wireless-adapters-in.html](http://bigjumpjames.blogspot.com/2008/04/setting-up-netgear-wireless-adapters-in.html)

Most of what's there's from this post anyway but hopefully the extra detail might help other new starters.  I got a bit lost at the end but hopefully I can tidy that up as I learn more.

---

### Post by stooshbunutu on 2008-04-17
> **morcs said:**
> Cheers, as a newcomer to Linux I've followed this through, got it working and documented the process I went through here:

[http://bigjumpjames.blogspot.com/2008/04/setting-up-netgear-wireless-adapters-in.html](http://bigjumpjames.blogspot.com/2008/04/setting-up-netgear-wireless-adapters-in.html)

Most of what's there's from this post anyway but hopefully the extra detail might help other new starters.  I got a bit lost at the end but hopefully I can tidy that up as I learn more.

Thankyou for referencing and linking to me on your page :)

---

### Post by ccalgreen on 2008-04-17
> **stooshbunutu said:**
> Are you just selecting your router from the drop down list or are you configuring manually like I suggest?

I have found that roaming mode (selecting from the dropdown) causes a bad connecting and doesn't save your configuration

PS what version of Ubuntu are you using?

I've tried both with the roaming and manual configurations.  Roaming keeps cutting in and out, but with manual, I think I must be missing a step, because even after I enter all my information and choose a connection in the configuration, it won't even attempt to connect.

I tried using DHCP and also assigning a static IP address, but I don't really know what I'm doing.  I was able to login to my router using the same hardware connection in Windows, but I wasn't sure if the information I was noting was what I required to configure the connection in Ubuntu.

Of course, this is probably the most critical piece of hardware I need to get operating, because I have to keep rebooting into Windows to get either advice or downloads since I have no internet connection in Ubuntu without this adapter/router combination working. :(

By the way, I'm using 7.10 Gutsy.

---

### Post by morcs on 2008-04-18
> **stooshbunutu said:**
> Thankyou for referencing and linking to me on your page :)

No problem! Only fair really :)

---

### Post by stooshbunutu on 2008-04-18
> **ccalgreen said:**
> I've tried both with the roaming and manual configurations.  Roaming keeps cutting in and out, but with manual, I think I must be missing a step, because even after I enter all my information and choose a connection in the configuration, it won't even attempt to connect.

I tried using DHCP and also assigning a static IP address, but I don't really know what I'm doing.  I was able to login to my router using the same hardware connection in Windows, but I wasn't sure if the information I was noting was what I required to configure the connection in Ubuntu.

Of course, this is probably the most critical piece of hardware I need to get operating, because I have to keep rebooting into Windows to get either advice or downloads since I have no internet connection in Ubuntu without this adapter/router combination working. :(

By the way, I'm using 7.10 Gutsy.

I have attatched how my setup looks:

You need your routers name (case sensitive) or if it is broad casting then you can select if from the drop down.

If your router is encrypted then you need to select the appropriate encryption type from the drop down and then  type in your password.

I then selected DHCP as it is automatic. Also on the menu before you get that tick the box next to Wireless Lan.

This should do it.

---

### Post by ccalgreen on 2008-04-18
> **stooshbunutu said:**
> I have attatched how my setup looks:

You need your routers name (case sensitive) or if it is broad casting then you can select if from the drop down.

If your router is encrypted then you need to select the appropriate encryption type from the drop down and then  type in your password.

I then selected DHCP as it is automatic. Also on the menu before you get that tick the box next to Wireless Lan.

This should do it.

Thanks - I think it works!  :)  Can it be that it takes a few minutes from a reboot for the adapter to start working?

---

### Post by stooshbunutu on 2008-04-20
> **ccalgreen said:**
> Thanks - I think it works!  :)  Can it be that it takes a few minutes from a reboot for the adapter to start working?

It can be yes but make sure you reboot with the adapter inserted for best results

---

### Post by IdealisticSlob on 2008-04-22
Thank you. Great easy to follow tutorial, it worked perfectly for me and I'm very new to Linux/Ubuntu.

---

### Post by stooshbunutu on 2008-04-22
> **IdealisticSlob said:**
> Thank you. Great easy to follow tutorial, it worked perfectly for me and I'm very new to Linux/Ubuntu.

You're very welcome

---

### Post by J-Tim on 2008-04-29
Great tutorial, and it works perfectly in 7.10, but absolutely no go on an 8.04. :(

Has anyone had any luck, getting WG111v3 to work on Hardy ?

---

### Post by stooshbunutu on 2008-04-30
> **J-Tim said:**
> Great tutorial, and it works perfectly in 7.10, but absolutely no go on an 8.04. :(

Has anyone had any luck, getting WG111v3 to work on Hardy ?

Yer I found that when I upgraded at the weekend, is there a way I can downgrade just as easily without loosing data and settings?

---

### Post by J-Tim on 2008-04-30
> **stooshbunutu said:**
> Yer I found that when I upgraded at the weekend, is there a way I can downgrade just as easily without loosing data and settings?

Not that I know of.

In my case it's a fresh install, as the box is brand new.

I ended up installing 8.04 anyway, hoping that the solution shall be found. Another reason is that because I couldn't get my SATA DVD-ROM drive to work under 7.10. 

Very painful. :(

---

### Post by oduartix on 2008-05-01
> **thehuckle said:**
> Guessed as much, I was just fiddling =]

In the Windows Wireless Drivers GUI, in the list of drivers I've installed WG111v3 is now listed (wooo), and the comment is "Hardware Present: Yes" (double wooo). Unfortunately there is still no wireless option in Network Settings - so still unable to connect (even after reboot).

This is exactly what happened to me too. 
Both in 7.10 and now in 8.04.
:(

---

### Post by stooshbunutu on 2008-05-01
Its strange though coz when i upgraded I downloaded the updates on the new system and it reads the driver, the wireless option appears in the network manager and it even gives me a signal strength on the drop-down next to the name of my router. But for some reason it just doesn't want to use the internet.

---

### Post by bocmaxima on 2008-05-02
I am having a problem with this too, it just isn't working...in the NDISGTK it says the hardware isnt present either...anyone have any ideas?

---

### Post by tora201 on 2008-05-03
My story:

I was experiencing random dropouts and was about to give up when I came across this guide. Anyway, for some reason, when I put in the ESSID as described in this tutorial, it somehow recorded it wrongly, because upon rebooting, wireless was NOT recognized -- no matter what I did. To solve it, I RIGHT clicked on the internet icon in the tray and selected "edit wireless networks". and then fixed the "bssids" to read the same as the "name." 

Mine was 
Name: 00160192A6EC --> as I originally entered it
bssids: 00:16:01:92:A6:ED  !!!  --> NOT EC! A bug in 8.04, perhaps?
Anyway, after changing it to EC, all worked fine upon reboot.

p.s I found no need to put a router password in when originally setting it up, btw.

---

### Post by Volume on 2008-05-07
Thank you for posting these instructions.  Just one problem.  How can I install the devices if I have no internet connection, except for the wireless one which I am trying to configure?

---

### Post by stooshbunutu on 2008-05-08
> **Volume said:**
> Thank you for posting these instructions.  Just one problem.  How can I install the devices if I have no internet connection, except for the wireless one which I am trying to configure?

either with an ethernet cable or you can download them before hand (on the computer you posted this from) and transfer them to you /home/username/ directory with a USB thumb drive or similar

---

### Post by imaginal on 2008-05-13
Following the directions word for word, I get hung up after typing "make"

> ***CFLAGS was changed in "/home/travis/ndiswrapper-1.49/driver/Makefile". Fix it to use EXTRA_CFLAGS. Stop

I have no idea what this means... any help?

---

### Post by J-Tim on 2008-05-16
No idea, sorry.

I can confirm though that authentication still doesn't work on 2.6.25.2 kernel. :(

---

### Post by erutangis on 2008-05-17
> **imaginal said:**
> Following the directions word for word, I get hung up after typing "make"



I have no idea what this means... any help?
Hi.

I did a global change from cflags to extra_cflags in the makefile and it fixed the problem.

However, I'm running 8.04 mythbuntu, and despite following the instructions I'm not getting a wireless connection coming up in the network manager.  The same machine has XP on it and I've tested the wg111v3 and the connection in XP and it works.

Any other suggestions?  Thanks to all the people that have helped on this thread :).

---

### Post by CollisionInc on 2008-05-17
Followed the instructions to the letter
Managed to see my Wireless device installed and set up
network options etc.

However when i rebooted again it was gone from the Networking Panel

Any Ideas?

> **stooshbunutu said:**
> I have done this successfully on numerous installations on numerous machines. So here is how it works:

**Step 1 - *Gathering the Drivers***

For the WG111v3 this code will gather and unzip the files in your /home/your_user_name/ directory.
```
wget http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz
wget http://www.avengergear.com/upload/WG111v3.tar.bz2
tar xvvf ndiswrapper-1.49.tar.gz
tar xvvf WG111v3.tar.bz2
```
For others use the same ndiswrapper code but you will need to find your own .inf and .sys files requires for your USB adapter.

**Step 2 - *Installing the drivers***

This code for WG111v3:
```
cd ndiswrapper-1.49
make
[COLOR="Blue"]sudo su[/COLOR]
apt-get remove ndiswrapper-common
apt-get install build-essential
make install
ndiswrapper -i ../[COLOR="Red"]WG111/WG111v3.inf[/COLOR]
depmod -a
modprobe ndiswrapper
ndiswrapper -m
exit
```
[COLOR="Blue"]Enter Your Password on prompt after sudo su[/COLOR]
[COLOR="Red"]For non-WG111v3 users replace the red path with the path to your USB's .inf file[/COLOR]

**Step 3 - *re-configure***

Reboot with your wireless USB inserted.
Then repeat Step 2.

**Step 4 - *Setup the connection***

Double-Click on the network icon in the system tray to bring up the Network Manager. Click on "Wireless Network" tick the box on the left of it and then click on "Preferences". For some roaming mode will work fine but for greater security and to stop it dropping out, untick the box and do the following:
[LIST=1]
[*]Find your notes from when you had the router installed
[*]In the top box type in what you named your router (case sensitive)
[*]Then select from the drop down box what type of encryption your router has
[*]Now enter your router password (again case sensitive)
[/LIST]
Now restart your computer again with the USB adapter inserted.

**Step 5 - *Using your connection***

It may be necessary for some to repeat Step 4.

When you use your USB adapter, for best connection have it inserted before you switch on your computer.

**To test your connection at any time:**

Type the following into terminal
```
ping -c1 google.com
```
If the output is *unknown host: google.com* then you have no connection. If the output shows an amount of time taken to connect with google.com then you have a connection.

For additional Ubuntu Support see my new help site - [helpbuntu.iwarp.com]("http://helpbuntu.iwarp.com/") - Happy surfing!

---

### Post by Johnno1234 on 2008-05-31
> **stooshbunutu said:**
> either with an ethernet cable or you can download them before hand (on the computer you posted this from) and transfer them to you /home/username/ directory with a USB thumb drive or similar

I too have tried following your instructions but when I get to 

apt-get install build-essential

it seems to try and connect to the internet then and as I am not connected I cannot download the package. Is there anyway round this other than finding an ethernet connection?

---

### Post by Johnno1234 on 2008-06-03
From 
[http://bigjumpjames.blogspot.com/2008/04/setting-up-netgear-wireless-adapters-in.html]("http://bigjumpjames.blogspot.com/2008/04/setting-up-netgear-wireless-adapters-in.html")
> 
Step Three - Handle Rebooting
After this great success, I was dismayed when next time I booted my machine I was back to square one. I wandered off to the gym and returned determined to work out what was going on. It turns out you need to do a little more work in order to have your wireless adapter set up each time you boot into Ubuntu.

Add NDISwrapper to boot

Again I'm not sure how this bit works, but intend to elaborate as I find out:

ndiswrapper -m

Then add the line "ndiswrapper" to the the /etc/modules file which you can edit using the following command:

gedit /etc/modules

Hopefully that's it!


---

### Post by perlPiper on 2008-06-13
**Thank You!!** for this excellent post. You ROCK!

---

### Post by Extra on 2008-06-13
step 4 isn't working for me, when I click on the network icon it doesn't give a wireless option.

(I'm using 8.04)

---

### Post by the goat boy on 2008-07-09
This is the same for me

ndiswrapper tells me that the device is there and the driver is loaded.

but if i click on network, there is no option for wireless

can some one please help us out.

i am totally fed up of beating my head against the wall.

---

### Post by icestac on 2008-08-01
> **erutangis said:**
> I did a global change from cflags to extra_cflags in the makefile and it fixed the problem.

I had this compile error and some others.  Each time I fixed one error another would pop up.  I finally just downloaded ndiswrapper-1.53 and it compiled and worked fine.  

BTW - This is on 8.04

Thanks!
~Jeff

---

### Post by duckfeet on 2008-08-05
I just installed Ubuntu 8.04 a couple of months ago, on this old Dell Laptop(Inspiron 2600), and have spent about three days working on this wireless setup, w/WG111v3, and getting more and more frustrated, and at first, this installation didn't work either, and I was about to give up, and say the hell with it, plug in a damn cable and quit, but I tried a couple things, it worked, and I felt I should post them, since I had similar problems that others mentioned, and even tho I still don't understand exactly *why* it's working now, I did keep a log of what I did, tho it's all sadly filtered thru my begninners' brain and vocabulary...

I gave up on the Synaptics Package manager, and needed to just use Stoosh's command-line instructions, after removing twice the "ndiswrapper" setup I got from Synaptics PM.

I had to *leave* in "ndiswrapper-common", or I got the same message others did..."that there was no such directory" or something...so I didn't uninstall it, and this was first inkling, this might work...

I had to play around a little w/the "tar" commands, and to make sure everything was in my "home" directory, *not* in the /usr/sbin, where Synaptics had put them...just didn't seem to work as good...

After a couple tries, again, finally the little light came on, and I almost fell off my chair, and forgot what to do next, but kept plugging, as only *then* did "Wireless" reappear on the Network Menu...I tried manual, but DHCP worked...didn't need static IP...

I still had no connection, and had to go back to my router, and see what kind of setup I  had: (WPA Personal), and I also didn't realize that even tho the Properties Menu didn't have enough *room* for the full 22 character key, it still was what I needed to put in, going where it needed to go, as it finally worked, and Ping, hell, "google" itself came up on my browser, and was *sooo* happy...

So anybody else struggling w/this, u have my sympathy, and as a frustrated noobie to Linux, I truly thankyou Stooshbunutu, as except for some rookie problems, this *worked* and nothing else had...:)

---

### Post by stooshbunutu on 2008-12-07
Ok so I understand that this tutorial became rather obsolete with the 8.04 system. However, I have got it working again for the 8.10 release and am posting now from my wirelessly connected laptop. I have altered the tutorial accordingly.

For those that are interested, the problem seemed to be with the make file in ndiswrapper 1.49 not being compatable with the latest version of the linux kernel. However I have switched to a more recent version of ndiswrapper from a different source and this is perfectly compatable. Also 8.10 seems to handle wireless connections alot better than previous distros.

So Happy times all around.

Regards

Stooshbunutu ):P

---

### Post by raccaman on 2008-12-08
I have a problem: I'm not so expert in linux, how can i install ndiswrapper 1.54, because I downloaded it, and it is a folder, how can I install it in ubuntu after having put in a flash memory (now without internet I'm using windows)?

---

### Post by stooshbunutu on 2008-12-08
> **raccaman said:**
> I have a problem: I'm not so expert in linux, how can i install ndiswrapper 1.54, because I downloaded it, and it is a folder, how can I install it in ubuntu after having put in a flash memory (now without internet I'm using windows)?

you copy that folder your home folder and the in terminal you use the

```
cd ndiswrapper-1.54
```

To change to that directory and then follow the tutorial from that point (step 2 ) with the next step being the ```
make
``` command

Note: the ndiswrapper-1.54 is the name of your folder, if yours is named something different then use that name, if there is a space in that name use quote marks around the folder name eg:

```
cd 'my folder'
```

Hope that works for you

Regards,

Stooshbunutu

---

### Post by patv on 2008-12-08
@stooshbunutu

I posted earlier today about my WG111v3 problems on Intrepid; full config etc. here: [http://ubuntuforums.org/showthread.php?t=1005482](http://ubuntuforums.org/showthread.php?t=1005482).

In short, the NIC and Intrepid worked out of the box, but I get disconnects from the WLAN and hangs when running traffic intensive tasks like torrent d/l. These need a full reboot to clear.

If I wanted to go down the ndis route as per your post, would I have to disable the existing realtek drivers -- auto installed -- somehow first? If so, how would I do that?

Thanks, Patrick (relative newbie).

---

### Post by stooshbunutu on 2008-12-09
> **patv said:**
> @stooshbunutu

I posted earlier today about my WG111v3 problems on Intrepid; full config etc. here: [http://ubuntuforums.org/showthread.php?t=1005482](http://ubuntuforums.org/showthread.php?t=1005482).

In short, the NIC and Intrepid worked out of the box, but I get disconnects from the WLAN and hangs when running traffic intensive tasks like torrent d/l. These need a full reboot to clear.

If I wanted to go down the ndis route as per your post, would I have to disable the existing realtek drivers -- auto installed -- somehow first? If so, how would I do that?

Thanks, Patrick (relative newbie).

I'l look into it (as I have only ever gone down the ndis route),

for know you could always limit the upload / download speed of the torent so it isn't as heavy usage. On the transmission client you right click on the torent, click details, go to the option tab and check the two limit boxes, setting the limit to say 50 up 50 down. While this is not an answer to your question it will at least allow you to use torrents for a while.

Also, is your router hidden / encripted as this can effect connectivity.

---

### Post by stooshbunutu on 2008-12-09
> **patv said:**
> @stooshbunutu

I posted earlier today about my WG111v3 problems on Intrepid; full config etc. here: [http://ubuntuforums.org/showthread.php?t=1005482](http://ubuntuforums.org/showthread.php?t=1005482).

In short, the NIC and Intrepid worked out of the box, but I get disconnects from the WLAN and hangs when running traffic intensive tasks like torrent d/l. These need a full reboot to clear.

If I wanted to go down the ndis route as per your post, would I have to disable the existing realtek drivers -- auto installed -- somehow first? If so, how would I do that?

Thanks, Patrick (relative newbie).

If your saying that you didn't install anything additional to the basic 8.10 install in the way of wireless workings, then no you don't need to disable anything. My tutorial is a complete initial installation to working wireless.

So answer to your question you won't need to disable anything.

---

### Post by patv on 2008-12-11
> **stooshbunutu said:**
> I'l look into it (as I have only ever gone down the ndis route),

Thank you.

> **stooshbunutu said:**
> for know you could always limit the upload / download speed of the torent so it isn't as heavy usage. On the transmission client you right click on the torent, click details, go to the option tab and check the two limit boxes, setting the limit to say 50 up 50 down. While this is not an answer to your question it will at least allow you to use torrents for a while.

Nope, tried that. Still bugs out after a short while...

> **stooshbunutu said:**
> Also, is your router hidden / encripted as this can effect connectivity.

No. And it's not a case of port forwarding not being setup, or anything daft like router logging (I've a Netgear DG834, which is apparently renowned for screwing up when logging) -- I setup specific rules to allow unrestricted and unlogged UDP and TCP traffic on the ports that the torrent client(s) were using.

> **stooshbunutu said:**
> If your saying that you didn't install anything additional to the basic 8.10 install in the way of wireless workings, then no you don't need to disable anything. My tutorial is a complete initial installation to working wireless.

So answer to your question you won't need to disable anything.

Even though I currently do have wireless connectivity? Simply installing the NDIS drivers will override the default (and working) built-in realtek ones?

Any further suggestions would be most welcome. Thanks.

---

### Post by stooshbunutu on 2008-12-11
> **patv said:**
> Even though I currently do have wireless connectivity? Simply installing the NDIS drivers will override the default (and working) built-in realtek ones?

Any further suggestions would be most welcome. Thanks.

The installation guide I have written works from a new installation, I gets all you need, and documents all the steps you need to take,

so essentially yes, it will.

---

### Post by mikeypc2006 on 2008-12-15
Hi,

I followed the instructions twice, both times with the wireless adapter plugged in.  I can see wireless networks, yet trying to connect to mine, WEP 64 encryption is not an option.  What am I doing wrong?

I'm running Ubuntu 8.10

Cheers! :)

---

### Post by stooshbunutu on 2008-12-15
> **mikeypc2006 said:**
> Hi,

I followed the instructions twice, both times with the wireless adapter plugged in.  I can see wireless networks, yet trying to connect to mine, WEP 64 encryption is not an option.  What am I doing wrong?

I'm running Ubuntu 8.10

Cheers! :)

Don't wory you haven't done anything wrong.

64 bit key is no longer a specific option, you need to select the WEP 40/128-bit Key as the sixty is included in the range 40 _<_ x _<_ 128, this is what I do with my 64 bit encryption and it works just fine.

Any more trouble just let me know and I will be happy to help

---

### Post by mikeypc2006 on 2008-12-15
> **stooshbunutu said:**
> Don't wory you haven't done anything wrong.

64 bit key is no longer a specific option, you need to select the WEP 40/128-bit Key as the sixty is included in the range 40 _<_ x _<_ 128, this is what I do with my 64 bit encryption and it works just fine.

Any more trouble just let me know and I will be happy to help

Thanks for your reply.  I've tried with WEP 40/128-bit Key with my network key but I still can't connect to my network.  It tries to connect and throws up the dialog box asking for the security details.

What is WEP index?  It's not an option on my Asus EEE but on my other laptop with the Netgear dongle, it is.  However, whatever I select, nothing seems to be the answer in terms of connecting to my network.

---

### Post by inxygnuu on 2008-12-15
thanks a lot, but I looked at "windows wireless drivers" to see why it wasn't working and it said "hardware not present" I am using a pci card for mine. I would also like to know if this works for jaunty, because not even my Ethernet works in jaunty...

---

### Post by stooshbunutu on 2008-12-16
> **inxygnuu said:**
> thanks a lot, but I looked at "windows wireless drivers" to see why it wasn't working and it said "hardware not present" I am using a pci card for mine. I would also like to know if this works for jaunty, because not even my Ethernet works in jaunty...

Glad I could help, as regards to juanty, I managed to get absolutely no internet working ever though I upgraded from gutsy using my wireless to download the additional files. I had to revert to gutsy with the alternate CD I have. I was so glad when I heard that intrepid had much better access to the internet and wireless capabilities.

---

### Post by stooshbunutu on 2008-12-16
> **mikeypc2006 said:**
> Thanks for your reply.  I've tried with WEP 40/128-bit Key with my network key but I still can't connect to my network.  It tries to connect and throws up the dialog box asking for the security details.

What is WEP index?  It's not an option on my Asus EEE but on my other laptop with the Netgear dongle, it is.  However, whatever I select, nothing seems to be the answer in terms of connecting to my network.

That occasionally happens to me. I have found that if this happens, unplug the USB dongle, count to 10 and then plug it back in, wait for it to load up and try again.

I realise that while with 7.10 it was best to have the wireless inserted on boot up, however now, in 8.10, it seems it is best to wait for it to boot up before inserting the wireless. I will change my tutorial accordingly.

WEP index? is just the password for the type of encryption on your router.

Is your network hidden or broadcast? One thing I have found is that you connect better always if you select the option connect to hidden wireless network and fill in the details accordingly.

Hope this helps

---

### Post by 2ashishs on 2009-01-25
Awesome.. atleast it seems.. havent fiddled arnd much.. just followed your tutorial step-by-step and i was able to detect to detect wireles networks in my area..

Thanks!!

---

### Post by stooshbunutu on 2009-01-25
> **2ashishs said:**
> Awesome.. atleast it seems.. havent fiddled arnd much.. just followed your tutorial step-by-step and i was able to detect to detect wireles networks in my area..

Thanks!!

You're very welcome, glad I could help

---

### Post by krishmish on 2009-01-30
perfect solution for installing the wg111v3 usb on intrepid...cheers!!!

---

### Post by stooshbunutu on 2009-01-30
> **krishmish said:**
> perfect solution for installing the wg111v3 usb on intrepid...cheers!!!

Glad I could Help :D

---

### Post by laffinet on 2009-02-07
Hi !

I followed your instructions but so far could not get my Netgear WG111v3 adapter to work.

I can see my wireless network, but I can't connect to it.

I'm being asked for the password, but it just keeps on trying to connect (I guess), without being successful.

I'm running Mythbuntu 8.10, wireless network not hidden, WPA encryption.

BTW One thing I noticed is that when I boot with the USB adapter in there's a long pause after logging in.

---

### Post by jjoltra on 2009-02-07
Hello all, 
I've got the same problem. It looks like everything is properly done, but it is unable to get a response from the DHCP server (set up in the WIFI router), and eventually it ends up with an autoconfig IP (the way Windows works). 
In the router logs, there is no evidence that the request ever got there.
Same happens with WPA, WEP or with no security at all.

Thanks from Valencia.
Juanjo.

---

### Post by tkaiser on 2009-02-18
You don't need to use the ugly ndiswrapper at all to get a WG111v3 working on Ubuntu 8.10. Here is what I did:

**Step 1:**
Get the latest compat-wireless sources ready:
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar -xvjf compat-wireless-2.6.tar.bz2
```

[B]Step 2:
[/B]Build the modules and unload all the previously installed ones. This might take a while as it will build all the modules incuded in this package.
```
cd compat-wireless-2.6
make
sudo make install
sudo make unload
```

[B]Step 3:
[/B]Load the rtl8187 driver
```
sudo modprobe rtl8187
```

[B]Step 4: 
[/B]Add the module to /etc/modules
```
gksudo gedit /etc/modules

```Add rtl8187 at the end of the list

**Step 5**
To avoid problems you should blacklist the ndiswrapper module.
```
gksudo gedit /etc/modprobe.d/blacklist

```
And add ndiswrapper to the end of the list

Activate wireless networks in network manager. Your network should show up and you should be able to connect perfectly. If not, try rebooting.

I hope this works for you too. I get a full speed connection with this, ndiswrapper gave me an unstable, slow connection. Please let me know if you are successful or not.

---

### Post by sailthesea on 2009-02-19
Great fix for the netgear router tkaiser
Had to thank you in person as I was linked to it and you weren't in the thread
I hope it works for everyone else
You've made a random person very happy!

Prosper friend

---

### Post by jjoltra on 2009-02-20
I have to check this out. If it works, I'll be glad.
Thanks,

---

### Post by pbb_84 on 2009-02-21
Tkaiser, 

Thanks for suggesting the installation of compat-wireless-2.6. For two days I have been struggling with nsdiswrapper with no results. Then, I saw your post. I am now able to connect perfectly. However, I had to reboot a few times before it worked.

---

### Post by maulattu on 2009-02-21
> **stooshbunutu said:**
> 
*cut*


it works, thank you! :popcorn:

ps: WPA is ok, not WPA2

---

### Post by oleirgens on 2009-02-22
> **tkaiser said:**
> You don't need to use the ugly ndiswrapper at all to get a WG111v3 working on Ubuntu 8.10. Here is what I did:



Thanks, this worked for me as well. However, I can't seem to get the speed above 11 mbps in a 54 mbps network. Any tricks or settings you can recommend?

Rgds

Ole Irgens

---

### Post by tkaiser on 2009-02-22
No, I have the same issue. I found out that the speed rises when you have stronger signal. However, 11MB have been the maximum for me. I tried setting a fixed bitrate via iwconfig but all it did was drop the connection.
I guess all we can do is hope that the developers will improve their code. :(

---

### Post by jjoltra on 2009-02-28
Eventually I have found time enough to spend on this issue and, eureka, thanks tkaiser your solutions worked for me as well. At first I had doubts as it missed a lot of packets (ping to the router) but in the end I saw it was nothing but a lack of coverage. 
Thanks again from Valencia!
JJ

---

### Post by fattinka on 2009-03-01
Shame, doesn't seem to work for Intrepid amd64 :(

---

### Post by c-lou on 2009-03-14
Thank you very very much to stooshbunutu! Your instructions worked perfectly on my Thinkpad R50e and Ubuntu 8.10 :)

---

### Post by strom83 on 2009-04-01
Thank you a thousand times for this great solution. I standard intrepid ibex rtl8187 modules, the connection was horrible! After I installed the new compat drivers it works great! :guitar:

---

### Post by lost123 on 2009-04-12
Hey i just tred this but still having problems..it seems that I can connect to an unsecure wireless network but it is not connecting to my WEP network. Both the little ball things turn green (on the wireles manager applet) but then it just asks for my password again :( please help...

Also i installed compat-wireless-2009-04-12.tar.bz2 instead of compat-wireless-2.6.tar.bz2 because i couldnt download it but i dont think thats the cause of the problem...

thanx

---

### Post by Mark Porter on 2009-04-24
Hi,

Installed compact-wireless-2.6 as you suggested. The wireless works fine. However, Java seems to now make my computer unstable. If I use any application/go to any webpage that needs java, my computer completely freezes. Any suggestions on how I can fix the issue?

Thanks!

---

### Post by xipmix on 2009-04-27
> **tkaiser said:**
> You don't need to use the ugly ndiswrapper at all to get a WG111v3 working on Ubuntu 8.10. Here is what I did:

**Step 1:**
Get the latest compat-wireless sources ready:
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar -xvjf compat-wireless-2.6.tar.bz2
```


This has changed - you now need to go to the download page
[http://wireless.kernel.org/users/Download/](http://wireless.kernel.org/users/Download/)
and *read* the information there before attempting to download something.

I tried the 2009-04-20 tarball and it failed to build on 8.10 (2.6.27-11-generic). 

Then I discovered an even easier method of doing the same thing:
```

sudo aptitude install linux-backports-modules-intrepid

```
in which all the hard work has been done.
The changelog showed it had been updated in about 2008 December which was recent enough for me.

---

### Post by losty on 2009-05-08
hello, im wubi and dual booting xp pro with ubuntu 9.04

the problem i have is the connection is incredibly slow or connection drops

however if i log out and boot onto XP, the connection is fast??!

any ideas?

---

### Post by ubudog on 2009-09-01
> **stooshbunutu said:**
> **[COLOR="Red"]NOW WORKING FOR 9.04[/COLOR]**

I have done this successfully on numerous installations on numerous machines. So here is how it works:

**Step 1 - *Gathering the Drivers***

This code will gather and unzip the required files into your /home/your_user_name/ directory.
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar -xvjf compat-wireless-2.6.tar.bz2
```


**Step 2 - *Installing the drivers***

```
[COLOR="Blue"]sudo apt-get -y install build-essential debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc lib64stdc++6-4.3-dbg lib64mudflap0[/COLOR]
cd compat-wireless-[COLOR="Red"]yyyy-mm-dd[/COLOR]
make
[COLOR="Blue"]sudo make install[/COLOR]
[COLOR="Blue"]sudo make unload[/COLOR]
[COLOR="Blue"]sudo modprobe rtl8187[/COLOR]

```
[COLOR="Red"]Replace with todays date in the same format[/COLOR]
[COLOR="Blue"]Enter Your Password on prompt after a blue line[/COLOR]

**Step 3 - *Add the rtl8187 module to /etc/modules***

```
gksudo gedit /etc/modules
```

Add *rtl8187* at the end of the list

**Step 4 - *Setup the connection***

Click on the network icon in the system tray to show the connections. Click on "_C_onnect to Hidden Wireless Network..." and simply:
[LIST=1]
[*]Find your notes from when you had the router installed
[*]In the top box type in what you named your router (case sensitive)
[*]Then select from the drop down box what type of encryption your router has
[*]Now enter your router password (again case sensitive)
[/LIST]
Click on connect and you should be away

**Step 5 - *Using your connection***

It may be necessary for some to repeat Step 4.

When you use your USB adapter, 
for best connection have your wireless adapter inserted before switching on your computer.
Always connect to your router with the connect to hidden wireless network option and avoid using the Auto version as this is more likely to drop-out.

**To test your connection at any time:**

Type the following into terminal
```
ping -c1 google.com
```
If the output is *unknown host: google.com* then you have no connection. If the output shows an amount of time taken to connect with google.com then you have a connection.

For additional Ubuntu Support see my new help site - [helpbuntu.mstrutt.co.uk]("http://helpbuntu.mstrutt.co.uk/") - Happy surfing!

Thank You so much!  This works! :D

---

### Post by stooshbunutu on 2009-11-02
> **ubudog said:**
> Thank You so much!  This works! :D

You're welcome :)

---

### Post by stooshbunutu on 2009-11-02
Hey all :)

Ok, so I've recently bought a new laptop. I now have a Sony VAIO VGN-NW11S. This comes with a built-in wireless card which connected to the internet seamlessly. I thought that I would still test out the WG111v3 to see if it works. I disabled my wireless card and connected using the USB instead (using WPA / WPA2). This seems to work fine but obviously it isn't quite as good seeing as this is a USB G rated compared to the N rated integrated card. I also discovered that I could connect to two networks via wireless now using the wireless card and the USB. Or connect to the same network twice when lots of people are using it to gain a double preference for when I want faster downloads.

So to summarise, in 9.10, you don't need to do anything to get the wireless adapter working... it just does.

---

### Post by alepippirimerlo on 2009-11-04
> So to summarise, in 9.10, you don't need to do anything to get the wireless adapter working... it just does. 
thank you anyway, man.
you'd been our salvation.
THANKS!):P

---

### Post by stooshbunutu on 2009-11-04
> **alepippirimerlo said:**
> thank you anyway, man.
you'd been our salvation.
THANKS!):P

Assuming that no special drivers were auto installed for my chipset. But yes, it would seem that way :) and ur welcome, glad to have been of service

---

### Post by alepippirimerlo on 2009-11-04
...annoying you again.:lolflag:
after a wonderfull installation of Kubuntu 9.10 iwconfig tell me : Access-Point not associated.
Do u have any idea to resolve it and let me surf?
thank u man!:KS
p.s.
i'm under se7en right now...

---

### Post by stooshbunutu on 2009-11-04
> **alepippirimerlo said:**
> ...annoying you again.:lolflag:
after a wonderfull installation of Kubuntu 9.10 iwconfig tell me : Access-Point not associated.
Do u have any idea to resolve it and let me surf?
thank u man!:KS
p.s.
i'm under se7en right now...

As an initial thought, noting seems to work properly on 9.10 until you run:
```

sudo apt-get update
sude apt-get upgrade
```

If still nothing let me know :)

---

### Post by alepippirimerlo on 2009-11-04
> **stooshbunutu said:**
> As an initial thought, noting seems to work properly on 9.10 until you run:
```

sudo apt-get update
sude apt-get upgrade
```

If still nothing let me know :)

but i haven't any connection on Kubuntu!

---

### Post by stooshbunutu on 2009-11-04
> **alepippirimerlo said:**
> but i haven't any connection on Kubuntu!

do you not have an ethernet cable you can temporarily plug in wiht? like used when u connected upt your router initially?

---

### Post by alepippirimerlo on 2009-11-06
i've reached pinging my router once!
the way to browser is coming..
BTW eth is several flats downstair ,and i don't like to transfer my tower..
i'm trying to install WICD, only for trying sake...

---

### Post by krtin on 2009-12-05
> **stooshbunutu said:**
> **[COLOR=Red]AS OF VERSION 9.10 THE ADAPTER WORKS ON A 'PLUG AND PLAY' BASIS.[/COLOR]**

**[COLOR=Red]NOW WORKING FOR 9.04[/COLOR]**

I have done this successfully on numerous installations on numerous machines. So here is how it works:


Thanks a lot it works perfect on ubuntu 9.10, with 95% connectivity

---

### Post by Burky on 2010-01-01
On 9.10 I've noticed that by default it works at 11 mb/s. If I used this tutorial will it go up to 54 mb/s?

---

### Post by stooshbunutu on 2010-01-03
> **Burky said:**
> On 9.10 I've noticed that by default it works at 11 mb/s. If I used this tutorial will it go up to 54 mb/s?

to be perfectly honest i dont know... i havent tried it, and have no need to as i dont use it as my wireless connector.

note though the tutorial was written for older versions of ubuntu

---

### Post by prabhat123 on 2010-02-16
Thank you for your instructions. I'm running into some problems though. I'm using wicd, rather than network-manager, and I don't see any wireless networks.  

Would the procedure be different?

---

### Post by prabhat123 on 2010-02-16
I was able to get wicd to work as well. Here's what I needed to do:

In Preferences, specify the Wireless Interface: wlan0.

Now, if I could only get an Ad-Hoc network working too.

---

### Post by fizyxnrd on 2010-10-28
I had this plug and play bliss in 9.10, but when I upgraded to 10.04, no joy.  I can't even get it working with ndiswrapper.

---

### Post by fizyxnrd on 2010-10-28
What worked for me was installing the linux-firmware-nonfree package, as explained in
[this thread]("http://ubuntuforums.org/showthread.php?t=1594592&highlight=netgear+wg111").

---

### Post by jure4422 on 2010-11-05
Hi!

Many thanks to stooshbunutu. 
I have just installed my new WG111v3 and it is working like a dream. Your description was prefect. Once again many thanks, great work! 

Bye,
Jure

---

### Post by stooshbunutu on 2010-11-05
> **jure4422 said:**
> Hi!

Many thanks to stooshbunutu. 
I have just installed my new WG111v3 and it is working like a dream. Your description was prefect. Once again many thanks, great work! 

Bye,
Jure

You're welcome as ever :)

---

### Post by StuartZ on 2010-11-22
When upgrading to Ubuntu 10.10 my WG111 quit connecting.  It still shows the connection information but keeps unsuccessfully trying to logon to the router.  Runs at about 75% signal.
I've deleted the connection and started a new one to no avail.  Even tried the 4 steps above...no luck.  Just keeps trying to logon.  The WG111 works on my Windoz laptop from the same area.
Any ideas.

---

### Post by stooshbunutu on 2010-11-24
Hey, unfortunately I don't have this adapter at the moment. It's currently on loan to a friend along with my old Laptop... they installed Windo$e on it :/ Will try and give it a look into though.

---

### Post by prayersfor.rain on 2010-11-27
Hello,
I'm running 9.10 (karmic) and I just got a new wg111v3 today (I returned the one I bought a few days ago because I thought I was having a problem with that).

When I plug in to Ubuntu, the light comes on and it starts telling me that I'm now offline.  When I click on network manager icon it either says that the wireless network isn't ready OR it doesn't show up at all.  It usually doesn't show up.  Once in a great great great while it'll show a couple of networks that are around me but that's maybe every 2 days.

I know it's supposed to be plug & play by now.
I tried following the directions on the first page but couldn't get past the first step. Probably because I'm not connected to the internet and it looks like you need it just do do that.

Now the first day I bought my first wg111v3 it wouldn't connect for like 3 hours and then randomly connected and was going strong until I restarted.  Now I get nothing.  According to the computer, that time when it auto connected was 5 days ago.


Help! Please :) if you have any ideas.  I'm using my roommate's laptop to  post this and I feel bad about just taking over her laptop for what might be a while.

---

### Post by geraldine_olivier on 2011-03-07
I have a NetGear WG111v3 WIFI dongle and this worke perfectly well for me. Thanks a lot!

---

### Post by breimer273 on 2011-03-15
> **Burky said:**
> On 9.10 I've noticed that by default it works at 11 mb/s. If I used this tutorial will it go up to 54 mb/s?

I am having this issue on 10.10. Anyone know how to restore to 54 Mb/s?:confused:

---

### Post by maadjones99 on 2011-04-18
Was quite happily using 10.04 and WG111V3 in harmony until an update got installed and now it seems the device is no longer supported. the network status shows as "Device not managed". I thought this USB adapter was meant to continue to be PnP.

---


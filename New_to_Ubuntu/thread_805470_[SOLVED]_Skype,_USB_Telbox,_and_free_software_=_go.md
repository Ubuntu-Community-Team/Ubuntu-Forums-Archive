---
title: "[SOLVED] Skype, USB Telbox, and free software = good!"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by anewguy on 2008-05-24
I don't know if it was the update to 8.04 or if it was changes in the supporting software (usbb2k-api & kb2kskype), but I am happy to report that my "generic" USB Telbox, the software, and Skype are working great in 8.04 - no more delays, no more garbled messages.

For those who don't know USB Telbox is kind of a generic name given to a series of small devices (mine says USB Adaptor, USB B2K on the back) that are available on places like Ebay really cheap and give you the ability to connect your regular phone to your PC for calls such as Skype.  I'm not trying to make any product plugs here, as I'm sure there are opther such devices and plenty of software around.  With mine, I have my regular phone line and my regular cordless telephone plugged into the device and a USB cable that runs to my computer.  I use my phone as normal but use it via the USB Telbox to make cheap or no cost long distance calls from my PC. 

In prior versions of Ubuntu, keeping in mind it was also older versions of usbb2k-api and kb2kskype, this didn't work well as the call was garbled (I could use commands to talk directly to usbb2k-api and skip kb2kskype, but it was a mess to do).  Everything is working great now.  I only have a PIII-500 wth 512mb, so it's not like you need a power house PC to do this.

Wanted to pass this along in case others had trouble in the past or are looking for a way to use their regular phone with Skype.

---

### Post by sam_delta on 2008-05-24
nice, glad ubuntu is getting better each release, it really shows the hard work behind ubuntu.

keep it up ubuntu devs

sam

---

### Post by altariel on 2008-05-25
Great to hear that everything works fine now! :)

---

### Post by komputes on 2008-05-25
[CENTER][IMG]http://kb2kskype.sourceforge.net/images/easyblue.gif[/IMG]
[/CENTER]

I tested this with Ubuntu 7.10 and 8.04 as well and it works perfectly. With usbb2k-api-mod2.8, kb2kskype-0.3.7 and skype-2.0.0.68-1, I was able to use my Yealink B2K perfectly. Please note that SkypeOut is not free, you must buy credit or a plan to call out. Of course there are some exceptions to these such as toll free numbers and certain areas that get free trial periods.

You can get these packages here:

[http://downloads.sourceforge.net/kb2kskype/usbb2k-api-mod_2.8-1_i386.kubuntu710.deb](http://downloads.sourceforge.net/kb2kskype/usbb2k-api-mod_2.8-1_i386.kubuntu710.deb)
[http://downloads.sourceforge.net/kb2kskype/kb2kskype_0.3.7-1_i386.kubuntu710.deb](http://downloads.sourceforge.net/kb2kskype/kb2kskype_0.3.7-1_i386.kubuntu710.deb)
[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

Once you install these, you must

1) start usbb2k-api (The way it is installed on Ubuntu, it should be running already as a system service)
```
$ sudo usbb2k-api
```

2) Startup Skype

3) Startup kb2kskype
```
$ kb2kskype
```4) Then to call in the USA or Canada dial the following in your phone

```

&#9556;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9559;
&#9553;OUT&#9553;PREFIX&#9553;AREA CODE&#9553;PHONE NUMBER&#9553;SEND&#9553;
&#9553;011&#9553;  1   &#9553;   212   &#9553; 555 -1212  &#9553;  # &#9553;
&#9562;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9565;

```

---

### Post by altariel on 2008-05-26
Actually, after installing the usbb2k-api-**package** that daemon should be started at boot time so the only thing to start as a normal user is 

* first skype
and then (after some delay, how long depends on the speed of your computer)
* kb2kskype

in some cases it does help to exclude these two programs from the session restore function in your desktop environment (gnome or kde)

there is an example of an autostart script for (k)ubuntu in 
/usr/share/doc/kb2kskype-0.3.7/example-scripts/skypeautolaunch.sh

---

### Post by anewguy on 2008-05-26
Indeed, usbb2k-api-mod is not valid - the command is simply usbb2k_api, at least for me with the mod installed.

The * key to switch from PSTN to USB/Skype works fine. However, for me at least, the "#" key does not dial the number.  So, for example, I can't be in PSTN mode, press * on the phone, dial a normal number and press # on the phone to force it to dial - it does nothing.

Also, I never meant to imply calls to PSTN (regular land line) phones would be free - that is based on the service you select.  I use Skype, and I also pay for SkypeOut so I can call any number in the US and Canada anytime, any day.  I personally pay under $6 for each 3 months of this, though normally it is just a penny or 2 under $30 for the entire year.  I did not want to plug any services, hence my generic opening post, but since others have then I will say you get a great bargain using Skype and SkypeOut.  My relatives are all over the country, so it works great for me.  I even paid (I think it was about $30 for 3 months at the time) for a SkypeIn number that was local to my parents in Arizona so they could call me by calling a local number - no long distance charges to them.

I know there are other services out there and I'm sure they are good as well - I just personally use Skype.

---

### Post by altariel on 2008-05-27
> **anewguy said:**
>  However, for me at least, the "#" key does not dial the number.  So, for example, I can't be in PSTN mode, press * on the phone, dial a normal number and press # on the phone to force it to dial - it does nothing.


Have you double-checked so that you too aren't dialing a too short number?
See the post above - try adding 011 before your number and please post the results :) 

See this thread for the reason why and such
[http://ubuntuforums.org/showthread.php?t=226632](http://ubuntuforums.org/showthread.php?t=226632)

---

### Post by komputes on 2008-05-27
Thanks guys, I fixed my post.

anewguy, the # key is only for USB mode, to SEND in skype. PSTN does not require this to dial a number.

---

### Post by kumarnarain on 2008-08-23
Hai
Thanks for the package...It worked for me well.....just needed to install a few dependencies on the usb side though.......Good UI and it works well. too. I have also seen this work on Win$ and I actually feel the sound was better in this. May be because of my good creative sound card..anyway keep up the good work.
Will this also work with any of the following:
[http://www.amperordirect.com/pc/c-internet-adapters/internet-phone-converter-au600.html](http://www.amperordirect.com/pc/c-internet-adapters/internet-phone-converter-au600.html)
[http://www.amperordirect.com/pc/c-internet-adapters/internet-phone-converter-callcenter.html](http://www.amperordirect.com/pc/c-internet-adapters/internet-phone-converter-callcenter.html)

Regards

Kumar

---

### Post by kumarnarain on 2008-08-27
Hai
Thanks for the package...It worked for me well.....just needed to install a few dependencies on the usb side though.......Good UI and it works well. too. I have also seen this work on Win$ and I actually feel the sound was better in this. May be because of my good creative sound card..anyway keep up the good work.
Will this also work with any of the following:
[http://www.amperordirect.com/pc/c-in...ter-au600.html](http://www.amperordirect.com/pc/c-in...ter-au600.html)
[http://www.amperordirect.com/pc/c-in...allcenter.html](http://www.amperordirect.com/pc/c-in...allcenter.html)

---

### Post by anewguy on 2008-08-27
> **komputes said:**
> Thanks guys, I fixed my post.

anewguy, the # key is only for USB mode, to SEND in skype. PSTN does not require this to dial a number.

Yes, I already knew that. 

Also, I don't need the 011 in front of my numbers.

As a side note - I switched from Skype to Vonage, and what a headache.  I'll be going back to Skype soon.  Turns out Vonage has no phone numbers available in my area, so I was assigned a long-distance number.  Imagine replacing your phone service with another and now your neighbor has to pay long distance charges just to call you!!

:)

---

### Post by 1numchucks on 2009-03-09
Thanks for all the info you guys provided. I have been able to get up and running. My only ? is how can we set up the speed dials? Like if I want to call Dad and set him up as speed dial 1#

---

### Post by kumarnarain on 2009-03-09
Well

All I did was to go to a browsing center ...log on to skype using M$ Os and set speed dial codes.....

Last heard...developer is working on it

---

### Post by 1numchucks on 2009-03-10
Thanks I also found that the B2k Controller automaticaly 
sets up speed dials for you. The 1st person you added as a
contact will be a low # the last will be the highest #.
These then can be changed by finding the phone # and giving
it a new speed dial.

---

### Post by altariel on 2009-04-02
you could alsy try the ppa lauchpad archive I set up (for hardy right now, will try to get at least intrepid as well) 

[https://launchpad.net/~alatariel/+archive/ppa](https://launchpad.net/~alatariel/+archive/ppa)

I think it should suffice to 
a) add the ppa to your apt sources list 
b) import the key (as per instructions on the page above)
and 
c) sudo apt-get install kb2kskype 
(this -should- pull in the usbb2k-api-mod as well)

:)

//Alatariel

---

### Post by 1numchucks on 2009-04-13
I did the repository and for some reason 
after I start Skype and then go to the 
terminal window and type
kb2kskype then enter I get this message

The program will now exit

check the usb driver is running and that you have write
permission on it. 

I do not know what to do. My device is no longer working except 
under Windows.

---

### Post by kumarnarain on 2009-04-13
Did you type kb2kskype or sudo kb2kskype??

---

### Post by 1numchucks on 2009-04-13
I think your on to something but I am to newbiefied to know course of action to take. Here are the results

bruce@ub8:~$ sudo kb2kskype
[sudo] password for bruce: 
kbuildsycoca running...
Error: "/var/tmp/kdecache-bruce" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-bruce" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-bruce" is owned by uid 1000 instead of uid 0.
bruce@ub8:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c00054

---

### Post by kumarnarain on 2009-04-13
try going to the /tmp folder and change the ownership to the subfolder /kdecache to yourself by typing using chown command. you can find an example usage here

[http://ubuntuforums.org/showthread.php?t=105213](http://ubuntuforums.org/showthread.php?t=105213)

---

### Post by blfer on 2009-05-02
Well, I've read about all this stuff and it looks like I am having the same problems as listed above.
I'm running Jaunty 9.04, USB Telbox USB Adaptor, KB2KSkype. I have Skype set up for in/out calling.

Here are the errors:

b***@Skype:~$ sudo kb2kskype
[sudo] password: ********************
Error: "/tmp/kde-burtY1ACNc" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-burtckPyep" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-burtckPyep" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-burtY1ACNc" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-burt" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-burtY1ACNc" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-burt" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-burt" is owned by uid 1000 instead of uid 0.
amixer: Unable to find simple control 'Mic',1

amixer: Unable to find simple control 'PCM',1

amixer: Unable to find simple control 'Mic',1

amixer: Unable to find simple control 'PCM',1

I read about the chown fix --- don't have a clue about it and am nervous about using command line anyway. Don't really know what to do or where to go from here. Any help would be appriciated. Thanks in advance.
blfer

---

### Post by blfer on 2009-05-02
As a follow-up:
I can make calls out using Skype on the computer but I can't hear anything on the receiver I have connected to the USB Telbox. I have changed the sound settings in ubuntu to no avail. I'm going to try to uninstall and re-install skype and KB2KSkype in a little bit. Otherwise I don't know what else to do except keep searching and trying.
Blfer

---

### Post by anewguy on 2009-05-03
Currently I am not using Skype (got suckered in to Vonage - what a mistake!).  However, back when I wrote this, I seem to remember just a single item that has to be changed in the Skype set up itself for the audio to work.  I'll try remember what it was (it wasn't the playback device, but something else) and post back.

Dave :)

---

### Post by 1numchucks on 2009-05-03
In response to Blfer.
I was unable to repair my skype so I did a fresh 
install just as you said you would. I went to page
1 of this thread and used the instructions and links
that komputes gave.  In addition to the sound problem
I read that downloading Gnome Alsa Mixer can help a 
great deal with sound problems. Very user friendly program.

In order for my skype sound to work 
I have to open up the skype window. Double Click skype symbol in tool bar
Mouse Click blue the blue S bottom left corner of Skype window
Click options
Click Sound Devices
On sound devices for sound in and sound out
you must select the Voip USb Phone device.
Hope this helps.

---

### Post by blfer on 2009-05-03
Yes! It did! I un-installed everything - and - re-installed everything. I used the Medibuntu Skype version of skype specifically for ubuntu.

Let me ask a question though, is terminal supposed to ALWAYS! run? When I go to close Terminal it says that if I exit the terminal window KB2K will stop running. What's up with that? Do I have to leave the terminal windo running ALL THE TIME? Seems rather odd to me. I'm going to try something to see if it works - I'll post the results here either way.

Well, I just tried it and --- Sucess! Again!! --- What I did is copied and pasted the B2K program start icon into a folder where it is easily accessible for me --- double click and away it went without starting the program in the terminal window. I'm going to test this for a few days. This little project is for a Skype server which will always be on. Thanks for the reply.

I will play with the settings over the next few days for sound to see what happens. I'm going to be writing a series of articles on my blog about this and document everything. Thanks for your help.
blfer

---

### Post by blfer on 2009-05-04
Does anyone know what the TelBox error message

Unknown Key: 01 64 (from telbox) 

I googled it and found nothing. Thanks for your help.
Blfer

---

### Post by brian_p on 2009-05-04
> **blfer said:**
> 

Does anyone know what the TelBox error message

Unknown Key: 01 64 (from telbox) 

What is your default B2K mode and what did you do to get this? Is it repeatable?

---

### Post by blfer on 2009-05-04
Well, the skype phone is working - sorta. When I place a call the following happens ---
I hear TWO (2) sets of rings, one from the number being called and one from the TelBox pulse generator.
Very annoying. Does anyone else have this problem? Has this problem been fixed? If so, please let me know. Thanks in advance.
BLFER

---

### Post by brian_p on 2009-05-04
> **blfer said:**
> 

Well, the skype phone is working - sorta.

Does skype work (e.g. echo123 or any other number) without kb2kskye? There isn't much point in looking for a fault in kb2kskype if it is not.

---

### Post by blfer on 2009-05-06
Well, I'm not sure what you mean. All I can say is that I am using the software interface for the Telbox USB K2B device. You can certainly use other devices with Skype, but I am concentrating on devices which are acessible to everyone and are cheap enough for everyone to acquire. In addition, I am concentrating on the OSS available to run those device(s). And, last but not least, this device has to be able to plug into the existing phone wiring in any house in North America. This puts me squarely into the B2K camp. It is the only one that I have tested so far which clearly meets all of the necessary criteria. After getting the software to work and setting up the server and service from Skype it has run with very little problems, except the one(s) listed. Minor stuff, but --- nonetheless --- stuff that still needs to be addressed.
Blfer

---

### Post by blfer on 2009-05-06
I re-read your post and --- yes, Skype works fine without the K2B device. The onle problem I have been told from the people being called on Skype is that they hear a very slight echo on their side of the conversation (all of them have reported this). Is their a fix for this? This (I think) is clearly a Skype problem, not K2B. The Other (the double ringing --- I think) is a K2B problem.
Blfer

---

### Post by 1numchucks on 2009-05-08
If I set up my sound out to Voip usb phone I can not 
listen to my voice mails on my computer speaker. 

There is a walk around to play back the voice mail. 
And that is to manully go into settings and 
change sound out to  my comp speakers.
Then when I want to use my Usb phone
I have to set Voice out back to Viop usb phone.

Another way is to pick up the Usb phone and hit the 
call button which will give a dial tone. 
Then you can hear your voice mail through the 
phone but the dial tone is annoying. 

I have searched the forums but have not found a 
solution to the voice mail problem. Trying to get
the wife & kids on board with Ubuntu but these small
problems drive them nuts.  Any tips or tricks would
be appreciated.

---

### Post by caiobos on 2009-06-04
Hello all!
Anyone know if USB B2k works with another softphone(talk SIP) unless skype?
More accurately I mean Asterisk.

Thanks!

---

### Post by komputes on 2009-06-04
> **caiobos said:**
> Hello all!
Anyone know if USB B2k works with another softphone(talk SIP) unless skype?
More accurately I mean Asterisk.

Thanks!

;)

I would also be interested in getting a USB B2K box working with Asterisk, through an IAX compatible softphone like slfphone instead of using skype. Is anyone currently doing this? Any tips/plans on hacking at kb2k to make it work with other software?

---

### Post by brian_p on 2009-06-04
> **komputes said:**
> ;)

I would also be interested in getting a USB B2K box working with Asterisk, . . . . . 

Why? Do the available ATAs lack something which only kb2kskype could do?

---

### Post by komputes on 2009-06-05
> **brian_p said:**
> Why? Do the available ATAs lack something which only kb2kskype could do?

No, current ATAs do not lack anything, I simply want to use the hardware that I already own instead of buying an ATA that is IAX compliant. I fear that without this software it will only act as a capture/playback device. Basically kb2kskype is able to generate a dial tone, make the phone ring (when the softphone rings), as well as convert DTMF tones from the phone into numbers and then hands it to the sophtphone client software. I was wondering if it was possible to modify kb2kskype so that it could send that data to an IAX compatible softphone client like sflphone.

[http://www.sflphone.org/download.php](http://www.sflphone.org/download.php)

---

### Post by brian_p on 2009-06-06
> **komputes said:**
> 

I was wondering if it was possible to modify kb2kskype so that it could send that data to an IAX compatible softphone client like sflphone.

[http://www.sflphone.org/download.php](http://www.sflphone.org/download.php)

I took a quick look at the description of sflphone and it has a commandline interface. The file in the kb2kskype source which controls how twinkle phones out is in skypeapidlg.cpp:

```
system((QString("twinkle --immediate --call ") + str).ascii());
```

Now it might just be a matter of altering that one line. Or it might not be!

---

### Post by tetralectic on 2009-08-21
> 1numchucks              **Re: [SOLVED] Skype, USB Telbox, and free software = good!**

 If I set up my sound out to Voip usb phone I can not 
listen to my voice mails on my computer speaker. 

There is a walk around to play back the voice mail. 
And that is to manully go into settings and 
change sound out to  my comp speakers.
Then when I want to use my Usb phone
I have to set Voice out back to Viop usb phone.

Another way is to pick up the Usb phone and hit the 
call button which will give a dial tone. 
Then you can hear your voice mail through the 
phone but the dial tone is annoying. I'm using a Uniden DECT 1560 Cordless Phone with the USB Telbox. I hit the Talk button which brings up the dial tone and then press any number and the dial tone goes away. The voice mail no longer competes with the dial tone  :)

---

### Post by Surabaya on 2009-09-20
Hi Komputes, 

Finally did you get success to make USB B2K working with sfl phone? Me also i would like to use something elese than skype with this box.

Thanks for your help in advance.

Surabaya


> **komputes said:**
> No, current ATAs do not lack anything, I simply want to use the hardware that I already own instead of buying an ATA that is IAX compliant. I fear that without this software it will only act as a capture/playback device. Basically kb2kskype is able to generate a dial tone, make the phone ring (when the softphone rings), as well as convert DTMF tones from the phone into numbers and then hands it to the sophtphone client software. I was wondering if it was possible to modify kb2kskype so that it could send that data to an IAX compatible softphone client like sflphone.

[http://www.sflphone.org/download.php](http://www.sflphone.org/download.php)

---

### Post by komputes on 2009-09-23
No I have not tried yet, even if  brian_p did recommend something, but I am not a developer yet, so I have no idea how to implement it. 

I have invited members of Savoir-faire Linux (which develop sflphone) to the Ubuntu Global Jam which my LoCo team is running on the first weekend of October. I will bring my usb b2k telbox and hopefully I'll be able to find someone to help me with this idea.

---

### Post by Surabaya on 2009-09-24
Ok thaks for your answer; let's wait and see.

---

### Post by Surabaya on 2009-11-29
> **Surabaya said:**
> Ok thaks for your answer; let's wait and see.

Update:

I tried to use my Yealink Telbox under Ubuntu 9.10 and 9.04; for both the result is the same: the sound is coming out only from the speakers, not from the DECT phone plugged on the box. From the phone I can dial a number but I cannot speak and hear anything. But I am not very suprised because on the sound preference of skype I cannot choose the VOIP USB in the menu for the speakers and microphone. I can only choose from my internal audio card (Pulse Audio Server (local)).

For information this is my cat /proc/asound/cards:

0 [Intel ]: HDA-Intel - HDA Intel HDA Intel at 0xe1280000 irq 16 1 [default ]: USB-Audio - VOIP USB Phone
Yealink Network Technology Ltd. VOIP USB Phone

Any help please, I really would like to make this box working. Thanks in advance!

---

### Post by Ripfox on 2010-09-18
I just figured this out...install pulse audio device chooser from synaptic, open it, choose the "playback" tab. Then start a test call or any call in skype, and then you can set the "Skype output on" to the Voip box. Now, the cordless handset acts as microphone and speakers too.

I also thought it was worth mentioning that I just put both kype and kb2kskype in the Startup applications under System/Preferences/Startup Applications and they load in fine order in the task bar. You can set Skype to auto log in and be minimized, but B2K will start maximized. No big deal, one click and I'm happily running in the task bar. Skype has a 2.99 usa unlimited plan and my skype in number is 18.00 for three months. 

What a deal, and I can use mu regular 5 handset phone system with it in my house for a grand total of 6 bucks a month!

Thanks guys!!

---


---
title: "linux drivers for Linksys CIT200?"
date: 2006-10-24
forum: Programming Talk
---

### Post by Peepsalot on 2006-10-24
Does anyone think it would be feasible/worthwhile to start a project to create Linux drivers for this device?
The Linksys CIT200 is a wireless phone for use with skype.  The base station interfaces with your computer via USB.  Linksys does not offer Linux drivers, so I thought of trying to make my own.

Is anyone interested in working on this project?
Has anyone here developed USB device drivers for linux before?

I have a college degree in computer science, and have spent the last 4 years working as a web application developer, but have no experience in writing Linux device drivers.  I think it would be great to work on something like this, but I'm not even sure if this sort of project is just too complex to be feasible.

Here are some basic links I've looked over so far.
[http://www.linuxjournal.com/article/7353](http://www.linuxjournal.com/article/7353)
[http://www.linuxjournal.com/article/4786](http://www.linuxjournal.com/article/4786)
[http://sourceforge.net/projects/usbsnoop/](http://sourceforge.net/projects/usbsnoop/)
[http://www.usb.org/developers/docs.html](http://www.usb.org/developers/docs.html)

I have run USB Snoopy on the device already and found that it uses 3 different USB drivers!
USB Composite Device
USB Audio Device
USB Human Interface Device

I made a log file, but not sure how to decipher it yet.

---

### Post by froggontherocks on 2006-11-16
I would very much like to see the driver written but unfortunately I don't have any experience writing drivers either. But wanted to throw in my 2 cents that there should be one.

---

### Post by viczh on 2006-11-19
You don't need to write a driver - CIT200 is a composite, comprised of two devices - isochronous phone/mic and HID. They are well known devices and can be accessed without drivers - there are class drivers for them already. CIT200 Windows app does not install any drivers (AFAIK) - they use this combination.

---

### Post by Peepsalot on 2006-11-20
Well, that is good news.  So do you know how I can make use of this phone with skype then?

In my skype configurations for Audio devices, I can see the CIT 200 and I have selected for audio in, audio out, and ringing.

But the handset display always says "DISCONNECTED" when plugged into my Linux box.  So this is were I'm assuming I have a driver deficiency.  In windows it would either say "SKYPE OFFLINE" or "CONNECTED" depending on whether the Skype application was running at the time.  I have never seen it say "DISCONNECTED" in Windows.  If I completely disconnect the USB cable for the base, the handset will say "SEARCH BASE".

So I can't dial from the handset because it is not speaking to the program.  In windows, the phone would load my list of contacts from the application, but in Linux I don't see anything.
If I dial from the skype program, I get no sound.

Here is what i get in dmesg when I connect the USB cable.
```
[17188923.272000] ohci_hcd 0000:00:02.1: wakeup
[17188923.656000] usb 2-3: new full speed USB device using ohci_hcd and address 11
[17188923.904000] usb 2-3: configuration #1 chosen from 1 choice
[17188925.412000] hiddev96: USB HID v1.01 Device [LINKSYS Linksys CIT200] on usb-0000:00:02.1-3
```
I don't see it saying anything about the audio device, but then how does skype know it exists?

---

### Post by Peepsalot on 2006-12-02
bump

---

### Post by viczh on 2006-12-14
It generally works like this:

It is composite device consisting of two devices: HID and audio. HID is a device for which you don't have to have a driver but this does not help - you still need to understand protocol, that is sets of messages this device exchanges with the application program. There are messages for setting time (have you noticed that it shows time, set on your computer), to pass a number you dialing, to fill out address book, and to turn on or off mic/phone combination. By default they are turned off physically, that is why you can not hear your computer sounds, but if you call someone and play some sound, you must hear this through your handset.

So beyond being recognized and connected by your USB HID and audio subsystems the device should be guided through all stages of phone call - dialing, waiting, connection or busy signal, disconnection. The program handling it, polls device every 10ms and if you stop polling, device mentions it pretty soon.

This same controlling program rules Skype through its official API - it tells it what number to dial, recognizes waiting signal callback and as soon as the other party answers, it turns on the device's mike and phone.

So it is still some work ahead on deciphering the meaning of device messages.

---

### Post by shoki on 2007-05-29
Has this been solved? This is the only issue (no CIT200 wireless phone for skype) keeping my wife away from ubuntu. If I can get this to work I can go 100% ubuntu desktop at home!

---

### Post by bagguley on 2007-06-03
Also the only thing keeping me from being a Windows free household. SInce going back to windows life is so slow! Anyone out there help??

---

### Post by theicepelican on 2007-06-03
skype does work on my computer and it does recognize the CIT200... however, after i set up the default audio and ringer to the CIT 200 nothing gets forwarded to it, and the handset says 'Disconnected' am i missing something?

---

### Post by Peepsalot on 2007-06-04
> **theicepelican said:**
> skype does work on my computer and it does recognize the CIT200... however, after i set up the default audio and ringer to the CIT 200 nothing gets forwarded to it, and the handset says 'Disconnected' am i missing something?

If I had to guess, I'd say you're missing drivers, like everyone else.

---

### Post by dwebb726 on 2007-06-17
I'm trying to crack this nut myself - but as far as I can tell this is *not* a driver issue.

The phone syncronizes with Skype via a program (cit200.exe I believe in windows) that uses the Skype API.

So somehow this program needs to run in Linux, I'm not sure if wine can handle it.

HTH,

Dan

---

### Post by Borrus on 2007-06-20
Just out of interest, I tried running the exe under wine. I was expecting to hit some kind of fault with the USB part of the puzzle, but before I got there, up came a dialog telling me I wasn't running Skype. I was of course - the linux version - but not the windows one.

Currently i'm trying to solve this bit - the Skype adaption bit. My plan is to write a Win32 program which pretends to be Skype - in terms of the API - and link the program with winelib so that I can make native linux calls and thus shuttle Skype API commands between the CIT200's EXE and the native linux version of Skype. The windows bit of this already works - its  just the linux side I haven't tackled yet.

The hard bit is the USB of course - which I'm hoping I can get to once the initial Skype part of the equation is resolved. What I'm not sure of (can anyone help answer this?) is whether I can expect the USB support in wine to provide for the needs of the CIT200 device - given that it supposedly uses only "out of the box" windows drivers? I'm not optimistic but it'd be nice.

In case you wonder, I did consider getting skype to work under wine, but from what i saw in various forums, it didn't sound as if people had had much luck getting it to run well, and I got the impression they'd had to mess about a lot to get it to play ball.

Anyone have any comments whether this is a sensible way to go? I know it sounds a bit bizarre :)

---

### Post by incgnito on 2007-06-21
I know this isn't a real answer to the problem but for those of you who said this was the only thing stopping you from going to linux at home has anyone considered installing a VM under something line Virtualbox or Xen and running your Skype/CIT200 from that?  Like I said I know it's just a workaround but for now it is a possibility.

Just a thought...

---

### Post by thalueng on 2007-06-25
yes, I did, it does not work in my VM WS 5.5 box under Ubuntu Edgy

---

### Post by Borrus on 2007-06-28
I tried it today and It does work (latest vmware, win xp, unbuntu feisty), however i wouldn't recommend the experience (problematic, mainly todo with getting the USB device into a happy state) - but (for me) it *does* work.

I eventually scrapped the 'running it under wine' idea I posted above. I couldn't get the cit200 process to accept that skype was running, even though the same test under native windows worked like a treat. I suspect wine isn't somehow communicating the inter-process windows messages across different the processes running in the wine environment.

Anyway, I'm currently trying to add support for the device natively, but currently stuck on understanding the protocol running on top of HID. Anyone got anywhere with this?

---

### Post by bagguley on 2007-08-12
Anyone got any further with this?? If running under VMware works is there any chance of a Howto guide as I wouldnt even know where to start (still getting to grips with wine).

Much like an earlier post, this is the only thing stopping me destroying windows.

Cheers

---

### Post by Borrus on 2007-08-19
How far have you got with VMWare - have you actually managed to install it, or having problems getting the CIT200 to work? If I remember correctly, Installation was relatively straightfoward - it was listed in the standard Ubuntu package list by Synpatic Package Manager. After installing VMWare itself, you need to install an OS on the new (virtual) machine. To do this, I followed the instructions here:

[http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html](http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html)

Once you have your new OS working ok in VMWare, you should notice a drop-down menu at the top of the VMWare window that lists all known USB hardware devices. There's a tick next to each one, allowing you to toggle the plugged-in / removed state for each. This allows you to simulate insertion/removal of the hardware device. You shouldn't physically remove it though, while VMWare is running. For devices to appear in this list, you need to physically insert them first, and then run VMWare. If you insert the CIT200 into your USB port first, then run VMWare up, you should be able to see it in the list, and check that it's 'inserted' (in the virtual sense). All you need to do then is run the Linksys CIT200 software, and Skype, just as you would on a normal Windows PC. For me, it all worked fine. I hope this is useful :)

Regarding native linux support, I have now set up a project on Sourceforge - it's here:

[http://sourceforge.net/projects/cit200](http://sourceforge.net/projects/cit200)

The resources currently available on the site are:
1. CIT200 Sniffer tool, based on SnoopyPro. This is a console-based tool that runs under Windows which dumps out the conversation between CIT200.EXE and Skype, and between CIT200.EXE and the Device. To run it, (i) close Skype and CIT200.EXE, (ii) make sure you've installed the USB 'capture' device by running SnoopyPro first and choosing 'unpack drivers', (iii) run the CIT200 sniffer, and then (iv) run CIT200.EXE.

2. CIT200 Protocol Spec document. Includes general info about command structure and format, and semi-formal BNF outlining the form of all commands that I've managed to unravel so far. This is virtually everything except the commands related to actually making a voice call (ok, i know - thats the most important part, being a phone ;), but its also imo the most complex area) 

3. Beginnings of a linux implementation. This is a native linux C program using the linux hiddev driver. All it does so far is issue a single command to the device and get a sensible (intelligible) response.

I will update here once Ive got further. :)

---

### Post by amgat on 2007-09-11
Is this project already dead? Can't see the project at sourceforge anymore. I can't understand why linksys don't want to release their source for this tiny software. unbelievable!

---

### Post by wkdown on 2007-09-15
I personally want to work on getting the CIT200 to work in Linux.  I never intend to use WINE or VMware or any kind of "Windows on Linux".  That defeats the whole purpose of having Linux.  Ubuntu is not going to catch on mainstream until many things are supported in Linux.  

I too have no experience in Linux drivers but I know my way around the command line pretty well, and I'm a programmer with knowledge in, among others, Perl.  If I remember right, drivers can be written in Perl and not necessarily always in C.

I am going to hunt for some information on writing Linux drivers.  If anyone has some helpful links or wants to contribute, use this thread.

---

### Post by Borrus on 2007-09-17
i pulled my project from sourceforge because i am worried about the legal ramifications (sorry) :(.

I may well consider making the project public at a later date, once i am more sure that its safe to do so, but this will probably not be on a US-hosted site (which i believe sourceforge is), due to DMCA etc. While the project is currently not public, I can confirm at least that I am still very actively pursuing this development effort. Watch this space. :) 

a couple of things i can say safely i think, in response to the points made above

1) if you do a quick google on the product name, you'll quickly see that linksys is not the developer of this hardware; rather, it is a 're-badge'. therefore they might be tight lipped because they are legally obliged to be so - because the intellectual property isn't entirely theirs. why would the orgiinal vendor not be happy for linux drivers to be written? complete speculation, but perhaps they only received a one-off payment rather than a royalty deal? I am purely speculating though, mind.

2) As covered already in this thread, you do not have to write any (kernel) device drivers. Only a user-mode ("normal") program. linux provides the required kernel support already in the form of hiddev.

One final issue is the EULA, which I am not entirely sure about. I am pretty sure that, at least here in the UK, it is not enforceable, but then again I am not a lawyer..

hope this helps

---

### Post by Borrus on 2007-10-07
quick update:
linux development here continues in earnest - implementation of core subsystem for dispatching commands to Device and for retrieving replies is almost complete, currently supporting a "keep-alive" function (only). Next stage is to beef this out with a larger set of the command types which are currently understood - status info, phonebook, voicemail, etc. Work at the other end - interfacing with Skype - not yet begun. Plan to make a public release eventually once the project is further developed.

---

### Post by amgat on 2007-10-08
Great work Borrus. My CIT200 is collecting dust right now and I can't wait to start using it on y linux computer. Please keep us updated on the progress. I can contribute with language translations and graphics if needed.

---

### Post by Borrus on 2007-10-08
thats a kind offer - thank  you :) it might be a while before I have anything to translate though, mind :)

---

### Post by ozite on 2007-10-08
I use a Windows PC for Skype/CIT200 and another PC for Ubuntu/MythTV.  It would be great to use only Ubuntu, but the lack of the option to use a CIT200 with Skype is the only thing holding me back. I am very interested in future developments in this project.

---

### Post by shift1186 on 2007-10-25
here is an update!

We just received confirmation that Linksys is looking into Linux support for the CIT200 Linksys/Skype IP telephone.

Karen, a senior manager over at Linksys, shot a note that although they don't have a time frame Linksys is looking into supporting Linux and know it's beneficial to provide support to the Linux user base. I'd take this as meaning if there's any user demand they'll be providing compatibility for Linux.

From:
[http://pcburn.com/article.php?sid=881](http://pcburn.com/article.php?sid=881)

---

### Post by amgat on 2007-10-26
Awesome! Can't wait for a public driver release!

---

### Post by Borrus on 2007-10-30
> **shift1186 said:**
> here is an update!

We just received confirmation that Linksys is looking into Linux support for the CIT200 Linksys/Skype IP telephone.

Karen, a senior manager over at Linksys, shot a note that although they don't have a time frame Linksys is looking into supporting Linux and know it's beneficial to provide support to the Linux user base. I'd take this as meaning if there's any user demand they'll be providing compatibility for Linux.

From:
[http://pcburn.com/article.php?sid=881](http://pcburn.com/article.php?sid=881)

that's very old news indeed - I read that story before I even started on my implementation back in June - and even then, people were moaning it was over a year old :(

---

### Post by Ultra Magnus on 2007-11-06
Just wondering How are these drivers going?

I've gotten complecent and bought one of these without checking whether it would work with Linux because everything else I have works fine.

I'm seriously angry though - seriously, how would they lose out by open soursing the driver

---

### Post by Borrus on 2007-11-12
coming along, slowly :)

Basic driver structure: two layers. Bottom layer provides a C/C++ API at its upper edge with functions such as "device wants to make a call", "device wants to change user status to away", etc. This bottom layer talks to the device through a usb interface (eg libusb). The upper layer talks at its lower edge to the fore-mentioned C/C++ API, and its upper edge communicates with Skype itself via the "public API".

No work at all yet on upper layer. On lower layer, main framework is finished. usb-level protocols are complete. Some of the "specific" services are complete: most of the phonebook ("contacts") are there, the user-status service is complete (you can tell the device that the user's now 'away', and the device itself can report that the user is now 'away' (or whatever status you desire). Call-control is the current activity - ie setting up a voice call. This is proving somewhat complex but it's all doable :)

So, in summary, good progress so far, but a long long way to go, too. Project started in June. Could well be another 4-5 months yet.

---

### Post by amgat on 2007-11-13
This is great news Borrus. Thanx for the update. Have you created a project page for the software? The people interasted in this project have most likely chosen to be notified as soon as someone posts something in this thread, but it would be great to have a project page anyway :)

---

### Post by Borrus on 2007-11-13
you're right - no, not yet - thats something i need to fix ;)

I'll post a link in this thread once I have something together. :)

---

### Post by Borrus on 2007-11-13
project now created here: 

[http://code.google.com/p/frisbi/](http://code.google.com/p/frisbi/)

no content added yet - but watch this space!

---

### Post by dvranizan on 2007-11-16
> **Borrus said:**
> project now created here: 

[http://code.google.com/p/frisbi/](http://code.google.com/p/frisbi/)

no content added yet - but watch this space!

Borrus,

I would really like to help you on this project!  I have experience in software and hardware engineering.  If I could be of any use to you or this project please say so!  I love the CIT200 and it is frustrating that it will not work on my linux machine.

Thanks!

---

### Post by Borrus on 2007-11-19
> **dvranizan said:**
> Borrus,

I would really like to help you on this project!  I have experience in software and hardware engineering.  If I could be of any use to you or this project please say so!  I love the CIT200 and it is frustrating that it will not work on my linux machine.

Thanks!

Thanks very much for the interest - we're ok for now though thanks, resource-wise. I've got a friend who's already expressed interest in helping with the upper layer of the project, so we should be fine :)

Quick update: I had a bit of a breakthrough last week: For the first time I was able to get the Device to think it was making a voice call. The little blue light lit up on the receiver unit, and by playing some audio to it's output audio channel (its loudspeaker), checked that it really was in "voice call" mode. The next bit's going to be tricky though - figuring out the sequences for incoming voice calls, putting the current party on hold or rejecting an incoming call, and so forth, but it's coming along nicely :)

Fairly soon what we're going to need quite badly is some help in checking the project installs and runs properly on the various linux distros, so stay tuned!

---

### Post by NiteShdw on 2007-11-19
> **Borrus said:**
> Fairly soon what we're going to need quite badly is some help in checking the project installs and runs properly on the various linux distros, so stay tuned!

I would be interested in testing it.  I have a CIT200 and have installed Skype 2.0 beta on Ubuntu 7.10 64-bit.

---

### Post by gamera06 on 2007-11-22
Hi Guys,

the idea is great !

I got a CIT200 & Ubuntu Gutsy Gibbon with Skype 2.0. I'm ready to test :-)

---

### Post by Borrus on 2007-11-25
(Removed)

---

### Post by RebateFX on 2007-11-28
> **Borrus said:**
> Thanks very much for the interest - we're ok for now though thanks, resource-wise. I've got a friend who's already expressed interest in helping with the upper layer of the project, so we should be fine :)

Quick update: I had a bit of a breakthrough last week: For the first time I was able to get the Device to think it was making a voice call. The little blue light lit up on the receiver unit, and by playing some audio to it's output audio channel (its loudspeaker), checked that it really was in "voice call" mode. The next bit's going to be tricky though - figuring out the sequences for incoming voice calls, putting the current party on hold or rejecting an incoming call, and so forth, but it's coming along nicely :)

Fairly soon what we're going to need quite badly is some help in checking the project installs and runs properly on the various linux distros, so stay tuned!

Great to hear of your progress. I'm ready to test too. The other thing I was thinking is where do I send the money for Pizza to show my appreciation? :D

---

### Post by bagguley on 2007-11-28
Also got a CIT200 and happy to test!

---

### Post by Borrus on 2007-11-30
sorry peeps but im afraid ive had to terminate this project now. the legal hurdles are too much of a pain. check out section 2b of this:

[http://www.skype.com/company/legal/terms/api.html](http://www.skype.com/company/legal/terms/api.html)

Skype's API is "open" in the sense that anyone can view what it is, but you can't actually use the damn thing unless you're "signed up". And, in the case of interfacing to a hardware device, that means becoming a hardware partner. lol, right.

I sent Skype an email asking for clarification, that I was merely aiming to provide support for a device under Linux that's already been approved by them, but I didn't get a response.

I'm bitterly disappointed about this because the project was coming on so well, and was a great deal of fun too. This Skype API issue is the final nail in the coffin for me.

ps no, you can't have my stuffz, sorry ;)

---

### Post by doubl00 on 2007-11-30
I have been following your progress and am disappointed, also.  I am a new user to Ubuntu having installed it on an older eMachine this week.    The previous use was as to run my LinkSys CIT200 phone under XP for Skype.  (I did not like having to set all the audio to the CIT200 and loose audio from all other programs).  

I am now playing with Linux on the eMachine to see if I can get rid of M$Windows.  I  wanted to continue to use CIT200 in a Linux OS.  

Has anyone looked at this link?  (Build a Skype Server for you Home Phone System)
[http://www.linuxjournal.com/article/8592]("http://www.linuxjournal.com/article/8592")


The hardware looks pretty simple (cheap).  Most home phone system (at least here in the US) have 2 pairs.  One pair could easily supply the sype phone through Linux.  

Any comments?  

a 60 year old engineer just learning Linux
/don

---

### Post by bagguley on 2007-12-01
An easier option would be to buy a skye/voip phone that plugs directly into a router, thus bypassing your pc m(and ubuntu unfortunately).

Ive been using ubuntu for 6 months or so now, and skypes unwillingness to allow access to their gui has been a consistent complaint from the open source community..

Unfortunately this is the only way i can see around it

---

### Post by RebateFX on 2007-12-22
> **Borrus said:**
> sorry peeps but im afraid ive had to terminate this project now. the legal hurdles are too much of a pain. check out section 2b of this:

[http://www.skype.com/company/legal/terms/api.html](http://www.skype.com/company/legal/terms/api.html)

Skype's API is "open" in the sense that anyone can view what it is, but you can't actually use the damn thing unless you're "signed up". And, in the case of interfacing to a hardware device, that means becoming a hardware partner. lol, right.

I sent Skype an email asking for clarification, that I was merely aiming to provide support for a device under Linux that's already been approved by them, but I didn't get a response.

I'm bitterly disappointed about this because the project was coming on so well, and was a great deal of fun too. This Skype API issue is the final nail in the coffin for me.

ps no, you can't have my stuffz, sorry ;)

Is it a matter of money? How much? I would be willing to pay your way if it meant I had a working CIT200 with skype in Ubuntu. :)

---

### Post by Ben1234 on 2008-03-13
Hi,

How about just making the thing work as a simple wireless microphone/speaker. (Don't even really need the speaker.)

From what I've read on this forum, the microphone in the phone exists an audio device, However it needs enabling, with some command sent to the phone. 

Could it be set up so that, if you press the green button, the phone thinks its in a call, the mike is activated etc. by the driver, you then dial from skype. when you hangup in skype, you also press the red button on the phone, (to save the battery of the phone.)

So far as I can see, you don't need any part of the skype API to get the thing working in this simple way, and its a lot better than nothing, It also seems with the work so far this would be quite easy.

Any thoughts on that?

Ben

---

### Post by Faust942 on 2008-03-13
I really would like this working with Ubuntu. I currently have a Windows XP system, but CIT200 is the only thing stopping me from switching permanently.

Anything happening?

Couldn't someone put it up as a torrent? Then there wouldn't be such a worry about legality. ;)

---

### Post by slack---line on 2008-06-13
> **Borrus said:**
> sorry peeps but im afraid ive had to terminate this project now. the legal hurdles are too much of a pain. check out section 2b of this:

[http://www.skype.com/company/legal/terms/api.html](http://www.skype.com/company/legal/terms/api.html)

Skype's API is "open" in the sense that anyone can view what it is, but you can't actually use the damn thing unless you're "signed up". And, in the case of interfacing to a hardware device, that means becoming a hardware partner. lol, right.

I sent Skype an email asking for clarification, that I was merely aiming to provide support for a device under Linux that's already been approved by them, but I didn't get a response.

I'm bitterly disappointed about this because the project was coming on so well, and was a great deal of fun too. This Skype API issue is the final nail in the coffin for me.

ps no, you can't have my stuffz, sorry ;)

Thats a real shame, I'd been hoping to get this device working under Linux, even if as a standard handset without any integrated Skype support.:(

Anyone else had success getting the handset to work at all?

---

### Post by TravisHaynes on 2008-07-31
So far I've been using VirtualBox to use my CIT200 phone with Skype. The latest version supports USB devices. It works fine, but I have to load VirtualBox every time I want to use Skype, and that takes about 50% of my computer's resources!

I managed to get Skype 3.0 working via Wine, and I installed the program on the CD, however, it doesn't appear that Wine supports USB devices as of yet... Bummer!

However, I thought it might be useful to post how I got the CIT200 program and the Windows version of Skype 3.0 running on my system (Ubuntu Hardy Heron):

[LIST]
[*]I started with fresh installation of wine-1.1.2-91 compiled from source.
[*]Ran winecfg and made sure my audio settings were working. Which, by the way, I had to completely remove PulseAudio from my system in order for this to work.
[*]Downloaded winetricks and used it to install Gecko and DirectX 9.
[*]Installed the version of Skype on the CD that came with the CIT200 phone, which can be found here: [path to cdrom]/Wizard/SetupWizard/Applications/SkypeSetup.exe
[*]Setup a rule using winecfg for Skype to run in Windows 2003 mode.
[*]The installation wizard for the CIT200 program doesn't work for me, so instead I located the actual installer on the disc and ran that: [path to cdrom]/Wizard/SetupWizard/Applications/Install/Applications/setup_eng.exe
[/LIST]

It was here that I ran into the road-block of the CIT200 program not being able to see the USB device.

Does anybody know of a way to get Wine to recognize a USB device? Because that's all we need to get this to work!

---

### Post by J1m on 2008-10-14
> **TravisHaynes said:**
> So far I've been using VirtualBox to use my CIT200 phone with Skype. The latest version supports USB devices. It works fine, but I have to load VirtualBox every time I want to use Skype, and that takes about 50% of my computer's resources!

I'd absoloutly LOVE to be able to use my CIT200 with VirtualBox!!

Any chance you could post the instructions on how you got it going.  VirtualBox WILL NOT recognize my CIT200 base.  I get error messages whenever I select it from the USB devices list :(

Thanks in advance if you can help.

Jim :)

---

### Post by powertower on 2008-10-19
I would also be very interested getting VirtualBox working with Ubuntu. Not a big deal, i sit in front of the puter all day anyways and the CIT200 would be a bonus to have functional.

---

### Post by TravisHaynes on 2008-10-28
> Originally posted by **J1m**
[I]I'd absoloutly LOVE to be able to use my CIT200 with VirtualBox!!

Any chance you could post the instructions on how you got it going. VirtualBox WILL NOT recognize my CIT200 base. I get error messages whenever I select it from the USB devices list[/I] 

It worked out of the box for me. I'm running Hardy on an Acer 5570Z laptop using Sun xVM VirtualBox 1.6.2 running Windows XP Professional. I didn't have to do anything special to get it going.

---

### Post by goldmanns on 2008-12-17
> **Borrus said:**
> sorry peeps but im afraid ive had to terminate this project now. the legal hurdles are too much of a pain. check out section 2b of this:

[http://www.skype.com/company/legal/terms/api.html](http://www.skype.com/company/legal/terms/api.html)

Skype's API is "open" in the sense that anyone can view what it is, but you can't actually use the damn thing unless you're "signed up". And, in the case of interfacing to a hardware device, that means becoming a hardware partner. lol, right.

I sent Skype an email asking for clarification, that I was merely aiming to provide support for a device under Linux that's already been approved by them, but I didn't get a response.

I'm bitterly disappointed about this because the project was coming on so well, and was a great deal of fun too. This Skype API issue is the final nail in the coffin for me.

ps no, you can't have my stuffz, sorry ;)

Dude, screw Skype! This licensing issue is just STUPID! Get your code out there anonymously and someone will pick it up! ;)

---

### Post by chrisrulesall on 2009-05-24
OK, its been A very long time since this thread was started, and I was wondering it there was any possibility of getting this project going again. I have a couple CIT200 devices and I am absolutely Dieing to get them working in Ubuntu.

---

### Post by ozite on 2009-05-24
I agree that it would be very nice be able to use the CIT200 in Linux... 

What are the chances of convincing Linksys to provide the software?

---

### Post by chrisling on 2009-10-22
I had a couple of CIT200, too.

How about "working with" Linksys guys rather than waiting for them to provide a driver for the community?

On a side note, there seems to be an issue with the CIT200 running under WinXP after the latest Windows Live Messenger is installed, somehow the WLM is interfering such that the CIT200 displays "DISCONNECTED".

I am sure there is a strong business incentive for Linksys on this, so it is a win-win if they can get involve on this project.

C

---

### Post by vinnn on 2009-11-02
Would be great if we had a driver, my CT200 has sat in a box since new as I couldn't even get it to work on a Virtualbox VM running Windows XP but I think that was a shortfall of Virtualbox's USB filtering at the time.

I have just retried the phone for the first time in about a year on a virtual Windows XP machine running in Virtualbox 3.0.10 on an Ubuntu 9.10 64bit host and it *almost* works, almost. :(

The Windows XP VM is running the old (2005) CT200 software version 3.4.4 with the newest version 4.1.0.179 of Skype for Windows.

Here's a couple of screenshots of it all running in seamless mode...

[http://farm4.static.flickr.com/3480/4069506561_78693045b0_o.png](http://farm4.static.flickr.com/3480/4069506561_78693045b0_o.png)
[http://farm3.static.flickr.com/2620/4069507347_6104fd4f25_o.png](http://farm3.static.flickr.com/2620/4069507347_6104fd4f25_o.png)

I can bring up my contacts on the phone and make & receive calls.... BUT... the audio playback is super choppy and sllooowwww. A huge shame as I was so close to having the CT200 phone working for the first time, albet fudging it by using a Windows VM.

---

### Post by mccljp on 2010-05-17
I just loaded Ubuntu on one of my machines,  My windows box crashed and I decided it was time to use Linux.  This thread did not leave me a happy camper.  Is there any solution in the works?

Thanks, John

---

### Post by gnif on 2010-12-29
I am absolutely horrified and shocked that Borrus did not release his code, or at-least the documentation of the protocol to talk to it so that a open driver could be written for this device! Who cares about Skype, this would be a great device to use for other VOIP services, including an asterisk server.

I have a Phillips VOIP321, which from what I can tell is the same beast, and I have spend the free time I have had here and there over the last year reverse engineering it, and making it operate.

So far I can:
* set the time on the device
* **ring it, and open the audio in/out**
* play audio over the device
* record from its microphone
* set the skype online status
* set the messages status
* respond to the USB ping keep-alive messages

The code has been released fully open here [http://code.google.com/p/voip321/](http://code.google.com/p/voip321/). This is a very primitive test application at this point, but I am currently working on a proper daemon that will be committed in the next day or two that can be controlled via a script.

I am still reversing the protocol, but making steady progress and hope to have at-least contacts working soon.

PS: This is one of the first USB devices I have reverse engineered, thus the progress is quite slow.

---

### Post by ozite on 2011-08-14
I've wanted to have the Linksys CIT200 working under Ubuntu since Dapper Drake.  No drivers have ever been available and I couldn't get it to work under Virtual Box/XP.  Below are some brief instructions that work for 10.10 and 11.04.

Install VMware Player Application 3.1.4
Download bundle, from terminal 'sudo sh Vm...bundle'

Start VMware Player (Apps/System tools), Create New Virtual Machine

Install Windows from XP ISO

Customize Hardware
Show all USB devices in Virtual Machine settings

It should find CIT200 in next step
Download and install any VMware updates
Install Windows XP
In the bottom bar, the CIT200 will have a red x over it. Right click and connect.  May give warning about snd-usb-audio and usbhid. The first warning will be taken care of later.

In XP, install Skype and CIT200 driver from Linksys.  Enable Windows updates.

CIT200  Blacklist (taken from [http://ubuntuforums.org/showthread.php?t=1389308](http://ubuntuforums.org/showthread.php?t=1389308))

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

add the following to the end of the file
# prevent snd-usb-audio from claiming usb-mic
blacklist snd-usb-audio

Also tried 'blacklist usbhid' but this did not seem to make any difference. 

System-Preferences-Startup Applications
Add new /usr/bin/vmplayer

Restart Ubuntu,  VMware Player should startup and then manually start XP virtual machine.

Still need to manually start Windows XP and open Skype to login.  

Perhaps this can help someone out that uses the Linksys CIT200 and Skype. Overall it is still a bit clunky, but at least the XP box that was on 24/7 can be replaced with the Ubuntu Box that also runs MythTV 24/7.

---

### Post by pippo06 on 2012-03-07
I do NOT know if there is still demand and I DO know that the topic is old, but I just wanted to say that I started a project called cit200xSkype that should help you to use Skype for Ubuntu (and maybe also on WIN since it uses LINUX/WIN compatible Python libraries:libusb and Skype4Py).

Please test it and report serious problems on github (or PM me):
[https://github.com/philsmd/cit200xSkype](https://github.com/philsmd/cit200xSkype)

TESTERS and Developers/Contributors wanted!

Thx!
Bye,
Pippo

---

### Post by ozite on 2012-03-10
> **pippo06 said:**
> I do NOT know if there is still demand and I DO know that the topic is old, but I just wanted to say that I started a project called cit200xSkype that should help you to use Skype for Ubuntu (and maybe also on WIN since it uses LINUX/WIN compatible Python libraries:libusb and Skype4Py).

Please test if and report serious problems on github (or PM me):
[https://github.com/philsmd/cit200xSkype](https://github.com/philsmd/cit200xSkype)

TESTERS and Developers/Contributors wanted!

Thx!
Bye,
Pippo

I'm a beginner and interested in your project. I tried your instructions, but received the following:

```
[i] Connecting to Skype..
Traceback (most recent call last):
  File "cit200xSkype.py", line 719, in <module>
    main()
  File "cit200xSkype.py", line 64, in main
    skype.Client.Start()
  File "/usr/local/lib/python2.7/dist-packages/Skype4Py/client.py", line 273, in Start
    self._Skype._Api.startup(Minimized, Nosplash)
  File "/usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py", line 179, in startup
    os.execlp('skype')
  File "/usr/lib/python2.7/os.py", line 327, in execlp
    execvp(file, args)
  File "/usr/lib/python2.7/os.py", line 344, in execvp
    _execvpe(file, args)
  File "/usr/lib/python2.7/os.py", line 380, in _execvpe
    func(fullname, *argrest)
ValueError: execv() arg 2 must not be empty

```

---

### Post by pippo06 on 2012-03-10
Hi ozite!
This may be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/skype4py/+bug/566303](https://bugs.launchpad.net/ubuntu/+source/skype4py/+bug/566303).

Please just check that your system is up-to-date: sudo apt-get update;sudo apt-get upgrade

Strange that the error is about DBUS since the code prefers X11 as transport over DBUS. You use X11? Is the $DISPLAY variable set?

I just did/used another patch that may be unrelated to this issue (or maybe not):
```

$ diff /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py.orig /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py
*** /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py.orig      2012-03-10 13:36:11.186580377 +0100
--- /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py   2012-03-10 13:36:19.902580088 +0100
*************** class SkypeAPI(SkypeAPIBase):
*** 87,88 ****
--- 87,98 ----
      def run(self):
+         # Bug fix 'segmentation fault core dumped' when using dbus.
+         self.logger.info('thread started')
+         if self.run_main_loop:
+             context = self.mainloop.get_context()
+             while True:
+                 context.iteration(False)
+                 time.sleep(0.2)
+         self.logger.info('thread finished')
+ 
+     def runOld(self):
          self.logger.info('thread started')

```


**EDIT:**
The fix that could work for you is to replace:
 os.execlp('skype') 
WITH
 os.execlp('skype','--')
in  /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_x11.py (as how it was explained in the bug-link above).
But only do that if an update does NOT resolve the problem, you could also try/check the skype4Py repository if there is still this bug.
```

diff -p1 /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_x11.py.orig /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_x11.py
*** /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_x11.py.orig    2012-03-10 13:56:30.098539764 +0100
--- /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_x11.py       2012-03-10 13:56:24.862539940 +0100
*************** class SkypeAPI(SkypeAPIBase):
*** 402,404 ****
                  os.setsid()
!                 os.execlp('skype')
  
--- 402,404 ----
                  os.setsid()
!                 os.execlp('skype',--)

```


and the same in posix_dbus.py:
```

$ diff -p1 /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py.orig /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py
*** /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py.orig      2012-03-10 14:06:28.998519810 +0100
--- /usr/local/lib/python2.7/dist-packages/Skype4Py/api/posix_dbus.py   2012-03-10 14:06:38.898519480 +0100
*************** class SkypeAPI(SkypeAPIBase):
*** 188,190 ****
                  os.setsid()
!                 os.execlp('skype')
  
--- 188,190 ----
                  os.setsid()
!                 os.execlp('skype','--')
  

```

---

### Post by ozite on 2012-03-10
> **pippo06 said:**
> Hi ozite!
This may be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/skype4py/+bug/566303](https://bugs.launchpad.net/ubuntu/+source/skype4py/+bug/566303).

Please just check that your system is up-to-date: sudo apt-get update;sudo apt-get upgrade

Strange that the error is about DBUS since the code prefers X11 as transport over DBUS. You use X11? Is the $DISPLAY variable set?

I just did/used another patch that may be unrelated to this issue (or maybe not):
----




My system was up to date. I don't know how best to check the$DISPLAY variable.  I'm using the default gui in 11.10.

```
ozite@ubuntu:~$ echo $DISPLAY
:0

```

```
nvidia-settings:  version 280.13  (buildd@yellow)  Fri Aug  5 12:31:28 UTC
2011
  The NVIDIA X Server Settings tool.

  This program is used to configure the NVIDIA Linux graphics driver.
  For more detail, please see the nvidia-settings(1) man page.

  Copyright (C) 2004 - 2010 NVIDIA Corporation.

```

It still had the same error, but that was solved by putting the ,'--' in the two files you described above.  Should it be "os.execlp('skype','--')" in each file, or "!                 os.execlp('skype',--)" in posix_x11.py?

Skype is opened when I execute "sudo python cit200xSkype.py", but I don't see any other audio devices.  The CIT200 phone only shows disconnected.  

I also get error messages "Another Skype instance may exist" if I quit Skype and try to reopen it.

---

### Post by pippo06 on 2012-03-10
Yes without the exclamation mark (which was generated from the diff tool)!

I think you have patched them correctly, but re-check that **both** posix_x11.py and posix_dbus.py have
os.execlp('skype','--')
instead of 
                os.execlp('skype')

I think the X11 is ok on your system

The next (and of course a different) problem seems to be the connection to the skype process:
- just try to close any instance of skype (check it also w/ 'ps aux|grep skype' just to be sure) and re-start cit200xSkype. 
- another way: test skype alone (does it still give the error saying that there is another instance?if yes a reboot will propably solve it, but killing skype completely will be faster)

> The CIT200 phone only shows disconnectedHow do you know that? Does some entries named similar to Linksys CIT200 appear in the sound devices list in the skype Options? I do NOT know how you can say that it is disconnected, you should plug the USB base in and lsusb will show a line identifying the device with ID 13b1:001d Linksys. Is that ok on your system? Remember that the CIT200 is a HID (Human Interface Device) and cit200xSkype is NOT a driver for it (the linux kernel supports these HID devices, i.e. the audio part etc since a while), but it is a tool to communicate w/ the base/phone by receiving/sending commands to it. Hope that clarifies what cit200xskype is and what was missing up until now (indeed one of the first posters in this thread already stated that the driver is NOT the problem). 

Hope this helps. Tell me if you have still doubts or experience any problems.

Best,
Pippo


**UPDATE:**
if you by disconnected mean that the device is displaying the text "DISCONNECTED" you should really try to issue the command:
```
$ lsusb
```and check if you find the Linksys device in the output w/ the ID I posted above. If it is different from mine and you are sure that it is THE cit200 phone just try to update the ID_VENDOR and ID_PRODUCT variables in cit200xSkype.py. But that should absolutely NOT be the case.

---

### Post by ozite on 2012-03-10
> **pippo06 said:**
> Yes without the exclamation mark (which was generated from the diff tool)!

I think you have patched them correctly, but re-check that **both** posix_x11.py and posix_dbus.py have
os.execlp('skype','--')
instead of 
                os.execlp('skype')

I think the X11 is ok on your system

The next (and of course a different) problem seems to be the connection to the skype process:
- just try to close any instance of skype (check it also w/ 'ps aux|grep skype' just to be sure) and re-start cit200xSkype. 
- another way: test skype alone (does it still give the error saying that there is another instance?if yes a reboot will propably solve it, but killing skype completely will be faster)

How do you know that? Does some entries named similar to Linksys CIT200 appear in the sound devices list in the skype Options? I do NOT know how you can say that it is disconnected, you should plug the USB base in and lsusb will show a line identifying the device with ID 13b1:001d Linksys. Is that ok on your system? Remember that the CIT200 is a HID (Human Interface Device) and cit200xSkype is NOT a driver for it (the linux kernel supports these HID devices, i.e. the audio part etc since a while), but it is a tool to communicate w/ the base/phone by receiving/sending commands to it. Hope that clarifies what cit200xskype is and what was missing up until now (indeed one of the first posters in this thread already stated that the driver is NOT the problem). 

Hope this helps. Tell me if you have still doubts or experience any problems.

Best,
Pippo


**UPDATE:**
if you by disconnected mean that the device is displaying the text "DISCONNECTED" you should really try to issue the command:
```
$ lsusb
```and check if you find the Linksys device in the output w/ the ID I posted above. If it is different from mine and you are sure that it is THE cit200 phone just try to update the ID_VENDOR and ID_PRODUCT variables in cit200xSkype.py. But that should absolutely NOT be the case.

The posix_x11.py and posix_dbus.py were both changed and seem to be okay. I restarted and can close Skype and run the "sudo python cit200xSkype.py" to start Skype again.

The only sound devices are PulseAudio Server (Local). The hardware works okay in Virtual Box/XP and I can make a call.

The device ID seems to be okay.

```
ozite@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 006: ID 13b1:001d Linksys 
Bus 002 Device 004: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
```

By disconnected I meant the display on the front of the phone.

Thanks for your patience.

Could pulseaudio be part of the problem?

---

### Post by pippo06 on 2012-03-10
Ok, the output is totally ok.
Can you also provide the output of sudo python cit200xSkype.py to see how far you are?

In the skype application on my system I have (along my HDMI audio device and the entry Default device (default)) also these lines (go to Options (CTRL-O) and click on Sound Devices):
```

Linksys CIT200, USB Audio Default Audio Device (default:CARD=CIT200)
Linksys CIT200, USB Audio Front speakers (front:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio 4.0 Surround output to Front and Rear speakers (surround40:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio IEC958 (S/PDIF) Digital Audio Output (iec958:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio Direct sample snooping device (dsnoop:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio Direct hardware device without any conversions (hw:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio Hardware device with all software conversions (plughw:CARD=CIT200,DEV=0)

```If you do NOT have any of these entries we should check if it depends on the audio backend (I use gstreamer at the moment, but it should work with pulseaudio also). What do you have in the systemsettings->Multimedia->Phonon->Backend? PulseAudio?

It could also be that a kernel module that I have added is missing (blacklisted?) on your system or that the device was already claimed by another application!? You currently do NOT use the device on vmware,do you? You should detach it from vmware for the moment if so.

Please also check if you use the most recent version of skype (just in case,but since it is updated only rarely that should NOT be the problem).

> Thanks for your patience.I thank you for the testing. I think we can find the problem and add it to the README/instructions!

Best,
Pippo

**EDIT:**
I saw that e.g. comment [#58]("http://ubuntuforums.org/showpost.php?p=11151878&postcount=58") (EDIT2: ok, that was even you to suggest that solution,so you know what needs to be undone?) suggested to black-list some modules. If you have done so, you need to undo it for these tests, otherwise it can't work of course. Please check it for instance w/ modprobe -l or simply undo the changes in the config files w/ a text editor.

---

### Post by ozite on 2012-03-10
> **pippo06 said:**
> Ok, the output is totally ok.
Can you also provide the output of sudo python cit200xSkype.py to see how far you are?

In the skype application on my system I have (along my HDMI audio device and the entry Default device (default)) also these lines (go to Options (CTRL-O) and click on Sound Devices):
```

Linksys CIT200, USB Audio Default Audio Device (default:CARD=CIT200)
Linksys CIT200, USB Audio Front speakers (front:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio 4.0 Surround output to Front and Rear speakers (surround40:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio IEC958 (S/PDIF) Digital Audio Output (iec958:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio Direct sample snooping device (dsnoop:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio Direct hardware device without any conversions (hw:CARD=CIT200,DEV=0)
Linksys CIT200, USB Audio Hardware device with all software conversions (plughw:CARD=CIT200,DEV=0)

```If you do NOT have any of these entries we should check if it depends on the audio backend (I use gstreamer at the moment, but it should work with pulseaudio also). What do you have in the systemsettings->Multimedia->Phonon->Backend? PulseAudio?

It could also be that a kernel module that I have added is missing (blacklisted?) on your system or that the device was already claimed by another application!? You currently do NOT use the device on vmware,do you? You should detach it from vmware for the moment if so.

Please also check if you use the most recent version of skype (just in case,but since it is updated only rarely that should NOT be the problem).

I thank you for the testing. I think we can find the problem and add it to the README/instructions!

Best,
Pippo

**EDIT:**
I saw that e.g. comment [#58]("http://ubuntuforums.org/showpost.php?p=11151878&postcount=58") (EDIT2: ok, that was even you to suggest that solution,so you know what needs to be undone?) suggested to black-list some modules. If you have done so, you need to undo it for these tests, otherwise it can't work of course. Please checked that e.g. w/ modprobe -l or simply undo the changes in the config files.

I commented the line that was blacklisting the snd-usb-audio and restarted.  I don't know yet if that is sufficient, but I did have a new entry under audio hardware.

I don't have a System Settings -> Multimedia.  I have a "sound" icon.  After commenting the blacklist, a Linksys CIT200, 1 Output/1 Input/Analog Mono Duplex device is now in hardware.  An input device is also listed for Liksys CIT200.  Seems like making progress, but...

Here's the output from a terminal.  
```
ozite@ubuntu:~/cit200xSkype$ sudo python cit200xSkype.py 
[sudo] password for ozite: 
[i] Connecting to Skype..
ozite@ubuntu:~/cit200xSkype$ 

```

Skype is opened and I login.

Under sound devices, only the PulseAudio server (local) is listed in Skype.

---

### Post by pippo06 on 2012-03-10
Hi,
sorry but it seems that you also need the first patch I suggested in comment [#61]("http://ubuntuforums.org/showpost.php?p=11753847&postcount=61"), this will let cit200xSkype continue (without the unexpected "crash",maybe a SEGV in posix_dbus of Skype4Py). Please test again with that patch.
And yes, if you have additional audio devices also Skype should list them. Please confirm that you use the most recent version and have restarted Skype after the modprobe changes!

**AND** please check also the "Why do I see only "PulseAudio Server (local)" in my devices list?" question in the skype official blog [http://blogs.skype.com/linux/2009/09/some_explanations.html](http://blogs.skype.com/linux/2009/09/some_explanations.html)! Maybe you can leave that setting there but then you need to tell pulseaudio to use the "right" device for skype (I'm NOT totally sure how to do that)

---

### Post by ozite on 2012-03-10
> **pippo06 said:**
> Hi,
sorry but it seems that you also need the first patch I suggested in comment [#61]("http://ubuntuforums.org/showpost.php?p=11753847&postcount=61"), this will let cit200xSkype continue (without the unexpected "crash",maybe a SEGV in posix_dbus of Skype4Py). Please test again with that patch.
And yes, if you have additional audio devices also Skype should list them. Please confirm that you use the most recent version and have restarted Skype after the modprobe changes!

**AND** please check also the "Why do I see only "PulseAudio Server (local)" in my devices list?" question in the skype official blog [http://blogs.skype.com/linux/2009/09/some_explanations.html](http://blogs.skype.com/linux/2009/09/some_explanations.html)! Maybe you can leave that setting there but then you need to tell pulseaudio to use the "right" device for skype (I'm NOT totally sure how to do that)

I applied the first patch and that helps.  Now I get the following:

```
ozite@ubuntu:~/cit200xSkype$ sudo python cit200xSkype.py 
[sudo] password for ozite: 
[i] Connecting to Skype..
[+] Successfully attached to skype process
[i] User status was changed to ONLINE
[i] Calling echo123       

```

I can initiate calls from the handset :-), but I can't get the audio/microphone through the handset (yet).

I'll read through the Skype for Linux blog link you provided and see if I can get some information there to deal with Pulseaudio and Skype.

---

### Post by pippo06 on 2012-03-10
That's awesome!
Hope you get a quick answer to the missing part (pulseaudio). Sorry,I'm NO expert w/ that and may NOT be able to help you further to get the right device selected (but there are many blog/forums around that address the problem).
Anyway, cit200xSkype seems at least to start and do its things correct (till now) on your system.
If it (the audio) really doesn't work w/ pulseaudio (but that should in my opinion be doable somehow) you still can give ALSA etc a try and switch back if you can't stand it!

Please report your progress here,I'm happy to here if my small project is usable at least for some people :D

**AND UPDATE:**
I remember to have used the pavucontrol utility once, pls check this [http://unix.stackexchange.com/questions/13570/sound-input-issue-with-skype-selecting-a-microphone](http://unix.stackexchange.com/questions/13570/sound-input-issue-with-skype-selecting-a-microphone)

[B]UPDATE 2:
[/B]I just want to note here that I accidentally changed my sound-backend this weekend to pulseaudio and also Skype had then displayed only the one item (PulseAudio Server (Local)) but by configuring the CIT200 Linksys device w/ pavucontrol (non-mute/non-disabled) it perfectly work w/ skype (and cit200xSkype). You just have to enable them (and maybe disable other audio devices). So there should be NO problem w/ pulseaudio in this regard.

---


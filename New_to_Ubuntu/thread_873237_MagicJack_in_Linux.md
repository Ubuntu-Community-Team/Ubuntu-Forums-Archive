---
title: "MagicJack in Linux"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2008-07-28
Just curious, just wondering, has anyone ever tried to use the Magicjack voip in Linux?

---

### Post by ashwinipn on 2008-08-08
I am also seraching for a "yes" and "how to" post on the topic... in case any of us comes across, would let it know to the other...

---

### Post by avibp on 2008-10-05
I am hoping hoping hoping someone (smarter than me obviously) finds a yes to this.

I want this to work on an old desktop unit and boot from a flash drive too so, this being my first step doesn't look promising so far.

---

### Post by kansasnoob on 2008-10-05
Not that I know of. I'm dual booted with XP and I just boot into XP to use it.

I'm amazed at how well it works.

---

### Post by ronnielsen1 on 2008-10-05
[http://ubuntuforums.org/showthread.php?t=511689](http://ubuntuforums.org/showthread.php?t=511689)

People working on it

---

### Post by josephdaniel on 2008-10-06
Check this post. I see there is some progress but I don't know how we can invest it.

[http://ubuntuforums.org/showthread.php?t=939995&highlight=magicjack](http://ubuntuforums.org/showthread.php?t=939995&highlight=magicjack)

---

### Post by cncgeorge on 2008-10-12
I am running Ubuntu 8.04 and wanted to install MagicJack on my Linux box to provide cheap phone service for my entire house. I have it partially working. The magicjack currently works on a headset plugged into sound card and not the phone.

I am currently running VirtualBox with Windows XP installed it recognized the magic jack and installed ok. Problem is no phone support on headset. If anyone has any info I would love to hear it.

Thanks!

---

### Post by JeffAtET on 2008-11-04
Hi, I just received my "MagicJack".  Worked in about a minute or two of plugging it into my iMac.  Quality was almost as good as my stand-alone voip phone "GrandStream GX2000".   

Just for fun I plugged it into my Asus eeePC 701, running standard Xandros linux and Skype.  Wow, it works great, clear, crisp sound, the touch-tone keys on the analog phone work.

What works in Skype:   

1)  Keys on standard analog phone 0,1,2,3,4,5,6,7,8,9,*,#
2)  Voice incoming and outgoing
3)  Good old dial tone.

What doesn't work in Skype:

1) Lifting the receiver doesn't answer the phone, you must click the green phone icon in the  pop up for an inbound skype or skype-in call.
2) Dialing out from the analog phone doesn't work, you must click on an existing contact or type in the number from the keyboard, but once connected to a land line, the touch-tone keys work with voicemail or other systems using touch-tones.
3) The phone rings through the pc speakers, not the phone's bell.

With my little Asus eeepc 701 (black) and this old black GE phone and magicJack, I've got my whole office in a very small bag.

When I looked at the skype audio settings, skype automatically had picked the usb-Tiger input/output.  I have Skype out and have called business phone numbers that require entering combination's of numbers to reach your desired extension, leave voicemail, listen to your voice message and save/send.   It all worked, which sounds trivial, unless you've tried soft-phones or voip phones where DTMF doesn't work.  I am very impressed so far.   

Have fun, ;-)

Jeff

---

### Post by bsskibum on 2009-03-31
I have implimented.. works perfect!!!
taken from dslreports.com

Successfully setup Ubuntu Linux + VMWare + XP + MagicJack

I was using a dedicated XP box for MagicJack and I have a 24x7 server running ubuntu so I decided to give it a try and was able to move MagicJack to my Ubuntu box successfully.

Here are what I did, hope it will help others like me who don't want a dedicated XP running just for MagicJack.

I started with an existing Ubuntu server install that does not have GUI.

Install GUI and VNC:
Downsize the system:
- sudo vi /etc/default/linux-restricted-modules-common:
DISABLED_MODULES="ath_hal fc fglrx ltm nv"

Install the X11 bare bone:
- sudo aptitude install x-window-system-core
- sudo aptitude install xorg
- sudo aptitude install fluxbox fluxconf #lightwight windows manager
- sudo aptitude install dillo #lightweight browser
- sudo aptitude install xfe #lightweight file manager

Change /etc/X11/xorg.conf:
- sudo dpkg-reconfigure xserver-xorg #guided setup
- manual edit /etc/X11/xorg.conf (use "gtf 1024 768 60" to obtain the Modeline values):

Section "Monitor"
Identifier "KDS k717s" #This is my monitor
HorizSync 31-80
VertRefresh 60-75
# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "KDS k717s"
Device "Configured Video Device"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
EndSection

Starting X:
- use startx
- Virtual console F7 is the x window (display :0)

Install X11vnc:
- sudo aptitude install x11vnc

Start vnc:
- startx
- x11vnc --forever &

Connect to server remotely via vnc:
- vncviewer host:0

By now, I got a light GUI Ubuntu box that can be accessed remotely via VNC.

Setup VMWare:
Get the kernel header:
- sudo apt-get install linux-headers-$(uname -r)

Then run the vmware-install.pl as root

Then run the vmware-config.pl (install will prompt to run this)

If you receive compilation error when run vmware-config.pl like this:
include/asm/bitops_32.h:9:2: error: #error only can be included directly, and vmmon-only compile failes
The solution is: change line 74 in vmmon-only source file to read: #include “linux/bitops.h”
Steps:
cd /usr/lib/vmware/modules/source
cp vmmon.tar vmmon.tar.orig
sudo tar xvf vmmon.tar
cd vmmon-only/include/
sudo vi vcpuset.h
change line 74 from: #include “asm/bitops.h” to: #include “linux/bitops.h”
rm vmmon.tar (return to the folder where you decompressed the tar file)
sudo tar cvf vmmon.tar vmmon-only/
sudo rm -rf vmmon-only/

Then re-run: sudo vmware-config.pl

After this I have a working vmware that can be launched by "vmware".

Guest XP OS install:
You would need to install and activate your XP Guest OS. I already have a VMware image so this is skipped.

Detect MagicJack USB devices:
I was initially having problem detecting the MagicJack USB devices. I did two things that fixed it:
1. Make sure the XP virtual machine has the USB Controller in the hardware list
2. Check that the vmx file of the virtual machine has:
usb.present = "TRUE"
usb.generic.skipsetconfig = "TRUE"
The second line is missing in my vmx file and I had to manually add it.

After this, I rebooted the guest XP OS and re-plug in the MagicJack. XP detected both devices properly and started its installation. After that the MagicJack is up and running and I was able to make calls.

Cheers!

BTW, I was posting this to the unofficialmagicjack forum but keep getting "Method Not Implemented, POST to /posting.php not supported." error when submit the post - tried 3 different browsers.

---

### Post by pizzaguy4hire on 2009-04-07
I have Magic Jack, Windows XP Pro legit software and license key, and I'm running "gOS" (Ubuntu derivative?) on my primary system - laptop - and I want to run the Magic Jack from within Linux.

Whether this means "native" or through an XP VM from within linux, I don't care, but I am a complete "n00b" when it comes to VM & VNC and scripting or anything... I came from Windows World, afterall!!!

If someone could assist me with this - even a step by step from the ground up on doing something similar to the long install post up above (assume I know nothing about Linux would be good) I would be EVER so grateful!!!

Many thanks,

Zach
AKA "PizzaGuy"

(No 30 minute or less guarantee here - but I'll get it done, even if it takes all night!)

---

### Post by imaginashawn on 2009-04-10
K, the question was Magicjack in Linux. Not Magicjack in Linux and Windows lol. Anybody can run it in Windows.
I copied this from another board. Hope that's ok.

Quote;
[quote="gnimsh"]So I've been doing a lot of testing of softphones in linux lately, and I've had some very mixed results.  I am currently using Ubuntu 7.10.  I installed a VMWare machine, and first ran the MJ on that fine, complete with phone support and everything.  But I wanted to go further than that and run something natively, so I didn't have to run the VM all the time.  

Here are the programs I tried: linphone, Kphone, wengophone, ekiga softphone, gizmo project, xlite (for linux, and the windows version under wine) and twinkle.  The only one I actually had any success with is twinkle.  Edit: I got Xlite to work, see instructions at bottom.

let's see if I an streamline this.

*********
TWINKLE
*********

You can find twinkle [here](http://www.twinklephone.com/) and they also have many packages towards the bottom for the major distros.  I'm gonna go through and show you guys how to set up twinkle to get it to work, because I got it to work the first time I installed ubuntu, didn't document it, and then reinstalled (from 64 bit to 32 bit) and struggled until just this morning to get it work. 

Here is a link to some deb files for very easy installation of twinkle: [http://www.getdeb.net/app/Twinkle](http://www.getdeb.net/app/Twinkle)

So first, in your user account you'll need to set up your user name.
Your name
username (E<your number here>01), the 
domain (just the IP address).  

Next the SIP authentication.  
Leave the realm field blank.  
authentication name is your username the E<your number here>01 number. 
Then fill in your password.   

Move next to the SIP server section.  
For the registrar you will need to use proxy1.nashville.talk4free.com:5070
Check the register at startup box.

Outbound proxy:  proxy1.nashville.talk4free.com:5070
Check use outbound proxy box.  Don't check the other 2 boxes below it.  

Next, for the voicemail, just fill in your phone number (minus the E and 01), and choose unsolicited from the dropdown menu.  

That's all you need for the basic functioning of the phone, so enjoy!
***********
X-LITE
*****
Click the button to the right of the "clear" button in the center of the xlite console. Choose system settings>SIP proxy>default.

Double click enabled, change to yes.
Display name: whatever you want.

Username: your proxy username
Authorization user: also your proxy username.
Password: Your sip password here
Domain/realm: UserDomain
SIP Proxy: proxy1.YourCityHere.talk4free.com
Out Bound proxy: proxy1.YourCityHere.talk4free.com:5070 (if your ProxyPort is different use that instead of 5070)
After this all the fields remain at default, change nothing.[/quote]

---

### Post by icanfly0307 on 2009-04-12
Hi, MagicJack actually works out of the box for me! Just plug it in, wait for a minute or two, pick up the phone and you should hear the dial tone! I tried this in Fedora 10 and it worked. Not sure about Ubuntu though. Someone could test it out, maybe?

Good Luck!

---

### Post by imaginashawn on 2009-04-12
Well, if a dialtone is all you want, congrats! :lolflag: Did you try calling someone before you posted? I have a dialtone also but that's all. I've just tried wine. It does recognize the usb but wont run the software.
I'm going to go try one of the methods I posted earlier that he says he got working.

---

### Post by twoblocked on 2009-04-12
I am successfully running MagicJack in Ubuntu 2.6.27-9-generic and VMware Server 2.0.1 with WindowsXP Pro. This box also runs Mythtv and is my workstation.

I could not get MJ to run in VirtualBox/WindowsXP. MJ connected and downloaded software, but the voice was too choppy to be usable. 

VMware requires patience and care when installing. There are other forums that cover the install and the required compiler parts.

You will need to register with VMware and get a free license in order to run the software. Be sure to copy the license number when it is generated, it is not sent by email.

tar -xf VMware-server-2.0.1-156745.i386.tar.gz 
cd vmware-server-distrib/
sudo ./vmware-install.pl 

Open a browser, put in
http://<your computer name>:8222/ui/#  for the URL. This should get you to the Virtual Machine where you can setup your Windows VM.

Be sure when you compile and run the VMware install.pl you make yourself (your Ubuntu login name) the administrator.  VMware defaults to root if you don't and then VMware owns all the hardware on your machine and won't share it with Ubuntu.

To create a Windows Virtual Machine in VMware, I had to make my WindowsXP install disk into an .iso file in order to load it.  The CDROM simply would not start the Windows Setup.  Insert the CD,

cat /dev/scd0 > /home/alan/WindowsXP.iso  (use appropriate device ID and home directory)

I like the fact I have just one computer running 24/7 for both Mythtv and my new phone.

---

### Post by icanfly0307 on 2009-04-13
Actually, I can make calls to people with Fedora. Not sure why it won't work in Ubuntu though...

---

### Post by mauro24 on 2009-04-14
> **icanfly0307 said:**
> Actually, I can make calls to people with Fedora. Not sure why it won't work in Ubuntu though...

so you just plug the magicjack in the fedora 10 and it will make a receive calls.  are you serious? because that's some real good news! Could you give more details, as how it sounds? what kind of computer you have?, I'm about to install fedora then.

---

### Post by icanfly0307 on 2009-04-14
Sorry for the confusion. I meant that I can get MagicJack to work with VMWare on Fedora. I couldn't get VMWare to work on Ubuntu...

---

### Post by bsskibum on 2009-06-02
just found this...april 2009 the owner said this....
[http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010](http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010)

Linux compatibility: Mac and PC users have been using magicJack for some time now, but Linux has been left out in the cold&#8211;but not much longer. According to Borislow, Linux compatibility should be available &#8220;3rd quarter of this year.&#8221;  This addition will be available to both current and new magicJacks

---

### Post by frankhdz on 2009-06-20
> **bsskibum said:**
> just found this...april 2009 the owner said this....
[http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010](http://blog.laptopmag.com/magicjack-scoop-new-features-new-device-coming-in-2009-2010)

Linux compatibility: Mac and PC users have been using magicJack for some time now, but Linux has been left out in the cold–but not much longer. According to Borislow, Linux compatibility should be available “3rd quarter of this year.”  This addition will be available to both current and new magicJacks

I doubt this will happen we are into 09 now and still no linux support. That comment was made in 08. I got it to work in VirtualBox but the sound is terrible  in order to use it I have to boot into windows and then the sound is flawless.

---

### Post by HtmlGifted on 2009-08-11
Hay.. need to ask you something..


  went from xp to ubuntu one my systems....  complete wipe....  Need to know... if some one can help me create a barrier breach between . two ideas I would like to mesh... Magic jack.. to work on my ubuntu.. With a small. cell phone capable software. either boost or a Sph A600 ... with the applications.... with phone.. extions.. from magic jack..(kind of a forwarding to a dead .. phone.. on a old signal.. no connect.... but from wireless.. wifi.... you see where i am going.. if you think i have something hit me.Up....  


Thanks.......

HtmlGifted

---

### Post by Locke_99GS on 2009-10-26
[quote="www.magicjack.com Knowledgebase"]Your Question: Will MagicJack work with Linux?
Answer: Not yet. We expect to offer Linux support the first quarter of 2010.[/quote]
.

---

### Post by HtmlGifted on 2010-01-03
Has any one tried Wine ... Maybe Try to add it in that way since wine and Magic Jack are both windows based.... Programs.... Might have to right a windows database for The acess to A windows complete environment In a Browser Window... That Runs Programs through it.... Like Q basic For Insistence... would Be A better learning Curve For Computer class If they Learned Linux.. They have a A Basic skill Of knowledge to work with THAT WILL OPEN DOORS for more creative idea's for our Children's Children...

Just Got caught up... Wish Magic Jack would Do something about this soon.?

Also... Need a Few Freinds.. To add thanks all.. For Having a discussion about this...

---

### Post by olyander562 on 2010-01-23
i will test magicjack with asterisk shortly. if i remember, i will post what i find.

nuff said

njoy, oly out

---

### Post by ehrichweiss on 2010-01-30
> **olyander562 said:**
> i will test magicjack with asterisk shortly. if i remember, i will post what i find.

nuff said

njoy, oly out

I'm anxiously awaiting your post. I've been trying to make it work with Fedora 12 and have had no luck with it other than Ekiga recognizing it when I plug it in, other than that I get a dial tone but no dial-out or incoming calls. 

I'm more interested in using it with asterisk since it could act as a FXS

---

### Post by ReallyANoob on 2010-03-19
> **icanfly0307 said:**
> Sorry for the confusion. I meant that I can get MagicJack to work with VMWare on Fedora. I couldn't get VMWare to work on Ubuntu...

Did you use windows at all? I downloaded Fedora 12 and install VMWare but it didn't work. Can you help me through the process of installing these things and getting it to work? Does it only work in Fedora 10. Do you need a certain version of VMWare? Thank you.

---

### Post by kgingeri on 2010-03-21
> **HtmlGifted said:**
> Has any one tried Wine ... Maybe Try to add it in that way since wine and Magic Jack are both windows based.... 
...

I've tried Wine and no worky there either.  :(  
'1st Quarter of 2010' is about over, and no news from MagicJack either  :(

---

### Post by anewguy on 2010-03-22
Forgive me for not reading the preceeding entries in this thread, so if I repeat something that has already been addressed please excuse me.

There were changes made a few releases ago for how some USB devices are mounted - in particular some are mounted with root as the owner, making use of these devices not possible unless you "sudo" things.  There is a way to changes the rules so you can get such a device working for all users - perhaps that is the problem here?

Try:

lsusb -> note the xxxx:yyyy string on the line for the MagicJack.


Do the following:

sudo gedit /lib/udev/rules.d/10-local-permissions.rules

in the blank file that opens up, add this line:

SUBSYSTEMS=="usb" ATTRS{idVendor}=="xxxx" attrs{idProduct}=="yyyy" MODE:="0666" SYMLINK+="MagicJack"

BE SURE TO REPLACE THE "xxxx" and "yyyy" WITH THE ACTUAL STRINGS FROM THE LSUSB OUTPUT.

Save this file, exit the editor.

Remove the MagicJack and wait a little while, then plug it back in and try again.

I don't think this will solve the problem, as I believe it is the software itself (more specifically, the actual USB driver for it) that needs to be adapted to Linux, but what the heck - it's worth a try!

BTW, for those who know the newest udev structure, while the documentation says to put new files in /etc/udev/rules.d, I have found that doesn't work for me.  Put the same file in /lib/udev/rules.d and it does work.

Dave ;)

BTW - if worse comes to worse, if someone were to run a USB trace in Windows with the device plugged in and go through all of it's motions (dial, connect, whatever else it might have), we can always try to reverse engineer it with libusb calls, if the manufacturer does not object.

---

### Post by kgingeri on 2010-03-24
> **anewguy said:**
> ...
There were changes made a few releases ago for how some USB devices are mounted - in particular some are mounted with root as the owner, making use of these devices not possible unless you "sudo" things.  There is a way to changes the rules so you can get such a device working for all users - perhaps that is the problem here?

Try:

lsusb -> note the xxxx:yyyy string on the line for the MagicJack.


Do the following:

sudo gedit /lib/udev/rules.d/10-local-permissions.rules

in the blank file that opens up, add this line:

SUBSYSTEMS=="usb" ATTRS{idVendor}=="xxxx" attrs{idProduct}=="yyyy" MODE:="0666" SYMLINK+="MagicJack"

BE SURE TO REPLACE THE "xxxx" and "yyyy" WITH THE ACTUAL STRINGS FROM THE LSUSB OUTPUT.

Save this file, exit the editor.

Remove the MagicJack and wait a little while, then plug it back in and try again.

I don't think this will solve the problem, as I believe it is the software itself (more specifically, the actual USB driver for it) that needs to be adapted to Linux, but what the heck - it's worth a try!

BTW, for those who know the newest udev structure, while the documentation says to put new files in /etc/udev/rules.d, I have found that doesn't work for me.  Put the same file in /lib/udev/rules.d and it does work.

Dave ;)

...

Thanks Dave.  However no joy (with Wine anyway) - I do get the device showing up (BTW /etc/udev/rules.d works for me ;v)...
```
$ ls -l /dev/MagicJack 
lrwxrwxrwx 1 root root 3 2010-03-24 00:56 /dev/MagicJack -> sr0

```

When I try the phone program it runs in wine but complains that I need to plug in the device - after it looks for it a while.  Is there a way of mapping a usb device for wine specifically - I might try to google that.

Here's output from 'udevadm monitor' when I plug it in...
```
# udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1269406912.509001] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2 (usb)
UDEV  [1269406912.515814] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2 (usb)
KERNEL[1269406912.517866] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0 (usb)
UDEV  [1269406912.517979] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0 (usb)
KERNEL[1269406912.521034] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12 (scsi)
KERNEL[1269406912.521140] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/scsi_host/host12 (scsi_host)
UDEV  [1269406912.522570] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12 (scsi)
UDEV  [1269406912.522663] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/scsi_host/host12 (scsi_host)
KERNEL[1269406912.525815] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1 (usb)
UDEV  [1269406912.525927] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1 (usb)
KERNEL[1269406912.578113] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1 (sound)
KERNEL[1269406912.578235] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/pcmC1D0p (sound)
KERNEL[1269406912.578333] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/pcmC1D0c (sound)
KERNEL[1269406912.578427] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/dsp1 (sound)
KERNEL[1269406912.578557] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/audio1 (sound)
KERNEL[1269406912.578655] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/controlC1 (sound)
KERNEL[1269406912.578751] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/mixer1 (sound)
KERNEL[1269406912.578853] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2 (usb)
KERNEL[1269406912.578955] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.3 (usb)
KERNEL[1269406912.579051] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4 (usb)
KERNEL[1269406912.579151] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/0003:06E6:C200.0008 (hid)
UDEV  [1269406912.585581] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1 (sound)
UDEV  [1269406912.585703] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4 (usb)
KERNEL[1269406912.592852] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/usb/hiddev1 (usb)
KERNEL[1269406912.592993] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/0003:06E6:C200.0008/hidraw/hidraw1 (hidraw)
UDEV  [1269406912.594568] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.2 (usb)
UDEV  [1269406912.595970] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.3 (usb)
KERNEL[1269406912.644316] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1 (sound)
UDEV  [1269406912.644438] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/pcmC1D0p (sound)
UDEV  [1269406912.644544] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/pcmC1D0c (sound)
UDEV  [1269406912.644648] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/dsp1 (sound)
UDEV  [1269406912.644747] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/usb/hiddev1 (usb)
UDEV  [1269406912.655122] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/controlC1 (sound)
UDEV  [1269406912.655272] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/0003:06E6:C200.0008 (hid)
UDEV  [1269406912.660374] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/mixer1 (sound)
UDEV  [1269406912.670477] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.4/0003:06E6:C200.0008/hidraw/hidraw1 (hidraw)
UDEV  [1269406912.670604] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1/audio1 (sound)
UDEV  [1269406912.698317] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.1/sound/card1 (sound)
KERNEL[1269406917.535729] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0 (scsi)
UDEV  [1269406917.535826] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0 (scsi)
KERNEL[1269406917.535918] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0 (scsi)
KERNEL[1269406917.536002] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/scsi_disk/12:0:0:0 (scsi_disk)
KERNEL[1269406917.536090] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/scsi_device/12:0:0:0 (scsi_device)
KERNEL[1269406917.536181] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/scsi_generic/sg5 (scsi_generic)
KERNEL[1269406917.536270] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1 (scsi)
UDEV  [1269406917.540476] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1 (scsi)
UDEV  [1269406917.540587] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0 (scsi)
UDEV  [1269406917.540668] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/scsi_disk/12:0:0:0 (scsi_disk)
UDEV  [1269406917.543121] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/scsi_device/12:0:0:0 (scsi_device)
UDEV  [1269406917.546236] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/scsi_generic/sg5 (scsi_generic)
KERNEL[1269406917.565882] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0 (scsi)
UDEV  [1269406917.565990] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0 (scsi)
KERNEL[1269406917.576716] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/block/sr0 (block)
UDEV  [1269406917.576833] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/scsi_generic/sg6 (scsi_generic)
KERNEL[1269406917.576918] add      /devices/virtual/bdi/11:0 (bdi)
KERNEL[1269406917.576995] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/scsi_device/12:0:0:1 (scsi_device)
KERNEL[1269406917.577085] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/scsi_generic/sg6 (scsi_generic)
UDEV  [1269406917.583134] add      /devices/virtual/bdi/11:0 (bdi)
UDEV  [1269406917.583261] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/scsi_device/12:0:0:1 (scsi_device)
KERNEL[1269406917.858689] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/block/sdf (block)
KERNEL[1269406917.858789] add      /devices/virtual/bdi/8:80 (bdi)
UDEV  [1269406917.859262] add      /devices/virtual/bdi/8:80 (bdi)
UDEV  [1269406917.902260] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/block/sr0 (block)
UDEV  [1269406918.843522] add      /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/block/sdf (block)
KERNEL[1269406919.270772] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1 (scsi)
KERNEL[1269406919.274264] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/block/sr0 (block)
UDEV  [1269406919.274378] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1 (scsi)
KERNEL[1269406919.278300] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/block/sdf (block)
UDEV  [1269406920.140175] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:1/block/sr0 (block)
UDEV  [1269406920.144653] change   /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/host12/target12:0:0/12:0:0:0/block/sdf (block)
```

---

### Post by anewguy on 2010-03-24
The last I checked, Wine doesn't support USB directly.  It does support some USB devices if they have a Linux driver and work under Linux from what I understand.  However, since there is no Linux driver for MagicJack as of yet, and hence why you are trying it in Wine, I don't think that will ever work.  It does need the non-existant Linux driver first.

Dave ;)

---

### Post by yoasif on 2010-03-24
watching their infomercial right now -- i love their blatant lies -- "no software needed".

I would stay away from this company just because of the lies. 

Also, they keep saying "free" but then they mention yearly fees. which is it?

---

### Post by kgingeri on 2010-03-24
> **yoasif said:**
> watching their infomercial right now -- i love their blatant lies -- "no software needed".

I would stay away from this company just because of the lies. 

Also, they keep saying "free" but then they mention yearly fees. which is it?

@Yoasif: Thanks for the concern, but I have REAL people (around the world) who have very good REAL EXPERIENCE with this device (including myself) and it is good for a VOIP solution.  _Definitely their marketing makes them seem very shady_ - this is too bad.  You do pay $20 a year for good VOIP service (+$20 for the initial device) and there is ads in the softphone that they provide.  They say no software needed (or rather to install) as it all runs off the device, which is also where all your registration info is stored.  There are two drives added on plugging it in - 1 the program and 2 the data.  The device also has it's own sound card it uses for the internet phone. I have used Vonage and this device is **much** better under the same network etc.

@anewguy:  Interesting as the sound card part of the device does get configured under Ubuntu - it even shows as Internet Phone in my sound prefs, and I can set it up (no way to test it though, I'm guessing).  I did try to go into Wine and set that as the sound card to use but it didn't help.  Just an FYI  :)

---

### Post by anewguy on 2010-03-24
> **kgingeri said:**
> @anewguy:  Interesting as the sound card part of the device does get configured under Ubuntu - it even shows as Internet Phone in my sound prefs, and I can set it up (no way to test it though, I'm guessing).  I did try to go into Wine and set that as the sound card to use but it didn't help.  Just an FYI  :)

I would say it fits into the vast majority of USB devices (notice I did say "some", so I guess we know where this device fits in!  :) ) that don't work with Wine.  Initially the Wine kernel stuff supposedly only supports things like USB mice and keyboards; others have had some success with things like printers and scanners when a valid driver exists in Linux.  So...I guess we add another to the "doesn't work" columun.  This probably still goes back to the MagicJack itself and lack of a Linux driver for the phone.

Thanks!

Dave ;)

---

### Post by EyeRguY on 2010-03-26
I too add my interest in seeing this work with linux especially Debian based systems.;) I have loved Ubuntu for some time now and have always dual-booted between the two. I decided that it was time to use Ubuntu exclusively. There seems to be a major bug in Karmic causing my Intel based machine to freeze fatally with no work around or bug fix to date. Which is Ok because KDE works great and I do like a lot of the Kpackages and apps. I have also tried an array of methods and techniques to get MJ to work with no luck. I want to try cloning a partition right after installing a fresh copy of XP and running MJ for the first time. Acronis has great features for this. And then restore the image in a virtual machine that way you could assure that all reg keys and data/dll's dependencies etc. for MJ are present but as stated before, The problem really rest in being able to dedicate a port directly to the VM and not the kernel.
But what are the odds of cloning your MJ credentials to a unix compatible softphone or maybe another type of hardware, Surely this would void the MJ's TOS, Right?

Back to dual-booting XP just for MJ for now.

---

### Post by nappyd on 2010-04-27
It is my opinion that Magic jack will never work with Linux. That is unless an outside source makes it happen. I do not think that Magic jack is even trying to make it compatiable, the first news was that it would be working with linux by the 3rd quarter of 2009 and now by the end of the first quarter of 2010. Well we are now a month past the first quarter and no compatibility.

I have also learned that they have just added an auto renew feature to all magic jacks meaning that when your subscription is expired it auto renews as long as it has your credit card number. This is easy to disable however by following the directions in this link.
[http://www.magicjacksupport.com/how-to-disable-auto-renew-on-magicjack-t7929.html](http://www.magicjacksupport.com/how-to-disable-auto-renew-on-magicjack-t7929.html)

---

### Post by Kafubie on 2010-04-27
This poast is 2/3 years old...
:confused:

---

### Post by oatkinson on 2010-06-04
I found this and just ordered one.  [http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html](http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html)

---

### Post by kgingeri on 2010-06-04
> **oatkinson said:**
> I found this and just ordered one.  [http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html](http://www.magicjacksupport.com/magicjack-runs-natively-on-linux-t8566.html)

@oatkinson:  Just know that this just uses a softphone and your MJ credentials which may be a violation of the Use Agreement you have with MJ.  Also the MJ hardware is useless with it (other than as a sound card) - you cannot use a standard phone or it's dial pad as a result.  :???:

---

### Post by flyinfishy on 2010-07-27
Okay, enough of running MagicJack in Wine.  Run it natively!  I am running MagicJack in Ubuntu 10.04.1 LTS Kernel 2.6.32-24 thanks to this post. [http://www.bauer-power.net/2010/05/how-to-hack-your-magicjack-to-make_27.html](http://www.bauer-power.net/2010/05/how-to-hack-your-magicjack-to-make_27.html)

Yes I can make calls to other people.  Yes I can configure Twinkle to use the TigerJet USB audio device for my speaker and microphone so I can hook my telephone into magicjack and talk to people.  No I can't direct dial from the phone.  I have to use Twinkle to dial then I can pick up receiver.
I also have to use the DTMF button in twinkle to enter my password for my voice-mail.

One big problem!  With the MagicJack plugged directly into USB port, at Startup, I get a Kernel Panic (caps lock and scroll lock flash repeatedly)  right after the login sound plays.  I can't pull out of it,  I have to do a hard power cycle.  not even pressing ctrl+alt+F1,2,3...  But if I unplug MagicJack and let the login screen load. then plug in magic jack and log in, everything is normal.  Can anyone tell me why this happens or how to fix? Thanks!:D

please see attached syslog

---

### Post by kgingeri on 2010-07-29
> **flyinfishy said:**
> ...

One big problem!  With the MagicJack plugged directly into USB port, at Startup, I get a Kernel Panic (caps lock and scroll lock flash repeatedly)  right after the login sound plays.  I can't pull out of it,  I have to do a hard power cycle.  not even pressing ctrl+alt+F1,2,3...  But if I unplug MagicJack and let the login screen load. then plug in magic jack and log in, everything is normal.  Can anyone tell me why this happens or how to fix? Thanks!:D

please see attached syslog

Hi flyinfishy, thanks for the post.  Not real sure why the kernel panic (haven't digested your log) - a couple of things to try maybe...
- you could make sure the boot option for a USB Key is off in your bios - tho this will likely not matter as it sounds like your booted well into Linux already
- look at specifically mounting both partions in the MJ by adding lines in /etc/fstab so the auto mount doesn't try to do something special with it - it may be trying to launch wine before it's ready 

I'll look at your log if I get a chance to soon.

UPDATE: BTW, just wondering if your setup allows for you to TAKE calls - i.e. do you receive calls normally - an attached phone rings, you pickup and talk?

---

### Post by LunaticHiatus on 2010-07-29
magicjack is confirmed spyware and have a very bad eula. I do not suggest using it.

---

### Post by kgingeri on 2010-07-29
> **LunaticHiatus said:**
> magicjack is confirmed spyware and have a very bad eula. I do not suggest using it.

VERY WRONG!

How about you tell us your source for that info - and not some other post on the net either!?

I have people all over the world using it and can confirm IT IS NOT SPYWARE!!!  :mad:

I hate this kind of mis-information!!!

I DO NOT WORK FOR MAGICJACK - but who do you work for?!

---

### Post by anewguy on 2010-07-30
> **kgingeri said:**
> VERY WRONG!

How about you tell us your source for that info - and not some other post on the net either!?

I have people all over the world using it and can confirm IT IS NOT SPYWARE!!!  :mad:

I hate this kind of mis-information!!!

I DO NOT WORK FOR MAGICJACK - but who do you work for?!

I would find it hard to believe it is spyware myself, however, they wouldn't be the first company to collect data about a user without permission.

I guess the other thing I would add:  remember that no one has Magicjack working natively in Linux - all the "working" ones are work-arounds that don't actually use the Magicjack software and you end up with very limited capabilities (not to mention no one has ever confirmed if it might be illegal using the code).

Dave

---

### Post by kgingeri on 2010-07-30
> **anewguy said:**
> I would find it hard to believe it is spyware myself, however, they wouldn't be the first company to collect data about a user without permission.

I guess the other thing I would add:  remember that no one has Magicjack working natively in Linux - all the "working" ones are work-arounds that don't actually use the Magicjack software and you end up with very limited capabilities (not to mention no one has ever confirmed if it might be illegal using the code).

Dave

Yes indeed. It does depend on how you classify 'spyware' - too loosely and Google search is spyware ;)

---

### Post by flyinfishy on 2010-08-02
> **kgingeri said:**
> Hi flyinfishy, thanks for the post.  Not real  sure why the kernel panic (haven't digested your log) - a couple of  things to try maybe...
- you could make sure the boot option for a USB Key is off in your bios -  tho this will likely not matter as it sounds like your booted well into  Linux already
- look at specifically mounting both partions in the MJ by adding lines  in /etc/fstab so the auto mount doesn't try to do something special with  it - it may be trying to launch wine before it's ready 

I'll look at your log if I get a chance to soon.

UPDATE: BTW, just wondering if your setup allows for you to TAKE calls -  i.e. do you receive calls normally - an attached phone rings, you  pickup and talk?

I have Twinkle's preferences set to ringtone my computer's sound card so when someone calls in, I hear the ring through my computer's speakers, then I have to hit the "answer" button in Twinkle and pick up the reciever.  I haven't figured out how to make the phone manipulate Twinkle.

As far as mounting partitions in fstab  I haven't ventured into that.  I'm not sure how to do that.  I will look into it.  Thanks!

---

### Post by mike555 on 2010-08-15
it may be coming to Linux soon if this is an indication ;
[http://www.redorbit.com/news/technology/1904584/magicjack_company_to_offer_free_calls/](http://www.redorbit.com/news/technology/1904584/magicjack_company_to_offer_free_calls/)

---

### Post by LBattis on 2010-08-15
Hate to have to broach politics however, with the Middle-East going up in flames I need to know if this will be an open source product. With their present posture I wouldn't trust Israel not to muck with surveillance mechanisms in the code.

---

### Post by kgingeri on 2010-08-16
> **LBattis said:**
> Hate to have to broach politics however, with the Middle-East going up in flames I need to know if this will be an open source product. With their present posture I wouldn't trust Israel not to muck with surveillance mechanisms in the code.

Hmmm - and you are assuming you can trust it, if it is open-source!?  
I may be pessimistic, but I'd venture to say anything can be wire-tapped, given enough time and deemed necessary by most modern governments.  

That said - I do hear you BUT there is no official Linux install and it certainly won't be open-source as that would be a violation of the MJ EUA.  :v(  We're still hoping for a closed source solution from MJ.

If however your talking about soft-phones running with MJ credentials - then the answer would likely be YES for the soft-phone software - at least you could find one that is. -> [http://www.voip-info.org/wiki/view/Open+Source+VOIP+Software](http://www.voip-info.org/wiki/view/Open+Source+VOIP+Software) for example.

---

### Post by kgingeri on 2010-08-16
> **LBattis said:**
> Hate to have to broach politics however, with the Middle-East going up in flames I need to know if this will be an open source product. With their present posture I wouldn't trust Israel not to muck with surveillance mechanisms in the code.

Hmmm - and you are assuming you can trust it, if it is open-source!?  
I may be pessimistic, but I'd venture to say anything can be wire-tapped, given enough time and deemed necessary by most modern governments.  

That said - I do hear you BUT there is no official Linux install and it certainly won't be open-source as that would be a violation of the MJ EUA.  :v(  We're still hoping for a closed source solution from MJ.

If however your talking about soft-phones running with MJ credentials - then the answer would likely be YES for the soft-phone software - at least you could find one that is. -> [http://www.voip-info.org/wiki/view/Open+Source+VOIP+Software](http://www.voip-info.org/wiki/view/Open+Source+VOIP+Software) for example.

---

### Post by LBattis on 2010-08-16
Grazi Mille I've made a living buttoning corporate systems up for 20 years and the Swiss Cheese I see surrounding me in TWA pisses me off exponentially. Free BSD is my favorite baby. Linux; my everyday love.

---

### Post by jdashbaugh on 2010-09-07
I too have been looking for an answer to this question. I have contacted Magic Jack and get the trained response, "our engineers are working on it." Their web site says by first quarter of 2010 and we are nearly in the 4th quarter of the year already. I think that **_they believe_** that Linux is not worth the time... not until enough Linux users start to complain and start to demand some action. I have only been using Linux now for about 7 months and I'm hooked. I would suggest everyone who reads this forum contact magic jack and ask for some action rather than their empty promises... as the old saying goes, "the squeeky wheel gets the greese!" Let's become the squeeky wheel!

---

### Post by fmontanez on 2011-03-13
I was able to setup and run magicjack in Ubuntu 10.10...

First i downloaded virtualbox 4.04 from the website instead of using the applications manager...

then I installed the extension packs for it...

installed win xp, enabling usb 2.0 support so the virtual OS would see USB devices on the host system...

once i started windows in vbox, it recognized the usb and magicjack did it's thing...

haven't tried any calls yet but i know if i call from my cell, the magicjack picks right up...

---

### Post by wep940 on 2011-03-14
Yes, it could always be run via a VM.  What we are talking about here is a native Linux set of drivers/apps to allow access without a VM.  It's what MagicJack has promised but not delivered.

---

### Post by saltsprung on 2011-11-09
The new magicjack plus

you can use it ***without*** a computer

with an ethernet splitter I guess...

[http://www.magicjack.com/plus-v05/](http://www.magicjack.com/plus-v05/)

and you can keep your old phone number

---

### Post by Forsiti on 2011-11-09
But, you can NOT upgrade your original magicJack to a magicJack Plus.  After a LONG text session with their "Live" customer support (computer generated help messages ???) I learned that the only thing you can do is order a magicJack Plus.  Therefore you lose your existing magicJack number and all services you have prepaid.
 
[FONT=Calibri][SIZE=2]Also, a4.8% “regulatory tax” applied to all orders, shipping and accessories.[/SIZE][/FONT]
 
Linus support:  "[FONT=Calibri]We still do not have the exact time frame for it but it will help if you can check our website from time to time."[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri]I like the telephone service provided bymagicJack, but their customer support is terrible !!!![/FONT]

---

### Post by kgingeri on 2011-11-09
Here's a chat I had with them/their computer...

[B]Please wait for a site operator to respond.
You are now chatting with 'Lira'
Your Issue ID for this chat is LTK5540142...X[/B]
**Lira**: Hello, how may I help you?
**Kgingeri**: Hi Lira, I see that Magicjack can now be used without a computer. Can I use my existing magicjack devices that way?
**Lira**: That is the magicJack plus device that does not need to plugged in to the computer.
**Kgingeri**: OK, can I upgrade mine then but keep the same numbers etc?
**Lira**: I'm glad that you're interested about our new product and I know how important it is to upgrade your current magicJack service to the new magicJack PLUS. I'm afraid to say this but magicJack cannot be upgraded to the new magicJack PLUS.
**Kgingeri**: So what are my options then?
**Lira**: Your option will be to purchase the magicjack plus device and that would cost you $69.95 with one year free service.
**Kgingeri**: What about my existing account? Do I forfeit these accounts? Can I keep the same numbers at least?
**Lira**: Yes, you can keep your existing account, you can use them both and you can also keep your numbers.
**Kgingeri**: ok thanks.
**Lira**: Is there anything else I may help you with today?
**Kgingeri**: no, that's all
...

@ saltsprung
> with an ethernet splitter I guess...

No they appear to be using a A/C to USB adaptor/charger for power at least.  
Not sure if a regular USB adaptor would work or not.  They may have some electronics in the adaptor to lock it to their MJ adaptor - not sure.

---

### Post by WinRiddance on 2012-02-08
Well, that last post is a little misleading though. To put it in proper context ...
The old MJ can't be upgraded to MJ PLUS because of the embedded hardware differences. YES, if you previously purchased additional years of service for the old device, you'll lose those just like I did. But in all fairness, for $30 bucks per year local including long distance, I don't really care. It's not pleasant, but a loss that's still easily made up by the savings and then some.

The $69.95 is only for the device plus a year of included service. However, additional years of service only cost $29.95 and that wasn't mentioned here. Last but not least, you do get to keep your old number. If you port an existing MJ number over to MJ PLUS there isn't even a porting fee. If you port other numbers the fee is $19.95 which is still cheaper than most other companies. We have two MJ PLUS devices and we don't use Windoze. They're plugged into our router and outlets.

YES, MagicJack support is the worst on this planet. I've been online since 1991 and their support sucks the pits. No phone, no email, strictly chat, often with people who don't really seem to know anything about the actual device themselves. Just reading a script which clearly shows their lack of knowledge if you ever have a real problem. BUT ... that's why you have search engines, an unofficial magicjack support forum, and a very nice FAQ section directly on the MJ site.
Again, for $30 bucks per year there really isn't anything to complain about when you consider the savings in your pocket.

.

---


---
title: "cursor on black desktop"
date: 2014-07-26
forum: New to Ubuntu
---

### Post by milty2012 on 2014-07-26
For about 4 days I have had the following issue - I leave my PC on 24/7 - each morning when I turn on my monitor I see a white arrow on a totally black screen. I can move the mouse - turn on caps lock, num lock, and scroll key lights but I cannot get to the Ubuntu desktop. The only way to fix this issue is to hold the power button to force a cold shutdown. I then leave the PC off for 30 seconds and power it back on. It seems to take longer than usual to fully boot back up. Ubuntu then works normally for the rest of the day - occasionally I may get one or two error messages - "Ubuntu has experienced a error". 

On a daily basis I check for new updates - I am up to date. 

Do you guys think a recent patch/update has caused this issue? Are others experiencing this behavior? 

Can I break out of this cursor/black screen somehow when it occurrs?  

Can I run any diagnostic? Check a log for errors? 

I appreciate any advice you guys can provide

Thanks....Milty

---

### Post by kira-yamato-2008 on 2014-07-26
Posting your display driver and system specs would be very helpful.  As a short-term possible fix I suggest shutting down when you're not using your computer.   Although it sounds like you may have a corrupt file somewhere. If you have SpinRite use it, otherwise you may have to reinstall the OS.

---

### Post by milty2012 on 2014-07-26
I am new to Ubuntu. How do I locate info on my display driver and system specs? What is SpinRite? How do I use it? 

Thanks...Milty

---

### Post by ibjsb4 on 2014-07-26
Not a fix, but something to try next time you get the black screen.  Press:
    
**Ctrl** + **Alt** + [B]F7

[/B]Also ..
I do not know how SpinRite is suppose to help, but to find your video, open a terminal and enter:
```
lspci | grep VGA
```
[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by milty2012 on 2014-07-26
My system properties:

  	 	 	 	   Ubuntu 14.04 LTS
 memory 2.0 GIB
 Processor Intel Pentium 4 CPU 2.80GHz x2
 Graphics Intel 945G x86/MMX/SSE2  
 Graphics per terminal  cmd lspci | grep VGA intel 82945G/GZ integrated graphics controller rev 02rev 02
 OS type 32-bit
 Disk 76.5 GB

---

### Post by kira-yamato-2008 on 2014-07-26
> **ibjsb4 said:**
> Also ..
I do not know how SpinRite is suppose to help,

For some reason, to my mind, it sounded like an issue with corrupted system files. Which can be a result of a hdd/ssd writing to bad sectors, or expanding drive corruption... Which might not be the case true.

> **milty2012 said:**
> I am new to Ubuntu. How do I locate info on my display driver and system specs? What is SpinRite? How do I use it? 

Thanks...Milty

SpinRite is a HDD/SSD Recovery and Maintenance tool, but since it's 89 dollars I won't link to it directly.  Although as ibjsb4 posted it might not be any use for you, because your problem is probably something else.

> **milty2012 said:**
> My system properties:

                        Ubuntu 14.04 LTS
 memory 2.0 GIB
 Processor Intel Pentium 4 CPU 2.80GHz x2
 Graphics Intel 945G x86/MMX/SSE2  
 Graphics per terminal  cmd lspci | grep VGA intel 82945G/GZ integrated graphics controller rev 02rev 02
 OS type 32-bit
 Disk 76.5 GB

Well aside from looking up specific drivers for your Intel Graphics... You might be having issues with Ubuntu being too demanding for your system, you might want to try Lubuntu or Xubuntu instead. They're both lower system requirement versions of Ubuntu. They can be found at lubuntu.net and xubuntu.org respectively. Others might have more useful suggestions for your issue though.

---

### Post by whitesmith on 2014-07-26
> **milty2012 said:**
> I am new to Ubuntu. How do I locate info on my display driver and system specs? What is SpinRite? How do I use it? 

Thanks...Milty

Please don't experiment with SpinRite. It is an expensive tool best used by experts. Evidently you are not in that category, since you had to ask what it is. The best way to destroy your system is to play around with stuff you don't fully understand. Begin by reading the two sources in my sig line. Be a patient student. Take your time learning or something will bite you. I speak from experience in that regard. The best of luck to you.

---

### Post by dave131 on 2014-07-26
I doubt anything is "bad".  Instead, look at your power settings and post them back here.  I suspect it's going to sleep or at least blanking the screen and not getting that restarted.

EDIT:  Also post back the results of:

lsmod

---

### Post by milty2012 on 2014-07-26
lsmod output:

bob@DGX620:~$ lsmod 
Module                  Size  Used by 
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342206  10 bnep,rfcomm 
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0 
ac97_bus               12642  1 snd_ac97_codec 
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm 
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_rawmidi            25135  1 snd_seq_midi 
i915                  705659  3 
dcdbas                 14448  0 
usblp                  18277  0 
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi 
snd_timer              28584  2 snd_pcm,snd_seq 
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi 
video                  18903  1 i915 
drm_kms_helper         47182  1 i915 
lpc_ich                16864  0 
soundcore              12600  1 snd 
drm                   244037  4 i915,drm_kms_helper 
serio_raw              13230  0 
i2c_algo_bit           13197  1 i915 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc 
mac_hid                13037  0 
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid 
psmouse                91329  0 
tg3                   152132  0 
ptp                    18445  1 tg3 
pps_core               18799  1 ptp 
bob@DGX620:~$ 

Power Settings: 

Suspend when inactive for = Don't suspend
Show battery in monitor bar = Never 


Thanks.....Milty

---

### Post by milty2012 on 2014-07-26
FYI - I downloaded via Ubuntu software a disktool terminal app - ran on disk drive - no errors detected. 

When I experience the cursor/black desktop behavior - I can hear the disk drive being accessed constantly and the disk drive light is on solid - don't know if this provides any clues.

Thanks....Milty

---

### Post by milty2012 on 2014-07-26
Are there any logs I can look at too check for errors - that may point to my cursor/black screen issue? or possible hardware or OS issues? 


Thanks...Milty

---

### Post by milty2012 on 2014-07-27
Are there any native OS or hardware diagnostic tools I can run? 

Thanks.....Milty

---

### Post by ibjsb4 on 2014-07-27
> Are there any logs I can look at too check for errors
This sounds like apport, try looking there.
/var/log/apport.log

Did you try ctrl, alt, f7?

---

### Post by milty2012 on 2014-07-27
Further observations - midday today - I was logged into Ubuntu running Google Chrome - walked away for 4 or 5 hours - on my return I am able to move the mouse cursor but OS is unresponsive or extremely slow to respond if at all. 

I ran a memory test and hard drive test on the PC successfully this morning. I'm trying to determine if I have a hardware or OS issue. Any advise on this post? 

Thanks....Milty

---

### Post by kira-yamato-2008 on 2014-07-27
It really sounds like your memory is filling up, or Ubuntu is running out of resources to run on.

I'm running a HP notebook that has the fallowing: 3GB Ram, AMD Turion X2 2.00 GHZ, nvidia GeForce 8200M G.
Since you have a similar setup you might find your system becomes more responsive and can endure long periods of being on with an LXDE based distro like Lubuntu, which is what I use.

At any rate Chrome might be the culprit as some of it's addons can cause trouble, you might want to eliminate some of them if you have a bunch of addons. Ideally if I were you I'd switch to FireFox though.

---

### Post by milty2012 on 2014-07-27
Interesting. I do have Firefox installed but also use Chrome. I will check Chrome addons. How do I switch to an LXDE based distro like Lubuntu? 

Thanks....Milty

---

### Post by kira-yamato-2008 on 2014-07-27
There should actually be a method built in to Ubuntu it self to switch Desktop Environments, I'm not sure how it works because I haven't actually used Ubuntu since 10.something. For Lubuntu you can go here: [http://lubuntu.net](http://lubuntu.net) you can run it off live disc/USB just like regular Ubuntu, and to save your files you may want to install it alongside Ubuntu.

*Edit: That's a bit of a ham-fisted approach. I'm not sure, but there might be a way to install Lubuntu from Ubuntu; however, I have absolutely no idea how it's done.*

---

### Post by dave131 on 2014-07-27
You could always just install lxde in ubuntu to get the desktop environment used in lubuntu.  If you use it and not the Unity desktop things would be a lot lighter, however, I still don't think that's the problem.  What's the size of your physical memory and what is your swap partition size?

---

### Post by kira-yamato-2008 on 2014-07-28
> **dave131 said:**
> You could always just install lxde in ubuntu to get the desktop environment used in lubuntu.  If you use it and not the Unity desktop things would be a lot lighter, however, I still don't think that's the problem.  What's the size of your physical memory and what is your swap partition size?

He said on the first page that his physical memory is 2 Gigs, so because swap should be at least double that so assume 4 gigs. When Lubuntu set up my system it made two swap partitions of equal size to my memory, I don't know if Ubuntu's standard Trusty Thar distro does that automatically though.

---

### Post by milty2012 on 2014-07-28
I  have two gig of memory. I don't know how to determine current swap size or number of swap partions. I believe I have installed Lubuntu desktop per earlier instructions but it looks the same as my previous desktop - is there a command I can run in Terminal to display current running desktop? Please advise

Thanks....Milty

---

### Post by MrSteve on 2014-07-28
install xscreensaver 
when you open xscreensaver it will give the option to stop the default screen saver deamon 
stop the default deamon 

then in startup set-up set xscreensaver to start on log on

name = xscreensaver
command = xscreensaver -nosplash

please try this as it sorted my black/blank screen problem ...

---

### Post by milty2012 on 2014-07-28
I did try ctrl, alt, f7?  No response.

I will check this log and reply back - /var/log/apport.log

Thanks....Milty

---

### Post by milty2012 on 2014-07-28
Steve, 

I will try this and reply back. I'm a newbie so it may take a bit of time to figure out.

Thanks...Milty

---

### Post by dave131 on 2014-07-28
> **kira-yamato-2008 said:**
> He said on the first page that his physical memory is 2 Gigs, so because swap should be at least double that so assume 4 gigs. When Lubuntu set up my system it made two swap partitions of equal size to my memory, I don't know if Ubuntu's standard Trusty Thar distro does that automatically though.

I don't believe the default created by the installer would be that, but I've never checked.  However, just a normal boot and going to a black screen with a blinking  cursor should not be from swap - at that point it could run without any  swap.

Also, the double the memory size plus a little for overhead has been for hibernating.  If you watch the forums, you'll notice people still have problems waking from hibernation.  This is due to the termendous numbers of configurations, drivers and hardware.  There is no one size fits all.  Systems with large amounts of memory don't necissarily need doulbe the size for swap - in fact most of the time, even for hibernation, it could be much smaller on such systems.

However, just a normal boot and going to a black screen with a blinking  cursor should not be from swap - at that point it could run without any  swap.  It could be a driver issue.  It could be something as simple as putting i915.modeset=0 or i915modeset=1 as a boot parameter.  It is using the 915 series driver - at least that shows in loaded modules output.  There have also been times when I've seen people change the "p15" part to match their particular chipset - in this case it would be "945" so the options might then be i945.modeset=0 or i945.modeset=1.  They might have to try one of those at a time to see which, if any, help.

If the user is trying to run a lot of multiple things all at one time, then swap may be an issue.    The only true way to know how much swap you need is by (1) wanting to hibernate (2) the number of processes running simultaneously and (3) running the system monitor under load and seeing how much swap is actually being used.

But again, if this is happening with just a normal boot, swap shouldn't be an issue.  At least that is my understanding.

Also, ctrl/alt/F7 is the desktop window, so it would still show exactly what you are seeing.  Instead, try ctrl/alt/F1 and see if you get a text screen asking for login.  If so, login with your normal userid and password (nothing shows on the screen as you enter you password - just type it and press enter).  Then enter:

EDIT:  I was incorrect in my original syntax, please do:

dmesg | tail -n 40

Look at those lines and see if you see anything about intel graphics, i915 or i945.  

Post back the output if you can.

---

### Post by milty2012 on 2014-07-28
apport.log is empty.

I will try alt ctrl f1 on next error occurance.

I setup the xcreensaver - it was already dis-abled when I checked it. its setup in startup now.

Here's content of command requested dmesg | tail -n 40  : 

```
bob@DGX620:~$ dmesg | tail -n 40
[   25.828218] Bluetooth: HCI socket layer initialized
[   25.828227] Bluetooth: L2CAP socket layer initialized
[   25.828243] Bluetooth: SCO socket layer initialized
[   25.845224] Bluetooth: RFCOMM TTY layer initialized
[   25.845251] Bluetooth: RFCOMM socket layer initialized
[   25.845267] Bluetooth: RFCOMM ver 1.11
[   26.169134] init: cups main process (624) killed by HUP signal
[   26.169176] init: cups main process ended, respawning
[   26.250006] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.250017] Bluetooth: BNEP filters: protocol multicast
[   26.250040] Bluetooth: BNEP socket layer initialized
[   29.748587] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.749306] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.293068] init: samba-ad-dc main process (681) terminated with status 1
[   31.334395] tg3 0000:02:00.0 eth0: Link is up at 100 Mbps, full duplex
[   31.334411] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
[   31.334444] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.260496] audit_printk_skb: 21 callbacks suppressed
[   34.260505] type=1400 audit(1406557187.275:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=772 comm="apparmor_parser"
[   34.260526] type=1400 audit(1406557187.275:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=772 comm="apparmor_parser"
[   34.260544] type=1400 audit(1406557187.275:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=772 comm="apparmor_parser"
[   34.261958] type=1400 audit(1406557187.275:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=772 comm="apparmor_parser"
[   34.261983] type=1400 audit(1406557187.275:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=772 comm="apparmor_parser"
[   34.262703] type=1400 audit(1406557187.275:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=772 comm="apparmor_parser"
[   34.269951] type=1400 audit(1406557187.283:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=771 comm="apparmor_parser"
[   34.269975] type=1400 audit(1406557187.283:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=771 comm="apparmor_parser"
[   34.270779] type=1400 audit(1406557187.283:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=771 comm="apparmor_parser"
[   34.271042] type=1400 audit(1406557187.283:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=777 comm="apparmor_parser"
[   38.569738] init: plymouth-upstart-bridge main process ended, respawning
[   38.628638] init: plymouth-upstart-bridge main process (1480) terminated with status 1
[   38.628679] init: plymouth-upstart-bridge main process ended, respawning
[   54.855888] audit_printk_skb: 135 callbacks suppressed
[   54.855899] type=1400 audit(1406557207.866:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2321 comm="apparmor_parser"
[   54.855920] type=1400 audit(1406557207.866:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2321 comm="apparmor_parser"
[   54.867825] type=1400 audit(1406557207.878:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2321 comm="apparmor_parser"
[   80.754351] init: plymouth-stop pre-start process (2798) terminated with status 1
[ 7238.147072] perf samples too long (2510 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[21289.963199] perf samples too long (5009 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[24505.305232] systemd-hostnamed[4650]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[25465.046019] systemd-hostnamed[4863]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
bob@DGX620:~$ 
```


Thanks....Milty

---

### Post by dave131 on 2014-07-28
You might also want to try:

dmesg | grep i9

This will show any lines with the driver mentioned.  There might be other error messages, etc., around those that might be worth looking at.

---

### Post by milty2012 on 2014-07-29
I installed Lubuntu this morning per a previous suggestion. All other fixes with Ubuntu did not work. One issue I have with Lubuntu is I can't print. I see the job hit the queue - leave the queue - but no printing. I have a HP Deskjet 1000 J110a. Any advice? 

Thanks....Milty

---

### Post by milty2012 on 2014-07-29
I installed a HP printer wizard and I am now printing. 

Another odd issue - I installed Google Chrome - when I launch it I can enter addresses in the URL but when I type in the search window it is blank. Any advice. 

Thanks....Milty

---

### Post by dave131 on 2014-07-29
> **milty2012 said:**
> I installed Lubuntu this morning per a previous suggestion. All other fixes with Ubuntu did not work. One issue I have with Lubuntu is I can't print. I see the job hit the queue - leave the queue - but no printing. I have a HP Deskjet 1000 J110a. Any advice? 

Thanks....Milty

Just installing the lxde desktop manager and logging in to it as I mentioned earlier would have done the same for you. While lubuntu is lighter, I'm sure the problems you were having were with trying to run the default unity desktop.  lxde is the same desktop manager as in lubuntu.

---

### Post by egeezer on 2014-07-29
First guess: your graphics are not adequate to handle what full Ubuntu requires.  But you might find out if you have a chance by trying isbjsb4's suggestion: when the black screen with cursor shows up, press Ctrl-Alt-F7, and if that doesn''t work, try Ctrl-Alt-F1.  If that last one works, it will give you a terminal-style login line.

---

### Post by dave131 on 2014-07-29
> **egeezer said:**
> First guess: your graphics are not adequate to handle what full Ubuntu requires.  But you might find out if you have a chance by trying isbjsb4's suggestion: when the black screen with cursor shows up, press Ctrl-Alt-F7, and if that doesn''t work, try Ctrl-Alt-F1.  If that last one works, it will give you a terminal-style login line.

Already been covered in the thread.  Keep in mind Ctrl/alt/F7 is the desktop x window, so you should have no change.  Ctrl/Alt/F1 was already asked for but the op chose to install lubuntu instead.  I suspected it was the video card, hence why I wanted some of the information from them, and also why I suggested installing lxde earlier.

---


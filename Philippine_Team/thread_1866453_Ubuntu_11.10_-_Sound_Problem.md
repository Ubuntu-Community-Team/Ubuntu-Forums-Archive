---
title: "Ubuntu 11.10 - Sound Problem"
date: 2011-10-21
forum: Philippine Team
---

### Post by SHENGTON on 2011-10-21
Hello guys, good evening po. :)

I got a problem with my sound here in my laptop. I'm using Ubuntu 11.10, I already upgraded the Ubuntu 11.10 using this command "sudo apt-fast upgrade" and restarted it. Ang problema ko ngayon ay, if magplay po ako ng musics and movies wala akong maririnig na sound. Same with Facebook and Youtube videos wala ring sound. Even if sa pag-open ng Ubuntu 11.10 wala ring sound. Ang model po ng laptop ko ay "Presario CQ61-105EE" and ang Linux kernel ay "Linux 3.0.0-12-generic(i686)". 

Just tell me kung ano pa yong mga kailagang ipost. Hope matutulongan niyo po ako. Salamat po at God bless! :)

---

### Post by Script Warlock on 2011-10-21
> **SHENGTON said:**
> Hello guys, good evening po. :)

I got a problem with my sound here in my laptop. I'm using Ubuntu 11.10, I already upgraded the Ubuntu 11.10 using this command "sudo apt-fast upgrade" and restarted it. Ang problema ko ngayon ay, if magplay po ako ng musics and movies wala akong maririnig na sound. Same with Facebook and Youtube videos wala ring sound. Even if sa pag-open ng Ubuntu 11.10 wala ring sound. Ang model po ng laptop ko ay "Presario CQ61-105EE" and ang Linux kernel ay "Linux 3.0.0-12-generic(i686)". 

Just tell me kung ano pa yong mga kailagang ipost. Hope matutulongan niyo po ako. Salamat po at God bless! :)

[this]("http://ubuntuforums.org/showthread.php?t=1179999") might help...

---

### Post by SHENGTON on 2011-10-21
Hello Script Warlock, good morning. :)

Salamat po sa pagtulong. Inapply ko yong sinabi doon sa isang thread, after restarting my computer still wala pa ring sound. Ito yong inapply ko:

> **Valpskott said:**
> I have a Compaq Presario CQ61-225EO and I had sound through headphone jack but not from speakers.
The following solution fixed my audio problem in both Jaunty and Karmic Koala.

> sudo gedit /etc/modprobe.d/alsa-base.conf 			 		

At the end of the file, add these lines
[QUOTE]options snd slots=snd-hda-intel
  options snd-hda-intel model=hp-hdx
  alias snd-card-0 snd-hda-intel
  options snd-hda-intel enable_msi=1[/QUOTE]

At ito rin nagtry rin ako nito but still wala pa rin: [LINK]("http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667")
> **drbongo said:**
> ICEBOX - I had exactly the same problem! But I  have just fixed it after several hours of pulling my hair out. I had  tried everything I could think of, as well as lots of solutions other  people had suggested, including installing the latest version if Alsa  from source etc. Nothing worked, until I found these four lines on  another forum. Simply paste them at the end of  /etc/modules.d/alsa-base.conf and save it.

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

Restart the computer and you should get sound out of the speakers as well as the headphone socket.

drbongo

Just tell mo po kung ano po yong gusto niyong ipost ko para ma supply ko agad. Salamat and God bless po! :)

---

### Post by SHENGTON on 2011-10-21
And kahit gagamit ako ng headphone wala rin akong naririnig na sound. Salamat and God bless po! :)

---

### Post by Script Warlock on 2011-10-22
ok do the [basic]("https://help.ubuntu.com/community/SoundTroubleshooting")

kung negative pa rin ang result fire up the live usb of 11.10 and check if the sound really works.

---

### Post by SHENGTON on 2011-10-23
[FONT=Arial][SIZE=2]Hello po Script Warlock, good morning. :)

**Here are the results:**
1. Is your volume turned all the way down, or is your speaker muted?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Wala pa ring sound.
[/SIZE][/FONT]
[FONT=Arial][SIZE=2] 2. Can you play a sound that is known to always play correctly?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Wala pa ring sound.[/SIZE][/FONT]

[FONT=Arial][SIZE=2] 3. Can another user play one of these "known-good" sounds?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Wala pa ring sound.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT][FONT=Arial][SIZE=2]4. Is the system recognizing your sound card?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:**[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/SIZE][/FONT]
[FONT=Arial][SIZE=2] 5. Do you have the sound modules installed?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Displayed a large list of items.[/SIZE][/FONT]

[FONT=Arial][SIZE=2] 6. Is the sound card physically installed and recognized by your hardware?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:**[/SIZE][/FONT]
[FONT=Arial][SIZE=2]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3069
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 94500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]7. Is my sound card supported by the Ubuntu sound system?[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Andoon sa listahan ng ALSA, supported yong sound card ko.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]8. Manual Installation[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Wala pa ring sound.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]9. Kung negative pa rin ang result fire up the Live USB of 11.10 and check if the sound really works.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]**Result:** Meron nang sounds.[/SIZE][/FONT]
[FONT=Arial][SIZE=2]
[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Ang ibig bang sabihin nito Script Warlock that I have to reformat fully and reinstall the Ubuntu 11.10? Kasi inupgrade ko lang ito, hindi ko kasi nireformat inupgrade ko lang. Salamat at God bless po! :)
[/SIZE][/FONT]

---

### Post by Script Warlock on 2011-10-24
not reformat just check the audio with live cd/usb.

---

### Post by Script Warlock on 2011-10-25
just to make sure before we break your ubuntu(joke), may i know the output of this.. 

cat /proc/asound/version

check any muted channel in alsamixer

some test tones
     speaker-test -c 2
     canberra-gtk-play --file=/usr/share/sounds/ubuntu/stereo/desktop-login.ogg   
     
do some reloading with /sbin/alsa reload or force-reload then test tone, any luck?

---

### Post by JCyberinux on 2011-10-27
this happens to me before i upgrade om ubuntu maverick on the other pc, then suddenly sounds doesn't working... :( but on the live cd and the usb live, it works perfectly... the only possible i can think of was to again to backup the disk and format with new release of ubuntu. :D

---

### Post by ysNoi on 2011-11-04
My upgrade from Natty to Oneiric has no problem on sound with my Presario CQ40...

Bro Shengton, double check mo sound settings then try mo work around sa Hardware -> Profile and test the sound output of left to right speakers.

In my case, working ang profile "Analog Stereo Duplex" and "Analog Stereo Output".

HTH...

---


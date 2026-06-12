---
title: "Still can't hear audio after upgrade"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by iamsamami on 2012-10-01
Can't hear audio after upgrading to U-10.04.
If I restart in original install I can still hear audio.
????

Recently have installed other softwares thinking something might turn the speaker on, but it still doesn't have sound.

And YES the audio level is on (not mute) and all the way up.

Can I do a compare between the two different installations to see which file might be being looked for?

---

### Post by iamsamami on 2012-10-01
I just installed lshw-gtk and got this following info:

Audio device
/0/100/1b

product: N10/ICH 7 Family High Definition Audio Controller [8086:27D8]
vendor: Intel Corporation [8086]
bus info: pci@0000:00:1b.0
version: 02
width: 64 bits
clock: 33MHz
capabilities:
    Power Management,
    Message Signalled Interrupts,
    PCI Express,
    bus mastering,
    PCI capabilities listing
configuration:
    driver: HDA Intel
    latency: 0
resources:
    irq: 16
    memory: fe938000-fe93bfff

What other info would be helpful???
Thanks,
IamSamAmI

---

### Post by houseworkshy on 2012-10-01
You could try a live session with the 10.04 and try out something free codex, an .ogv video for example.  There are a lot of free ogv's here [http://archive.org/details/movies](http://archive.org/details/movies) so you could bung something on the hard drive before doing the live session test.
For complete hardware spec's you could install "sysinfo" which is in the standard repositories.  Any of the gui installers or "sudo apt-get install sysinfo" followed by your password when asked, in the terminal will do that.  Once installed, open it, it will put a link in your Applications>System tools menu, and choose "save file" which will create a text file with detailed hardware specs.  Its a useful program which reduces posting system spec's to an attachment, worth having anyway.

As to fixing.  It would be worth hearing if audio is absent when the hardware drivers are installed and enabled or not enabled.  So System>Administration>Hardware drivers will take you there.  Make a note of which drivers are available too.  Sometimes one will work when others don't, if you are given a choice that is, for some cards there is only one.
Also try putting in the "restricted extras"; a meta package which has the non free codex, flash, some archiving tools  etc.  So System>Administration>Synaptic Package manager.   Find "ubuntu-restricted-extras" using the search and install it.  

After that you could be looking at some issue to do with pulse audio but check the above before diving into that.  Could be that "hardware drivers" or restricted extras just fixes it.

---

### Post by iamsamami on 2012-10-01
sysinfo gave me less info than lshw-gtk;
Hardware drivers, only showed there's Broadcom drivers being used, but showed absolutely nothing else.
ubuntu-restricted-extras, didn't do anything either.
Typed "pulse audio" in Synaptic, that posted a few files; i tried a couple that appeared related. Still nada!

Anybody else, anything else???

again, thanks,
IamSamAmI

---


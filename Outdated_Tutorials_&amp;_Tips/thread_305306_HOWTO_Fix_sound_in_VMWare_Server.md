---
title: "HOWTO: Fix sound in VMWare Server"
date: 2006-11-23
forum: Outdated Tutorials &amp; Tips
---

### Post by MonkeyWrench32 on 2006-11-23
What worked for me (and probably should for a lot of users) is to replace **libsdl1.2debian-alsa** with **libsdl1.2debian-all**.  This enables OSS support which VMWare seems to need.

To do the replacement, just copy and paste this line into a terminal:
```
sudo aptitude install libsdl1.2debian-all
```

Sound now works perfectly for me in Ubuntu and XP Pro on VMWare, including sound mixing.  Give it a go and see if it works for you!

---

### Post by ajm2005 on 2006-11-25
:)

---

### Post by MonkeyWrench32 on 2006-11-25
Excellent!  I'm glad this worked for another user.  :)

---

### Post by RikBlankestijn on 2006-12-03
I'm using alsa-oss for soundmixing and now I've also installed the package you mentioned as well but I still do not have sound in vmware. Which sound-adapter device did you specify in your vmware preferences?

---

### Post by MonkeyWrench32 on 2006-12-03
> **RikBlankestijn said:**
> I'm using alsa-oss for soundmixing and now I've also installed the package you mentioned as well but I still do not have sound in vmware. Which sound-adapter device did you specify in your vmware preferences?
I have a DViCO HDTV card that Ubuntu put at /dev/dsp and my Sound Blaster Audigy 2 is at /dev/dsp1.  I found this info in the Device Manager (System -> Administration -> Device Manager).  I found my audio card on the left side and went through the "ADC Capture/Standard PCM Playback OSS PCM Device" entries while having the "Advanced" tab opened on the right side.  I went through the list until I saw an "oss.device_file" entry on the right side with /dev/dsp1 in it.  So I manually edited the VMWare settings for my sound card and pointed it to /dev/dsp1.  Presto.

Try to find the same /dev/dspX device for your sound card as I did and you should be good to go.

---

### Post by XandR on 2006-12-22
That's not the only way...
a faster way is :
```
apt-get install alsa-oss
```
and then  (If y our vmware doesn't detect it):
```
aoss vmware
```
so you wont uninstall your  libsdl1.2debian-alsa

---

### Post by talen.quickblade on 2006-12-28
I'm on a Dell Latidude running dapper and at first attempt neither of these work arounds has proved successful.  Sound is running fine in GNOME, just cant seem to get any more that a system beep from the guest OS (WinXP) running locally through VMWare server.

further when connected the sound device at startup (/dev/dsp) VMWare tells me it believes the device to be in use by another service.

---

### Post by Scotty562 on 2007-02-23
THANK YOU! :) :) :) 

> **MonkeyWrench32 said:**
> What worked for me (and probably should for a lot of users) is to replace **libsdl1.2debian-alsa** with **libsdl1.2debian-all**.  This enables OSS support which VMWare seems to need.

To do the replacement, just copy and paste this line into a terminal:
```
sudo aptitude install libsdl1.2debian-all
```

Sound now works perfectly for me in Ubuntu and XP Pro on VMWare, including sound mixing.  Give it a go and see if it works for you!

---

### Post by phenest on 2007-03-18
I've tried this and other solutions to this problem, but it doesn't work completely:

If a sound has played in the host Kubuntu OS, the guest XP OS *NEVER* plays anything and I only get the VMWare sound error. If I start the guest OS first, wait for the Windows Start music, and then play something in the host Kubuntu OS, VMWare gives its sound error message for the rest of the time the guest OS is running.

Me no understand.

---

### Post by mathewc on 2008-03-31
Hello all,

So before I give this a shot, how do I undo: sudo aptitude install libsdl1.2debian-all

?

Thanks,
-Mathew

---

### Post by afallenhope on 2008-06-13
> **mathewc said:**
> Hello all,

So before I give this a shot, how do I undo: sudo aptitude install libsdl1.2debian-all

?

Thanks,
-Mathew


To undo it: sudo aptitude remove --purge libsdl1.2debian-all

---

### Post by Phkillah on 2008-09-14
I can't manage to work with Ubuntu 8.04 (64bits with OSS) and VMWare v6 with XP inside...

:(

---

### Post by freonchill on 2008-09-23
i installed alsa-oss via synpatic

and vmware server 2.0 beta now says that my sound is working
i was surprised that it worked immediately especially since vmware 2.0 beta is webpage based (e.g. there is no program)

now just to figure out how to get the driver for windows 98se
(guess ill try reinstalling vmware tools)

edit: scratch that - alsa-oss is not working after actually got driver installed in the client os
the interface is for vmware not working

---

### Post by freonchill on 2008-09-24
might i refer everyone to the following post for further information in regards to any problems w/ audio in vmware

[http://ubuntuforums.org/showthread.php?t=331175&page=8](http://ubuntuforums.org/showthread.php?t=331175&page=8)

---

### Post by Paradigm_Complex on 2008-10-09
I got it to work without having to install any new libraries.  For anyone else who's having trouble:

I realized that, for whatever reason, I didn't have anything at /dev/dsp.  I did a quick

$ find /dev -name dsp

And found a file at /dev/.static/dev/dsp

When I added a sound device to the XP VM in VMware, rather than letting it automatically find a sound device I typed in that address and it's been working beautifully since.

---

### Post by Cato2 on 2009-02-19
I used essentially the method pointed to by freonchill above, i.e. [http://ubuntuforums.org/showthread.php?t=331175](http://ubuntuforums.org/showthread.php?t=331175).  You don't need to set the sticky bit on the library though.

I also had to tell VMware to use /dev/dsp explicitly as it was not autodetecting (I have several sound devices in the host Ubuntu 7.10).  The .vmx file looks like this:

```
sound.autodetect = "FALSE"
sound.fileName = "/dev/dsp"
sound.present = "TRUE"
sound.allowGuestConnectionControl = "FALSE"
sound.pciSlotNumber = "34"

```

I now have sound working fine with Windows XP in a VM.

One other issue I had was that the Add Hardware Wizard would hang with a 'loading' message - hence I had to edit the .vmx file directly.

---

### Post by sunbear on 2009-02-23
After much struggling and trying various magic incantations from various threads, what fixed the sound for me was to upgrade my virtual machine.

Originally I was using a virtual machine with Virtual Hardware Version 4. Upgrading moved me to Virtual Hardware Version 7. After a reboot of the Windows guest, sound immediately started working.

My setup is:
VMWare Server 2.0.0 Build 122956
Host: Ubuntu 8.10 64-bit
Guest: Windows XP Professional SP2

The only problem was that windows asked me to reactivate, but this wasn't a big deal since when I selected to activate via the web, everything proceeded fine without even any need to enter any activation codes or anything.

---

### Post by NimoTh on 2009-04-12
> **sunbear said:**
> After much struggling and trying various magic incantations from various threads, what fixed the sound for me was to upgrade my virtual machine.

Originally I was using a virtual machine with Virtual Hardware Version 4. Upgrading moved me to Virtual Hardware Version 7. After a reboot of the Windows guest, sound immediately started working.

My setup is:
VMWare Server 2.0.0 Build 122956
Host: Ubuntu 8.10 64-bit
Guest: Windows XP Professional SP2


That sounds most interesting, sunbear! Finally someone who also has the new version 7 with vmware server 2. So now I'm only wondering why it works out of the box for you but not for me. I'm on the exact same VMWare Server build but running Ubuntu 8.10 32-bit and Windows XP SP3. I don't suppose that difference makes a difference, though.

May I ask what you have configured for your sound device? Could you also post the relevant parts from your config file? (Now comfortable to be found in the advanced virtual machine configuration settings.)

Thanks a bunch

Martin

---

### Post by supergumby on 2009-04-24
For those who might be interested, I had the same issue, no sound within my XP SP3 VM. I reinstalled my ubuntu machine recently with 8.04.2 (amd64) and installed VMware-server-2.0.1-156745.x86_64, and replacing auto detect with /dev/dsp did the trick.

---

### Post by cmcginty on 2009-04-30
Can anyone suggest a fix for this with Jaunty? I have tried most of the suggestions, but nothing works.

Is there any debug output that Vmware produces? How do I access it?

---

### Post by sunbear on 2009-08-27
> **NimoTh said:**
> That sounds most interesting, sunbear! Finally someone who also has the new version 7 with vmware server 2. So now I'm only wondering why it works out of the box for you but not for me. I'm on the exact same VMWare Server build but running Ubuntu 8.10 32-bit and Windows XP SP3. I don't suppose that difference makes a difference, though.

May I ask what you have configured for your sound device? Could you also post the relevant parts from your config file? (Now comfortable to be found in the advanced virtual machine configuration settings.)

Thanks a bunch

Martin

Sorry, I wan't subscribed to this thread before so I didn't see your post.

Unfortunately the bad news is that after I recently applied some recent Ubuntu updates, my VMWare sound and keyboard mappings were broken once again. I'm now wrestling with the dreaded "Failed to open sound device /dev/dsp: Device or resource busy Virtual device sound will start disconnected." error message that I had before.

For what it's worth, the sound device that I was using was /dev/dsp. Some people mention using /dev/audio but that never worked in my case.
 
I'll let you know if I ever get it working again. In the meantime, please let me know if anyone has any suggestions. I'm wondering if it's worth upgrading to my VMWare Server build to 2.0.1 | 31 March 2009 | Build 156745.

Has anyone had any success with this version? I seem to remember having to patch files from the previous download before they were usable. Is this still the case, and if so, does anyone have a link to the patch instructions?

Thanks!

---

### Post by cmcginty on 2009-08-27
Hi, I fixed all my sound issues. Here is the command:

```
sudo apt-get install virtualbox-2.2
```


](*,)

---

### Post by NimoTh on 2009-08-28
Yes, that's what I did, too. Forget vmware. Virtualbox is much better.

---

### Post by sunbear on 2009-08-28
I have found a workaround for getting sound back in VMWare. I have to run
> sudo killall pulseaudio 

before launching my virtual machine. I don't really like this solution though, so I've started another thread to see if people can improve on it:
[http://ubuntuforums.org/showthread.php?p=7861663#post7861663](http://ubuntuforums.org/showthread.php?p=7861663#post7861663)

---

### Post by sunbear on 2009-08-29
> **aircondirect said:**
> [SIZE=2][FONT=Arial]**It is very easy to setup audio in the latest version of VMware Server**. The following steps will show you how this can be done.[/FONT][/SIZE]
[LIST=1]
[*][FONT=Arial]Launch VMware as root: [gksudo vmware][/FONT][FONT=Arial][/FONT]
[/LIST]

Are you using VMWare Server 2.0 (i.e. not VMWare Workstation or something else)? On my installation, this command doesn't seem to work. I just access the settings via a URL:
http://localhost:8222/ui/#{e:%22VirtualMachine|128%22,w:{t:true,i:3}}


> **aircondirect said:**
> [SIZE=2][FONT=Arial]**It is very easy to setup audio in the latest version of VMware Server**. The following steps will show you how this can be done.[/FONT][/SIZE]
[LIST=1]
[*][FONT=Arial]Click “Edit virtual machine settings.[/FONT][FONT=Arial][/FONT]
[*][FONT=Arial]Under the Hardware tab click “+ Add”.[/FONT][FONT=Arial][/FONT]
[*][FONT=Arial]Choose “Sound Adapter” and click Next.[/FONT][FONT=Arial][/FONT]
[/LIST]

The web user interface that I see seems to have different names and options so I'm not sure that we are necessarily on the same page here. However, just for the hell of it I clicked on the "Add Hardware" link inside the "Commands" window. The "Sound Adapter" option is completely greyed out.

Can you at least confirm that we are talking apples and apples here? 
[LIST=1]
[*]What version of VMWare are you using?
[*]What version of Ubuntu?
[*]32-bit or 64-bit?
[*]Have you applied any additional tweaks above any beyond simply downloading VMWare server and running vmware-install.pl?
[/LIST]

I tend to think that this is not a configuration problem. If my VM did not already include Sound Hardware, then it wouldn't be possible play any sound from within VMWare. In my case, I can get sound, but only if I do
> killall pulseaudio
before launching my VM.

---


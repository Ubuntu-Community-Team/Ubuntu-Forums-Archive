---
title: "No sound: Acer Aspire 6920"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by blankfile1 on 2008-06-06
Hello everyone.

I recently got a new laptop, an Acer Aspire 6920. I installed 8.04 yesterday, only to find out that i could not get the sound running.

I (obviously) verified that my hardware was working beforehand, so that is a non-issue.

```
asoundconf list
Names of available sound cards:
Intel
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I made sure that nothing was muted in alsaconfig, as i have seen that was an issue in other threads. 

I have also read that quite a lot of people have trouble with this specific sound card. However, none of the fix i have seen worked so far. So, i thought i might have more luck by asking.

Thanks!

---

### Post by ibuclaw on 2008-06-06
Have you set all playback PulseAudio to ALSA in the Sound properties? ("**System>Preferences>Sound**" in the Gnome Menu).

Do you get anything from the beep test?


running alsamixer in the terminal will show the current volume level.
```
alsamixer
```
And running this command should produce a three clicking sounds from your speakers, if they have been detected properly..
```
for i in 1 2 3; do echo >/dev/dsp1; done
```

Regards
Iain

---

### Post by blankfile1 on 2008-06-06
I have made sure that every sound in alsamixer is both maxed and un-muted.

```
raphael@raphael-laptop:~$ sudo for i in 1 2 3; do echo >/dev/dsp1; done
bash: syntax error near unexpected token `do'
raphael@raphael-laptop:~$ for i in 1 2 3; do echo >/dev/dsp1; done
bash: /dev/dsp1: Permission denied
bash: /dev/dsp1: Permission denied
bash: /dev/dsp1: Permission denied

```

So no, not getting any sound, i find that quite strange to be honest.

---

### Post by ibuclaw on 2008-06-06
Interesting...
At first look, seems like the audio device module isn't turned on.

This will probably prove otherwise
```
ls -ld /dev/dsp*
```
If the device is shown (will be in yellow), can you post the output of this command.
```
groups
```

But while you are doing that. I will look into seeing if there is a way to enable it for you.

Regards
Iain

---

### Post by blankfile1 on 2008-06-06
```
raphael@raphael-laptop:~$ ls -ld /dev/dsp*
crw-rw----+ 1 root audio 14, 3 2008-06-06 13:32 /dev/dsp
raphael@raphael-laptop:~$ groups
raphael adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin pulse pulse-access pulse-rt

```

the /dev/dsp part is indeed shown in yellow.

---

### Post by ibuclaw on 2008-06-06
Ah, OK. It is there then (just wasn't under the name I was expecting).

So the proper command to test would be
```
for i in 1 2 3; do echo >/dev/dsp; done
```
then. (minus the "1").

After looking around a bit, the only thing I can suggest at the moment is do you have your backports and ubuntu modules installed for your current kernel version?
```
sudo apt-get install linux-backports-modules-$(uname -r) linux-ubuntu-modules-$(uname -r) linux-restricted-modules-$(uname -r)
```
After installing them, reboot.

Iain

---

### Post by blankfile1 on 2008-06-06
```
for i in 1 2 3; do echo >/dev/dsp; done
```
Works, but i do not hear any clicking, or any sound at all.

 Installed those 3 backport packages, rebooted, and still nothing.

---

### Post by ibuclaw on 2008-06-06
OK, the best option I've found so far is [here.]("http://ubuntuforums.org/showthread.php?t=747054&page=3")
Sorry about the wait. But sources are scarce.

First, check that this file is present:
```
test -s /lib/modules/$(uname -r)/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko && echo YES || echo NO
```
You should get the answer "**YES**" on screen.

If so, open up the alsa's modprobe config file:
```
gksu gedit /etc/modprobe.d/alsa-base
```
And add this line to the bottom:
> options snd-hda-intel model=mitac

Then the command
```
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel

```
To restart you device. (reboot may be required, but shouldn't be necessary).

[EDIT]
There is also an apparently fix at launchpad
[https://bugs.launchpad.net/ubuntu/+bug/210865](https://bugs.launchpad.net/ubuntu/+bug/210865)
Read and follow the instructions on the last post.


If it still isn't working, check out this [post here and give OSS4 a try]("http://ubuntuforums.org/showpost.php?p=4806206&postcount=25").
Apparently, using OSS4's drivers work much better than ALSA's with newer soundcards.

Also, if you do get them working, first thing I suggest before you try to test is that you turn the volumes down by half ;)
Just incase the sudden loud sound scares you.

Regards
Iain

---

### Post by blankfile1 on 2008-06-06
Adding the line 
> options snd-hda-intel model=mitac 
Did not work, so i went on and tried the launchpad fix. This one did not work either.

So i'm gonna go try the OSS4 method.By the way, thank you very much for your help, it is very much appreciated.

---

### Post by blankfile1 on 2008-06-06
I used the step-by-step instructions to install OSS4 found [HERE]("http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4").

And guess what? it WORKED! My precious sound is working now.

Thanks again for the help, greatly appreciated.

---

### Post by ibuclaw on 2008-06-06
Hey man, I'm glad you found it.

Well Done to you :popcorn:

Regards
Iain

---

### Post by emmerc on 2008-06-22
Hello blankfile1!! I am buying this Acer 6920-6621. And I am planning to wipe Vista out and then do a clean installation of Ubuntu 8.04 on it. I friend of mine bought it some weeks ago and has Ubuntu 8.04 running on it but has not configurated the built in mic and has not bothered trying with the sd card reader.

I would like to know if you have you gotten the webcam and the mic to work and how? What about the built-in sd card reader? I will appreciate your so kind replay!

---

### Post by 7raTEYdCql on 2008-06-22
I have Acer 5920, and had a similar problem initially.
This is how i solved it.


in terminal type alsamixer
then the surround option increase it.

That will solve your problem.

---

### Post by mendoh on 2008-07-22
> **blankfile1 said:**
> I used the step-by-step instructions to install OSS4 found [HERE]("http://ubuntuforums.org/showthread.php?t=780961&highlight=oss4").

And guess what? it WORKED! My precious sound is working now.

Thanks again for the help, greatly appreciated.

Blankfile, I have tried your suggestion with my Acer Aspire 8920 and it works...however, I only succeeded in having 2 (out of 5) speakers working at nearly half the volume level I get from VISTA, no matter volume controls are set to their maximum level.

Would you please tell me if you succeeded in having the full surround sound system working correctly and if so, how did you do that?

Thanks a lot in advance

---

### Post by ALxB on 2008-07-23
Hello tinivole, I was having the same problem with my Acer desktop.  Thanks to your first reply I have my sound working.  I do have a question though.  I set the first four boxes in sound to ALSA, should I do anything with the Default Mixer Tracks?  I don't even know if this thing has a mixer or how to check.  

Thanks, Al

---

### Post by blankfile1 on 2008-07-26
> **mendoh said:**
> Blankfile, I have tried your suggestion with my Acer Aspire 8920 and it works...however, I only succeeded in having 2 (out of 5) speakers working at nearly half the volume level I get from VISTA, no matter volume controls are set to their maximum level.

Would you please tell me if you succeeded in having the full surround sound system working correctly and if so, how did you do that?

Thanks a lot in advance

Sorry mendoh, i am still facing the same problem as you. The sound is incredibly low, even at maximum settings. I am still lurking to find a way around that, but no clue so far. I am positive that the surround is *NOT* working either. I am also experiencing some trouble with the headphones, which i suspect to be somewhat related.

I will update here when/if i find some way to fix those problems.

---

### Post by CJay554 on 2008-07-28
Im happy that you got your sound to work, and so have i through this post =]

but another problem, the volume control is a bit iffy (because we switched from the gnome standard alsa to OSS4) so i cant control my volume through the touch pad, or through keyboard shortcuts. Anyone have the same problem as me?


Webcam:  
The webcam works amazing in ubuntu, you will however have to install easycam2 (which u can find through google and will lead to one of ubuntu's helpful help sites.

The mic not so much on getting it to work yet (i havent really bothered)

I really hope one day ubuntu will have full support for this laptop because it is simply amazing, and i would hate to have to leave it in Microsoft's hands.

---

### Post by jansaell on 2008-07-29
I have had the same problem but on my ACER Aspire 8920 and found 2 ways of solving this. I have them listed on my blog at [http://jan.saell.org/blog/archives/30]("http://jan.saell.org/blog/archives/30").
In short:
Way 1 - Exactly as you desripbe, remove ALSA and install OSS4 - this works and gives sounds but i had problems with mics on that but playback was ok.

Way 2
[LIST=1]
[*]Upgrade to ALSA 1.0.17 - not totally sure that that's fully required
[*]Set model to acer-aspire in /etc/modprobe.d/alsa-base
[*]Download and compile hda-verb from [here]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2")
[*]Copy the compiled program to /usr/local/bin
[*]Run the command (prefably from /etc/rc.local so it will happend every bootup): /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
And you have to run that as root
[/LIST]
That should give you sound working.

---

### Post by alpho2k on 2009-02-13
I just created a blog in wich I will list all the problems I have with ubuntu on an acer aspire 6920.

[http://monespaceperso.org/blog-en](http://monespaceperso.org/blog-en)
	
Thank you to make a short visit :)

---


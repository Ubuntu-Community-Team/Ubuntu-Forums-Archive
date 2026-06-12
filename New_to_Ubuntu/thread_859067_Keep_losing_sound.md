---
title: "Keep losing sound"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by kdm on 2008-07-14
Hi all,

Can anyone help me with my problem with sound ?

At best, it appears as though my sound is shared between applications, i.e. if my web browser is using sound then I cannot use a music program such as Amarok in the background - it appears to be one or the other.

At other times however, I just appear to totally loose my sound completely.  I haven't changed anything, it just appears to stop without any explanation 

Anyone got any ideas ? 
Thanks

---

### Post by Paz13 on 2008-07-14
don't know about the sound, but my computer did that i couldn't use exile if i used amarok for some reason i went into the settings for sound and kept it all open and to defult that solved it i could use sound on two programs

---

### Post by kdm on 2008-07-14
Tried changing the settings but it doesn't appear to help, although I am fairly certain that if I restart it will start to work again - for a while anyway - Until I try and use sound in 2 programs again !

---

### Post by kdm on 2008-07-14
Is there even any command I could throw through the terminal in order to 'reset' the sound without rebooting ?

---

### Post by insub2 on 2008-07-14
I had the same problem (at least in symptoms) and I solved it (I hope) by switching all my options to ALSA.

Hope this helps you.

---

### Post by nkri on 2008-07-14
Are you running a dual boot between Windows and Ubuntu?  If so, make sure that the Windows sound is not muted before shutting down/hibernating.  I'm not quite sure why, but this always seems to work for me:).

Good luck!
-nkri

---

### Post by kdm on 2008-07-14
Hi, 

Thanks for the replies.

It is a dual boot between *Ubuntu* & *Microsoft Faulty*,  oops I mean *Microsoft Vista*, but the sound was working when I first started up, so I think I can discount that possibility.

I have set all settings to ALSA and the sound is back :)
Thanks !

---

### Post by hellzkeeper1216 on 2008-07-14
how do you switch all you're settings to alsa.. sorry newb question..

---

### Post by nkri on 2008-07-14
> **hellzkeeper1216 said:**
> how do you switch all you're settings to alsa.. sorry newb question..

Go to System>Preferences>Sound.

There will be a lot of drop-down menus, and most probably say "Autodetect."

Click them to see all options and select ALSA for each one.

Good luck!
-nkri

---

### Post by appi2012 on 2008-07-14
you might want to mark this as [solved]

---

### Post by kdm on 2008-07-14
> **appi2012 said:**
> you might want to mark this as [solved]

Unfortunately it is not !

Just tried to play some video in Firefox, and although all my settings are allo still set to ALSA and I can hear the "Test Sound," the sound in my browser will not play :(

---

### Post by kdm on 2008-07-14
Somebody ?

Anybody ?


Oh come on its simple stuff like this which weakens ones resolve not to rejoin the darkside ! :(

---

### Post by johnswb on 2008-07-14
I agree, I'm trying to stay away from the Federation (The Dark Side), but now I'm getting the same thing in my browser (Mozilla Firefox 3.0).  All was working Friday and today I get nothing.  If I play an MP3 or a AVI I can hear the audio just fine.  It's only in Firefox that I can not.

---

### Post by johnswb on 2008-07-15
Today all is good... Don't know why?  Maybe after one of the latest patches?  I'm running Ubuntu 8.04 

uname -a
Linux meditor 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by ender1598 on 2008-07-16
I've got this problem too.  I've got ALSA selected in the sound manager and at any time I can hit test and hear something.  But I'll have a movie open in a web browser and when I try to use Ventrilo it simply won't work.  So I close the browser down and then restart vent and the sound works.  But later I quit vent and go open up a browser and there is no sound.  I try to play an mp3 with a media player and it just refuses to start.  I assume I could just restart the computer and this'll go away temporarily....  but come on... this is Linux!!!  I shouldn't have this Windows type problems that only rebooting will solve.  

It seems like there's been a lot more wackiness since installing Hardy Heron too.  Anyone else have some suggestions?

---

### Post by kansasnoob on 2008-07-16
I just got done dealing with the same situation on a fresh install and found the following at:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

> Firefox/Flash and PulseAudio

Be Default, libflashplugin (Flash 9 support in Firefox) doesn't work properly with PulseAudio.

Update: libflashsupport is available in Hardy as a package via the synaptic package manager.

Go to logicalnetworking.net to download the libflashsupport .deb and install it:

wget [http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb](http://logicalnetworking.net/other/libflashsupport_1.0~2219-1_i386.deb)
sudo dpkg -i libflashsupport_1.0~2219-1_i386.deb

Restart Firefox to enable simultaneous audio output from flash and other sources (rhythmbox, totem, etc).

- OR -

Instead I found the files [WWW] [http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz](http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz) and [WWW] [http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.dsc](http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.dsc). --akaihola

Note: You can download and compile it by doing:

wget [http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz](http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz)
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

Note: For Hardy64 users:

[http://ubuntuforums.org/showpost.php?p=4350045&postcount=12](http://ubuntuforums.org/showpost.php?p=4350045&postcount=12)



So far so good, but no guarantees!

BTW I used synaptic rather than .deb

---

### Post by kansasnoob on 2008-07-16
Sorry, lousy post, must be bedtime, but look here:

[ATTACH]77882[/ATTACH]

---

### Post by ender1598 on 2008-07-16
I've already got the libflashsupport installed.  I think I did that the last time I searched the forums trying to fix this sound problem.

---

### Post by johnswb on 2008-07-18
The problem came back again.... grrrrr

I just installed libflashsupport and now the sound is working in FireFox as of right now.

I've noticed before when I would play an MP3 or a local video and then go back and play a video on YouTube, my audio would stop working.  

I can say after installing libflashsupport my audio has not failed yet. 

Also, I do agree with "ender1598" this is Linux; why should I have to reboot to fix a problem?  Let's not start working like "The Federation" (aka DarkSide).

---

### Post by kdm on 2008-07-19
I too have installed libflashsupport, but alas to NO avail !

If it helps any, I get the following error message when I set everything to ALSA, have a 'no-sound' application running in the background and click on "TEST" under "SOUND PREFERENCES"...
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

---

### Post by kdm on 2008-07-19
I have no idea what I done, but I copied the following seemingly incomplete code Which it is claimed rebuilds ALSA....
>   sudo apt-get install alsa-source
  cd /usr/src/
  sudo tar xvjf alsa-driver.tar.bz2
  cd modules/alsa-driver/
  sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes
  cd alsa-kernel
And it appears to have done the trick ! I now for the first time ever have simultaneous sound in Firefox & Amarok !!!:)

Did this work for anyone else ?

BTW what sound cards are you using?
Is it a 82801H (ICH8 Family) controller by any chance ?

---

### Post by kdm on 2008-07-19
> And it appears to have done the trick !

Scratch that !

The sound has gone again !!!:confused:

---

### Post by johnswb on 2008-07-22
I guess I'm lucky this time.  My audio is still working in Fire Fox.  My browser now crashes of and on when I try and pay a video or anything with audio.  :confused:

---

### Post by kdm on 2008-07-31
Does no-one even have a work-around for this problem, I still have no sound !:(

---

### Post by ender1598 on 2008-08-07
I just had it happen again.  Suddenly my mp3s won't play and there's no sound.  I really hate these intermittant type bugs that are such a pain to troubleshoot. :(

---

### Post by marcordenis on 2008-08-07
I don't know if the workaround (last post) in this thread [http://ubuntuforums.org/showthread.php?t=862209](http://ubuntuforums.org/showthread.php?t=862209) helps you, but it's the way I fixed my problem, and now I can have Firefox, Amarok and VLC all playing at the same time... not sure if it's very safe, but it worked for me.....

---

### Post by donkeyX on 2008-08-09
Good one guys, the libflashsupport also fixed my problems with flash audio ;)

Cheers Dave

---

### Post by Crafty Kisses on 2008-08-09
That is super weird, post the following output:
```
lspci
```

---

### Post by airencracken on 2008-08-10
I have the same issue. Only one audio source will work at one given time. This seems to be true even if one is paused (Amarok and Firefox). Its as if one program lords over the inputs.

---

### Post by batasrki on 2008-08-13
> **airencracken said:**
> I have the same issue. Only one audio source will work at one given time. This seems to be true even if one is paused (Amarok and Firefox). Its as if one program lords over the inputs.

I know how you feel. I lived with that problem for a month or two. I fixed it with the libflashsupport installation and restart of both Firefox and Opera.

I, however, used **sudo apt-get install libflashsupport** on the command line as opposed to the method outlined on the first page of this thread

---


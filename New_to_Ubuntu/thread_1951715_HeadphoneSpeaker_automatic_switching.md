---
title: "Headphone/Speaker automatic switching"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by barneyjoseph on 2012-04-03
Hi,

I am an absolute newbie to Ubuntu. Is there a way that in Ubuntu Maverick that I could just plug in my headphones in and the speakers automatically get cut off and the headphones come on? Also when the headphones are unplugged that the speakers would come back on?

I have followed many tutorials and troubleshooting steps that instruct me to reinstall alsa and remove pulse. The only thing I can do to enjoy like a normal human is to go into "**pavucontrol**" and set the output to "**Analog** **headphones**" for the speakers to cut off and the headphones to play the music. Once I'm done I have to set the output back to "**Analog** **Output**" in "**pavucontrol**". Nothing seems to be muted in the **alsamixer**. 

Please help me. 

Thanks,
Barney.

---

### Post by flurospar on 2012-04-03
Don't know whether this will work, but have you tried running dpkg-reconfigure on the packages of pulseaudio and alsamixer (you need sudo)?

---

### Post by rgreener25 on 2012-04-03
you should try running these commands at terminal

```
sudo dpkg-reconfigure pulseaudio
```

then when done

```
sudo dpkg-reconfigure alsamixer
```

---

### Post by rgreener25 on 2012-04-03
it worked?

---

### Post by barneyjoseph on 2012-04-04
Hi,

Sorry for the delay in replying. It didn't work. It says that alsamixer is not installed. But I have it installed. It somehow doesn't recognise it.

```

sudo dpkg-reconfigure pulseaudio
[sudo] password for barney: 
 * PulseAudio configured for per-user sessions
 * PulseAudio configured for per-user sessions

sudo dpkg-reconfigure alsamixer
Package `alsamixer' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: alsamixer is not installed

```I still have to go to pavucontrol to use the headphones.

Thanks for replying so soon guys :)

[EDIT]
If you are interested, this is the troubleshooting that I followed: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
I followed it till step7!
[]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

---


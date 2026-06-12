---
title: "what exactly do I do here?"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by fredfelter on 2008-08-31
I am still trying to get my sound recording working. This is an excerpt from a link on adjusting PulseAudio for Skype to achieve that:

   ¨Firstly, add these lines:

   default-fragments = 8
   default-fragment-size-msec = 5

   at the end of "/etc/pulse/daemon.conf"

   Then, edit "~/.asoundrc" and add the following lines if they do not  exist:

   pcm.pulse { type pulse }
   ctl.pulse { type pulse }¨

My problem:
1) I pasted the /etc/pulse... into Terminal but got ¨permission denied¨, even as root user. What is that about? Same with ~/ .asoundrc.

Thanks

---

### Post by billgoldberg on 2008-08-31
> **fredfelter said:**
> I am still trying to get my sound recording working. This is an excerpt from a link on adjusting PulseAudio for Skype to achieve that:

   ¨Firstly, add these lines:

   default-fragments = 8
   default-fragment-size-msec = 5

   at the end of "/etc/pulse/daemon.conf"

   Then, edit "~/.asoundrc" and add the following lines if they do not  exist:

   pcm.pulse { type pulse }
   ctl.pulse { type pulse }¨

My problem:
1) I pasted the /etc/pulse... into Terminal but got ¨permission denied¨, even as root user. What is that about? Same with ~/ .asoundrc.

Thanks

Not really an answer to your question, but something else you can try.

Try using ALSA instead of PulseAudio. It might work right away.

You can change to ALSA in the "system -> preferences -> sound" dialog.

---

### Post by Vadi on 2008-09-02
Try doing alt+f2, "gksudo gedit /etc/pulse/daemon.conf". Are you able to edit and save the file fine now?

---

### Post by kostkon on 2008-09-02
> **fredfelter said:**
> I am still trying to get my sound recording working. This is an excerpt from a link on adjusting PulseAudio for Skype to achieve that:

   ¨Firstly, add these lines:

   default-fragments = 8
   default-fragment-size-msec = 5

   at the end of "/etc/pulse/daemon.conf"

   Then, edit "~/.asoundrc" and add the following lines if they do not  exist:

   pcm.pulse { type pulse }
   ctl.pulse { type pulse }¨

My problem:
1) I pasted the /etc/pulse... into Terminal but got ¨permission denied¨, even as root user. What is that about? Same with ~/ .asoundrc.

Thanks
Please follow this [how-to]("http://ubuntuforums.org/showthread.php?t=789578") and you will be fine.

*~/.filename* means a hidden file/folder in your home folder. *~/* means your home folder. Thus, you don't need to use *sudo*.

---

### Post by fredfelter on 2008-09-03
Thanks for the replies.
I feel that I'm so close but still no recorded sound in either Sound Recorder or Skype. 

Here are my settings:

Skype > audio devices > sound card, pulse pulse. Test sound works. Test call results in hearing the call, waiting while I talk but a quick hangup after no recorded sound.

System > Pref > Sound Pref > auto, auto, auto, ALSA, sound card (Alsa mixer)

Vol Control Pref > sound card (alsa mixer)

Vol Control > Open > recording tab > Capture is the only control, is all the way up and nothing is in red.

Any further ideas? Thanks again.

---

### Post by whitethorn on 2008-09-03
I don't know if this helps much.  I'm not sure, but I think skype doesn't work with pulse.  

[http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype)

Well according to what ur doing it should work.  If it doesn't you could try starting skype from the terminal with

```
pasuspender skype
```

You'd have to change your settings for sound in and sound out to directly use your soundcard instead of the pulse server. The only problem with this is you won't be able to use other applications that need sound. There are a couple different workarounds on the website maybe one will work for you...

---


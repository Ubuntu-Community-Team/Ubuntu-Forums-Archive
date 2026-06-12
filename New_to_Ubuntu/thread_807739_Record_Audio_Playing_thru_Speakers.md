---
title: "Record Audio Playing thru Speakers"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by onthefence on 2008-05-26
Does anyone know of a program that can record the audio that you are hearing out of your speakers? Does this require special soundcard or drivers?

---

### Post by iaculallad on 2008-05-26
> **onthefence said:**
> Does anyone know of a program that can record the audio that you are hearing out of your speakers? Does this require special soundcard or drivers?

All you need is the "Sound Recorder" (Applications->Sound and Video) application that comes along with Ubuntu, and the speaker cable (which should have both "male" jack) that could be plugged in your Sound Card'saudio-out (colored green) to your Sound Card's audio-in plug (colored blue). Loop-back style.

---

### Post by cwgatling on 2008-05-26
Audacity will do it. Just select 'Stereo Mix' in the dropdown box and record.

[http://audacity.sourceforge.net/help/faq?s=recording&i=streaming](http://audacity.sourceforge.net/help/faq?s=recording&i=streaming)

---

### Post by diablo75 on 2008-05-26
You just need to enable PCM capture in your volume control.  If you double-click on the sound volume icon at the top, you'll get a panel with levers on it.  Many options are not shown by default, so you should click Edit>Preferences, and then check off things like "PCM Capture" and anything else you see that you might want to have some control over later.  Once your done, the panel will have changed and should have a new "Recording" tab.  Look it over to see if your PCM capture levels are being shown, and to make sure the little microphone looking icon just below it is not crossed out.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=71619&stc=1&d=1211787740[/IMG]

So it looks like this ^

Hope that helps.

---

### Post by onthefence on 2008-05-26
> **cwgatling said:**
> Audacity will do it. Just select 'Stereo Mix' in the dropdown box and record.

[http://audacity.sourceforge.net/help/faq?s=recording&i=streaming](http://audacity.sourceforge.net/help/faq?s=recording&i=streaming)

Thanks, but now i fell blind. Where is the Stero Mix drop down?!?!

---

### Post by cwgatling on 2008-05-26
As far as I can remember, it's the only dropdown box on the main Audacity screen. Sometimes it's called 'Wave Out' rather than stereo mix. The link has the info you'll need.

Also, the other solutions look cool too.

---

### Post by onthefence on 2008-05-26
> **diablo75 said:**
> You just need to enable PCM capture in your volume control.  If you double-click on the sound volume icon at the top, you'll get a panel with levers on it.  Many options are not shown by default, so you should click Edit>Preferences, and then check off things like "PCM Capture" and anything else you see that you might want to have some control over later.  Once your done, the panel will have changed and should have a new "Recording" tab.  Look it over to see if your PCM capture levels are being shown, and to make sure the little microphone looking icon just below it is not crossed out.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=71619&stc=1&d=1211787740[/IMG]

So it looks like this ^

Hope that helps.

Not getting an option for PCM Capture...see attachment, don't know how to embed image in th post.

---

### Post by onthefence on 2008-05-26
might just have to go with the old audio cable trick
thanks

---

### Post by sayakb on 2008-05-26
The simplest way: Goto Applications->Sound and video->Sound recorder and select "Record from input" as Mix.

---

### Post by dustigroove on 2008-07-13
From within the Volume Control utility (*gnome-volume-control*) go to the **Edit** menu, select **Preferences**, and then make sure that the checkbox next to **Capture** is checked off. Now you will see a tab for **Recording**. Make sure it is not muted and then select a desired volume level for your recording (getting the right level may take some trial and error after you test the next part below).

Next open the Sound Recorder (*sound-recorder*) application and select **Capture** as your audio source from the **Record from Input** drop-down box. Click on the **Record** button and then start the audio you wish to record. Click on **Stop** and then the **Save** buttons once finished.

Cheers,

---

### Post by LarryJ2 on 2009-04-02
>  Re: Record Audio Playing thru Speakers
Audacity will do it. Just select 'Stereo Mix' in the dropdown box and record.

[http://audacity.sourceforge.net/help...ng&i=streaming](http://audacity.sourceforge.net/help...ng&i=streaming)

This post must be referring to the windoze version of audacity.  As far as I can see there isn't any Stereo Mix Dropdown box or menu or whatever.

Frustrating.

---

### Post by LarryJ2 on 2009-04-02
Once you get pulse audio setup,(following directions here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578))   then look at the following for a fairly complete step by step guide to get audacity running with pulse audio input.

[https://wiki.edubuntu.org/PulseAudio]("https://wiki.edubuntu.org/PulseAudio")  In particular, read the section **Recording example using PulseAudio and Audacity**.

I have this working with Audacity 1.35beta and  Hardy Herron 8.04.  What comes out of the speakers is recorded by audacity.

LJ

---


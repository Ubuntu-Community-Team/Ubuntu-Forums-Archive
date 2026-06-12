---
title: "firefox keeps closing unexpectedly"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Matt26 on 2008-07-05
for some reason firefox (v3.0) keeps shutting down unexpectedly on me- it never used to do this... i recently replaced my motherboard but i don't expect that this would have any bearing on FF closing down all the time... any ideas anyone?

thanks.

---

### Post by Dark_Stang on 2008-07-05
Is it happening on a certain site? Does it happen on sites with flash?

---

### Post by Matt26 on 2008-07-05
i have multiple tabs opened in the FF window- some have flash some don't- the entire FF window closes every time, then when i open it again it says that FF was not closed down properly and gives me the option of resuming my last session or continuing with a new one.

---

### Post by miwaypet on 2008-07-05
Flash problem. Go to synaptic and mark for complete removal the flashplugin-nonfree. After that is done install ubuntu restricted extras. Problem should correct.

Edit: nearly forgot. If you have installed any multimedia plugins through mozilla add-ons you need to remove them. They will cause FF to crash. Go this page for a simple quick guide to installing your multimedia: [http://blogs.zdnet.com/hardware/?p=2061&page=1]("http://blogs.zdnet.com/hardware/?p=2061&page=1").

---

### Post by Matt26 on 2008-07-06
thanks for the suggestions- i have completely removed flashplugin-nonfree and installed ubuntu restricted extras but FF still crashes... how do i remove any multimedia plugins that were installed through Mozilla add-ons?  i'm not certain that i have ever added any this way but i don't know where to check this.

thanks.

---

### Post by DezSP on 2008-07-06
Try running firefox from a terminal, you should then get an error message in the terminal window when it crashes, which might give better insight.

---

### Post by Matt26 on 2008-07-06
here is the output from the terminal window when FF crashes:

GCJ PLUGIN: thread 0x805f150: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805f150: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805f150: NP_GetValue
GCJ PLUGIN: thread 0x805f150: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805f150: NP_GetValue return
GCJ PLUGIN: thread 0x805f150: NP_GetValue
GCJ PLUGIN: thread 0x805f150: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805f150: NP_GetValue return
Segmentation fault

---

### Post by miwaypet on 2008-07-06
Go to synaptic package manager and type in the search box: openjdk.

Scroll down the list and mark for complete removal those boxes that are full. Accept any changes it shows and remove those items. Now make sure that you have sun-java6 bin, jre, and plugin installed. Should clear up after a restart.

---

### Post by Matt26 on 2008-07-07
i have completely removed openjdk and reinstalled sun java 6 as suggested but firefox is still crashing... here is the error i receive now when firefox crashes when it is opened via the terminal window:

(firefox:7163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:7163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

any ideas?

---

### Post by miwaypet on 2008-07-08
Start here: [http://ubuntuforums.org/showthread.php?t=749465]("http://ubuntuforums.org/showthread.php?t=749465")

---

### Post by miwaypet on 2008-07-08
What version of FF are you using. Are you using the latest ubuntu release. Have you been updating your OS?????

---

### Post by Sawubona on 2008-07-20
Hey I don't know if you've solved this yet but i had the same problem up until yesterday. I tried a lot of things nothing worked until I stumbled across a thread last night. I would refer you to it if i could remember where it was, but i had had a few beers so i can't remember.

Basically adobe flash player 9 and Pulseaudio don't like each other. In my case FF would always crash right at the start of a flash video when the audio was loading. However flash player 10 has apparently fixed this problem.

The solution:

- uninstall flashplugin-nonfree using the synaptic package manager.
- get flash player 10 from: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Hope this fixes the problem. My knowledge is limited though, as it was a monkey see monkey do fix. Haven't had a crash yet which is a great sign.

---

### Post by Bosconian on 2008-07-20
I had the same problem. Flash 10 beta makes things better but still crashes (just not quite as often).

I solved it by going back to Flash 9 and going to the sound settings and changing all PulseAudio to ALSA in the settings.

I'll use this setup until they fix the Flash/Pulseaudio issues.

---


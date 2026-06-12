---
title: "Desktop sound recorder??"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by justinram22 on 2008-07-20
is there a desktop sound recorder, so like i can record what my computer is listening to? its a good process for getting free music, just play a youtube vid and record it, i used to be able to do it in audacity in windows, but i can't seem to figure it out... any help would be great, i wouldn't mind just using audacity, but any software works, im not trying to record my desktop, just the sound of my desktop.

---

### Post by jimmy the saint on 2008-07-20
This forum really isn't an appropriate place to be discussing ways to steal music.  Asking for assistance for such things is a violation.

---

### Post by scragar on 2008-07-20
Even if this did have possible problems with the rules I would like to know about a possible program for the same task, although my task is more assosiated with recording skype calls(without annoying plugins, the one of which I got recomended saps about 90% of my CPU constantly and still comes out with bad sound quality).

I'm sure there must be a method of doing this, esspecialy since pulseaudio acts as a layer between programs and alsa, other programs must be able to do the same and record said content.

---

### Post by t0p on 2008-07-20
> **justinram22 said:**
> is there a desktop sound recorder, so like i can record what my computer is listening to? its a good process for getting free music, just play a youtube vid and record it, i used to be able to do it in audacity in windows, but i can't seem to figure it out... any help would be great, i wouldn't mind just using audacity, but any software works, im not trying to record my desktop, just the sound of my desktop.

Sorry, can't help you with recording just the audio from a vid - but you could copy the video files using the Firefox add-on **downloadhelper**, or by simply playing the entire video file, then going to your /tmp directory and moving the copy made by Ubuntu to your home directory. There's also a command-line app **youtube-dl** available in the repos.

---

### Post by kevmitch on 2008-07-20
Ok there are legitimate reasons to want to do this so let's just pretend like recording music you aren't supposed to wasn't mentioned and proceed from there.

This will likely depend on your soundcard and most importantly whether your soundcard can do it. I know I heard about Dell disabling this capability on some of their recent laptops under pressure from the RIAA. However, if you say you can do it in Windows, then I'd say it's a safe bet that your hardware allows it. On the other hand as you say, pulse audio might even get around hardware limitations, but then I don't know much about pulse audio since I don't really use it. 

Here is how I can do it using pure ALSA:

The first thing you can try is to open up gnome volume manager (I Think double clicking on the speaker in the upper right system tray should do it). Go to preferences and select all of the channels to be visible. Now click on the recording tab.

This is where you might encounter different options depending on your soundcard. I've got an intel HDA sound controller:
```

# lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

It shows me a "Capture" and a "Digital" channel on the recording tab. I enable recording on BOTH of these by clicking the microphone to make sure it doesn't have a red X over it and then I set the levels to something reasonable. 

Next I open up audacity and go to **Edit->Preferences->Audio I/O**. For the recording device, select "ALSA:default" and 2 channels (stereo).
Now exit the preferences dialog and click on the arrow next to the microphone and below the associated input level metre. Select "Start monitoring" and you should see the levels associated with whatever is coming out of your sound card at that moment. Now go back gnome-volume-manager and adjust the capture and digital levels so that the bars don't max out and aren't tiny.  

Now hit record and you should get a recording of the stream captured coming out of your sound card.

---

### Post by dominiquec on 2008-07-20
Here's how you can extract audio from an AVI file:

[http://ubuntuliving.blogspot.com/2008/03/extracting-audio-from-avi-file.html](http://ubuntuliving.blogspot.com/2008/03/extracting-audio-from-avi-file.html)

---

### Post by saratchandra on 2008-07-20
Audacity can record output sound too. Install it from synaptic.

---

### Post by dhughes on 2008-07-20
> **jimmy the saint said:**
> This forum really isn't an appropriate place to be discussing ways to steal music.  Asking for assistance for such things is a violation.

 I can see your point but it will be poor quality anyway; some countries allow it (Canada has a levy on CD and DVDs to compensate artists); it's no worse than a VCR recording a TV show; it's already on/stored in your computer if you're viewing it or listening to it.

---

### Post by Morpheun on 2008-07-21
Exactly, in the United States there are even cases that allow recording off radio specifically. If that really what he is trying to do, I wouldn't worry about it, although I suspect it's far more benign

---


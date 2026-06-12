---
title: "HDMI question"
date: 2015-06-04
forum: New to Ubuntu
---

### Post by planetketu on 2015-06-04
I am completely NEW to unbuntu/linux os. I dont know what a command line is, or how to open terminal. I am currently using version unbuntu 14.04. I would like to hook up my laptop to my tv so that I can watch movies on the big screen. When I hook up through HDMI I can view my desktop on the tv, but I cannot see/hear the VLC player on my TV.  (I am currently waiting for some intro books in the mail about using unbuntu, and looking online for tutorials for linux) Any help would be greatly appreciated!

---

### Post by Bucky Ball on 2015-06-04
Welcome. Open Pulseaudio Volume Control and have a tweak about in there (I don't use Unity desktop but I think you just need to look for it in the dash?). You probably have your audio set to analogue outputs, speakers or headphones, and not HDMI. Sometimes it doesn't automatically switch. 

As for seeing your desktop, switch off everything. Make sure HDMI cable is firmly plugged both ends. Switch on TV and set source input to HDMI*, i.e. whatever your computer is plugged into. Switch on computer and let boot. 

Any luck? Generally the TV needs to be on first, in my experience at least.

I would go for seeing it first and hearing it second. Have a look in PAVolume control and let us know if you have more questions/issues with it. ;)

---

### Post by grahammechanical on 2015-06-05
HDMI is a connection between the graphic adapter and the monitor/TV. I do not think that computer audio output is provided by graphic adapters. The laptop should have an audio output that can be connected to an audio input (perhaps called an AV connection) on the TV if it has one.

Ubuntu will have an icon for Audio in the top panel on the right. That will provide a link to the sound Settings. Or we can go to System Settings>Sound to set input and output sources.

Regards.


Regards

---

### Post by Bucky Ball on 2015-06-05
> **grahammechanical said:**
> HDMI is a connection between the graphic adapter and the monitor/TV. I do not think that computer audio output is provided by graphic adapters. The laptop should have an audio output that can be connected to an audio input (perhaps called an AV connection) on the TV if it has one.

Well, it is a connection from your computer to your TV. HDMI carries audio as well as video (I currently have about five devices doing exactly that). There is no need for a separate audio connection. It is one of the benefits of HDMI over VGA and others. One less cable. HDMI is NOT the same as plugging in a VGA or DVI cable which has NO capabilities for carrying audio and you can more easily imagine that it is connected directly to your video card. ;)

If you go to PAVolume Control and check the output device you'll find you have an entry for HDMI. See in the configuration tab there if you can't find it elsewhere.

---

### Post by yetimon_64 on 2015-06-05
> **Bucky Ball said:**
> Well, it is a connection from your computer to your TV. HDMI carries audio as well as video (I currently have about five devices doing exactly that)....

If you go to PAVolume Control and check the output device you'll find you have an entry for HDMI. See in the configuration tab there if you can't find it elsewhere.

Yes I can confirm that, very easy to control sound streams to a TV via HDMI cables.

@ OP, see the next 2 screenshots for the configuration tab and the playback tab settings to adjust. With the HDMI cable connected (mine isn't in the screenshots) ensure the HDMI on the configuration tab is set to stereo or surround (depending on TV speaker type etc) for the TV and the HDMI  option is not turned "off". 

Then with the application running go to the playback tab (shown in the second screenshot), click on the "Built in audio" button and select/click the HDMI entry on the pop up menu; shown highlighted and ready to click in the screenshot, when clicked the sound will be passed over to the TV immediately. Cheers.

---


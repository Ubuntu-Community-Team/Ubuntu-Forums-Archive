---
title: "[SOLVED] Audacity on Intrepid Ibex"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by cwsnyder on 2008-11-18
This tutorial is from Gnome, but mostly concerns Audacity, so all variants should be covered.

A short tutorial on Ubuntu using Audacity to record from external player through Line In to digital music file:

    * Download and install Audacity (and Lame) from the Ubuntu repositories. Make sure to enable the ubuntu-restricted-extras package (or whichever -restricted-extras package applies to your version), also. The library which Audacity requires to encode MP3 files will be put in /usr/lib/ (so you know where to find it when Audacity asks).
    * Right click on your speaker icon and select Open Volume Control from the context menu. Click on preferences and make sure Line In (Playback) and Capture (Recording) are checked. On the Playback tab, make sure that the Line In slider is not muted and the slider is at about 80% of full scale.
    * Click on the Recoding tab. Make sure the Capture control (speaker icon) is not muted and the slider is set for about 80% of full scale.
    * Click on the Options tab. Check that the input source is Line for at least one of the Input Source selections.
    * Device: at the top of the dialog box should match your sound device which has the line input. In my case it reads HDA ATI SB (Alsa Mixer) for the motherboard 883 sound system. You can close this dialog box now, or simply leave it open.
    * Open Audacity from the Applications >> Sound & Video >> Audacity menu. Open Audacity's Edit >> Preferences menu selection to open the preferences dialog box.
    * On the upper right in the Recording >> Device area with Audio I/O selected, select the ALSA input device which matches closest to the selection you chose from the mixer/line input device. In my case there are two devices, one ending in [0,0], the other ending in [0,4]. I had to do some experimenting to find out that the rear of the tower Line Input was connected to the device at [0,0]. Just a word of warning that this might also happen to you. Set the Channels to 2 (stereo) to enable stereo recording.
    * Select Import/Export from the left menu of the dialog box. Select from the now visible MP3 Library area the Find Library button and browse for the libmp3lame.so.0 at the bottom of the list in /usr/lib/ folder. You can close the dialog box now.
    * Back in Audacity, select from the menu View >> Toolbars >> Device Toolbar. This allows you to change the input device from the toolbar, rather than going back into Edit >> Preferences >> Audio I/O area. 

You should now be ready to record whatever is playing into the line input of your computer's sound system. Your Recording >> Capture volume control is the one you will have to play with to set the input volume from your source from your Volume Control settings.

I hope this helps someone else. It took me about 8 tries to finally figure out all of the correct settings on my computer. The settings for Audacity on Windows are accessed by a drop box on the toolbar, which the Audacity documentation still refers to. Unfortunately, the version of Audacity in the Ubuntu repository seems to have been changed without having the documentation updated.

I like Audacity, but I had to record 2 cassettes for friends from Windows because I could not get the Linux version to work for me.

---


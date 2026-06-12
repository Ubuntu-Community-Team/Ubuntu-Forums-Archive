---
title: "[SOLVED] *.wav file playback issues"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by jenkinbr on 2008-11-19
Original post: [http://ubuntuforums.org/showthread.php?t=985409](http://ubuntuforums.org/showthread.php?t=985409)

I am hesitant to bring this up here, but the thread mentioned above is not receiving much attention and quickly gets buried. I am having problems playing and burning wav audio files in the default applications in Ubuntu 8.10.  To quote my original post in that thread:

> **jenkinbr said:**
> After upgrading to ubuntu 8.10, I have begun to notice that some players (like totem) and some CD burners (Brasero) no longer play .wav audio or burn it to an audio CD.  This is rather annoying, as I use .wav files frequently due to the high sound quality they hold.  Even .wav files created by dragging from an audio CD do not play.

There is nothing wrong with the files - Amarok, alsaplayer, +others play the files just fine, and I can open them in Audacity without issue.

I'm guessing that this may be an issue with gstreamer (btw, I installed gstreamer*, thereby giving me all the plugins), but I am not sure.  Any ideas?

As mentioned later in that post, I have the wavpack codec installed and that still does not help things.  I have gathered the following info as of about an hour ago using the terminal:

```

jenkinbr@jenkinbr:~$ totem 2>&1
/home/jenkinbr/.themes/Divinorum-Revisited-Personallized/gtk-2.0/gtkrc:1392: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.

** (totem:6884): WARNING **: Invalid borders specified for theme pixmap:
        /home/jenkinbr/.themes/Divinorum-Revisited-Personallized/gtk-2.0/Menu-Menubar/menubar.png,
borders don't fit within the image

(totem:6884): Gtk-WARNING **: Radio group does not contain an action with value '-2'

(totem:6884): Gtk-WARNING **: Radio group does not contain an action with value '-2'

(totem:6884): Gtk-WARNING **: Radio group does not contain an action with value '-2'
jenkinbr@jenkinbr:~$ nautilus ~/Audio/ 2>&1
/home/jenkinbr/.themes/Divinorum-Revisited-Personallized/gtk-2.0/gtkrc:1392: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
jenkinbr@jenkinbr:~$ serpentine 2>&1
/home/jenkinbr/.themes/Divinorum-Revisited-Personallized/gtk-2.0/gtkrc:1392: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
/usr/bin/../lib/python2.5/site-packages/serpentine/preferences.py:262: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  g = glade.XML (filename, "preferences_dialog")
/usr/bin/../lib/python2.5/site-packages/serpentine/preferences.py:171: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self._speed.widget.set_range(low, max_speed)

** (serpentine:7059): WARNING **: Invalid borders specified for theme pixmap:
        /home/jenkinbr/.themes/Divinorum-Revisited-Personallized/gtk-2.0/Menu-Menubar/menubar.png,
borders don't fit within the image
Segmentation fault
jenkinbr@jenkinbr:~$ 

```

Lots of GTK warnings, but no playback errors displayed.

Neither serpentine, or totem show any sign of error.  Totem thinks the wav file is streaming audio for some reason, but does not play it.  Clicking the play button is actually what was generating the ```
(totem:6884): Gtk-WARNING **: Radio group does not contain an action with value '-2'
``` warnings shown above.

Serpentine simply tells me that it could not add the file to the playlist and to make sure I have all the gstreamer plugins installed (I have all of them).  Re-installing all of this does not help.

Please note that I run an offline Ubuntu installation, so I will not be able to post any command output until tommorrow.  Depending on the dependancy tree, It could be a day or two before I can install software as well.

---

### Post by CraigPaleo on 2008-11-19
Same issues here. Wav files are seen as streaming; even a 244.7 MB wav file! 

No matter what I use to try to play it, it says it's streaming or has zero length, ever since the Ibex update. 

I'm glad you brought this up here as no one has responded to the original post.

---

### Post by mc4man on 2008-11-19
As far as playback of .wavs with totem-gstreamer, one word that's synonymous with totem-gstreamer in general,

Broken

While i don't use brasero it seems to work ok in a test.
What are you trying to do with it exactly?

---

### Post by CraigPaleo on 2008-11-19
All I'm trying to do is play a wav file that had no problem being played before the Ibex update. It doesn't matter which player I use. It says "streaming" and/or that it has zero length.

I've downloaded new wav files and they play properly, as they should. It's the saved, old wav files that are a problem for me.

I just want to play them. I think Jenkinbr wants to burn them.

---

### Post by mc4man on 2008-11-19
do you have mplayer installed?

Are you able to play these new .wavs in totem-g? From what I see it won't play any .wav ripped from an audio cd or an audio cd itself. (though I haven't tried anything out of the ordinary - normally .wav and audio cds should play 'out of the box' so to speak.

---

### Post by CraigPaleo on 2008-11-19
Mc4man! 

They're working in Mplayer now!!!! The old wav files, that is. The new ones were not effected at all. 

Sorry, I must have confused Movie Player with M Player. Still, something must be wrong since they worked in every player, before the update.

Thanks!

---

### Post by mc4man on 2008-11-19
I'm assuming you did an upgrade vs. fresh install? If so you may want to reinstall the other affected apps. and or delete their config file. (emphasis on config. files

What else do you have installed that's a problem (excluding totem-gstreamer

Edit : if you want a 'totem' that works install totem-xine and libxine1-ffmpeg

---

### Post by CraigPaleo on 2008-11-19
Yes, I did a simple update. The only other thing I have installed that is/was problematic is KDE. I put it on a separate partition because the applets of one would show up on the desktop of the other. Both Gnome and KDE! 

I haven't tried the wav files in KDE yet. It's hard to get the plasmoids to work right. There's not even an option to move them when right clicking on them.

---

### Post by mc4man on 2008-11-19
I've got a standalone install of kubuntu 8.10 - interesting to say the least. Took me a solid 1/2 hr. before I realized the 'desktop' isn't a desktop at all. (was coping and pasting some files from flash drive to the 'desktop' and couldn't understand why they weren't really there, and nothing useful on r. click.

the other thing that stumped me was where does an audio cd go. Never did find physically but they can be accessed at this location for copying and or converting. 
audiocd:/

---

### Post by CraigPaleo on 2008-11-20
> **mc4man said:**
> I've got a standalone install of kubuntu 8.10 - interesting to say the least. Took me a solid 1/2 hr. before I realized the 'desktop' isn't a desktop at all. (was coping and pasting some files from flash drive to the 'desktop' and couldn't understand why they weren't really there, and nothing useful on r. click.

the other thing that stumped me was where does an audio cd go. Never did find physically but they can be accessed at this location for copying and or converting. 
audiocd:/

LOL! I love you! What's the point in having a desktop if it's not an actual desktop? 

If I wanted to download something to a window, I'd download it to an open window. The supposed desktop is as annoying as heck!

---

### Post by jenkinbr on 2008-11-20
> **mc4man said:**
> As far as playback of .wavs with totem-gstreamer, one word that's synonymous with totem-gstreamer in general,

Broken

While i don't use brasero it seems to work ok in a test.
What are you trying to do with it exactly?

> **CraigPaleo said:**
> All I'm trying to do is play a wav file that had no problem being played before the Ibex update. It doesn't matter which player I use. It says "streaming" and/or that it has zero length.

I've downloaded new wav files and they play properly, as they should. It's the saved, old wav files that are a problem for me.

I just want to play them. I think Jenkinbr wants to burn them.

Correct - I need to be able to burn them.  My wav files are typically ripped off of CDs (using either nautilus in gnome, but have also tried an actual rip using <default audio CD ripper - the name escapes me..>

> **mc4man said:**
> do you have mplayer installed?

Are you able to play these new .wavs in totem-g? From what I see it won't play any .wav ripped from an audio cd or an audio cd itself. (though I haven't tried anything out of the ordinary - normally .wav and audio cds should play 'out of the box' so to speak.

Yes.  I have mPlayer, alsaplayer, amarok, +others, they all work.  It's just totem* that will not play them...

> **mc4man said:**
> I'm assuming you did an upgrade vs. fresh install? If so you may want to reinstall the other affected apps. and or delete their config file. (emphasis on config. files

What else do you have installed that's a problem (excluding totem-gstreamer

Edit : if you want a 'totem' that works install totem-xine and libxine1-ffmpeg

I do a fresh install for every release.  I have never tried using the upgrade path on my offline machine, mainly because I don't think I could get it to work unless I made a full mirror of the repositories - too much work, and it's simply easier to start fresh.

I will try dumping config files, though, because my ~home partition does not get wiped.

I have no problems with any other app I've installed - except for serpentine (was default pre-hardy days...)  My problems with wav audio lie in totem-anything, serpentine, and brasero (which is the next on the list to reinstall, as brasero-everything is whack - none of it works, wasted five disks on it before I went back to nautilus-cd-burner).  Also, previewing the wav files in nautilus does not work, but I think that's because totem is used for this...

---

### Post by mc4man on 2008-11-20
Totem-xine should be able to play .wav, in 8.10 totem-gstreamer can't.
Not too big a deal, neither are 'music players' per se. Do note that playback of .wav doesn't require any additional libs, codecs ect. (you can do so off of any livecd, with any player with the sole exception of totem-gstreamer in 8.10.

If you were to right click on a .wav -> open with other application and choose "Movie Player (Xine)" it fails?

As noted i never use brasero or any linux iso creating/burning app except out of curiosity due to the frequent issues people have with them.

While I did test brasero in 8.10 to make an audio cd I only had it copy a cd and burn which it did quite handily.

I'll give a try making a cd off of ripped tracks and let you know.

---

### Post by jenkinbr on 2008-11-20
mplayer did work, as did the others mentioned above (alsaplayer, amarok, ...) 
Totem isn't the main concern at this point, as I can listen to wav files in  alsaplayer just fine (and have set that as the default for wav files)

edit: I don't know for sure if totem-xine is installed on my system and cannot find out until later.  If I don't have it, I will work on getting it, but that could be a day or so...

However, burning them currently does not work in any app I have tried so far.

---

### Post by CraigPaleo on 2008-11-20
I've downloaded and installed Totem xine and it's worked.

Do the burners and other programs need xine too? If so, is there a way to configure them to use it?

Have you tried Gnomebaker or K3b? K3b should work since it's a KDE app.

__________________
[Raw Paleo Diet Group]("http://health.groups.yahoo.com/group/rawpaleodiet/")

---

### Post by mc4man on 2008-11-20
This is just a quick look and while i don't use any of the apps you mentioned it's very interesting.
(I use rubyripper, grip for ripping, encoding, Imgburn for iso creation and burning.

I'd also note that as far as AV stuff 8.04 is great, 8.10 **much** less so overall.

As far as .wav's and  ripping, burning in 8.10

Using two supported apps, rhythmbox to rip, brasero to burn they both worked well to their capabilities and a good cd was created. 

After that it went downhill quickly.

Serpentine seems to be a no go, .wav is 'unsupported' no matter what the source (ripped with rhythmbox, cd audio extractor or otherwise.

Gnomebaker **will fail** on any .wav ripped by rhythmbox and  audio cd extractor (internal data flow error.

It **will** work with  .wav either copied directly in nautilus or ripped with grip.

Brasero will** not** accept .wav ripped with grip or taken directly in nautilus. (unsupported format, lol

A quick conculsion is in 8.10 a .wav is not a .wav unless ripped with a gstreamer app and burned in a 'supported' app. (unless you stay away from gstreamer apps altogether 

I'm going to see later what a burner that's above all this nonsense does with a 'gstreamer .wav' (Imgburn

---

### Post by jenkinbr on 2008-11-21
> **mc4man said:**
> This is just a quick look and while i don't use any of the apps you mentioned it's very interesting.
(I use rubyripper, grip for ripping, encoding, Imgburn for iso creation and burning.

Does Imgburn also burn audio?
> **mc4man said:**
> 
I'd also note that as far as AV stuff 8.04 is great, 8.10 **much** less so overall.

As far as .wav's and  ripping, burning in 8.10

Using two supported apps, rhythmbox to rip, brasero to burn they both worked well to their capabilities and a good cd was created. 

After that it went downhill quickly.

Serpentine seems to be a no go, .wav is 'unsupported' no matter what the source (ripped with rhythmbox, cd audio extractor or otherwise.

Gnomebaker **will fail** on any .wav ripped by rhythmbox and  audio cd extractor (internal data flow error.

It **will** work with  .wav either copied directly in nautilus or ripped with grip.

Guess I'll have to try this...
> **mc4man said:**
> 
Brasero will** not** accept .wav ripped with grip or taken directly in nautilus. (unsupported format, lol

A quick conculsion is in 8.10 a .wav is not a .wav unless ripped with a gstreamer app and burned in a 'supported' app. (unless you stay away from gstreamer apps altogether 

Well, then, :razz: on gstreamer.
> **mc4man said:**
> 
I'm going to see later what a burner that's above all this nonsense does with a 'gstreamer .wav' (Imgburn

I wonders if there is a bug mentioned in launchpad for any of this.... 

I did look last night, and I do not have totem-xine installed.  I opened up synaptic, enabled my offline repo, and generated a download script for totem-xine (+ a few other things...), which I will clean and feed to a download manager later today.

Thanks for doing all this testing.  It is greatly appreciated.

I'm coming to the conclusion that I should have stuck with LTS and saved the nifty features of 8.10 for later...  Hopefully this all gets fixed in an update, or at the latest, 9.04.

btw, what in the world is the diff between a .wav from gstreamer and a .wav from some other app?:confused: Shouldn't they all have the same format?

---

### Post by mc4man on 2008-11-21
Imgburn needs to be run in wine and due to a small potential bug in wine needs 1 change in it's settings. (8.04 - the I/O needs to be set on ASPI - WNASPI32.DLL due to wine 'losing' drives' if blank media or an audio cd in in the drive)
I haven't installed yet on 8.10, will do tonight, if interested I'll post what if any changes are needed from it's default settings.
support for audio, bin and cue was recently added

if you want to ck. out and read ect. google Imgburn

> I'm coming to the conclusion that I should have stuck with LTS 


IMHO 8.04 is great as far as AV stuff. 8.10 feels 'restrictive' for some reason and certainly has some 'roadblocks' and 'potholes'
In regards to 'third party' apps 8.10 is a problem, either they don't work yet (if ever) or they don't run as well.

> btw, what in the world is the diff between a .wav from gstreamer and a .wav from some other app? Shouldn't they all have the same format?

Got me there - just observing behavior. Nothing surprises me in regards to gstreamer and it's associated apps.

---

### Post by jenkinbr on 2008-11-24
> **jenkinbr said:**
> 
btw, what in the world is the diff between a .wav from gstreamer and a .wav from some other app?:confused: Shouldn't they all have the same format?

I think I figured this much out:

I had sox installed, so I ran it on a file named 'Track 1.wav' like so:

```
sox Track\ 1.wav Track\1.1.wav
```

I then compared filesize between the two using 'ls -l' and discovered that 'Track 1.1.wav' was bigger by ~75 bytes or so
(I don't remember the exact number)

From this, I am guessing that the non-gstreamer wav files lack something in the header that sox put in.  I then opened 'Track 1.1.wav' in totem-gstreamer and it played.  A test burn using serpentine was also successful - no errors.

Thanks everyone for all the help and testing.

---

### Post by jamesisin on 2009-01-05
Know much about encoding?

[http://ubuntuforums.org/showthread.php?t=1031973](http://ubuntuforums.org/showthread.php?t=1031973)

---


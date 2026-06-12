---
title: "Script to fool TV into not displaying input mode"
date: 2011-11-13
forum: Programming Talk
---

### Post by wannabegeek on 2011-11-13
Hi everyone,

I'm back with another help request for setting up my media server....
Everything is ALMOST perfect....video and audio is worked out and running Ubuntu 11.10 and loving it....

Using an older Sony Bravia KLV S10A, which has an HDMI input but does  not want a PC connected to it. Instead the instructions say to use the  RGB inputs.... lame.

FINAL ISSUE:
The clock display shows up, the screen res "P720" label pops up and the  input mode "VIDEO 5" displays, when I open a new window. They all turn  off in a few seconds.  But when I open a window to navigate the desktop,  that damned "Video 5" pops up  and doesn't go away until I've closed  the window.

When I watch a Movie, they all turn off.  I suspect that the TV is  detecting the changes in the video data and making assumptions about  what has happened.

I  think  there might be a way to fool the TV into not ever displaying the  banners, by having a light weight program run in the background which  sends some data which tricks the TV but does not show t othe human eye.  Then , with some logic , prevent the script from running during movie  playback if that's a problem.

Any ideas ...?

Thanks again ! 
wbg

---

### Post by papibe on 2011-11-13
HDMI inputs usually requires TV resolution and timings. What resolution are you trying on the HDMI input? I would go with a typical 1280x720 for example.

Does the TV has a VGA input? that should be much better than RGB.

Just some thoughts,
Regards.

---

### Post by wannabegeek on 2011-11-13
Hi papibe....

I had to tweak my screen resolution since the TV was reporting numbers which didn't fit my screen. The res from gtf for the published res didn't work. I got the HDMI to work great now by looking up the res used from /var/log and adjusting some if the modeline numbers.

It's just the annoying behavior of the labels popping up that kinda sucks.

I might have to go back nad use the VGA input....I just bilt this inexpensive but new and modern computer so it feels lame to be going back to VGA....

thanks for your reply,
wbg

---

### Post by papibe on 2011-11-13
If the resolutions you tried didn't fit the very well, may be you were experiencing your TV doing the ugly thing: [overscan]("http://en.wikipedia.org/wiki/Overscan").

What is your graphic card?

Regards.

---

### Post by wannabegeek on 2011-11-13
I am using the integrated Intel graphics on my Asus P8H67 MOBO. ThisMOBO has a ton of BIOS options for graphics,
I just don't understand them....

I read on a Ubuntu site some where, that TV's often do not report  good modelines. I think the myth help pages...

For now I'm fine with my picture, it's the input label in the left corner. The TV manual specifically says not to connect a 'PC' to the HDMI input....hopefully I'm not burning out a an amp inside....The input labels turn off and on as if they are
trying to assume that a DVD player has been turned on or a movie has started....

I might try making some image files with invisible data and seeing if I can trick the TV. Perhaps I can use MATLAB to make an image with some weird data type not recognized as image data but enough to keep the label from activating....

wbg

---


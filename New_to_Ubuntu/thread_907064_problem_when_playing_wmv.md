---
title: "problem when playing wmv"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by inter-m on 2008-09-01
ever since i upgraded Ubuntu 8.04 ive been having a problem playing wmv files... when i play it on vlc as i usually do it plays but there is no voice... and on totem it will play very slow... i dont know why this happened... any help plz... 

K.H

---

### Post by swoll1980 on 2008-09-01
Maybe a reinstall will help?(the apps not the whole os)

---

### Post by inter-m on 2008-09-11
> **swoll1980 said:**
> Maybe a reinstall will help?(the apps not the whole os)
i tried reinstalling both applications but no change... also ive noticed something else now that ogg videos play with no sound also...

---

### Post by SuperSonic4 on 2008-09-11
Sounds like a sound driver problem. Do any other filetypes/applications work with sound?

---

### Post by inter-m on 2008-09-11
now that i tried avi also i think that none are working at this moment on vlc and totem... but youtube is working fine on firefox should that have anything to do with it...

---

### Post by inter-m on 2008-09-11
i forgot to mention that my wife accidentally removed the power supply to my laptop when i was working on it a couple of weeks ago... and ever since i try to boot it just freezes on me so i boot from the recovery mode through grub then i choose resume normal boot and it works fine for a couple of times then it freezes on me when i boot again... do u think this has to do with what is going on here... keeping in mind that im only having a problem with vlc and totem all my other apps r working fine..

---

### Post by Lord Xeb on 2008-09-11
Try VLC. It works quite well and I use it since it plays nearly ALL formats :D

---

### Post by inter-m on 2008-09-11
> **Lord Xeb said:**
> Try VLC. It works quite well and I use it since it plays nearly ALL formats :D

its vlc that im having problems with :)

---

### Post by Tatty on 2008-09-11
Im not sure what the problem is here.  But perhaps it might be worth running these apps from the command line to see if they output any error messages when trying to play your files.

---

### Post by inter-m on 2008-09-11
> **Tatty said:**
> Im not sure what the problem is here.  But perhaps it might be worth running these apps from the command line to see if they output any error messages when trying to play your files.

when i run vlc from the command line it works with no errors but the sound is not playing....

and this is what i get when i run totem

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 58 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by Tatty on 2008-09-11
Try, in VLC, going to Settings->Preferences->Audio->Output Modules.  Then click the "Advanced Options" checkbox in the bottom right hand corner.

Then click the dropdown that appears and select "ALSA audio output".  Im just wondering if this might be a problem with pulseaudio in VLC.

---

### Post by anewguy on 2008-09-11
I'll be watching this thread, as you are not alone.  With the restricted packages I had all of this working fine until I upgrade to 8.04.  Now it doesn't matter if it's VLC, etc., everytime I try a wmv they either play VERY slow (like a frame every so often) or not at all.  I've tried all kinds of things and have not been able to get this to work either.

Dave :)

---

### Post by inter-m on 2008-09-12
> **Tatty said:**
> Try, in VLC, going to Settings->Preferences->Audio->Output Modules.  Then click the "Advanced Options" checkbox in the bottom right hand corner.

Then click the dropdown that appears and select "ALSA audio output".  Im just wondering if this might be a problem with pulseaudio in VLC.

i did all of that but nothing changed...

---

### Post by inter-m on 2008-09-12
> **anewguy said:**
> I'll be watching this thread, as you are not alone.  With the restricted packages I had all of this working fine until I upgrade to 8.04.  Now it doesn't matter if it's VLC, etc., everytime I try a wmv they either play VERY slow (like a frame every so often) or not at all.  I've tried all kinds of things and have not been able to get this to work either.

Dave :)

im glad to know that im not alone... :D

---

### Post by SunnyRabbiera on 2008-09-12
are these files DRM protected?

---

### Post by inter-m on 2008-09-12
> **SunnyRabbiera said:**
> are these files DRM protected?

i dont really know what DRM protection is... but when im using windows on my pc i can view the files with no problems...

---

### Post by SunnyRabbiera on 2008-09-12
> **inter-m said:**
> i dont really know what DRM protection is... but when im using windows on my pc i can view the files with no problems...

DRM = Digital restrictions management, meaning if a file is coded it might not be playable in linux.
Not a linux fault, but the media gets a kick out of it.

---

### Post by anewguy on 2008-09-12
None of what I'm trying is copy protected.  I've been looking at building a recumbent bicycle, and as such have been checking out designs at atomiczombie.com.  Some of their designs have a video you can play to the bike in action.  I have yet to be able to watch one of these videos.  I have changed Firefox to use VLC for the various video files, and still no luck.  The video is downloaded, then VLC tries to play it and it's just either a single frame, or jumps to random frames but never actually plays.  This is with the restricted stuff installed.  The default to Totem or movie player or whatever it was before I tried VLC always did the same thing.

Try going to that site and playing a video, then, if you have success with them all, tell us how you are set up, etc., so we can try to match it and try our various problems.

Dave :)

---

### Post by anewguy on 2008-09-15
I'm going to bump up this thread, as no results have been given.  Please note that the problems I experience with the videos at atomiczombie.com for the recumbent bicycles are just indicative of the problems I have overall with videos on the net and locally, even with the restricted packages installed.  As mentioned previously, this all worked until the upgrade to 8.04.

Thanks in advance!

Dave :)

---

### Post by anewguy on 2008-09-18
Has anyone tried these videos and what are your results?  If they are okay, what player are you using, what are it's settings, what codecs, etc., do you have installed?

---


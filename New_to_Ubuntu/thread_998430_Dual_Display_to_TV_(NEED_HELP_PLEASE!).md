---
title: "Dual Display to TV (NEED HELP PLEASE!)"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by HypnoSquid on 2008-11-30
I've had Ubuntu 8.10 for nearly a month now and I have gotten to the point that I would rather be using it exclusively instead of having to switch over to windows to watch movies and TV (from my PC). The only thing is that I cannot seem to get dual display to work with my Radeon 7000. In windows I have it set up so my main monitor signal comes out of the video cards VGA output and my television signal comes from the s-video output on the card. On windows it works flawlessly and also was immediately set up. I understand that things in linux take a little bit more work but I haven't gotten this to work after hours and hours of trials and tribulations. 

When I go to edit my xorg.config file I just have "Configured Device" and "Configured Monitor" and when I try to set up xinerama or any other dual display setup, it either has no effect or makes Ubuntu boot up into "low res". I would love to get rid of windows forever and I cannot until I can watch my movies on my TV screen. I realize that it would be easier if I had a newer video card but I am unemployed and cannot afford one.

Is there any way I can get the proper driver working with my video card and then have dual displays using my s-video output???

Any help would be greatly appreciated!!!!! THANKS IN ADVANCE!!!!

---

### Post by ayip on 2008-12-01
I was able to get my old HP Pavilion laptop with ATI 9000 Radeon to output to S-Video and play videos with VLC.  Without the xvattr, you can get video out but no playback.

No changes to xorg.conf.  Just use xrandr and xvattr as this

xrandr --addmode S-video 800x600 
xrandr --output S-video --mode 800x600
xrandr --output S-video --set ntsc
xvattr -a XV_CRTC -v 1


Here's the original thread...

[http://ubuntuforums.org/showthread.php?p=3467287#post3467287](http://ubuntuforums.org/showthread.php?p=3467287#post3467287)


Hope this helps.

---

### Post by HypnoSquid on 2008-12-01
THANKS! that actually kind of worked!!! the tv is recieving a signal but it is a little grainy (which i can deal with) but the bottom side of the screens image is cut off!!!!

when i run the command "xrandr --output S-video --set ntsc" i get a list of commands so i think that this command is actually missing something. any idea of why its not working? (i think this will cause the image to fit the screen if i can figure out what is missing)

THANKS AGAIN FOR YOUR HELP!!!!

---

### Post by HypnoSquid on 2008-12-01
ok i found that i was missing one term which made that command:

 "xrandr --output S-video --set tv_standard ntsc"

but still the bottom part of the screen is cut off. if i switch the main screen resolution to 800x600 then run those commands the image is fine, but then i have to have 800x600 resolution on my monitor.

is there anyway to run 1024x768 on my monitor and 800x600 on my tv (s-video out) without having the tv image cropped????

---

### Post by ayip on 2008-12-01
Sorry for the typo on the command, must have been cut and paste error, yours is correct.

S-video only provides 480 lines of resolution so you're stuck there on the bottom and sides, I switch to 800x600 then play with the aspect ratio in vlc to get best playback.

BTW..to switch the playback back do

xvattr -a XV_CRTC -v 0

---

### Post by ayip on 2008-12-01
Maybe there is something here which might help, there is a way to statically configure it via xorg.conf.  Perhaps it can detect the S-video load and switch.

[http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV)

---


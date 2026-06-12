---
title: "ubuntu 11.10 dell inspiron mini sound and video problems"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-12-16
I have a dell Inspiron mini 1010 and I just upgraded from 10.04 to 11.10 by updating the distribution three times through the releases because I do not have an external cd drive. 

once I updated I went to go watch my friends new video on youtube, ever since I put ubuntu on my notebook I have had graphics problems and I have not researched enough to update it before. although now the sound dose not work and so I started to do some reading to see what i can do to fix it. I came upon this...

[http://ubuntuforums.org/showthread.php?t=1894547](http://ubuntuforums.org/showthread.php?t=1894547) and this...
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

and when I copy and paste the code how do I save it? and reboot the computer? do I just copy paste and close terminal?


and in regards to the video I did this...

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

following to guides to emgd driver version 1.8

and it made my screen have weird virtical lines and when I rebooted It would not load past the first ubuntu loading screen. I waited to see if it would just take some time...it did not it seems to have frozen after an hour of waiting. so i held down power button and rebooted. i did this about three times and it froze every time so I got an external cd drive and downloaded on a friends computer 11.10 and reinstalled the os. and now I dont want to mess it up again.

anybody have any suggestions?
 I will do anything to get this working! please!

---

### Post by kamaji792 on 2011-12-16
> and when I copy and paste the code how do I save it? and reboot the computer? do I just copy paste and close terminal?

It does depend what code you are talking about.  Looking at the links you posted they appear to be text you have to enter into a terminal.

So for:
> Open file:
sudo nano /etc/modprobe.d/alsa-base.conf

Add this to the bottom:
options snd-hda-codec-realtek index=-2

Open a terminal and at the command prompt type:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```

Press the Return or Enter keys, enter your password.
This will start the nano editor that will run in the terminal.

Now go to the bottom of the file and add the following line:
```
options snd-hda-codec-realtek index=-2
```

I hope that helps k

---

### Post by joshcanfield on 2011-12-16
ok I have gotten that much i am asking this... after I add the new line what then? should it automatically do something? or is there some way to save what I typed? or do I simply just close the terminal after i type the code in?

it says modified at the top right corner of the window when i start typing and if I open the file a second time non of the stuff I added is there anymore.

EDIT: ok so i realized that there is a menu at the bottom that shows how to close and save. I hit "ctrl" "X" and saved and exited it so I reopened my banshee and tried to play the mp3 I added to my computer to test it and it still didnt work. my headphones work great but my internal speakers still don't work

---

### Post by anewguy on 2011-12-16
Try rebooting.  A change to that file probably doesn't "take" until a reboot, unless you also find some text about doing a "modprobe xxxxxxx" in which case you would use the modprobe to load/update the module to the kernel.

Dave ;)

---


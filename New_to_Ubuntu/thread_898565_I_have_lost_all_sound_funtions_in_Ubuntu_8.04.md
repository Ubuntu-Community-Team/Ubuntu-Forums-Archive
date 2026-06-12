---
title: "I have lost all sound funtions in Ubuntu 8.04"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Bryan P on 2008-08-23
I am rather new to Linux and installed Ubuntu a week ago and all was well untill a night ago. I was customizing my desktop and was trying to also change the sounds that play when the login screen appears. I tryed to change the sound that first sounds ,"the intro"of the login screen in home/user/shared/sound and was not able to add additional wav files. I noted that the permissions were owned by root and not user, so I looked for a way to become user. On the Ubuntu website I found a document explaining root permissions and how to install a launcher in the panel for drag and drop abilities. I the command I gave the launcher was, gksudo "gnome-open %u" and I then draged and droped the home/user/shared/sound folder to this launcher. I then asked for my password and I was then able to add the wav file of my choise. But this still did not work for the login sound play back. I gave up for the time being and moved on to other things. I then found that any application that out puts sound has lost that ability. The application opens fine but no sound. I have re-installed these applications which did not fix the problem.

Does any know what went wrong? and how to fix it? I can just reinstall Ubuntu but that would not be very sporting as the challenge is to fix the things I FUBAR and not just run from then. 

Any help would be great.
BP.

---

### Post by cwsnyder on 2008-08-24
It sounds like you _moved_ your /home/user/shared/sound folder to the /home/user/desktop folder in a launcher, rather than _copied_ the files to the launcher.  You are probably going to have to recreate the folder.  If you are using the GNOME desktop environment the terminal commands are: 
sudo mkdir /home/user/shared/sound [use this if the folder is gone]
cp /home/user/desktop/*folder_name* /home/user/shared/sound
where *folder_name* is the name of the folder found in Places >> Desktop.

I hope this helps.

cwsnyder

---

### Post by Bryan P on 2008-08-24
Thanks,
I checked it out and the sound folder is still where it belongs. I was incorrect in the first thread though. The folder that dragged and dropped to the desktop launcher was /user/shared/sound  not /home/user/shared/sound. In any case I can still navigate to this folder and see the files there. Nothing got moved, the only thing that should have happened was the launcher should have given me a window of opportunity as "sudo" so that I could add a new .wav file to the above mentioned folder, which it did. The new .wav file is in the sound folder along with all of its original files and other various folders. I also checked out to see if my sound driver was still installed and it was. I have run out of ideas.

Any other suggestions? I will try anything at this point.

---

### Post by cwsnyder on 2008-09-07
I will have to say, I don't have enough expertise to make any more suggestions.

---


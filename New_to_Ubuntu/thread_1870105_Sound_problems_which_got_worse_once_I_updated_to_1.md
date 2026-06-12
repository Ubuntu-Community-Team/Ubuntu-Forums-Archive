---
title: "Sound problems which got worse once I updated to 11.10"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by does not compute on 2011-10-26
With the old version, I was able to go into alsamixer, through the terminal or just clicking it. Problem then was I always had sound but my mic wasn't/isn't working, or couldn't be heard through skype etc.

I can always hear the other party too so I just type back. Well that's still like that but now if I plug in my headphones I can't get sound, I also can't get into alsamixer even though it's installed, tried uninstalling it and reinstalling but no dice.

I can get into the terminal but headphones is up full it says. I can't get into the proper alsamixer to see if it's muted or what.

Also, I'm getting this panic occurred error, seems like a windows blue screen. I guess a full reinstall is required but I can't do that just yet as I've nothing to back up my files onto just yet.

The no mic thing is my biggest problem though, I looked through threads about sound problems but haven't seen anything about just mic problems, people seemed to have just no sound and the installation of alsamixer and unmuting seemed to fix them up.

Any help would be much appreciated, cheers.

---

### Post by does not compute on 2011-10-29
Bump.

The main problem is my mic isn't working. Anyone have any idea? Cheers.

---

### Post by realitykid on 2011-10-29
It's best to try a reinstall if you can. The way I did it, so I wouldn't lose everything, when I needed to was to reinstall Ubuntu without reformatting the drive. You can do this by clicking "Custom" (I think) when it gives you installation options.

A list of your partitions should come up. Select the partition in which Ubuntu is installed and click the "Edit" button. Select ext4 in the format drop down menu, but uncheck the format option. Then edit the mount point so that it reads "/" (without quotations).

Or you can remove alsa for now and install pulseaudio until you can get something to back up your important files. Either way, give it a shot and see what happens.

However, if you do choose the installation method, make sure that it doesn't tell you that you'll lose all the data on your drive.

I hope this helps. It's the best I can do at 3:53 am and from memory.

---


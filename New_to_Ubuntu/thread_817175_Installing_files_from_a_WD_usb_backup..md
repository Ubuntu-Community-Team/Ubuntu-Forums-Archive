---
title: "Installing files from a WD usb backup."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-06-03
Hi All,

As a newbie all is going great and loving ubuntu.

I wanted to move a couple of music files to my Ubuntu from a western digital usb hardrive. Plugged it in and showed up no problem.

Thought maybe I would get lucky and just drag the files to rhythm box but no luck. Did it the manual way. Seemed to work fine and played music ok.

I know all you linux pros can see this coming. *S*

Unplugged the usb drive and launched the music player and all the music was there for about 5 seconds then vanished.

Any suggestions ?

bikinguy

---

### Post by bikinguy77388 on 2008-06-03
Sorry guys,

Forget to add they were backed up from win2000 using the synkback software.


bikinguy

---

### Post by bumanie on 2008-06-03
Have you installed all the necessary codecs? If not, in termainal cut and paste this command > sudo apt-get install ubuntu-restricted-extras

---

### Post by ajgreeny on 2008-06-03
Sounds as if you were simply playing the files (reading them) from the external drive.  When you unplugged it they didn't show any more.

When you say "Did it the manual way" what do you mean?  It seems to me that you need to copy the files to your internal drive in some way, either just by dragging, which you seem to have failed with, or by using rsync or grsync or even good old cp in the terminal.  Once they are on your internal drive there should be no further problem.

Can't be codecs missing that's causing the problem (though they might be) as that would not stop them showing, just playing.

---

### Post by bikinguy77388 on 2008-06-03
Thanks guys

Will try the sudo command first.

I copied the files over to the rhythm box and played them from the program. Must have some other software involved from the syncback software.

bikinguy

---

### Post by bikinguy77388 on 2008-06-03
Well,

Had a major 'DUH" attack. Sure just dragged it to the desktop and assoc it with rythum box. 

That sudo command loaded alot of stuff...looks like some video as well...cool.

---

### Post by bumanie on 2008-06-03
If you have not installed all the video codecs (assuming you are using hardy heron) > sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list then > sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update followed by > sudo apt-get install libdvdcss2 and then > sudo apt-get install w32codecs (change the 32 to 64 if using a 64bit OS). Would also suggest installing vlc player. It is good for nearly all codecs, even plays vob files. > sudo apt-get install mozilla-plugin-vlc

---

### Post by cosine352 on 2008-06-03
ajgreeny if right. I had the same problem (?). You need to copy the files in your internal HD and then add to the player. That solved my problem.

---


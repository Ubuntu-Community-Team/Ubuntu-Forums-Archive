---
title: "upgrade 10.10 to 11.10, many small problems"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by aneblanc on 2012-11-07
I have just upgraded from 10.10 to 11.10 and I wonder now if I would have had to.

I have a netbook Mini Dell with 8gB internal memory and a 16gB memory card.

1. I used to be able to get the launcher only in going to the top left corner, now everytime I hit the whole left side of the screen with the cursor I get it. How can I get back to the top left corner only?

2. It used to be very easy to format my MP3 with a right click. I don't even find the MP3 when I plug it in. Now I have to open a disk utility program. I have plenty of options that I don't really understand like format the volume or format the drive. How can I simply format the MP3 to clean it so that I can load new stuff on it?

3. I used to close the laptop lid and the computer would shut down. How can I do that?

4. My microphone automatically slides back so that it is impossible to skype anymore. How can I change that?

5. It takes at least twice as long to start Ubuntu. How can I shorten the start time?

That would be the first questions I have,

Thanks

---

### Post by Kevin McCready on 2012-11-07
Sorry to hear about all your problems. I guess going back to the earlier version isn't possible? Why did you want to upgrade?

---

### Post by aneblanc on 2012-11-07
Thanks to take pity!

I solved one of the problem, I installed advanced settings and I can now close the lid to shut down the computer.

My biggest issue is the computer shutting down when I unplug it (another problem I did not mention). 
I have this answer: 

[I]For 11.10 run:
gsettings set org.gnome.settings-daemon.plugins.power 'use-time-for-policy' 'false'[/I]

in [http://askubuntu.com/questions/65889/computer-shuts-down-when-unplugged](http://askubuntu.com/questions/65889/computer-shuts-down-when-unplugged)

but I still don't know what to do in order to run!

---

### Post by aneblanc on 2012-11-07
> **Kevin McCready said:**
> Why did you want to upgrade?

Oh, and I upgraded because the update manager told me that programs would not be supported anymore.
I realise now it was a hasty decision!

---

### Post by mikewhatever on 2012-11-10
While an upgrade from 10.10 was a good idea, as it's no longer supported since April 2012, IMHO, a clean install of 12.04 would have been a better choice. 11.10 will reach End of Life in April 2013, but 12.04 got a five year support cycle, also, Unity is more mature in 12.04.

1. I've not used 11.10 much, but have seen tools and howtos for managing Unity components. Try searching, it shouldn't be hard to find.

2. Formatting seems like an overkill for that. Just select everything on the MP3, and press Shift-del.

3. Not sure. I think the default behavior has always been to suspend.

4. Skype has a setting for that in its sound preferences. It's on by default, so Skype mutes the mic when it deems necessary.

5. What exactly takes long, from Grub to login, or from login to the desktop?

To apply the power management workaround, simply copy/paste that command into a terminal window and hit Enter. Varify that the value got changed with 
```
gsettings get org.gnome.settings-daemon.plugins.power 'use-time-for-policy'
```

---

### Post by aneblanc on 2012-11-10
> **mikewhatever said:**
> While an upgrade from 10.10 was a good idea, as it's no longer supported since April 2012, IMHO, a clean install of 12.04 would have been a better choice. 

I read a bit more and also realised the fact. I upgraded again to 12.04 LTS. My problems are all gone
Regarding the MP3, it must be a fault, when I delete the files it doesn't work. I always have to format to make room. The MP3 is getting old, maybe 6 years.

Thanks for your help.

---

### Post by mörgæs on 2012-11-10
Good. If the problem is solved, please mark the thread so.

---


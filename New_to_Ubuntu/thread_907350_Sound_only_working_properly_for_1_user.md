---
title: "Sound only working properly for 1 user"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by zero_koop on 2008-09-01
I have 2 admin users on my computer.  The one I initially set up with the new installation has sound working fine in all areas.  The other user, added later, only has sound when playing mp3s in Amarok (not sure about other players) and when hovering the mouse over an mp3.  All other sound (such as video, dvd, flash websites, startup music, etc) does not work.  I've looked all over the volume controls on both the system and the program in use and none are muted or turned down.  Also, my Sound Preferences are the same for both users.  Any idea where I can check to see whats going on here?  I appreciate the help.

---

### Post by django0909 on 2008-09-01
Try this. It's from [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), which is 2 years old, but I don't see why it doesn't apply.

**********************************
A very common cause for a user to not have sound is not having his/her username in the /etc/group.


```
grep 'audio' /etc/group
```

You should see a line similar to


```
audio:x:29:
```

followed by a username i.e. if the username is "ubuntu" then you should see


```
audio:x:29:ubuntu
```

If you see something else i.e.


```
audio:x:29:root
```

you should add your username to the file by doing


```
sudo nano /etc/group
```

. Now find the line that looks like


```
audio:x:29:root
```

and change it to


```
audio:x:29:root:moocow
```

only replacing moocow with your real username.

Hit CTRL + 0 to save, then CTRL + X to exit. 

***********************************

Hope that did it! Post back if it did.


--django

---

### Post by zero_koop on 2008-09-01
here is the output from that first command:
> audio:x:29:pulse,username1,username2
I replaced the actual user names.  So I don't believe that is the problem because both users seem to be in place properly.  Any other ideas?  Keep in mind that audio does work for the troubled user in 2 specific cases (in Amarok and when hovering the mouse over an mp3 or ogg file in the file browser).

---

### Post by django0909 on 2008-09-01
It might not make a difference, but the usernames need to be seperated by colons, and not commas...

---

### Post by zero_koop on 2008-09-01
Nope, that didn't work either.  I changed the commas to colons and even restarted, but it didn't change anything.  Since the usernames were separated by commas everywhere else in the file I changed them back after I tested it, so I think you may be mistaken about the colon thing.  This is really frusterating, does anyone else have any ideas?

---

### Post by django0909 on 2008-09-01
Very strange.

Try Alsamixer,

```
sudo alsamixer
```

Does everything look normal? Are all the levels on the 'shared' section up far enough?

--django

---

### Post by zero_koop on 2008-09-01
Things do look normal, although I've never used that command before.  My master is up high and changes when I adjust the volume from the desktop control.  I don't understand what you mean by the "shared" section?  I can switch the view by using tab and I can adjust the volume of the controls by using the arrow keys, but I don't see anything that says "shared".  Can you clarify?  Thanks.

---

### Post by django0909 on 2008-09-01
Sorry, I'm confusing myself now.

If you scan along to the last four faders, they should be specific to your sound card. Make sure they are all on max, and try playing with the rest of the faders to see if you get any difference.

I can't think what else might be causing you bother :S

--django


Oops. Don't put them all on max, about 3/4 is sufficient :)

---

### Post by zero_koop on 2008-09-01
I assume by faders you mean the volume adjustment bars.  Along the bottom the faders I have are Master, Master M, 3D Contr, 3D Contr, 3D Contr, PCM, Surround, and Surround.  As you can see a few repeat, but they are different because I can adjust them to different levels.  3 of them have an "MM" just under the bar, 3 others have "00" including the Master one that works with my normal volume control.  Any idea what those mean?  Maybe the MM means muted, but I'm not sure how to get at adjusting them.  I think I've gone through every device in the Sound Preferences to make sure nothing is muted.

---

### Post by django0909 on 2008-09-01
Thats what I mean by faders, yes. The up/down keys adjust them....

Did you get anywhere?

---


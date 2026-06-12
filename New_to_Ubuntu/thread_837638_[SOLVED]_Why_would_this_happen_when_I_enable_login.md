---
title: "[SOLVED] Why would this happen when I enable logins"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by hufferd on 2008-06-22
Please read my post about sound issues [here]("http://ubuntuforums.org/showthread.php?t=836187") And then I will ask the question

So as you were reading in my other post I was having sound issues ONLY after I disabled the automatic login function. If I leave automatic login turned on I dont have any issues with sound at all.  

As you can read there if I disable the automatic login I also then can not play back music or any videos..... And here is the kicker after some more playing around I found out that system sounds in general work - under either setting.  

I have not as of yet set up any other users for my system the only thing I was doing was turning OFF the automatic login function. 

So bottom line is this 

If automatic login is on = I have sound,music and video play back.

If automatic login is off (ie. I have to sign in with my user name and password) = I only have SOME sounds enabled and I lose music and video playback....

What in the world is going on - Im not switching users just turning auto login off.. 

Anyone have any ideas?

~D:confused:

---

### Post by hufferd on 2008-06-22
bump :)

---

### Post by hufferd on 2008-08-07
Bump - 

Sorry trying to clear up some old isses that I still am having...  And have not been able to find answers 


D

---

### Post by silverglade00 on 2008-08-07
Just a quick thought... you might want to make sure that both your account and your girlfriend's accounts are added to the audio group. 

System -> Administration -> Users and Groups. If the Unlock button is available, press it and enter your password. Then double click your username. Click on the User Privileges tab and make note of the checked boxes. Click cancel and then double click her account. Make sure all of the relevant boxes are checked.

I had a problem on Red Hat once where only the root user could use any audio until I changed the permissions on /dev/audio. That's what made me think of this.

---


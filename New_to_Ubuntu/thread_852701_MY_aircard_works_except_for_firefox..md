---
title: "MY aircard works except for firefox."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-07
I'm so close after months of toil trying to get this aircard working.   I got it to work for skype and thats all I can tell.  firefox is in offline mode and can't surf the internet.  Any suggestions?  Ideas?

---

### Post by lazyart on 2008-07-08
What happens when you untick "Work Offline"?

---

### Post by adamogardner on 2008-07-08
then the icon becomes two computers ie. no connection.  then I flip on kppp start and skype works firefox does not.  hmmmm..

---

### Post by lazyart on 2008-07-08
In Firefox, click File->Work Offline.  That should clear the checkmark and put Firefox online.

---

### Post by adamogardner on 2008-07-08
it didn't work.  nothing happened.  
I had to unclick that "work offline" box in order to send this and then It claimed I had no security tokens   so hopefully this one gets through.
question.  whats the difference between enable wireless, and enable networking?  I've only been unselecting the wireless.

---

### Post by lazyart on 2008-07-08
For whatever reason, the aircard is separate from networking.  The network manager applet (the one with enable wireless/enable networking) controls your wired or wifi connection.  If you disable wireless you turn off the wifi.  If you disable networking you turn off both wired and wifi connections.

Don't have my laptop right now but will look back this evening and see what's missing.  If skype works however, I don't understand why FF doesn't. :(

---

### Post by adamogardner on 2008-07-08
i dont' understand either.

---

### Post by adamogardner on 2008-07-10
B
.u
..m
...p
....!

---

### Post by sydbat on 2008-07-10
Dumb question, but how are you posting here? Are you using Firefox to do so? Is it through Ubuntu? Windows? Blackberry?

---

### Post by adamogardner on 2008-07-10
no I am on firefox.  I am on someones wireless who lives in this building (is that like stealing btw?)  It's built into my laptop.

---

### Post by timcredible on 2008-07-10
ff3 does a check for a network connection made my the network manager, if the network manager says there's no connection, then ff3 says it's offline.  in network manager, under wireless, uncheck roaming mode, that will set network manager to manual and it will tell ff3 that you're always online.

---

### Post by adamogardner on 2008-07-11
ok well so much for trying a new thread about finding my ipaddress, sub net mask,  gateway address, let alone my configuration, password typoe and network name and password.  
When I unclick roaming, those fields need to be filled in.  I don't get it.  I don't think I should post the output of ifconfig -a   should I?  
Also,  you do know I have a laptop, and roam which is why I bought an aircard.  I'm learning some aircards have modems or stuff like that.  not mine.   whats the deal?

---

### Post by adamogardner on 2008-07-12
bump|qmud

---


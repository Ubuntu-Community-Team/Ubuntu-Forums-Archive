---
title: "Oh oh..."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Lakeside on 2008-11-07
Oh, oh, what have I done now? Because my mysql info was not showing up in phpinfo.php, I decided to make sure it was installed, and entered 
sudo apt-get install mysql server, and got this:  
[sudo] password for b***y: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
I also got that when I entered sudo apt-get install gnome-device-manager. Hmmm, what have I done now :(

---

### Post by Bronto on 2008-11-07
You get that message because you have another package manager (synaptic maybe?) running.

---

### Post by Lakeside on 2008-11-07
Ahhh! Has to be my dumbest question so far..(shh don`t tell anyone lol)
Thanks Bronto you were right :)

---

### Post by Bölvaður on 2008-11-07
please have more descriptive title names... "Oh oh...." just just as well be "Pink ponies, my belly hurts".. no indication of what is happening :KS

---

### Post by Lakeside on 2008-11-07
I was hoping no one would catch that, sorry Bölvaður..I just didn`t know what to say, and it`s been a long day. :)

---


---
title: "Almost like this but need some final help, WMA and startup"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by iminhell on 2008-11-25
First off num lock disables on shut down and I have to turn it back on every time I restart. How can I enable num lock on startup?

Then I can not get Amarok to play WMA audio, I have all the proper codecs far as I know (good, bad, ...). It comes up with an error saying no decoder available. I can't find what I apparently need. Same issue with Rythembox. So that tells me some codec didn't take.
All my music is WMA (loss less) so I'm kind of upset on this one.


-John

---

### Post by unutbu on 2008-11-25
Have you tried Ubuntu-freak's Comprehensive Multimedia & Video Howto:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) ?
It is long, but it has helped a boatload of people.

And for the numlock problem, perhaps install the numlockx package.

---

### Post by mc4man on 2008-11-25
if you didn't get wma going  - for amarok
install libxine1-ffmpeg  (will enable everything but wma lossless

for wma lossless add w32codecs (from medibuntu repo - see above link for how to add or

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

or direct dl, install
[http://packages.medibuntu.org/intrepid/w32codecs.html](http://packages.medibuntu.org/intrepid/w32codecs.html)

[http://packages.medibuntu.org/hardy/w32codecs.html](http://packages.medibuntu.org/hardy/w32codecs.html)

if your running hardy (8.04) and enable medibuntu as repo source you'll get an upgraded amarok

---

### Post by iminhell on 2008-11-25
Nicely played mac4man.
It was "w32codecs" that I needed to play wma lossless. Working fine now.


Still have the num lock issue though, numlockx didn't change a thing.
I did forget to mention I am running 8.10, sorry about that.

---

### Post by mc4man on 2008-11-25
Good to see your using amarok, In 8.10 I'd stay away from depending on gstreamer players for anything more than a menu entry. (just my opinion 

As far as the numlock, the numlockx is just an on/off during a session.

Maybe look in preferences -> keyboard and see what layout it's set on / # of keys ect.  (not really up on that, mine is set as generic, 105-key and works fine thru reboot.

---


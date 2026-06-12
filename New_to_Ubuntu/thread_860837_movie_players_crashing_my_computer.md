---
title: "movie players crashing my computer"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by checkmateinc on 2008-07-16
Hey im new to linux so i was wondering if anyone can help? I just installed linux unbuntu 8.04, and everyt time i play a movie it crashes my computer.
 Im running a 6200geforce nivida card(256mb), my screen savers and all other video works fine. but when i use totem or any movie player it crashs my computer. i got a 2.00 ghz proccesor, the chip is a sempron 2800+(AMD). Any suggestions?

---

### Post by nanotube on 2008-07-16
> **checkmateinc said:**
> Hey im new to linux so i was wondering if anyone can help? I just installed linux unbuntu 8.04, and everyt time i play a movie it crashes my computer.
 Im running a 6200geforce nivida card(256mb), my screen savers and all other video works fine. but when i use totem or any movie player it crashs my computer. i got a 2.00 ghz proccesor, the chip is a sempron 2800+(AMD). Any suggestions?

as an easy first step- try a different movie player, and see if the crashes still occur.

i'd suggest looking at "vlc" and "mplayer".

---

### Post by OutOfReach on 2008-07-16
I had this problem, with my Intel graphics, for all video players. I found that the problem was Compiz. So I have to disable Compiz, by going to System>Preferences>Appearence>Visual Effects tab and choosing None, everytime I watch a video that isn't in Flash. Luckily I don't watch too many non-flash videos :P

---

### Post by OldGamer on 2008-07-16
I have also been having this problem since I upgraded to Hardy Heron, in all video players, but not in flash.  Sometimes it works if I open VLC first, and then open my video right from there, instead of just double clicking on it from nautilus.  I will try disabling compiz next time I want to play a video...

---

### Post by mc4man on 2008-07-16
> Hey im new to linux so i was wondering if anyone can help? I just installed linux unbuntu 8.04
you should benefit from reading thru here
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It is a bit extensive so for mainly dvds here's what I do from fresh install of hardy. Note at bottom a strongly suggested of  setting vlc as a  default player choice. At very least it's important to change the launcher command for vlc as noted (provides proper disk navigation)

[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

There may or may not be issues trying to add the medibuntu repo as normally  done (with a wget command) - read the edit.

The Very first thing to address is whether a region has been set on the drive. If you've ever played a commercial dvd with that drive (xp, vista, ect.) then it's been set. If your not sure open a terminal (Applications -> Accessories -> terminal) and paste this in
```
sudo apt-get install regionset
```
 press enter and after that runs _with a dvd in the drive_ paste this in the terminal and run
```
regionset
```
Here's what a set drive looks like
```
doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET   [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE
Would you like to change the region setting of your drive? [y/n]:n

```
If your drive isn't set then choose yes and enter the number of your region 1 for n.america, 2 for europe, see here for others
[http://en.wikipedia.org/wiki/DVD_region_codes](http://en.wikipedia.org/wiki/DVD_region_codes)
After a region has been set run thru either the commands from the sticky or my link and you should be good to go. (if not post back)

just to reinforce something - if someone gives you a command in a code box to run it is as above - copy and paste into an open terminal and press enter. ( my apologizes if too newbie)

---

### Post by checkmateinc on 2008-07-16
Thanks for the advise, i turned off compiz and it went longer then before but still froze. I don't know if it's because i was on the internet doing stuff trying to post, or what? I got 1gig of ddr, do you think I need more memory? If I do need more memory, would any of you know where to find out what the upgrades are for a AMD Sempron 2800+ 2.0Ghz? Im thinking I need more memory but I'm not really sure?

---

### Post by checkmateinc on 2008-07-16
Oh yeah I already got vlc and gplayer installed and both of them freeze up my computer too. All the movie players are.

---

### Post by checkmateinc on 2008-07-16
switching my totem player to xine instead of the gsstreamer thing seems to be working, thanks

---

### Post by checkmateinc on 2008-08-08
reinstalling totem xine works haven't froze in 2 days

---


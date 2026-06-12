---
title: "Modem trouble"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by moltar512 on 2008-11-29
sorry if this is an old topic, but i've looked in the forums and I can't really find anything that helps.

Recently, my mom got an old Dell computer from someone she works with.  I put windows xp on it, and everything was fine... until she got a virus.

Now, i've set the computer up with a dual boot of windows and ubuntu 8.10 (Intrepid Ibex, downloaded Wednesday night).  I'm actually on it right now;  I brought it to her for Thanksgiving.  

The problem is that she has dial up.  The windows dial up I set up in like 5 minutes.  At my house, where I have cable internet, I already updated ubuntu and installed updates.  My problem is that I can't figure out how to set up her modem under ubuntu.  

I was reading some thread last night ([http://ubuntuforums.org/showthread.php?t=988472](http://ubuntuforums.org/showthread.php?t=988472)) trying to figure out how to get it to work.  I tried "sudo wvdialconf", but it says that there was no modem detected.  

Is there some sort of ubuntu driver that I have to load to make it recognize the modem?  Windows Device manager says I have a "Conexant D850 56k V.9x DFVc Modem".  Like I said, under Windows all I had to do was load the drivers from the Dell website, so this driver works fine.

How do I get linux to recognize the modem and get dial up networking to work?

---

### Post by endoubt on 2008-11-29
This seems like a better guide. I don't have any way of testing it myself because I haven't had a phone line since 2001.

[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html]("http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html")

---

### Post by jimmy the saint on 2008-11-29
There may be a way to get the modem working.  I did not look up that specific model, but thre are a few softmodems that have software to make them work with linux.  They are ALWAYS a pain in the butt.  Look online for an old usrobotics serial modem or for a new zoom serial modem.  The problem is that most newer modems are designed to have the software (designed for windows) do all the work (hence "softmodems").  Some even rely on widnows itself(winmodems).  You need a "hardmodem" which does all the work itslef and is, therefore, platform independent.  

I purchased my grandmother a zoom hardmodem for $60 at Office Depot and it worked like a charm.  Plugged it in and it worked right away.  I spent two days trying to get the "solutions" working with the softmodem that came in the PC to work, but it was just not worth it.  

Good Luck.

---

### Post by lswb on 2008-11-29
For an internal softmodem like jimmy describes, check out this site:
[http://linmodems.org/](http://linmodems.org/)

and follow their instructions for the scanmodem program. Some of the are not too tough to get working, but I agree that a full hardware modem is much easier to set up.

---

### Post by Andavane on 2008-11-30
> **lswb said:**
> For an internal softmodem like jimmy describes, check out this site:
[http://linmodems.org/](http://linmodems.org/)

and follow their instructions for the scanmodem program. Some of the are not too tough to get working, but I agree that a full hardware modem is much easier to set up.

A useful link, Thanks.
With my laptop I think that the game may not be worth the candle;
the link says download the scanmodem tool, but not sure how to do that if it won't connect to the net.

Am currently writing this on an old IBM; Windows XP.

I think jimmy the saint in the previous post has a valid point, to get hold of a generic "hard" modem, and let it do all the work. Will do that early January 2009.

Kind regards

John

---


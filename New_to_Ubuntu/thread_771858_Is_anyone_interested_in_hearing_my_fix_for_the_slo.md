---
title: "Is anyone interested in hearing my fix for the sloooow main menu?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by oakgrove on 2008-04-28
I love Gnome but I hate the huge "Applications|Places|System" buttons.  So, I opted to replace them with the all in one menu button.  Only problem is, unlike the long bar that works basically instantly, you press the menu button and it takes what seems like forever (probably only about 3-5 seconds) to pop the menu up.  I looked everywhere for a solution to this, found a few suggestions, tried them, and was disappointed at their complete lack of effect.  There doesn't seem to be any way to force it to cache itself.

Well, I seem to have found an almost perfect solution :)(at least it's working for me) that makes the menu button just as snappy as the whole menu bar.  If anyone's interested in hearing it, reply and I'll type it in.

---

### Post by southernman on 2008-04-28
Why don't you just go ahead and write up a nicely formatted howto for it. I'm sure someone, at some point in time, will use and benefit from it. After writing it, you can post it in tips and tutorials... [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

How's hotlanta? we're practically neighbors.

---

### Post by daimaru on 2008-04-28
> **oakgrove said:**
> I love Gnome but I hate the huge "Applications|Places|System" buttons.  So, I opted to replace them with the all in one menu button.  Only problem is, unlike the long bar that works basically instantly, you press the menu button and it takes what seems like forever (probably only about 3-5 seconds) to pop the menu up.  I looked everywhere for a solution to this, found a few suggestions, tried them, and was disappointed at their complete lack of effect.  There doesn't seem to be any way to force it to cache itself.

Well, I seem to have found an almost perfect solution :)(at least it's working for me) that makes the menu button just as snappy as the whole menu bar.  If anyone's interested in hearing it, reply and I'll type it in.
wow the only thing missing here is your link to go to [www.buymystupidassipod.com]("http://www.buymystupidassipod.com") where you can get the password for the super amazing answer on the 5878's line where it says "I don't give a **** <insert crap here>". :lolflag: just kidding why don't you just post your solution mate?
no offense intended. but for anyone who wants a way to make the menu more responsive just install "preload"
```
sudo apt-get install preload
```

---

### Post by oakgrove on 2008-04-28
> wow the only thing missing here is your link to go to [www.buymystupidassipod.com](www.buymystupidassipod.com) where you can get the password for the super amazing answer on the 5878's line where it says "I don't give a **** <insert crap here>".

That's golden, I'll have to remember to do that next time.  My solution (which I'll get to in a second) is actually very simple, I just wanted to make sure somebody was interested.  For all I know, this could be an issue that only I cared about or one that was solved ages ago and I just need to get with the program.  Also, you'll probably notice by my name, I've posted something like 25 times on here and I've asked several questions, none of which have ever been answered.  I don't mean to sound like sour grapes or anything and I know my questions tend to be a little off the beaten path but it is a bit frustrating to not ever get a single response.

Anyway, enough about that.  The thing about the main menu is, unlike the menu bar, it isn't cached.  You can't just cache your icon set either, that doesn't work.  And preload doesn't fix this issue.  I had preload on my 7.10 install and now on my 8.04 install and it's never done anything about the slow loading of the main menu.  However, and pay attention because this is where the magic happens, if you have the menu bar and the main menu on your panel simultaneously, just by virtue of the menu bar being cached, the main menu gets cached also, since the menus inside of both applets are the same just configured a little differently.  Only problem is, you're right back where you started with a big old menu bar on your panel that you don't want along with the main menu that you do want.  

My solution was to just add a drawer to the panel and simply put the menu bar in it.  Of course, I do have a drawer on there now but it's a lot easier to live with a little picture of a drawer than the whole bar sitting on there staring at me.  This works perfectly, and now my main menu is cached so that when I boot up my computer, and click on the button, the menu pops up immediately instead of my having to wait several seconds for it to wake up.  This makes quite a difference when you are demoing your box to your Windows using friends and they're snickering because your "Start" menu is so slow.  Especially when your demo box is a Core2Duo with 2 Gigs of RAM.  Think what you want, but it solves the problem quite easily and as far as I can tell, this is the only solution yet though I'd be happy to be corrected on that.

Nice to hear from a fellow southerner, Southernman.  And the Atl is treating me great these days.

---

### Post by PhoenixP3K on 2008-04-28
> **oakgrove said:**
> [...]Also, you'll probably notice by my name, I've posted something like 25 times on here and I've asked several questions, none of which have ever been answered.  I don't mean to sound like sour grapes or anything and I know my questions tend to be a little off the beaten path but it is a bit frustrating to not ever get a single response.[...]

I spend some time in the forum, but most of the time I just don't know the answer to peoples questions. Whenever I can contribute I do, but most of the time if you have a new thread with a question and it gets buried quite fast. If no one with the answer got to see it in time you can always wait a while and bump the question back up.

---

### Post by Lemvigh on 2008-04-29
Aaah!! I've often had to wait for 10 seconds - and sometimes longer for the main menu to appear. It's so frustrating that I have to wait longer for the menu to load, than to launch many of the apps it contains...

This solution is a bit unsatisfying, I would like to think, there was a more direct way to do the same, but it's the only thing I've tried that worked. Thank you very much for sharing it!

---

### Post by spiderbatdad on 2008-04-29
Mine opens instantly except the first time after a restart...then it takes an entire second. I had no idea this was an issue.

---


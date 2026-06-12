---
title: "Hardy Heron doubts"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Ghaarnok on 2008-05-09
Well, I'm no ubuntu expert, I'm quite the noob really. But I've gone from gutsy gibbon to hardy heron and I must say that whilst, on the whole, many things work and are fine, I still have a few gripes...

Performance...
I'm not sure why but it feels like hardy heron is bloated. I feel like I'm back to XP standards on loading times and so on. Essentially, hardy heron feels like a memory hog.

Crashes....
In gutsy gibbon I rarely had program crashes, however in hardy heron I seem to be getting more crashes and windows "graying out" more often.

Firefox....
Don't get me wrong, I love firefox. I work as a web developer and I love everthing about firefox .... but using a beta of firefox 3? I quite like firefox 3 so far but I don't think a beta version should have been included in the latest version of ubuntu.


Overall I'm a linux noob. But hardy heron just feels not right. It feels like it has somehow been rushed and is incomplete. I hear people say that the stability of linux is amazing but Hardy Heron feels like a let down.

---

### Post by Ghaarnok on 2008-05-09
Oh and another thing...

I seem to have pink drop shadows on all the windows open. I know they shouldn't be pink and they are normally grey. However, it seems to be pink drop shadows for me. Interestingly if i change theme the pink shadows are replaced by what they should be. But, should i have to do that every time i boot into ubuntu?

---

### Post by dStrom on 2008-05-10
I'm having the same issue  ... currently using a nvidia geforce 8400 gs

---

### Post by dRock1286 on 2008-05-10
yeah.  pink drop shadows for me too.  using an nvidia 8500 gt.  not really liking it so anyone know of any fixes?

---

### Post by Perfect Storm on 2008-05-10
The problem is the current Nvidia driver that Hardy uses. It's latest stable from Nvidia but also the buggiest. What to do is installing the beta driver,, though it have some glitches as it's a beta driver.


You don't have to use Hardy, if Gutsy works best for you, use it instead., then wait a 3 month and try hardy again when alot of patches have been added.

---

### Post by dRock1286 on 2008-05-10
Since I don't really use my comp for gaming anymore (quit WoW and went fully Ubuntu), do I even need a driver for my nvidia card?  Rather, is there a default driver I can choose to use to rid this?

---

### Post by Perfect Storm on 2008-05-10
Yes, but I don't know how well you can use compiz with it. But your Desktop may also be less responsive.

Here's what you do;

Open the terminal, and type;
```
sudo nano /etc/X11/xorg.conf
```

Find 
[b]Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
[/b]

change "nvidia" to "nv"

Save [ctrl]+[o], exit [ctrl]+[x]
Restart X [ctrl]+[alt]+[backspace]

---

### Post by dRock1286 on 2008-05-10
FYI to anyone trying this, can't use any desktop effects at all...it sets the Visual Effects to "None" and won't allow you to change to "Normal".  I think I'll just accept the pink shadow and go back...thanks anyways though!  :D

---

### Post by FuturePilot on 2008-05-10
The fixed driver for the pink shadows is in Hardy Proposed. If you give it a few days it should come through the regular updates.

---

### Post by dRock1286 on 2008-05-10
Thanks.

---

### Post by Ghaarnok on 2008-05-10
It's good to hear that the pink drop shadows are a recognised problem. Incidentally I'm running a 8800GT.

I would switch back to gutsy gibbon but I don't want the hassle of re-installing everything. I'll just wait for updates on Hardy Heron.

It still does feel "rushed to market" though.

---

### Post by Perfect Storm on 2008-05-10
> **Ghaarnok said:**
> It's good to hear that the pink drop shadows are a recognised problem. Incidentally I'm running a 8800GT.

I would switch back to gutsy gibbon but I don't want the hassle of re-installing everything. I'll just wait for updates on Hardy Heron.

It still does feel "rushed to market" though.

So was gutsy when it was released and feisty before that etc. etc.
When a couple of month have past it should be good.
Ubuntu is the thing between the latest and the stable, so there'll be some rough edges all the time.

---

### Post by Ghaarnok on 2008-05-10
> **Artificial Intelligence said:**
> So was gutsy when it was released and feisty before that etc. etc.
When a couple of month have past it should be good.
Ubuntu is the thing between the latest and the stable, so there'll be some rough edges all the time.

I was guessing this to be the case. Like I say, they're only minor niggles I have with it, on the whole I'm quite happy with the latest release. I think I was perhaps expecting too much from it.

---


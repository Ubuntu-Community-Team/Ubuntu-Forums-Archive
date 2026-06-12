---
title: "Stuck in Ubuntu 2D hell"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by qaissi on 2011-09-28
I can not get back to the Ubuntu normal desktop with Unity.  

I have tried:

Ctrl+Alt+F1 and then doing

unity --reset and it does not complete

I have tried:

Ctrl+Alt+F1 and then doing

sudo apt-get update

sudo apt-get upgrade

This completed and then when I tried rebooting and selecting the Ubuntu option in the logon screen it still takes me to a blank desktop with the Nautilus menu across the top and nothing else.

No Unity

Any ideas?

---

### Post by dino99 on 2011-09-28
make huge clean up :)

purge *unity* *compiz* from synaptic, then reinstall

to have nautilus menu off:
gnome-panel --replace

and if necessary
metacity --replace

---

### Post by qaissi on 2011-09-28
ok and how do I do that when I can only do Ctrl+Alt+F1?

Nothing else besides Nautilus is working.

---

### Post by dino99 on 2011-09-28
sudo apt-get purge ...

---

### Post by qaissi on 2011-09-28
Well that was fun - not!  lol

So I purged Unity and Compiz.  When I rebooted the only option I had left for logging into 11.10 was Ubunty 2D.

That brought me back to the same issue - I log into my desktop and the menu bar for Nautilus only in the top panel.  No notification area at all.  And no unity of course.

So I Installed Unity and compiz again and upon reboot I now have the option to log in with Ubuntu and Ubuntu 2D both of which got me back to the same situation.

I did a gnome-panel --replace which gave me the log in option of Ubuntu Classic and Ubuntu Classic(No Theme)as well as Ubuntu and Ubuntu 2D

None of this is getting me anywhere though it is nice to be able to log into the classic ubuntu with gnome 3.

But I still can not log into just plain Ubuntu and get anything other then my desktop, no notification area, no unity, and the top panel showing the Nautilus menu.  When I use Ctrl+Alt+F1 I get a black screen asking for my user ID and password - basically a terminal running full screen.

When I do a unity --reset I get a lot of things happening on the screen until it gets to setting-update "Run_Key" where it stalls out.

Any further suggestions or should I just reinstall?

---

### Post by qaissi on 2011-09-28
No more ideas?

---

### Post by ventrical on 2011-09-28
> **qaissi said:**
> No more ideas?

Go to the terminal and install:

sudo apt-get install fvwm-crystal

then  log onto that DE, find your way through to synaptic (or if you do not have synaptic then use the gnome terminal and :

sudo  apt-get install synaptic

and see if that can get you started.

---

### Post by ventrical on 2011-09-28
If worse comes to worse...


sudo apt-get install fglrx

for video driver probs..

it worked for me once and I had the exact same problem

---

### Post by thatguruguy on 2011-09-28
> **ventrical said:**
> If worse comes to worse...


sudo apt-get install fglrx

for video driver probs..

it worked for me once and I had the exact same problem

Did he say that he has an ATI graphics card?

---

### Post by thatguruguy on 2011-09-28
> **qaissi said:**
> I can not get back to the Ubuntu normal desktop with Unity.  

I have tried:

Ctrl+Alt+F1 and then doing

unity --reset and it does not complete

I have tried:

Ctrl+Alt+F1 and then doing

sudo apt-get update

sudo apt-get upgrade

This completed and then when I tried rebooting and selecting the Ubuntu option in the logon screen it still takes me to a blank desktop with the Nautilus menu across the top and nothing else.

No Unity

Any ideas?

What kind of graphics card do you have?  What drivers do you have installed?

---


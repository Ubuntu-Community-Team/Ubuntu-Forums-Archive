---
title: "Help!! Upgrade to Hardy !!!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by ALex! on 2008-04-24
Today I was downloading my upgrade from Gutsy to Hardy via the Update Manager... It took a long time, but when it was about to finish, something went wrong with my Firefox surfing and my computer restarted...

Now I can't restart my Upgrade again!! :cry: There is a message asking whether I'd like to do a partial update.... I decided to click The upgrade to hardy heron in the window... but when it starts... nothing happens!!! :( 

What should i Do?! 

Please help me!!! :cry:

---

### Post by Paqman on 2008-04-24
Try putting
```

sudo dpkg --configure -a

```
into a terminal. Then run the Update Manager again.

---

### Post by ALex! on 2008-04-24
oh! thank you... but what's that for?

---

### Post by ptcbus on 2008-04-24
YOu are better off using torrents. Much much much faster with torrents compared to the ubuntu servers which are way overcrowded today. See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by ALex! on 2008-04-24
but... is all my progress lost?! i had just like 1 hour left!

---

### Post by Paqman on 2008-04-24
> **ALex! said:**
> oh! thank you... but what's that for?

Good question!

If the package management system gets interrupted while working this command will tell it to resume configuring where it got stopped. In fact if you try to install using the command line after this happens you'll see it'll explicitly stop and tell you to use this command to restore things to an even keel.

Your progress won't be lost. The package manager caches things as it downloads them.

---

### Post by ALex! on 2008-04-24
> **Paqman said:**
> Good question!

If the package management system gets interrupted while working this command will tell it to resume configuring where it got stopped. In fact if you try to install using the command line after this happens you'll see it'll explicitly stop and tell you to use this command to restore things to an even keel.

Your progress won't be lost. The package manager caches things as it downloads them.

OMG! brilliant...!

---

### Post by Paqman on 2008-04-24
> **ALex! said:**
> OMG! brilliant...!

Of course, you did say your machine crashed while the package manager was working. So things may not work exactly like they're supposed to...fingers crossed, eh? :)

---

### Post by ALex! on 2008-04-24
Thanks To Everyone That Took The Time To Help A Newbie Like Meeee!!! =D

---


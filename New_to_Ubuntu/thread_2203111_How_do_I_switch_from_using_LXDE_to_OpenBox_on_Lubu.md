---
title: "How do I switch from using LXDE to OpenBox on Lubuntu?"
date: 2014-02-01
forum: New to Ubuntu
---

### Post by Punchy71 on 2014-02-01
Greetings,
  I just finished installing Lubuntu on my laptop and was wanting to know how to switch from the default LXDE desktop environment to using the OpenBox desktop environment? On [the Distrowatch page dedicated to explaining Lubuntu,]("http://distrowatch.com/table.php?distribution=lubuntu") it mentions that Lubuntu uses either LXDE *OR* OpenBox. 

Thank you

---

### Post by Dave_L on 2014-02-01
At the login screen, you don't have a menu for selecting the session type, e.g. lxde or openbox?

---

### Post by Dennis N on 2014-02-01
Lubuntu 13.10: The top panel on the login screen has 4 icons on the right. The first one changes the session.

---

### Post by Punchy71 on 2014-02-01
Hmm,  when installing, I chose the option to log me in automatically, so I don't have the option to log in manually (which is a nuisance) everytime I boot up my laptop. So no log-in screen, and therefore no options to choose which session I want. 

  I may be jumping to a conclusion here, but, does that mean I have to re-install Lubuntu and choose the option to let me log in manually everytime I boot into my laptop so I can chose the desktop session I want?

---

### Post by Dennis N on 2014-02-01
It is still possible. you could log out, and then you will reach the same login screen to choose the session.

---

### Post by Dave_L on 2014-02-01
Try this: [http://askubuntu.com/questions/182274/how-to-disable-autologin-in-lubuntu](http://askubuntu.com/questions/182274/how-to-disable-autologin-in-lubuntu)

---

### Post by Punchy71 on 2014-02-01
Okay, that fixed the problem. I can now log into an OpenBox session by going out the backdoor so to speak. Now I just have to learn how to use the OpenBox desktop environment for the first time. It looks a lot more stark and empty than some of the images I've seen on the internet. It's just an empty gray screen with no Lubuntu theme or anything like that which is what I was expecting. But I guess that is an issue for a seperate post... anyway...

Thanks for the help.

---

### Post by vasa1 on 2014-02-01
I don't mean to sound negative, but if you want to use an Openbox session rather than the Lubuntu session, you're in for some work. From what I can see, there aren't too many people here using an Openbox session on Lubuntu 13.10 (or if there are, they aren't admitting it ;) ). There was a time Openbox users were here in decent numbers but that was some years ago.

---

### Post by sammiev on 2014-02-01
> **Punchy71 said:**
> Okay, that fixed the problem. I can now log into an OpenBox session by going out the backdoor so to speak. Now I just have to learn how to use the OpenBox desktop environment for the first time. It looks a lot more stark and empty than some of the images I've seen on the internet. It's just an empty gray screen with no Lubuntu theme or anything like that which is what I was expecting. But I guess that is an issue for a seperate post... anyway...

Thanks for the help.

OpenBox is a hobby for me and takes a little time. You need to add your own menus or run the programs from terminal. I have a few bookmarks from other ppl and I was going to post them but I'm in a different OS at this time. So I posted here so I would be sub to this thread.

---

### Post by vasa1 on 2014-02-01
> **sammiev said:**
> ... I have a few bookmarks from other ppl and I was going to post them but I'm in a different OS at this time...
You mean you haven't synced your bookmarks :)  ??
I have mine in the cloud (Dropbox) so it isn't browser-specific.

@sammiev, I was posting some Openbox stuff here: [http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126) but maybe this thread will get more traction.

---

### Post by sammiev on 2014-02-01
> **vasa1 said:**
> You mean you haven't synced your bookmarks :)  ??
I have mine in the cloud (Dropbox) so it isn't browser-specific.

@sammiev, I was posting some Openbox stuff here: [http://ubuntuforums.org/showthread.php?t=2173126](http://ubuntuforums.org/showthread.php?t=2173126) but maybe this thread will get more traction.

Using 4 different OS I do try to keep them separate from each other. :) My bookmarks are a mess! lol

---

### Post by mcduck on 2014-02-02
> **Punchy71 said:**
> Okay, that fixed the problem. I can now log into an OpenBox session by going out the backdoor so to speak. Now I just have to learn how to use the OpenBox desktop environment for the first time. It looks a lot more stark and empty than some of the images I've seen on the internet. It's just an empty gray screen with no Lubuntu theme or anything like that which is what I was expecting. But I guess that is an issue for a seperate post... anyway...

Thanks for the help.

That would be because OpenBox is not a desktop environment, it's just a window manager (although to make things a bit more useful it can give you an application list on right-click menu.) Any other features you want, you'll need to add separate software for it and configure it yourself. 

There are quite many guides to setting up OpenBox sessions, usually with recommendations on what software to use for things like panels, desktop wallpaper (and icons, if you want), file managers, etc. On the other hand since you already have LXDE and it's packages around, you should have most applications already and the rest is just a question of getting a desktop setup you prefer. (I'd recommend using something like Tint2 for panels, and Nitrogen or Feh to daw the desktop. Although your file manager might already have the option to handle the desktop for you)

---

### Post by Dave_L on 2014-02-02
Openbox has a right-click menu for accessing your stuff.   What more do you need? :grin:

---

### Post by vasa1 on 2014-02-02
OP, I've been reading some of the other threads you've started today and it's unclear whether you like doing  research or not.

My impression is that there's a significant bit of fiddling required to get Lubuntu's Openbox session into usable form.

On the other hand, there are other distros that take into account Openbox's features (and lack of them) and present the user with a "complete" Openbox system off the bat.

A few of them that come to mind are Bento, Crunchbang, and Manjaro.

BTW, this, from the first post isn't correct:
> On the Distrowatch page dedicated to explaining Lubuntu, it mentions that Lubuntu uses either LXDE *OR* OpenBox.
 The Lubuntu session uses **both** LXDE **and** Openbox.

---


---
title: "[SOLVED] Fluxbuntu upgrade"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Inxsible on 2008-05-25
I have a dual boot of Fluxbuntu and Xubuntu. But the latest for Fluxbuntu is 7.10.

Is there any way to upgrade it to Hardy, apart from actually installing/uninstalling each and every package including the new kernels etc?

---

### Post by aysiu on 2008-05-29
Sure.

Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.gutsy
sudo nano /etc/apt/sources.list
``` Replace every instance of the word *gutsy* with the word *hardy*. Then save (Control-X, Y, Enter) and ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Inxsible on 2008-06-02
Thanks aysiu...worked great !

---

### Post by snowpine on 2008-06-10
> **Inxsible said:**
> I have a dual boot of Fluxbuntu and Xubuntu. But the latest for Fluxbuntu is 7.10.

Is there any way to upgrade it to Hardy, apart from actually installing/uninstalling each and every package including the new kernels etc?

I am thinking about trying this on my Fluxbuntu system. What are the advantages/disadvantages of upgrading Fluxbuntu from Gutsy to Hardy? My concern is that it might break something, since Fluxbuntu is not an "official" branch of *buntu. Anyone have experience running Fluxbuntu 8.04 over a period of time?

---

### Post by Inxsible on 2008-06-10
> **snowpine said:**
> I am thinking about trying this on my Fluxbuntu system. What are the advantages/disadvantages of upgrading Fluxbuntu from Gutsy to Hardy? My concern is that it might break something, since Fluxbuntu is not an "official" branch of *buntu. Anyone have experience running Fluxbuntu 8.04 over a period of time?Sorry...I have now moved on to using Debian Lenny core + Fluxbox. It seems much faster and the best part is that I can install whatever apps I want as opposed to getting Kazehakase and the like. Although I must admit that Fluxbuntu is very minimal even in the software that they provide- which is really good.

if you don't want to go to Debian, you could also try to use Ubuntu minimal + fluxbox.

---

### Post by snowpine on 2008-06-10
> **Inxsible said:**
> Sorry...I have now moved on to using Debian Lenny core + Fluxbox. It seems much faster and the best part is that I can install whatever apps I want as opposed to getting Kazehakase and the like. Although I must admit that Fluxbuntu is very minimal even in the software that they provide- which is really good.

if you don't want to go to Debian, you could also try to use Ubuntu minimal + fluxbox.

Thanks for the quick reply Inxsible! It is like you read my mind. I am very new to fluxbox. I have two computers right next to each other, one running fluxbuntu 7.10 and one running ubuntu 8.04 + fluxbox. I really like the way fluxbuntu is set up (rox-filer, automount, menus, the gorgeous theme/artwork, etc.) so I've been studying fluxbuntu, figuring out how things are done, and then trying to apply the ideas myself in fluxbox. 

The main reason I want to learn this is so that I have the option of booting to gnome/ubuntu sometimes. Sometimes my non-linux friends log in to my computer to check their email or print a document, and I would rather they use gnome than fluxbox. I tried apt-get install ubuntu-desktop from within fluxbuntu, and let's just say it did not go well! I would love to see a fluxbuntu-desktop (and/or fluxbuntu-artwork) package in the Hardy repositories someday.

---

### Post by Inxsible on 2008-06-10
> **snowpine said:**
> Thanks for the quick reply Inxsible! It is like you read my mind. I am very new to fluxbox. I have two computers right next to each other, one running fluxbuntu 7.10 and one running ubuntu 8.04 + fluxbox. I really like the way fluxbuntu is set up (rox-filer, automount, menus, the gorgeous theme/artwork, etc.) so I've been studying fluxbuntu, figuring out how things are done, and then trying to apply the ideas myself in fluxbox. 

The main reason I want to learn this is so that I have the option of booting to gnome/ubuntu sometimes. Sometimes my non-linux friends log in to my computer to check their email or print a document, and I would rather they use gnome than fluxbox. I tried apt-get install ubuntu-desktop from within fluxbuntu, and let's just say it did not go well! I would love to see a fluxbuntu-desktop (and/or fluxbuntu-artwork) package in the Hardy repositories someday.I am not quite a fan of rox-filer. I prefer pcmanfm which is really neat. If you install Ubuntu minimal + Fluxbox, the only thing you won't get is the Fluxbuntu leafy theme :)

But yeah, if you do want to keep gnome around, then your best bet would be to install Ubuntu and then simply install fluxbox over it. I am not sure why installing ubuntu-desktop would give you problems. What errors did you get?

---

### Post by snowpine on 2008-06-10
> **Inxsible said:**
> I am not quite a fan of rox-filer. I prefer pcmanfm which is really neat. If you install Ubuntu minimal + Fluxbox, the only thing you won't get is the Fluxbuntu leafy theme :)

But yeah, if you do want to keep gnome around, then your best bet would be to install Ubuntu and then simply install fluxbox over it. I am not sure why installing ubuntu-desktop would give you problems. What errors did you get?

Thanks, I will check out pcmanfm. I've also been experimenting with nautilus (using --no-desktop) and I've heard good things about thunar. (I'm not obsessed with keeping things ultra-light, clearly.)

I *think* the problem with installing ubuntu on top of fluxbuntu is that one uses xorg and the other uses slim--there are two different windows managers competing with each other. I was able to get everything working, but ubuntu was very slow. Starting up and shutting down took forever. Whereas installing ubuntu first and then fluxbox on top of it worked flawlessly for me.

When I startup ubuntu, the login screen has a "choose session" option where I can pick gnome, fluxbox, xfce, etc. but fluxbuntu does not have this feature. I just don't think it's designed to share a computer with the "official" *buntus (unless it's on a separate partition).

---

### Post by Inxsible on 2008-06-10
> **snowpine said:**
> Thanks, I will check out pcmanfm. I've also been experimenting with nautilus (using --no-desktop) and I've heard good things about thunar. (I'm not obsessed with keeping things ultra-light, clearly.)

I *think* the problem with installing ubuntu on top of fluxbuntu is that one uses xorg and the other uses slim--there are two different windows managers competing with each other. I was able to get everything working, but ubuntu was very slow. Starting up and shutting down took forever. Whereas installing ubuntu first and then fluxbox on top of it worked flawlessly for me.

When I startup ubuntu, the login screen has a "choose session" option where I can pick gnome, fluxbox, xfce, etc. but fluxbuntu does not have this feature. I just don't think it's designed to share a computer with the "official" *buntus (unless it's on a separate partition).
I guess so...the little experience I had with Fluxbuntu was that I installed in on a separate partition. you are probably right, Slim and GDM are probably fighting with each other, but you could always un-install one of them and see if that works. Slim and GDM both are capable of adding Gnome and Fluxbuntu respectively to its sessions.

---

### Post by snowpine on 2008-06-10
> **Inxsible said:**
> I guess so...the little experience I had with Fluxbuntu was that I installed in on a separate partition. you are probably right, Slim and GDM are probably fighting with each other, but you could always un-install one of them and see if that works. Slim and GDM both are capable of adding Gnome and Fluxbuntu respectively to its sessions.

Oh, thanks, I misunderstood what Slim was... there may be hope for me yet!

---

### Post by snowpine on 2008-06-10
Here is the update. I did a fresh install of Fluxbuntu. Then, I upgraded to Hardy using the method above. Everything worked fine.

Then, rather than install Ubuntu, I did this:

```
sudo apt-get install gnome-core
```

(Thanks aysiu!)

Then I did this:

```
sudo nano /etc/slim.conf
```

Scroll down to where it says "sessions" and I changed it to:

```
sessions    startfluxbox,gnome-session
```

Now, when I log in and get to the Fluxbuntu splash, I can press F1 and log in to Gnome!

So far it's been working well, though it has only been an hour. Thanks to everyone for their help.

ps I think I could install GDM to have an easier way to switch sessions. I am grooving on slim for the time being! :)

UPDATE: So far, this is working well, with one exception: It occasionally logs me into gnome, even if I select fluxbox. I attribute this to slim not really being designed for multiple sessions (in their documentation, they call this an "experimental feature"). I have taken Gnome off my laptop and gone back to pure Fluxbuntu Gutsy. I'm keeping both Gnome and Fluxbuntu on my desktop for the time being, and if I continue to have the login problem, I will probably switch from Slim to GDM.

---


---
title: "youtube videos doenst show"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by einfinger on 2008-07-27
im having some problems with flash it seems, videos wont start when i enter a page like youtube.. i go in to see a video and all i get is a white screen where the video is supposed to be, ive installed the flash player a few times and uninstalled firefox aswell but it doesnt seem to do the trick

any ideas ?

---

### Post by billgoldberg on 2008-07-27
> **einfinger said:**
> im having some problems with flash it seems, videos wont start when i enter a page like youtube.. i go in to see a video and all i get is a white screen where the video is supposed to be, ive installed the flash player a few times and uninstalled firefox aswell but it doesnt seem to do the trick

any ideas ?

Open up a terminal and enter (copy/paste) this code:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

That should fix all your flash/codecs troubles.

---

### Post by einfinger on 2008-07-27
that didnt help :/

---

### Post by WildeBeest on 2008-07-27
I have the same problem.

I'm using Hardy Heron (64 bit) and Firefox 3.

---

### Post by rockerphil on 2008-07-27
i'd suggest installing the flash plugin from the repos. so just pull up a terminal and run this 

sudo apt-get install flashplugin-nonfree

then restart Firefox and Flash should work,

Phil

---

### Post by einfinger on 2008-07-27
ive already done that, even reinstalled it :/

---

### Post by gjoellee on 2008-07-27
You may have installed one other plugin. I don't remember what it is called but i think it starts with the letter "G". It can disturb flash. Please tell me all the plugins you have....found in Tools->Addons->Plugins (in firefox and not gnome menu)

---

### Post by rockerphil on 2008-07-27
ok, then the next thing i'd try is downloading the plugin from the Adobe web site and installing it that way. i'd personally get the .rpm package (since they don't supply a .deb package) and use alien to convert it to .deb, then just use dpkg to install it. hope this helps,

Phil

----------------
Now playing: [Atmosphere - Sunshine](http://www.foxytunes.com/artist/atmosphere/track/sunshine)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by gjoellee on 2008-07-27
if you are using Ubuntu you have to install alien first to use .rpm > sudo apt-get install alien in Ubuntu it is meant for you to download .tar.gz if you wan to install in manually. Flash is supposed to be installed when firefox asks you to install a missing plugin

---

### Post by einfinger on 2008-07-27
ive got the latest flash player

ive got no plugins starting with g. 

i have however two shockwave flash player plugins installed,tried to remove them and reinstall and such but no luck yet.

---

### Post by billgoldberg on 2008-07-27
What files are in /home/rw/.mozilla/plugins ?

There should be a mention of "libflashplayer.so", that's the flashplayer plugin.

Is it there?

Try removing the rest (might want to keep the java one).

And then restart firefox.

---

### Post by litlfrog on 2008-07-27
I was having a problem with very blocky playing in YouTube, so I did the codec install listed in the code above. It worked fine and videos play well (thanks), but now there are some font changes in Firefox that I'm not crazy about. Can anyone tell me how to undo the change to type?

---

### Post by gjoellee on 2008-07-27
you can change fonts, in Edit->Prefernces->Content

---

### Post by einfinger on 2008-07-30
nobody ? i really dont wanna reinstall :(

---

### Post by mattchesters on 2008-07-30
I always thought flash didn't work in 64bit?

---

### Post by einfinger on 2008-07-30
i dont have 64bit :P

---

### Post by ConMan318 on 2008-07-30
> **mattchesters said:**
> I always thought flash didn't work in 64bit?

Uh nope.  I have 64-bit and Flash works just fine.

Earlier though my Flash videos did stop working (because of an update), though.  I just went into Synaptic and marked 'flash-plugin-nonfree' for complete removal and applied.  Then I marked it for installation and installed it, and restarted Firefox (you didn't forget that you have to restart the Fox did you?) and everything was well again.

---

### Post by einfinger on 2008-07-30
ive reinstalled nonfree aswell..

Does anyone know how i can remove the flashplayer from adobe ?

---


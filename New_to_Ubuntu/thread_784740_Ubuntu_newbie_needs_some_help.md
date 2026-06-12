---
title: "Ubuntu newbie needs some help"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Knubs on 2008-05-06
Hi all. Totally new to ubuntu/linux. Actually just installed yesterday, so far I love it. To hell with windows.. 

My problem is when I try to play a .m4a file in exaile it tells me I don't have the right gstreamer plugin installed. I googled gstreamer and there's about a thousand different plugins. Very confusing. I just need a little help getting and installing that plugin I guess. Any help?

---

### Post by c4v3m4n on 2008-05-06
Which media player are you using?

---

### Post by PeterJS on 2008-05-06
> **Knubs said:**
> Hi all. Totally new to ubuntu/linux. Actually just installed yesterday, so far I love it. To hell with windows.. 

My problem is when I try to play a .m4a file in exaile it tells me I don't have the right gstreamer plugin installed. I googled gstreamer and there's about a thousand different plugins. Very confusing. I just need a little help getting and installing that plugin I guess. Any help?

Do you have restricted extras installed? There's more plugins and codecs than you can shake a stick at included there, that'd be a good place to start.

Restricted extras can be installed with the Synaptic package manager under System > Administration > Synaptic Package Manager. If you search for restricted extras you should find a couple, install the one that matches the desktop you're using or use the most.

EDIT:

It might not be available in the base set of packages for legal reasons. Quoting from the amarok-xine package description from Medibuntu:
> 
This package is built with Itunes AAC-LC (.m4a) support enabled.
Therefore, it is in Medibuntu as it might violate patents.


I'd bet the gstreamer plugin is also there, I'm going to go dig around a bit more for it.

---

### Post by drascus on 2008-05-06
OK if it is Gstreamer based try to open the file in movie player. It will search for find and install the correct plugin for you. Then you should be able to open it in any media player that is Gstreamer based.

---

### Post by drascus on 2008-05-06
> Do you have restricted extras installed? There's more plugins and codecs than you can shake a stick at included there, that'd be a good place to start.

I would only suggest against installing restricted extras because there may be things in there that you don't want or are questionable legally in your country of Origin.

---

### Post by NightwishFan on 2008-05-06
Try perhaps to hit all the birds with one stone:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```
Also try Vlc player:
```
sudo apt-get install vlc
```

---

### Post by Knubs on 2008-05-06
> **NightwishFan said:**
> Try perhaps to hit all the birds with one stone:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```
Also try Vlc player:
```
sudo apt-get install vlc
```

Already ran both commands and I have tried VLC, but with VLC I get some weird crackling/stuttering with playback, which is why I went with exaile. 

Someone just told me to grab xmms2 stuff, I did through synaptic and now it's working. However some of the .m4a files cause the player to close, others will play fine. 

But thanks for the help. :)

---

### Post by PeterJS on 2008-05-06
Interesting, looks like it might be **libfaad0**:
> 
freeware Advanced Audio Decoder - runtime files FAAD2 is the fastest ISO AAC audio decoder available. FAAD2 correctly decodes all MPEG-4 and MPEG-2 MAIN, LOW, LTP, LD and ER object type AAC files.


Which can be installed by itself, or as part of the "gstreamer0.10-plugins-bad" collection.

EDIT:

> **Knubs said:**
> Already ran both commands and I have tried VLC, but with VLC I get some weird crackling/stuttering with playback, which is why I went with exaile. 

The poor quality is probably what landed it in the "bad" collection of codecs in the first place.

---

### Post by Knubs on 2008-05-06
I'm using Hardy Heron 8.04 and I *think* that the "bad" package comes with it. I looked in synaptic and it's already installed. Which is strange because they wouldn't play??


Anyway. rather than start a new thread I have another problem (of the many to come I'm sure...) 

I've downloaded a theme package for the gui and I can't figure out how to install. 

The package is in a .tar and I extracted. then I have a folder with contents and a readme. 

I could post the readme but it's kind of big, is that thing shunned here?

---

### Post by PeterJS on 2008-05-06
Link to where you got it from and I'll download it and take a look that the read me. Odds are the installation is as easy as copying the unpacked theme to $HOME/.themes.

---

### Post by Knubs on 2008-05-06
I actually tried that and it never shows up under system>preferances>appearence. even under the customize tab...give me a min to dig up where I got it from and I'll post it.

---

### Post by Knubs on 2008-05-06
Sorry for so many posts rapid fire but I'm bored and want to figure this out :)

Heres a link: [http://www.gnome-look.org/content/show.php/Hardy+Theme?content=74045]("http://www.gnome-look.org/content/show.php/Hardy+Theme?content=74045")

---

### Post by NightwishFan on 2008-05-06
Go to appearance, on the first tab hit install and install if its a tar.gz

---

### Post by Knubs on 2008-05-06
Won't show up. 

It's actually a folder packed in a .tar packed in a .gz file.

---

### Post by PeterJS on 2008-05-06
Ah, there we go. The file you got wasn't actually one theme, but a whole collection of themes for different things that all fit together.

If you look in the GTK folder you'll find a folder named Hardy-Mariux 2.0, that actually contains the main theme, and that's the folder you need to put in to $HOME/.themes. The Emerald theme you'll want to put some place easy to find (might I suggest the desktop), and install that with the emerald theme manager. The tangerine iconset should already be installed so no need to mess with that.

The other stuff isn't so important, have a look at the read me or ask if you've got any questions.

---

### Post by Knubs on 2008-05-06
Awesome. That works. Thanks for the help!

---


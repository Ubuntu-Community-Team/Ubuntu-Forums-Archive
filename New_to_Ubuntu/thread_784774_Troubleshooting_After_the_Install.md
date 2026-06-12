---
title: "Troubleshooting: After the Install"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by AeThEr777 on 2008-05-06
Ok ive had the new Ubuntu gutsy Gibbon now for about 2 weeks there are just a few things I need fixed before my machine is running 100% better then say windows :P. Ok So i will list them out. If anyone knows the answer to any of them just say the number and ill get to it. So here goes.

1. Youtube video area is all wacked out. First of all the taskbar is all skewed the volume control shows up where play and pause are. Play and pause button dont appear until scrolled over with the mouse, and the loading bar doesnt show completly until the video is loaded. 

2. Flash player just doesnt work. The main page on IGN wont show the animation and on any other site the flash player just doesnt work. Ive already followed a how-to on how to get flash but it still wont work properly.

3.Anyway to decrease the initial load time of the os. Ive seen videos on Youtube of people running similar if not worse specifications and the OS seems to load much faster for them. Ive got around a 3 minute wait. Ive got a 1.6MHZ core duo, 2GB ram gateway laptop. 

4.Music player so banshee in a word sucks. Just not the usability ive learned to love on itunes. I am really just looking for a better program that organizes my music like itunes and has ipod support. 

5. Ive seen so many amazing Ubuntu setups.....I WANT ONE...lol first of all Dock like on Leopard for macs. How the hell do i get one of those. And themes anywhere where i can dowload more themes.Where the hell does everyone get there amazing desktop images, like background. Ive seen so many amazing ones. 

6. Gadgets, widgets, whatever. Do these exist for ubuntu? 

Please if anyone can help me on any of these i would greatly appreciate it.

---

### Post by AeThEr777 on 2008-05-06
Seriously? Nobody?

---

### Post by malangaman on 2008-05-06
Do you really mean Gutsy Gibbon? Or by "new" do you mean Hardy 8.04?

---

### Post by AeThEr777 on 2008-05-06
By new i meant new OS post windows. I am using Gutsy gibbon not hardy.

---

### Post by RequinB4 on 2008-05-06
5-6) Google is your freind, but I'd suggest gnome-look ([www.gnomelook.org](www.gnomelook.org)) for all your eye candy needs.  Make sure you know how to install everything!

Sounds like you need to get flash.

---

### Post by AeThEr777 on 2008-05-06
how do i get flash. any help on  that?

---

### Post by AeThEr777 on 2008-05-06
bump

---

### Post by RequinB4 on 2008-05-06
First, install the multiverse repository in System - Administration - Software Sources.

The ubuntu-restricted-extras packages has all of the commonly used restricted software in ubuntu, such as flash plugin for mozilla or mp3 playback.  Note that these are NOT liscenced under the GPL, and by downloading these you agree to the respective manufacture liscences. For more details read the description in synaptic
```

sudo apt-get install ubuntu-restricted-extras

```

Alternatively, you could just get flash from adobe, but it won't be part of the restricted extras metapackage.  Same rules apply.
```

sudo apt-get install flashplugin-nonfree

```

Restart your web browser.  If this doesn't work, you may have to get rid of whatever flash substitute you have now.

---


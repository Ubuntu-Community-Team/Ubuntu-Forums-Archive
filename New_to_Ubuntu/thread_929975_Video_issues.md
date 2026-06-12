---
title: "Video issues"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by fignig on 2008-09-25
i'm tired of this happening only in ubuntu hardy heron. when i want to watch a clip of a video or something, on any site this usually happens. when i click the video to watch it, it goes black/gray. and i usually have to close all of my browsers and open them back up again, and try to click the video again before it plays, and sometimes it doesn't. does anyone else have this problem or is it just me?

---

### Post by fignig on 2008-09-25
when i say gray/black i mean blank.

---

### Post by fignig on 2008-09-25
happens when i open another website/video as well..

---

### Post by fignig on 2008-09-27
no one else has this problem except for me?

---

### Post by tariquepark on 2008-09-27
whilst im am a relative newb myself try this
open your browser and type about:plugins in the address bar
it will list all the plugins
most all of them should have a yes next to them
those that arent will be the plugins you need
shockwave and flash can be very fussy if there is more than 1 plugin for it

that would be a colon between about and plugins with no spaces

---

### Post by fignig on 2008-10-01
i have the plugins it's when i try to look at videos. most of the time i have to close all firefox apps and relaunch. there shouldn't be a need for this. i should be able to watch the videos without closing/reopening firefox

---

### Post by RedRat on 2008-10-01
> **fignig said:**
> i have the plugins it's when i try to look at videos. most of the time i have to close all firefox apps and relaunch. there shouldn't be a need for this. i should be able to watch the videos without closing/reopening firefox

I don't know if this will help or not but you might want to check your monitor refresh rate. On my Dell 530n with an nVidia 8600GT card and 2 Gb memory, somehow my refresh rate to my monitor (Samsung SyncMaster 191T) somehow got set to 75 Hz (which it can handle). When in this mode, I had all kinds of problems with Firefox and only firefox! Why should that be?? I have not got a clue, but when I set the refresh rate to 60 Hz all was fine. I could not even open some sites that displayed jpg files, yet alone videos. I just figured it must be some issue with nVidia drivers, the card, and FireFox. You might want to check that out, this may or may not help you.

---

### Post by fignig on 2008-10-02
> **RedRat said:**
> I don't know if this will help or not but you might want to check your monitor refresh rate. On my Dell 530n with an nVidia 8600GT card and 2 Gb memory, somehow my refresh rate to my monitor (Samsung SyncMaster 191T) somehow got set to 75 Hz (which it can handle). When in this mode, I had all kinds of problems with Firefox and only firefox! Why should that be?? I have not got a clue, but when I set the refresh rate to 60 Hz all was fine. I could not even open some sites that displayed jpg files, yet alone videos. I just figured it must be some issue with nVidia drivers, the card, and FireFox. You might want to check that out, this may or may not help you.

lol i'm at 50Hz and that's the only option i have. so i have no idea what the problem is..

---

### Post by fignig on 2008-10-02
it's starting to happen more often. and sometime when i try like 9-10 times to open a video it doesn't work so i  have to give up and not watch it. wtf is wrong? and can anyone help? anyone?

---

### Post by tjwoosta on 2008-10-02
the problem you are having is definatly caused by flash

(it used to happen to me)

this used to be a very common issue with flash and firefox in ubuntu but i was under the influence that the issue was resolved


you could try using opera webbrowser  

or you could try upgrading your flash player to flash10 (assuming you are still using flash 9)

---

### Post by RedRat on 2008-10-02
> **fignig said:**
> it's starting to happen more often. and sometime when i try like 9-10 times to open a video it doesn't work so i  have to give up and not watch it. wtf is wrong? and can anyone help? anyone?

Have you tried running nvidia-settings? Do you have that installed? Now you must run this using the sudo or gksudo as follows:
Open a terminal session and type in:
gksudo nvidia-settings

There you can set your monitor and nvidia settings. Then save the settings. If you do not run using sudo or gksudo, the configuration file will not be saved since you need root privileges.

---

### Post by RedRat on 2008-10-02
> **tjwoosta said:**
> the problem you are having is definatly caused by flash

(it used to happen to me)

this used to be a very common issue with flash and firefox in ubuntu but i was under the influence that the issue was resolved

I not only had problems with flash but also with large .jpg files. Going to pages that contained a lot of graphics, without flash btw, caused FireFox to stop, grey out, and quite. Exactly why that should happen I don't understand since my other graphic programs (e.g., digi-Kam, Gimp) could open large .jpg files with no problem. My only resolution was to set the refresh rate down to 60Hz. Something else must be at play here.

---

### Post by fignig on 2008-10-02
> **tjwoosta said:**
> the problem you are having is definatly caused by flash

(it used to happen to me)

this used to be a very common issue with flash and firefox in ubuntu but i was under the influence that the issue was resolved


you could try using opera webbrowser  

or you could try upgrading your flash player to flash10 (assuming you are still using flash 9)

how do i figure out what flash i'm using?

---

### Post by fignig on 2008-10-02
btw i think they discontinued flash10 for ubuntu hardy b/c i was trying to install it. and it kept saying error 404 when i was trying to wget it.

---

### Post by kansasnoob on 2008-10-02
If it's a flash thing, rather than a movie player thing, look at my post #9 here:

[http://ubuntuforums.org/showthread.php?t=936003](http://ubuntuforums.org/showthread.php?t=936003)

BTW: if it's a "movie player" thing you'd know it in Firefox because the "downloads" window would pop up.

BTW #2: That flash 10 RC works fine in Opera too .... just so long as it's Hardy! If it's anything other than Hardy you must use a tar.gz to install.

---

### Post by kansasnoob on 2008-10-02
Oh, I just happened to think of something else, there are many options: totem,  a few flavors of mplayer, vlc, and xine to mention a few and what I do is:

Go to Synaptic Package Manager and search **totem**, there most totem should be installed by default - I make sure that **totem-mozilla** is *uninstalled*.

Then I search **vlc** and I install **mozilla-plugin-vlc** and **vlc** and everything that begins with **vlc-**.

Another popular option is mplayer. I've found many people I've installed Ubuntu for like the smplayer. And of course there is a mozilla-mplayer.

And I've found that some people like xine for dvds.

The thing is there are many options. Just break out the old spiral notebook and keep track of all changes (using synaptic makes that easy) so you can reverse things if wanted.

---

### Post by tjwoosta on 2008-10-02
yea i think i may have read the first post wrong the first time

i just read it again and i guess it does kinda sound like a problem with the video player plugins

---

### Post by fignig on 2008-10-03
> **tjwoosta said:**
> the problem you are having is definatly caused by flash

(it used to happen to me)

this used to be a very common issue with flash and firefox in ubuntu but i was under the influence that the issue was resolved


you could try using opera webbrowser  

or you could try upgrading your flash player to flash10 (assuming you are still using flash 9)

i can't upgrade to 10 b/c i can't find it. all of the websites pull 404 errors:
i'm using an amd64 and i can't find that version.

---

### Post by fignig on 2008-10-03
> **tjwoosta said:**
> the problem you are having is definatly caused by flash

(it used to happen to me)

this used to be a very common issue with flash and firefox in ubuntu but i was under the influence that the issue was resolved


you could try using opera webbrowser  

or you could try upgrading your flash player to flash10 (assuming you are still using flash 9)

LOL i'm still laughing at your suggestion to use opera. i installed and tried using it to watch videos. it crashed every single time i tried. every single time. opera fuking blows kid. don't ever recommend it again..

---

### Post by tjwoosta on 2008-10-04
> LOL i'm still laughing at your suggestion to use opera. i installed and tried using it to watch videos. it crashed every single time i tried. every single time. opera fuking blows kid. don't ever recommend it again..

opera works fine on both of my computers  with hardy 64bit

its actually a higher score then firefox on the acid3 test

so just because it didnt work for you doesnt mean it wont work for anybody

---

### Post by fignig on 2008-10-08
> **tjwoosta said:**
> opera works fine on both of my computers  with hardy 64bit

its actually a higher score then firefox on the acid3 test

so just because it didnt work for you doesnt mean it wont work for anybody

well i'm just stating my opinion on the matter. opera sucks. can anyone help me w/ my problem? i'm on flash 9. and i can't seem to find flash 10 anywhere, i see traces, but all broken links. anyone?

---

### Post by bwang on 2008-10-08
Install Flash 10:
```
sudo apt-get remove flashplugin-nonfree
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar -zxvf flashplayer10_install_linux_091508.tar.gz
cd install_flash_player_10_linux/
./flashplayer-installer

```

---

### Post by fignig on 2008-10-16
> **bwang said:**
> Install Flash 10:
```
sudo apt-get remove flashplugin-nonfree
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_091508.tar.gz
tar -zxvf flashplayer10_install_linux_091508.tar.gz
cd install_flash_player_10_linux/
./flashplayer-installer

```


and again someone fails to give me complete instructions that work...

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

can anyone help? or do i have to switch back to Windows to watch my videos?

---


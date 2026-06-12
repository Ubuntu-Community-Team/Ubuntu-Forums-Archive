---
title: "About themes in 'Appearance Preferrences'"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by opendevlite on 2008-10-31
I wanted to install Human Compact theme in "Appearance" but a message says:

This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed.

How do i install the engine?

Thanks

---

### Post by dracayr on 2008-10-31
sudo apt-get install gtk2-engines-ubuntulooks

dracayr

---

### Post by opendevlite on 2008-10-31
when i mark gtk2-engines-ubuntulooks for installation, synaptic tells me, that human-theme, ubuntu-artwork, and ubuntu-desktop will be remove is it safe?

i'm currently using ubuntu 8.10 now

---

### Post by ben2talk on 2008-11-01
> **opendevlite said:**
> when i mark gtk2-engines-ubuntulooks for installation, synaptic tells me, that human-theme, ubuntu-artwork, and ubuntu-desktop will be remove is it safe?

i'm currently using ubuntu 8.10 now



>>>>>>>>>>>>>BUMP - I've just about managed to destroy most of my theming - and now installed Human theme again from Synaptic after moving all the theme folders out of /home/ben/.themes and /root/themes and /usr/shared/themes - I moved them all to an archive folder.

The themes all started to report that parts were missing. Now, if I drop my 'OS V.tar.gz' in the window, it reports 
'GNOME Theme OS V correctly installed'
Okay? So now I see it in my Appearance Preferences window, and select it ...

"This theme will not look as intended because the required GTK+ theme engine 'osv' is not installed"

GGGrrrrrrrr it's installed nearly all the way - except for tabs and menu's. Now on my 'customize' tab, it's getting messed up already. I can see OS V ghosted out, so will select 'SlicknesS' instead, and now the complaint is that "the required GTK+ theme engine" is not installed.

What engine is "" , and why is it not installed?

How can I completely clear out and install all themes again? Now I have 'Darkroom, Human, Human-Clearlooks' which are easily installed from Synaptic 'gnome-themes'.

I have the metacity window decoration from OS V - but really I want to fix the theming of my menu's and buttons.

[http://farm4.static.flickr.com/3178/2991233812_1e66fa83b8_o.png](http://farm4.static.flickr.com/3178/2991233812_1e66fa83b8_o.png)
[http://farm4.static.flickr.com/3294/2991233808_be39b16a0e_o.png](http://farm4.static.flickr.com/3294/2991233808_be39b16a0e_o.png)

---

### Post by ben2talk on 2008-11-01
Updates - I rebooted from the CD, and had no trouble installing themes on the live desktop - however there were the same messages saying 'it wont' look right cos the GTK engine isn't working', even though it's working fine - I had SlicknesS, OS v, and Sunday folders ready. They're fine to install on root and the user (ubuntu on liveCD) accounts - and I could select elements of all three at will.
I can't establish if this issue was created by my upgrading from an 8.04 installation to 8.10 (not to the beta, just the first release). Someone did tell me that he used the CD to upgrade and he has this issue.

This should be filed as a bug right?

To recap - liveCD no problem (just warnings), but installation will only let me theme the root account. My user account only allows the theme to get the window borders/panel and colours, except for the preinstalled themes (Human is fine). As 'root' there aren't any issues (except warnings).
:confused:

---

### Post by ben2talk on 2008-11-01
OpenDevlite - can you give an update? Solved? abandoned? reinstalled?

---

### Post by pcozzy on 2008-11-01
> **opendevlite said:**
> when i mark gtk2-engines-ubuntulooks for installation, synaptic tells me, that human-theme, ubuntu-artwork, and ubuntu-desktop will be remove is it safe?

i'm currently using ubuntu 8.10 now

I have the same problem after a distribution update to intrepid ubuntulooks will not install unless it removes those 3.  I will not take any chances since removing ubuntu-desktop will ruin your system.  I don't even care to install ubuntulooks but there is a large number of programs that are trying to use this program after intrepid update.  All these programs work but I never like to see error messages.  

Any work arounds will be appreciated.

pcozzy

---

### Post by EvilTchnlgy on 2008-11-02
I just ran
apt-get install gtk2-engines-ubuntulooks
let it remove the 3 and then
apt-get install ubuntu-desktop put back the 3 it deleted

---

### Post by brandoncolorado on 2008-11-02
For other people who read this post:

When you download themes, make sure you pick themes that don't require an 'engine' if you are a beginner.  It is much easier with these themes, because you can just download them and drag them into the theme window.

---

### Post by scylla2 on 2008-11-05
Has this been confirmed to be a bug? I also can't install any GTK2 themes under Ububtu Intrepid. I get the "the required GTK+ theme engine" error and the theme is only partially loaded.

Will an eventual update fix this problem?

---

### Post by brandoncolorado on 2008-11-05
*edited because I am slow*

---

### Post by ben2talk on 2008-11-08
> **opendevlite said:**
> I wanted to install Human Compact theme in "Appearance" but a message says:

This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed.

How do i install the engine?

Thanks

IGNORE THE MESSAGE!

I went around in circles with this one, and ended up backing up my tar.gz themes to my backup folder, deleting lots of themes and starting fresh. The messages come whether or not the engines are installed!

You can see if you have your buttons themed, your menu's themed, and so on - you don't need silly messages :P it's a bug they need to iron out.

Try out OS V theme - it's a very complete theme, you can see that it themes EVERY aspect (and if you use it, it needs modifying - make the font slightly orange so it doesn't dissapear, cos this theme is not light or dark, but sometimes the font and background coincide).

Install this theme and you'll be 100% confident it's all there - despite the message.

BTW, I think this theme has the finest (small) metacity border I have used so far. (works well with Slickness too)

---

### Post by ben2talk on 2008-11-08
> **EvilTchnlgy said:**
> I just ran
apt-get install gtk2-engines-ubuntulooks
let it remove the 3 and then
apt-get install ubuntu-desktop put back the 3 it deleted

Strange idea - install gtk2 ubuntulooks removing the three, and then replace the three which will remove the ubuntulooks!
Why not just not install it in the first place?

---


---
title: "[SOLVED] Youtube full screen problems"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by anotherconfused1 on 2008-08-12
I tried searching google for this and these forums, but either I'm not searching the right terms, or I'm blind. Anyways, when I click the full screen button on youtube videos it flahes to full screen for like half a second and goes back to normal screen. I am running Ubuntu 8.04 Hardy and I have an Nvidia Geforce 7000 i think... I can't remember how to check lol

---

### Post by perlluver on 2008-08-12
> **anotherconfused1 said:**
> I tried searching google for this and these forums, but either I'm not searching the right terms, or I'm blind. Anyways, when I click the full screen button on youtube videos it flahes to full screen for like half a second and goes back to normal screen. I am running Ubuntu 8.04 Hardy and I have an Nvidia Geforce 7000 i think... I can't remember how to check lol

Do you have compiz turned on?  System>Preferences>Appearance last tab, Visual effects.  Type lspci in the terminal and look for, vga, to find out the card.

---

### Post by starcannon on 2008-08-12
It's not compiz, its you-tube, oddly enough if you watch the same exact video in google-video you can use the full screen feature there.

---

### Post by anotherconfused1 on 2008-08-12
I have compiz turned on, and I have an Nvidia GeForce 7800 GT and I just turned off compiz while I was typing this and full screen works now. So no compiz fusion and full screen?

---

### Post by starcannon on 2008-08-12
> **anotherconfused1 said:**
> I have compiz turned on, and I have an Nvidia GeForce 7800 GT and I just turned off compiz while I was typing this and full screen works now. So no compiz fusion and full screen?

Only a problem for me at You-Tube, if I watch the same video on Google-Video the full screen mode works fine, with compiz turned on.

/shrug

---

### Post by perlluver on 2008-08-13
> **anotherconfused1 said:**
> I have compiz turned on, and I have an Nvidia GeForce 7800 GT and I just turned off compiz while I was typing this and full screen works now. So no compiz fusion and full screen?

Yeah that is how it works sometimes.  But yes when you want to watch a youtube movie, turn off compiz.

---

### Post by khaard on 2008-08-13
Go to **Advanced Desktop Effect settings** and make sure that **Unredirect fullscreen windows** in **General Options** is unchecked. Worked for me.

---

### Post by starcannon on 2008-08-13
> **khaard said:**
> Go to **Advanced Desktop Effect settings** and make sure that **Unredirect fullscreen windows** in **General Options** is unchecked. Worked for me.

Awesome thanks that worked for me as well.

---

### Post by oobe-feisty on 2008-08-20
> **khaard said:**
> Go to **Advanced Desktop Effect settings** and make sure that **Unredirect fullscreen windows** in **General Options** is unchecked. Worked for me.

I use Kubuntu and am suffering from the same problem im not sure how to find Advanced Desktop Effect is this somthing in gnome or am i looking in the wrong place


Wait a sec found it couldnt see it at first

---

### Post by Canis familiaris on 2008-08-20
I would recommend Well make a keyboard shortcut to switch from Compiz to Metacity whenever you want to watch the video.

Go to:
System->Preferences->Advanced Desktop Effects Settings

Go to General Options

Choose Command Tab

In keybindings choose whichever key you'll prefer. I recommend Super + Z (i.e. Win + Z) and corresponding command will be 
```
metacity --replace
```

and now you can always have Compiz enabled and whenever you want to disable Compiz, press that shortcut key and it will be disabled. And Compiz would be re-enabled next time you log in.

---

### Post by housefly7k on 2008-09-01
Thanks, worked for me on Ubuntu hardy 8.04 nVidia Corporation GeForce 7150M (rev a2)

---

### Post by justgrant2009 on 2008-09-05
I'm using Emerald, is there a way that i can set up a command to switch back to Emerald after using the command to switch to Metacity to watch the video? I tried just setting up my own command <super>+o, and the command emerald --replace, which is what i put in my sessions to start in emerald.  but it doesn't do anything and i also tried to just run it in a terminal without the shortcut, and it just hangs.  I'm gonna take an educated guess and say no?

---

### Post by MickS on 2008-09-05
I use compiz switch to switch it on and off, nice little button in the panel, one click for off and another click for back on. I think it's in the repository, I can't remember where I got it from but it's worth hunting down.

Mick

---

### Post by almahtar on 2008-09-10
> **khaard said:**
> Go to **Advanced Desktop Effect settings** and make sure that **Unredirect fullscreen windows** in **General Options** is unchecked. Worked for me.

Worked for me as well. Awesome. Thanks.

---

### Post by christianvaldes on 2008-10-09
> **oobe-feisty said:**
> I use Kubuntu and am suffering from the same problem im not sure how to find Advanced Desktop Effect is this somthing in gnome or am i looking in the wrong place


Wait a sec found it couldnt see it at first

Where do I do this?

---

### Post by christianvaldes on 2008-10-09
> **christianvaldes said:**
> Where do I do this?

sudo apt-get install compizconfig-settings-manager

---


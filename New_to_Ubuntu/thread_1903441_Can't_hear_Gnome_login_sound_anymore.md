---
title: "Can't hear Gnome login sound anymore"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by HunterDX77M on 2012-01-02
For the past week, I haven't heard the Gnome login sound when I login. Its enabled in the startup programs and the volume and alert volume is on. What could be the issue?

---

### Post by HunterDX77M on 2012-01-05
bump

---

### Post by KdotJ on 2012-01-05
I'd be pleased not to hear it lol. Is sound working for you otherwise?

---

### Post by Learning Linux 2011 on 2012-01-05
To change the startup sound go to: 
System -> Preferences -> Startup Applications 

look for GNOME Login Sound  and make sure it is checked.

Then click edit and make sure it is:
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

---

### Post by grahammechanical on 2012-01-05
@kdotj

Good news. The word is that the start up sound is being removed from 12.04. When I converted an 11.10 install into a 12:04 development branch the log in sound got unchecked in the Startup Applications lists.

The thinking is that such a sound is not necessary because the boot up will be a lot faster (fingers crossed). So, having the system wait for a start up sound to be played will slow down the loading of the desktop.

Regards.

---

### Post by HunterDX77M on 2012-01-07
> **KdotJ said:**
> I'd be pleased not to hear it lol. Is sound working for you otherwise?

Yes sound is working fine elsewhere (Online, games, etc.).

---

### Post by HunterDX77M on 2012-01-07
> **Learning Linux 2011 said:**
> To change the startup sound go to: 
System -> Preferences -> Startup Applications 

look for GNOME Login Sound  and make sure it is checked.

Then click edit and make sure it is:
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

That's exactly what it says.

---

### Post by Frantic_Earthling on 2012-01-08
Same problem here!

Startup sound is enabled in Startup Applications but no startup sound.

Sound works fine otherwise, I mean with videos, games, etc.

---

### Post by tersogar on 2012-01-08
You may try this link: [http://askubuntu.com/questions/85051/no-login-sound-on-startup](http://askubuntu.com/questions/85051/no-login-sound-on-startup)

---

### Post by Frantic_Earthling on 2012-01-08
> **tersogar said:**
> You may try this link: [http://askubuntu.com/questions/85051/no-login-sound-on-startup](http://askubuntu.com/questions/85051/no-login-sound-on-startup)

Many thanks but no joy.
"Event Sounds" was already ticked.
Startup sound won't play!

---

### Post by HunterDX77M on 2012-01-08
> **Frantic_Earthling said:**
> Many thanks but no joy.
"Event Sounds" was already ticked.
Startup sound won't play!

Same. :(

---

### Post by cottfcfan on 2012-01-08
Go to system settings, Sound & make sure default is selected, I found that changing the default sound alert lost my login sound.
You could also install dconf-tools. Then open dconf-editor & go to org/gnome/desktop/sound & click "set to default". That should solve your problem.

---

### Post by Frantic_Earthling on 2012-01-08
> **cottfcfan said:**
> Go to system settings, Sound & make sure default is selected, I found that changing the default sound alert lost my login sound.
You could also install dconf-tools. Then open dconf-editor & go to org/gnome/desktop/sound & click "set to default". That should solve your problem.

Did all that already.
I'm afraid that did nothing.

---

### Post by cottfcfan on 2012-01-08
Have you tried changing the login sound altogether.
Try downloading the dream for ubuntu sounds from here.
[http://gnome-look.org/content/show.php/Dream?content=75398](http://gnome-look.org/content/show.php/Dream?content=75398)
Extract the file to usr/share/sounds.
Then open dconf-editor as in my last post, make sure that both the sound boxes are ticked, then change the theme name to Dream & reboot.
It may be that the ubuntu sound file is corrupted somehow.
Doing this will tell.

edit.. Make sure Dream is typed in the right case it may be dream.

---

### Post by Frantic_Earthling on 2012-01-08
cottfcfan, I actually realised that I never took the trouble to _first_ highlight "theme-name" _then_ and only then click on "set to default":roll:.

I did not make a note of what it was earlier, but after clicking on "set to default", it changed to "freedesktop" and it works now!:cool:

Thanks ):P

(I extracted the Dream directory to /usr/share/sounds but did not manage to get it to work. Anyway, it does not matter. I am happy with the standard startup sound.)

---

### Post by Frogs Hair on 2012-01-08
Install the following if not already .

```
sudo apt-get install dconf-tools 
```

Open from dash by typing dcon .

Proceed to org > gnome > desktop > sound and make sure event sounds is checked . 

Next to "theme name" left click replace the words "free desktop" with ubuntu in lower case .

Close and open to make sure the setting stays . If any entries aren't fully deleted any entries the setting won't remain in place. Hold delete key even if no letters are visible just for good measure .

---

### Post by cottfcfan on 2012-01-09
Actually Frantic-Earthling, Frogs hair is right. If you want the original sounds back, the sound theme needs to be ubuntu & not freedesktop.
Anyway sounds like your sorted so that's good.

---

### Post by Frantic_Earthling on 2012-01-09
> **cottfcfan said:**
> Actually Frantic-Earthling, Frogs hair is right. If you want the original sounds back, the sound theme needs to be ubuntu & not freedesktop.
Anyway sounds like your sorted so that's good.

I did give the suggestion a try.
"ubuntu"in lower case. Check whether the setting stays.
I got no sound :confused:

EDIT: Actually, just for the sake of it, I tried again. It worked! However, the startup sound I get with the "ubuntu" setting and the one with "freedesktop" is... the same. :confused::confused:

---

### Post by HunterDX77M on 2012-01-25
I still have the problem for any body that can offer some assistance. Here's something new to add to the mystery: When I login as a guest on the login screen, I hear the sound. I still don't hear it when I login to my own account.

---

### Post by HunterDX77M on 2012-03-04
> **Frantic_Earthling said:**
> cottfcfan, I actually realised that I never took the trouble to _first_ highlight "theme-name" _then_ and only then click on "set to default":roll:.

I did not make a note of what it was earlier, but after clicking on "set to default", it changed to "freedesktop" and it works now!:cool:

Thanks ):P

(I extracted the Dream directory to /usr/share/sounds but did not manage to get it to work. Anyway, it does not matter. I am happy with the standard startup sound.)

This solved it for me :)

---


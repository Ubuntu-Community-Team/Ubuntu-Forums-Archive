---
title: "How to fully apply a theme to Ubuntu ?"
date: 2017-01-25
forum: New to Ubuntu
---

### Post by tempusfugit1 on 2017-01-25
Hi everyone, 

I'm trying to change the theme of Ubuntu, I've tried one of these, I don't remember which (they're all looking great), however, when I try to do it, the icons don't change at all, there is just the "bar" of the windows (sorry, English isn't my first language) that changed a littt ... 

I've tried Unity Tweak Tool, but like I said, nothing changes ...

I know I might seem very new to Ubuntu and how to manage theme and stuff, I'm sorry about that.

Thanks in advance for the help

---

### Post by Frogs Hair on 2017-01-25
Hello and Welcome 

What theme are you trying to apply ?

---

### Post by tempusfugit1 on 2017-01-27
Thanks !

I'd like to install Arc Darker !

---

### Post by Perfect Storm on 2017-01-27
have you tried follow this guide (ubuntu version): [http://www.noobslab.com/2017/01/arc-theme-light-dark-versions-and-arc.html](http://www.noobslab.com/2017/01/arc-theme-light-dark-versions-and-arc.html)

---

### Post by vasa1 on 2017-01-27
What version of Ubuntu are you on?

---

### Post by tempusfugit1 on 2017-01-27
> **Artificial Intelligence said:**
> have you tried follow this guide (ubuntu version): [http://www.noobslab.com/2017/01/arc-theme-light-dark-versions-and-arc.html](http://www.noobslab.com/2017/01/arc-theme-light-dark-versions-and-arc.html)

I just did, thanks for the link, when I tried to install arc-icons, I haven't been able to find the package

Sorry, completely forgot that : Ubuntu 16.04

---

### Post by Perfect Storm on 2017-01-27
> **tempusfugit1 said:**
> I just did, thanks for the link, when I tried to install arc-icons, I haven't been able to find the package

When you say package do you mean in the theme changer or in the terminal?

---

### Post by tempusfugit1 on 2017-01-27
In the terminal : 

(output) : ```
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
W: Target Translations (fr_FR) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
W: Target Translations (fr) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
E: Impossible de trouver le paquet arc-icons


```

Last line : "arc-icons" package was not found."

---

### Post by Perfect Storm on 2017-01-27
> **tempusfugit1 said:**
> In the terminal : 

(output) : ```
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
W: Target Packages (Packages) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
W: Target Translations (fr_FR) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
W: Target Translations (fr) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
W: Target Translations (en) is configured multiple times in /etc/apt/sources.list.d/arc-theme.list:1 and /etc/apt/sources.list.d/vertex-theme.list:1
E: Impossible de trouver le paquet arc-icons


```

Last line : "arc-icons" package was not found."

My French isn't great but I guessit says impossible to get the package. You could try get it manually here: [https://launchpad.net/~noobslab/+archive/ubuntu/icons/+packages](https://launchpad.net/~noobslab/+archive/ubuntu/icons/+packages)

look for arc-icons - 1.2~yakkety~NoobsLab.com and pick the *all.deb file.

EDIT: doh, you translated the line, I didn't see -_-

---

### Post by leunam12 on 2017-01-27
Download the icon package directly, unzip it and follow the directions in the README file or simply put the "Arc" directory in your icons directory.
```
cd ~/Downloads
wget https://github.com/horst3180/arc-icon-theme/archive/master.zip
unzip master.zip
sudo mv arc-icon-theme-master/Arc/ /usr/share/icons/
```

---

### Post by leunam12 on 2017-01-27
There is a note on teh website that says the package is unfinished and may not work sometimes, it also requires other icon themes.> Note: This is still unfinished. It may not work as expected in some cases.

At the moment this theme mainly includes icons for folders and mimetypes.
Requirements

This theme doesn't provide application icons, it needs another icon theme to inherit them. By default this theme will look for the Moka icon theme to get the missing icons. If Moka is not installed it will use the Gnome icon theme as fallback. To change the application icons, edit Arc/index.theme and replace Moka with the name of your preferred icon theme

[https://github.com/horst3180/arc-icon-theme](https://github.com/horst3180/arc-icon-theme)

---

### Post by tempusfugit1 on 2017-01-27
> **Artificial Intelligence said:**
> My French isn't great but I guessit says impossible to get the package. You could try get it manually here: [https://launchpad.net/~noobslab/+archive/ubuntu/icons/+packages](https://launchpad.net/~noobslab/+archive/ubuntu/icons/+packages)

look for arc-icons - 1.2~yakkety~NoobsLab.com and pick the *all.deb file.

EDIT: doh, you translated the line, I didn't see -_-

No problem, it's okay ! Btw it seems to be working ! Thanks a lot !

However, below the Ark Dark Theme picture, there is that phrase written : > *Pictured: My current desktop with Arc Dark GTK and Shell theme. I  have modified Arc with a transparent header. The icons are numix circle.*

What is "Shell Theme" ? The result of the combination of Arc theme and "Shell theme" is looking great !

---

### Post by Perfect Storm on 2017-01-27
Shell theme is that Gnome uses wherre ubuntu uses unity.

---

### Post by tempusfugit1 on 2017-01-27
> **Artificial Intelligence said:**
> Shell theme is that Gnome uses wherre ubuntu uses unity.


Ok I see, what does installing Gnome implies ? In terms of energy, performance, general user experience ? (Yea, I like to work in an environment that pleases me :-o) If I decide to install GNOME, and don't like or have problems with it, can I go back to Unity easily ?

Thanks again man for taking the time to answer me (I ask a lot of questions :P)

---

### Post by Perfect Storm on 2017-01-27
Shell theme is that Gnome uses wherre ubuntu uses unity.

---

### Post by tempusfugit1 on 2017-01-27
> **Artificial Intelligence said:**
> Shell theme is that Gnome uses wherre ubuntu uses unity.


Ok I see, what does installing Gnome implies ? In terms of  energy, performance, general user experience ? (Yea, I like to work in  an environment that pleases me :eek:) If I decide to install GNOME, and don't like or have problems with it, can I go back to Unity easily ?

Thanks again man for taking the time to answer me (I ask a lot of questions :razz:)

---

### Post by Perfect Storm on 2017-01-27
Seems a hiccup on the servers lol 
I think you should try the gnome-ubuntu live to see if it's something for you. then you can decide if it's for you.
[https://ubuntugnome.org/](https://ubuntugnome.org/)

---

### Post by tempusfugit1 on 2017-01-27
> **Artificial Intelligence said:**
> Shell theme is that Gnome uses wherre ubuntu uses unity.


Ok I see, what does installing Gnome implies ? In terms of  energy, performance, general user experience ? (Yea, I like to work in  an environment that pleases me :eek:) If I decide to install GNOME, and don't like or have problems with it, can I go back to Unity easily ?

Thanks again man for taking the time to answer me (I ask a lot of questions :razz:)

---

### Post by tempusfugit1 on 2017-01-27
> **Artificial Intelligence said:**
> Seems a hiccup on the servers lol 
I think you should try the gnome-ubuntu live to see if it's something for you. then you can decide if it's for you.
[https://ubuntugnome.org/](https://ubuntugnome.org/)

So if I want to use Gnome, I need to make a fresh install ? Nevermind then, the result I have now is more than ok !

PS : I thought my connection had troubles ... :)

---

### Post by Perfect Storm on 2017-01-27
You could install gnome Desktop along with unity:
```
sudo apt-get install ubuntu-gnome-desktop
```

---


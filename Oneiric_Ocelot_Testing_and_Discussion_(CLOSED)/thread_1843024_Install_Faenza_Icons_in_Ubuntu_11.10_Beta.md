---
title: "Install Faenza Icons in Ubuntu 11.10 Beta?"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by JonM33 on 2011-09-12
I used the following to install but not sure where to actually change it. I do not see the option to change icon themes in Appearance at all.

```
sudo add-apt-repository ppa:tiheum/equinox
sudo apt-get update
sudo apt-get install faenza-icon-theme
```

Can anyone help?

---

### Post by shafin on 2011-09-12
you need to install gnome-tweak-tool and change the icon theme from there.

---

### Post by JonM33 on 2011-09-12
> **shafin said:**
> you need to install gnome-tweak-tool and change the icon theme from there.

I've read on the forums here not to use that with the 11.10 Beta. Does that not still stand? Does it work for you?

---

### Post by DustinCasler on 2011-09-12
I'm not sure if gnome-tweak-tool causes other problems in the 11.10 beta. But changing the icons through that program worked great for me. The only issue I had is that it changes the cog to a blue computer monitor type icon. I'm not sure that constitutes an issue really, but I guess it sort of messes with the look of the top panel. It also works to change themes if you install any, but some of them don't really work out too well in 11.10 so far.

---

### Post by cariboo on 2011-09-12
> **JonM33 said:**
> I've read on the forums here not to use that with the 11.10 Beta. Does that not still stand? Does it work for you?

The only problem I've run into, is that gnome-tweak-tool depends on gnome-shell, which means it will be installed if it isn't already, which really isn't a problem as far as I'm concerned.

---

### Post by rvchari on 2011-09-12
> **JonM33 said:**
> I've read on the forums here not to use that with the 11.10 Beta. Does that not still stand? Does it work for you?

i ve installed faience (an off shoot of faenza and again created by the same author) from gnome-look. i downloaded the tarball and extracted to my .icons folder. then i chose that from gnome-tweak-tool and its functioning just well in unity as well as gnome-shell.

gnome-tweak-tool is not fully functional at beta1 stage i think (i am not able to chose the shell and extensions) but apart from that things are working fine...

---

### Post by shafin on 2011-09-13
If you're really against installing gnome-tweak-tool, install dconf-editor and change icon themes under org>gnome>desktop>interface.

---

### Post by TheNessus on 2011-09-13
some icons don't fit nicely into the indicators, at least not in non-dark faenza.

---

### Post by PuddingKnife on 2011-09-13
> **DustinCasler said:**
> I'm not sure if gnome-tweak-tool causes other problems in the 11.10 beta. But changing the icons through that program worked great for me. The only issue I had is that it changes the cog to a blue computer monitor type icon. 


I'm having that same problem. Is there a way to keep the rest of the Faenza set, but restore the 'power-cog' back to its former glory?

---

### Post by cariboo on 2011-09-13
> **PuddingKnife said:**
> I'm having that same problem. Is there a way to keep the rest of the Faenza set, but restore the 'power-cog' back to its former glory?

Wouldn't be easier to get the creator of the icon set to create a Unity icon?

---

### Post by PuddingKnife on 2011-09-13
Would it? I dunno. 

I would have ventured a guess that I could simply edit a config file to have the power-cog reset to default.

---

### Post by DustinCasler on 2011-09-13
I have tried messing around in various settings and searching around but still no way to get the original power cog back. I'm hoping that since we're still in beta a solution will be figured out soon. As popular as the icon set is with Ubuntu users I would imagine there will be a fix.

---

### Post by rvchari on 2011-09-13
> **TheNessus said:**
> some icons don't fit nicely into the indicators, at least not in non-dark faenza.

in the non-dark Faenza and its variants, i edited the index.theme.
in the inherits i edited Faenza to Faenza-Dark and that did the trick

---


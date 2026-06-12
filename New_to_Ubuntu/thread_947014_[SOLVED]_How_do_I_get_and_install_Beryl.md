---
title: "[SOLVED] How do I get and install Beryl"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-13
Hello,

I am installing Ubuntu for the first time because i saw Beryl and I really think it looks great.

I visited the Beryl website but I am not sure what I am supposed to download and how I would integrate Beryl into Ubuntu. Can anyone offer some help? Thank you.

p.s. I have a Dell XPS M1210 with the T7600 2.33GHz and 3.25GB of RAM available. I have 4GB of RAM installed in total. My video card is the Nvidia GeForce go 7400. Will I be able to use those cool Beryl effects with my current setup? Thank you again.

---

### Post by overdrank on 2008-10-13
> **GumpTron said:**
> Hello,

I am installing Ubuntu for the first time because i saw Beryl and I really think it looks great.

I visited the Beryl website but I am not sure what I am supposed to download and how I would integrate Beryl into Ubuntu. Can anyone offer some help? Thank you.

p.s. I have a Dell XPS M1210 with the T7600 2.33GHz and 3.25GB of RAM available. I have 4GB of RAM installed in total. My video card is the Nvidia GeForce go 7400. Will I be able to use those cool Beryl effects with my current setup? Thank you again.

Hi and beryl is no longer, you can look at the FAQ's link in my signature for compiz

---

### Post by HereInOz on 2008-10-13
Beryl is now Compiz, and if you have a recent version of Ubuntu, from Gutsy on, if I remember rightly, Compiz should already be installed.

Check out System > Preferences > Appearance > Visual Effects and you can configure it there.

You may want also to install the Compiz configurations settings manager, to give you more control over the effects.

Compiz, and all its accessories, is available using Synaptic Package Manager.

---

### Post by REDace0 on 2008-10-13
The command line way to get the compiz settings manager is
```
sudo apt-get install ccsm
```
You can also get more plugins for compiz if you like, and configure them using ccsm. Search the forums for info.

Also, I thought Beryl was the old version of Compiz-Fusion's window decorator (does window themes). As far as I know, it's now called Emerald, and is available in synaptic or using
```
sudo apt-get install emerald
```
Search the forum for help on setting it up.

---

### Post by johnycage on 2008-10-13
I use K-ubuntu 8.04, & I've enabled/installed compiz desktop effects but dont know where to costomise it...?

---

### Post by master5o1 on 2008-10-13
> **REDace0 said:**
> Also, I thought Beryl was the old version of Compiz-Fusion's window decorator (does window themes). As far as I know, it's now called Emerald, and is available in synaptic or using


Beryl was basically extra plugins for Compiz. Compiz Fusion is a merge of the plugins side of Compiz and the beryl team.
Emerald is the window decorator for Beryl (and now for Compiz Fusion too).


I.E.: Beryl is to Compiz as Emerald is to Metacity.



(I'm sure I'm right, but feel free to correct me...)

---

### Post by GumpTron on 2008-10-14
I activated the "extra" visual effects and now I have that cool wobbly effect with my windows. However, i recall wanting an effect that gives you something like a 3day rotation of 4 desktops. Can anyone help me with this?

---

### Post by schauerlich on 2008-10-14
> **GumpTron said:**
> I activated the "extra" visual effects and now I have that cool wobbly effect with my windows. However, i recall wanting an effect that gives you something like a 3day rotation of 4 desktops. Can anyone help me with this?

Once you install compizconfig-settings-manager then you will be able to enable the Desktop Cube effect. Make sure you have 4 workspaces, otherwise you will end up with what looks like a piece of cardboard (or a triangular prism, or a pentagonal prism, etc)

---

### Post by master5o1 on 2008-10-14
You need to have "Advanced Desktop Effects Settings" aka "Compiz Config Settings Manager" installed.


terminal:
`sudo aptitude install compizconfig-settings-manager`

or search for `compizconfig-settings-manager` in synaptic package manager.


You then should be able to check/uncheck options from the "Advanced Desktop Effects Settings" in System>Preferences.


I can't quite remember it all though...

---


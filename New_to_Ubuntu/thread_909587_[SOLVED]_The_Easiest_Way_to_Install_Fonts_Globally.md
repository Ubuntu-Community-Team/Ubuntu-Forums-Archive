---
title: "[SOLVED] The Easiest Way to Install Fonts Globally?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-09-03
In Ub' 7, there was a wonderfully stupid-easy way to install fonts globally: Press Alt-F2 to open a command prompt, type in "fonts://" and click &#8220;Run&#8221;, then drag the new fonts into the resulting Nautilus box. Done in a snap.

After a switch in machines, installing Ub' 8 and beginning the process of re-entering old files, I'm perturbed to find this doesn't work anymore. Rather than a Nautilus box, I get the following error pop-up: 
"Couldn't display "fonts:///". Nautilus cannot handle fonts: location."

So, what happened? Why doesn't this work anymore, and what are my options now?

---

### Post by ajgreeny on 2008-09-03
I have "cheated" and installed kcontrol which has a page which allows font installation on a system wide basis.  I agree the lack of something similar, unless I've just missed it, is an annoying problem in gnome, but I really don't like kde now I've got so used to gnome, so I just pick the few kde apps that I need and use them on my gnome desktop.  They look strange, but so what?

---

### Post by billgoldberg on 2008-09-03
> **E.T.Smith said:**
> In Ub' 7, there was a wonderfully stupid-easy way to install fonts globally: Press Alt-F2 to open a command prompt, type in "fonts://" and click “Run”, then drag the new fonts into the resulting Nautilus box. Done in a snap.

After a switch in machines, installing Ub' 8 and beginning the process of re-entering old files, I'm perturbed to find this doesn't work anymore. Rather than a Nautilus box, I get the following error pop-up: 
"Couldn't display "fonts:///". Nautilus cannot handle fonts: location."

So, what happened? Why doesn't this work anymore, and what are my options now?

This doesn't work anymore in Hardy.

Go to your home folder, and create a folder called ".fonts" (see the "." !).

In that put your fonts. And you should be able to use them.

---

### Post by E.T.Smith on 2008-09-03
> **ajgreeny said:**
> I have "cheated" and installed kcontrol which has a page which allows font installation on a system wide basis.

Where do I find it, and can it be added easily by either Add/Remove or Synaptic?

EDIT: Scratch that, I found it through Synaptic myself and just installed it. Er, but I don't know where this application installed *to*; I can't find it through any of the desktop menus. Where should I look?

> **billgoldberg said:**
> Go to your home folder, and create a folder called ".fonts" (see the "." !). In that put your fonts. And you should be able to use them.

Will this install them globally (usable in all applications by all users) and will I have to make an index file as some other linux distros require upon font installation? And what is the "**"." !**"?

---

### Post by knattlhuber on 2008-09-03
This isn't necessarily the easiest way to install fonts globally but it isn't rocket science either:

Create a folder for your fonts

```
sudo mkdir /usr/share/fonts/truetype/myfonts
```

Download some fonts and put them in that folder

```
sudo cp ~/Desktop/greatfont.ttf /usr/share/fonts/truetype/myfonts
```

Change in your new font folder and update the font config files from there

```
cd /usr/share/fonts/truetype/myfonts
sudo mkfontdir
sudo fc-cache
```

and you are good to go.

EDIT: Oops, sorry. Just read your signature. If you're strictly GUI, please ignore my post.

---

### Post by ajgreeny on 2008-09-04
No, putting fonts in your home/.fonts folder does not do the job for all users, only that one.  To open kcontrol, simply use Alt+F2 and enter **kcontrol** in the command box.  Up it will pop and you will find the Font Installer in the System Administration at the bottom.  Go there and click on Administrator Mode to do the job system wide.

---

### Post by E.T.Smith on 2008-09-04
> **ajgreeny said:**
> To open kcontrol, simply use Alt+F2 and enter **kcontrol** in the command box.  Up it will pop and you will find the Font Installer in the System Administration at the bottom.  Go there and click on Administrator Mode to do the job system wide.

Thanks, that got it. Frankly the kcontrol interface is a little unclear (it doesn't seem to acknowledge any switch to Administrator Mode, so I'm just assuming clicking the button worked) but the fonts are installed now across applications. All due credit to the Ubuntu community, but I have to echo your sentiment expressed earlier, that a easy native font installer seems like it should be an obvious feature. Yet I'm now on my third version of Ub' and in each edition I've had to install fonts in a different "backdoor" way.

---

### Post by sloggerkhan on 2008-09-04
there is a cool little program in the repos now called fonty python that you can use do make groups of fonts and do all kinds of font management.

---


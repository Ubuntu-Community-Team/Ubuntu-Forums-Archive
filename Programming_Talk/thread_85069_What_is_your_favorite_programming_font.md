---
title: "What is your favorite programming font?"
date: 2005-11-01
forum: Programming Talk
---

### Post by mfyahya on 2005-11-01
I'm using Andale mono since I moved to Ubuntu. It used to be fixedsys in Windows.
There are some nice ones [here]("http://www.proggyfonts.com/index.php?menu=download") specifically designed for coding.

What do you guys use?

---

### Post by swerner on 2005-11-01
[SIZE="3"][FONT="Courier New"]courier new, size 12 to 14 depending on screen res.[/FONT][/SIZE]

---

### Post by 23meg on 2005-11-01
Wherever there's code my eyes look for Bitstream Vera Sans [Mono].

---

### Post by Crazy Man on 2005-11-01
Courier New size 10 - 12 depending on resolution

---

### Post by JmSchanck on 2005-11-01
monospace 10 (@ 1024x768 resolution)

---

### Post by Buffalo Soldier on 2005-11-01
Bitstream Vera Sans Mono. Size 10 - 12.

---

### Post by tomchuk on 2005-11-02
[Proggy Clean, Slashed Zero, Bold Punctuation](http://www.proggyfonts.com/index.php?menu=download) or [Profont](http://www.tobias-jung.de/seekingprofont/)

---

### Post by Moonbuzz on 2005-11-03
[ProFont](http://www.tobiasjung.net/profont/), if only someone will finally help me install them :)

---

### Post by toojays on 2005-11-03
Nobody else here uses terminus?

---

### Post by LorenzoD on 2005-11-06
From ~/.gvimrc:

set guifont=Bitstream\ Vera\ Sans\ Mono\ 10

---

### Post by absolut on 2005-11-09
can someone post how to install these fonts?  i installed profont and could see it in gnome, but i couldnt see it in xfontsel.  is proggy easy to install?:confused:

---

### Post by gray-squirrel on 2005-11-09
I use Courier New exclusively when programming (not counting the times I use the terminal).  It's easier on my eyes, especially when syntax highlighting is on.

---

### Post by GTvulse on 2005-11-09
[QUOTE=absolut]can someone post how to install these fonts?  i installed profont and could see it in gnome, but i couldnt see it in xfontsel.  is proggy easy to install?:confused:[/QUOTE]
You need to installl profont somewhere public, such as
```
/usr/local/share/fonts
``` which already exists, for a reason :-).
Add the path to ```
/etc/X11/xorg.conf
``` (the syntax is self-explanatory). then in the directory where you installed the fonts type:
> 
sudo fc-cache .
sudo mkfontscale
sudo mkfontdir

in that order. Now, log out your session, hit ctrl-alt-backspace, watch X reboot, log in again and you should have your fonts working.

Edit: I typed mkfontcache but I shuold have typed mkfontscale.... My nemory is going fast...

---

### Post by Pathogenix on 2005-11-09
I know this is odd, but I use 11px Verdana - monospaced fonts aren't as easy on the eyes. If I need a monospaced font then it's usually andale mono.

---

### Post by absolut on 2005-11-09
thank you, it works fine now.  some of these programming fonts are tiny!
[QUOTE=dradul]You need to installl profont somewhere public, such as
 which already exists, for a reason :-).
Add the path to ```
/etc/X11/xorg.cof
``` (the syntax is self-explanatory). then in the directory where you installed the fonts type:

in that order. Now, log out your session, hit ctrl-alt-backspace, watch X reboot, log in again and you should have your fonts working.

Edit: I typed mkfontcache but I shuold have typed mkfontscale.... My nemory is going fast...[/QUOTE]

---


---
title: "What is the deal with Firefox?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by PureRicanGringo on 2008-07-29
It is constantly going to a sort of modified "full screen" mode where the screen resizing buttons dissapear and things sort of tend to freeze up and slow down. The only to fix it is to press F-11 to get it to true full screen mode and then switch it back to normal. It tends to happen at random when clicking on links to other pages. 

Because I like Linux I set up one of the office PCs with Hardy and I was just starting to get people to stop bitching about it but with this they are threatening mutiny.

---

### Post by hyper_ch on 2008-07-29
I'd say delete that whole FF profile and restart again

---

### Post by philinux on 2008-07-29
I think there might be a bug. Same here. It only happens when compiz is on. No problem with metacity.

---

### Post by PureRicanGringo on 2008-07-29
I am not sure I know what a FF profile is. Anyway, it is happening on my laptop too.

---

### Post by PureRicanGringo on 2008-07-29
It's OK, I just sort of hoped this was some kind of a known issue for which there existed an easy fix.

---

### Post by nvteighen on 2008-07-29
That's probably not FF, but Compiz's Window Manager failing (that's why it doesn't occur with Metacity).

Try Disabling effects and enabling them again (System->Preferences->Theme)

---

### Post by pedrogent on 2008-07-29
> **PureRicanGringo said:**
> I am not sure I know what a FF profile is. Anyway, it is happening on my laptop too.

Hi.

To see your Firefox profile go to your Home Folder in your home directory, e.g.

/home/pedro

Do a Ctrl+H to expose hidden files and directories in there. This will show up a whole bunch of 'dot' files (such as .mozilla). The 'dot' out the front is the way files get hidden in Unix.

If you delete .mozilla nothing 'bad' will happen. The next time you open up Firefox it will be like it has been freshly installed. Of course, this means  that you'll lose any bookmarks and extensions, etc. that you may have so you'll want to back-up all these first (or even make a back up of .mozilla).

---

### Post by philinux on 2008-07-29
The effect I'm seeing if I turn compiz on is that the whole top row of firefox disappears and any other app.

Go into the Advanced Desktop Effects Settings and untick windows decorations then tick it and the fault is cured. For now.

---

### Post by LowSky on 2008-07-29
Having the same issue randomly but it only occurs to FireFox. Something in Compiz doens't like FF3?

Well theres always opera and epiphany

---

### Post by include_pr on 2008-08-07
Same problem here.

I don't understand this,  Firefox is basically the default Browsing aplication in Ubuntu And Compiz comes enabled by default in Ubuntu. So basically these two aplications MUST cohexist. This problem is happening to a lot of people and the people who make the aplication / OS cannot address this problem.  To me that is the problem with Linux taking over the Desktop environment from Windows. It is just really unstable in this kind of things.  I love Ubuntu because it is good for managing Servers but in terms of Compiz and daily use of the desktop it falls short of other OS's. Back to searching the web to correct the issue. !@#%$#.

---

### Post by loligager on 2008-08-08
[http://www.blogsdna.com/430/9-fix-for-firefox-3-crashes-hanging-problem.htm](http://www.blogsdna.com/430/9-fix-for-firefox-3-crashes-hanging-problem.htm)
this might help

---

### Post by K.Mandla on 2008-08-08
> **philinux said:**
> The effect I'm seeing if I turn compiz on is that the whole top row of firefox disappears and any other app.
Is it possible to get a screenshot of that?

---

### Post by vikramaditya on 2008-08-08
Sorry I don't have a clue what's up with FF, but I'd appreciate a brief breakdown of its advantages over Opera.  I switched to Opera (NOT from the repos but d/l'ed v. 9.51 from their site) soon after installing Hardy & have been extremely pleased with its stability & functionality.  Flash works great, pages usually load very quickly, & I haven't suffered any real issues to speak of.  Granted I'm not a browser guru experimenting with plugins, toolbars, etc. so maybe I just don't understand what the big deal is with FF?

---

### Post by mcduck on 2008-08-08
Just check the Compiz settings, you might have a shortcut configured for full-screen.

(I have Alt-Enrter, but I think the default was something else.)

---

### Post by howlingmadhowie on 2008-08-08
> **vikramaditya said:**
> Sorry I don't have a clue what's up with FF, but I'd appreciate a brief breakdown of its advantages over Opera.  I switched to Opera (NOT from the repos but d/l'ed v. 9.51 from their site) soon after installing Hardy & have been extremely pleased with its stability & functionality.  Flash works great, pages usually load very quickly, & I haven't suffered any real issues to speak of.  Granted I'm not a browser guru experimenting with plugins, toolbars, etc. so maybe I just don't understand what the big deal is with FF?

firefox is (apart from some of the artwork and the name) Free software.

---

### Post by vikramaditya on 2008-08-08
> **howlingmadhowie said:**
> firefox is (apart from some of the artwork and the name) Free software.
The last I checked, so is Opera!  ;)

---

### Post by philinux on 2008-08-08
> **K.Mandla said:**
> Is it possible to get a screenshot of that?

Ok i just turned on desktop effects and this is what i get. also the bottom panel goes too. Thats hitting print screen ie the full screen. Have to either alt f4 or File quit. Then bottom panel is still there so I guess maybe firefox is resizing or something weird.

---

### Post by mcduck on 2008-08-09
The definitely looks like you have accidentally hit the keyboard shortcut to full-screen the program. (I'm not talking about the F11 fullscreen in Firefox, but the one done by the window manager).

Check System/Preferences/Keyboard Shortcuts -> Window Management/Toggle fullscreen mode.

Like I already posted, I have that set to Alt+Enter, but the default setting might have been something else. Using this feature will set any program to run full-screen, hiding all panels and window frames. Just like in your screenshot.

If that's not configured to any key combination, check Compiz settings if there's some similar shortcut. Although the Gnome's shortcut works even with Compiz running, at least without Emerald. (I remember either Compiz or Emerald having the same setting, might have been Emerald as I can't find it now and I haven't got Emerald installed any more..)

---

### Post by howlingmadhowie on 2008-08-10
> **vikramaditya said:**
> The last I checked, so is Opera!  ;)

to the best of my knowledge opera is proprietary, not free.

---

### Post by yairohayon on 2008-08-22
Hi all,
I think i might found the solution , you can google the problem and find that os x is having the same problem.
try go in firefox to about:config and change param - Browser.fullscreen.autohide to false.
it solved it for me and this problem was constant after i updated the gmail notifier plugin (maybe it changed this param - i am not sure).
Good luck.

---


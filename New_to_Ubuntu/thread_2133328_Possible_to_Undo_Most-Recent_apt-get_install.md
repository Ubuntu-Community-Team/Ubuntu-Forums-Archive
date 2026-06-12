---
title: "Possible to Undo Most-Recent apt-get install?"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by Iggy64 on 2013-04-07
I have made a major gaff, and I wonder if there is an easy way out.

I am using Bodhi Linux, based on Ubuntu.  For this particular machine, I chose Bodhi to keep the install light on disk space, and because I like the menu setup in e17.  In any case, I made a big booboo today, and wonder if there is a way out.

I was looking for a way to tweak the appearance of my GTK apps, especially the fonts.  I read a bit about the gnome-tweak-tool (but obviously did not read far enough) and it sounded like it might help.  So did an apt-get-install.  Bad idea.  In addition to the tweak tool, I got the gnome shell, nautilus, pulseaudio, and hundreds of other things.  Most of this stuff I don't need.  Although I have now somewhat "learned my lesson" about doing a test install first, I'm wondering if there is any way to essentially "undo" this hundreds-of-items download/install.

I have not installed anything further since that goof, so it was the last install done.  

Any possible solution?  I looked in the log, and there's no way I can remove all those packages one by one.

---

### Post by sandyd on 2013-04-07
Run
```

awk '!/^Start|^Commandl|^End|^Upgrade:|^Error:/ { gsub( /\([^()]*\)/ ,"" );gsub(/ ,/," ");sub(/^Install:/,""); print}' /var/log/apt/history.log
```

copy the last line of output (it may wrap)
```

sudo apt-get remove [packageshere]
```
replace [packageshere] with the last line

---

### Post by ibjsb4 on 2013-04-07
Wow, its a keeper :)

Thanks sandyd

---

### Post by Iggy64 on 2013-04-07
Wow!  That sure is very clever.  And VERY much appreciated.

Before I "pull the trigger," let me ask you this:

Should I be adding any purge or autoremove to your command.  I don't know if there are any config files or whatever to remove.  Sorry to be such a noob; but this is a great education.

---

### Post by Cheesemill on 2013-04-07
> **ibjsb4 said:**
> Wow, its a keeper :)

Thanks sandyd

Isn't it just.

I've needed something that does exactly this several times recently :KS

---

### Post by Impavidus on 2013-04-08
I'd say using```
sudo apt-get remove the-package-you-installed
sudo apt-get autoremove
```should work too. The first command will remove the package you mistakenly installed, the second will remove all its dependencies you no longer need. It's not exactly an undo, but it would solve your problem.

---

### Post by Iggy64 on 2013-04-08
Thanks to all who made suggestions.

I believe that the

sudo apt-get remove [pkgname]
sudo apt-get autoremove

approach would be helpful, but not a complete solution.  In the present case, the package brought along a lot of recommends, in addition to the dependencies.  I believe the autoremove will take out the dependencies that are not needed elsewhere; but I don't think it will take out recommended programs like Nautilus, PulseAudio, Gnome Shell, and so on.  Of course, I am a rank beginner, and am not certain at all about this.  Nevertheless, I am grateful for the suggestion.

I went ahead with the solution written by sandyd, which appears to address very specifically all of the packages that were installed alongside the gnome-tweak-tool.  (There were 158 packages!)  It appears to have worked like a charm.  The only remaining question I had was whether I should have added a purge to the command.  I subsequently looked into Synaptic and saw all the residual config files that were left behind.  But it is easy enough to simply remove them all in Synaptic.

Hopefully, I've learned my lesson about installing packages without thoroughly researching them, and without running a trial install.  That said, I have copied the elegant solution written by sandyd to my special folder of Linux tricks, just in case.

Again, many thanks to sandyd for bailing me out, and to the others who took time to help.

---


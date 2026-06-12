---
title: "Panel Problems 12.04 gnome classic"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by bikefreakvinnie on 2012-05-01
I've accidentally deleted everything off the gnome classic top panel and now i desperately want to replace them! 

I've been able to add a few things back onto the panel (using alt + right click) but not the:
volume control
battery status
wireless menu


In previous versions of ubuntu i used delete the panel and replace it using the following (from a thread):

 gconftool-2 — – shutdown

 rm -rf ~/.gconf/apps/panel

 pkill gnome-panel

and then restart

However in 12.04 this just replaces the panel without the features which i have deleted! 

Thanks in advance if anyone knows how to solve this either to simply add the features that i've deleted or to replace with a fresh original panel...

---

### Post by bikefreakvinnie on 2012-05-03
bump

---

### Post by prattler on 2012-05-05
Seems that gnome-panel, etc settings moved to dconf, whatever that is.

To recover the original gnome panel settings try doing something like this in the terminal.
WARNING: this will reset other gnome-shell (?) settings, too.

```
mv ~/.config/dconf/user ~/.config/dconf/user-backup
killall gnome-panel
```

If gnome-panel doesn't reappear, you can relauch it:

```
gnome-panel &
```

Separate settings can be edited with the program ```
dconf-editor
```, but I'm having trouble with that, perhaps someone could enlighten us all.

---

### Post by bikefreakvinnie on 2012-05-05
Well done prattler -you did it! thats been annoying me for days - cheers for that!

---

### Post by Nico-dk on 2012-05-09
My thanks to prattler as well :)

---

### Post by SmallWorld on 2012-09-11
I just had the same problem, but the above solution didn't work for me - my panels would disappear and then reappear in the same (broken) state.

I'm running Gnome3 Classic on Ubuntu DE 12.04.1 64bit.

The second post at [http://askubuntu.com/questions/125662/how-to-reset-gnome-panel]("http://askubuntu.com/questions/125662/how-to-reset-gnome-panel") gave me a solution that did work.  To paraphrase that post, my solution was:

```
sudo apt-get install dconf-tools
dconf reset -f /org/gnome/gnome-panel/
```

This reset my panels to the default settings.

---

### Post by chukkers on 2012-10-25
> **prattler said:**
> Seems that gnome-panel, etc settings moved to dconf, whatever that is.

To recover the original gnome panel settings try doing something like this in the terminal.
WARNING: this will reset other gnome-shell (?) settings, too.

```
mv ~/.config/dconf/user ~/.config/dconf/user-backup
killall gnome-panel
```

If gnome-panel doesn't reappear, you can relauch it:

```
gnome-panel &
```

Separate settings can be edited with the program ```
dconf-editor
```, but I'm having trouble with that, perhaps someone could enlighten us all.

after having set up 2 displays earlier on 2day i thought i was going to have to re-install as 3 top and 3 bottom panes were a bit much lol
  
thank you so much this did the trick ;P

---

### Post by descomputer on 2013-05-29
After backing up the conf file I ran the "dconf reset -f /org/gnome/gnome-panel/" listed above and all is well.
I just need to get the day and date working which I saw on another post

---

### Post by Cory_Mittleider on 2013-08-19
> **prattler said:**
> Seems that gnome-panel, etc settings moved to dconf, whatever that is.

To recover the original gnome panel settings try doing something like this in the terminal.
WARNING: this will reset other gnome-shell (?) settings, too.

```
mv ~/.config/dconf/user ~/.config/dconf/user-backup
killall gnome-panel
```

If gnome-panel doesn't reappear, you can relauch it:

```
gnome-panel &
```

Separate settings can be edited with the program ```
dconf-editor
```, but I'm having trouble with that, perhaps someone could enlighten us all.

Great this helped me repair my panel.  12.04 -Gnome classic
Thank you

---

### Post by Bisneff on 2014-06-11
> **prattler said:**
> Seems that gnome-panel, etc settings moved to dconf, whatever that is.

To recover the original gnome panel settings try doing something like this in the terminal.
WARNING: this will reset other gnome-shell (?) settings, too.

```
mv ~/.config/dconf/user ~/.config/dconf/user-backup
killall gnome-panel
```

If gnome-panel doesn't reappear, you can relauch it:

```
gnome-panel &
```

Separate settings can be edited with the program ```
dconf-editor
```, but I'm having trouble with that, perhaps someone could enlighten us all.


Thank you!

---


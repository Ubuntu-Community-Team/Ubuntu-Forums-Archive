---
title: "Running Kubuntu in Ubuntu"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by jermza on 2012-01-04
Instead of installing Kubuntu over Ubuntu, is it possible to run Kubuntu in Ubuntu 11.10?

If so, then is it recommended NOT to do so? That is, will Ubuntu / Kubuntu break or will each of them run smoothly?

---

### Post by Lars Noodén on 2012-01-04
If you want KDE then you can install the package kde-plasma-desktop.  If you want full Kubuntu with all of the default applications, then install kubuntu-desktop.  Then when you log in you can choose KDE from the pulldown menu as you enter your username.

---

### Post by jermza on 2012-01-04
What are the pros and cons of doing it that way? (Installing both options, that is.)

---

### Post by Lars Noodén on 2012-01-04
Installing kubuntu-desktop will also install kde-plasma-desktop along with everything else belonging to Kubuntu.  It will take more space, but will give you the full Kubuntu experience.  Installing just KDE will give you KDE and not add any applications, leaving your system otherewise as it was.

---

### Post by jermza on 2012-01-04
If I install the full Kubuntu desktop from the Software Centre, and then decide to remove it in the same way, then will my Ubuntu desktop (and apps) be reverted to the way they were? Or will there be undesirable residual leftovers?

---

### Post by Lars Noodén on 2012-01-04
The package kubuntu-desktop will only add to what you have, not replace anything.  

That said it is harder to uninstall because it is a metapackage and as such only points to other packages as dependencies.  I'm not sure of an easy way to uninstall it.  You could of course make a list of what you have now and then later uninstall the difference.

---

### Post by mastablasta on 2012-01-04
here is a one line command (you can copy it) that will remove Kubuntu and bring you back only Gnome as you originally had: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
 
Installing Kubuntu desktop - there will be one difference. you could see some doubling in programmes/widgets. for example you might see Gnome battery monitor and a KDE battery monitor next to it.
still it is a good way to test it and you can always revert back to origial Ubuntu only by using the command in link above.
 
another way to test out Kubuntu is to use a live disk (CD or USB).

---

### Post by jermza on 2012-01-04
Thanks. I did all of that and have successfully removed Kubuntu from my Ubuntu installation.

One little issue.

My system fonts have gone funky. I have the MS core fonts installed, so fonts like Arial are still there, yet it seems that all of my anti-aliasing has gone, despite checking the correct settings in Advanced Settings.

Any advice?

EDIT: It sort of looks as if I don't have the MS core fonts installed, yet it shows me that they are.

---

### Post by mcduck on 2012-01-04
> **jermza said:**
> Thanks. I did all of that and have successfully removed Kubuntu from my Ubuntu installation.

One little issue.

My system fonts have gone funky. I have the MS core fonts installed, so fonts like Arial are still there, yet it seems that all of my anti-aliasing has gone, despite checking the correct settings in Advanced Settings.

Any advice?

EDIT: It sort of looks as if I don't have the MS core fonts installed, yet it shows me that they are.

Try uninistalling and then reinstalling the MS fonts package. It's a bit tricky one because the fonts aren't actually included in the package itself (due to the restrictions Microsoft has for distributing the fonts), it's just a script that downloads the fonts for you. So if the package installation fails in some way (the script can't download the fonts for some reason or other, or you don't accept the license) you can end with the package installed but without the actual fonts.

---

### Post by jermza on 2012-01-04
I've removed and installed it a few times. Each time I install, I get no prompt to accept the licence. And I can see that Arial, for example, is installed because I can select it in Advanced Settings for my system-wide font and it changes.

Yet, my fonts in Thunderbird and Firefox look mono and terrible.

---

### Post by drmrgd on 2012-01-04
I wonder if the fonts database needs to be updated, and you're actually just seeing a ghost listing in there.  Try running:

```
sudo fc-cache -fv
```

That will update the fonts database and may help.  You could also try a reboot (if you've not done that already!).

---

### Post by jermza on 2012-01-04
Here's how Google now looks. You can see how small and aliased the text is.

[IMG]http://i.imgur.com/XSHI4.png[/IMG]

EDIT: Something is definitely broken because, if I navigate to my own website - which uses Arial - then the displayed font is right. I've used Synaptic Package Manager to remove and install the MS core fonts (and accepted the licence) and I can see that Arial is being used in, say, Nautilus (after using Advanced Settings to change the font).

---

### Post by jermza on 2012-01-04
It seems that, system-wide, the fonts are displaying correctly. 

The fonts are NOT, however, displaying correctly in Firefox and Thunderbird.

EDIT: Nor they display correctly in Chromium.

---


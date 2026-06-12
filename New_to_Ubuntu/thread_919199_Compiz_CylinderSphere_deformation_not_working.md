---
title: "Compiz Cylinder/Sphere deformation not working"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-09-13
I just upgraded to Compiz 0.7.6 using this guide on Hardy:

[http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28](http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28)

I have an Intel GMA 950 integrated. It should be the latest driver.

Compiz still works. Even though I selected 'Sphere' or 'Cylinder' for the cube deformation, my desktop is still a cube even though I rotate it. It doesn't change into a sphere or anything.

Help? Thanks.

---

### Post by tarahmarie on 2008-09-13
> **akiratheoni said:**
> I just upgraded to Compiz 0.7.6 using this guide on Hardy:

[http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28](http://maketecheasier.com/make-your-ubuntu-desktop-rotate-as-a-cylindersphere/2008/07/28)

I have an Intel GMA 950 integrated. It should be the latest driver.

Compiz still works. Even though I selected 'Sphere' or 'Cylinder' for the cube deformation, my desktop is still a cube even though I rotate it. It doesn't change into a sphere or anything.

Help? Thanks.

I just worked with this too.  Did you (a) enable cube reflection and deformation in CompizConfig Settings Manager? (b) select Cylinder for deformation? (c) enable "unfold cube deformation"? (d) up the aspect ratio to about half (or whatever)? (e) enable "deform caps"? (f) enable all the options in 'appearance'?

---

### Post by tarahmarie on 2008-09-13
It might also be that the option "enable deformation only on mouse rotate" is checked or unchecked, depending on what you want.

---

### Post by Bigbob22 on 2008-09-13
try restarting your computer and then trying it.

---

### Post by pratiks19 on 2008-10-19
I get this error when i type "compiz -replace &" in the terminal

problems after installing emerald:
1) window title bar not visible
2) Alt+F2 doesnt start the run, though it is still present in the keyb shortcuts

[1] 6553
Checking for Xgl: pratik@pratik-laptop:~$ not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin '–replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_border_picture
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

plz help

---

### Post by superscalar0 on 2009-01-05
@akiratheoni

I noticed the same problem you describe when I enabled Emerald, and **it was fixed** when I went back to Metacity. Maybe that will work for you.

[COLOR="Blue"]I tried going back to Emerald to recheck but could not reproduce the problem. BUT, as far as I can tell, I had the same problem as you, so it's worth a shot.[/COLOR]

I don't know yet how to install older versions of software in Ubuntu, but I suspect that there may be a bug in current releases of Emerald or maybe Compiz.

[COLOR="Blue"]I could be completely wrong here too.
[/COLOR]
@pratiks19

You have to use **two** dashes to replace, as in: ```
 compiz --replace & 
```

Also, you shouldn't need to --replace with compiz. Just go to System->Preferences->Appearance->Visual Effects and enable some graphical effects. That will enable Compiz. After that, get CompizConfig Settings Manager (search ccsm in Synaptic) and you can customize it.

You can try Emerald with the command ```
emerald --replace &
```
To have it loaded with Compiz, go into CCSM and find the plugin "Window Decoration".  Switch what's in the Command section to "/usr/bin/emerald" (no quotes). Reboot, and you'll see emerald.

As for the other stuff, I don't know.


This is my third day with Ubuntu, and I am very impressed! I had run FreeBSD for a few months (you get some :twisted:HARDCORE:twisted: diagnostic experience with that), but Ubuntu's just great!

---

### Post by ben2talk on 2009-05-23
I'm sorry - but I just found this thread - my cylinder deformation JUST stopped working, and these tips aren't helping at all.

I used Fusion-icon to change settings, reload, switch managers, and in settings I enabled sphere/cube and turned them on and off, it just seems the plugin has died. Any ideas?

Using 'compiz-check' gets a list of green OK's and it seems okay apart from the deformation.

---

### Post by naarkhoo on 2009-11-18
> **ben2talk said:**
> I'm sorry - but I just found this thread - my cylinder deformation JUST stopped working, and these tips aren't helping at all.

I used Fusion-icon to change settings, reload, switch managers, and in settings I enabled sphere/cube and turned them on and off, it just seems the plugin has died. Any ideas?

Using 'compiz-check' gets a list of green OK's and it seems okay apart from the deformation.

I have got exactly the same problem, how should I fix?
> 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
compiz 0.8.4

And I am on Karmic

---

### Post by xtracool_protik on 2009-11-18
I confirm the same issue on Karmic

@narkhoo
 Can u try wallpaper plugin even that doesn't seem to be working for me after trying all tricks available online.
 
 And is there a way to enable/disable compiz plugin on terminal so that I can see wats going on? As my wallpaper plugin switches back to disabled state when I enable it would like to paste output of terminal but don't know the way to enable/disable through terminal

---


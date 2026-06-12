---
title: "Where did my installed software go?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by zzzonked on 2008-08-15
I used Synaptic Package Manager to install POV-Ray. The dialog box came up saying that it was installed, but now I can't seem to find it. I'm pretty sure it's nowhere under applications. Any suggestions? Where do the programs usually go? I tried launching a .pov file but it wouldn't launch, i.e. nothing happened when I double clicked it, lotsa times :(

---

### Post by Crafty Kisses on 2008-08-15
> **zzzonked said:**
> I used Synaptic Package Manager to install POV-Ray. The dialog box came up saying that it was installed, but now I can't seem to find it. I'm pretty sure it's nowhere under applications. Any suggestions? Where do the programs usually go? I tried launching a .pov file but it wouldn't launch, i.e. nothing happened when I double clicked it, lotsa times :(

Try running it in Terminal.

---

### Post by zzzonked on 2008-08-15
Err... sorry, but how? :p I typed the entire directory of the .pov file in Terminal but Terminal doesn't seem to read spaces (one of the folder names has a space in it).

---

### Post by Crafty Kisses on 2008-08-15
> **zzzonked said:**
> Err... sorry, but how? :p I typed the entire directory of the .pov file in Terminal but Terminal doesn't seem to read spaces (one of the folder names has a space in it).

Try running:
```
povray
```

---

### Post by iaculallad on 2008-08-15
> **zzzonked said:**
> Err... sorry, but how? :p I typed the entire directory of the .pov file in Terminal but Terminal doesn't seem to read spaces (one of the folder names has a space in it).

Locating an application through terminal would be:

```
which application_name
```

As this will give you the directory of where you're app/package is installed.

---

### Post by LeetSpeak on 2008-08-15
Go to applications>accessories>terminal and type

[HTML]which application_name[/HTML]



should come up now, I hope it worked.

---

### Post by billgoldberg on 2008-08-15
Right-click a .pov file in the file manager.

Go to properties -> open with -> add.

Then select povray or use the command povray to add it if it isn't there.

Then when you double click a .pov file, it should open in povray.

Btw, what is a .pov file. 

Are you sure povray has a gui?

---

### Post by zzzonked on 2008-08-15
Okay, which povray worked. Now I know where it is :) But, nothing happens when I double click the icon :(

---

### Post by zzzonked on 2008-08-15
Yep, I'm pretty sure it has a GUI. It did in Windows.

---

### Post by zzzonked on 2008-08-15
Err... so how do I get it running once I've located it? Nothing happens when I double click the icon. And double clicking .pov files won't enable me to open it either :( The .pov files were created when I was still using Windows, and launching them would launch POV-Ray by default, but apparently that's not the case here...

---

### Post by Paqman on 2008-08-15
> **zzzonked said:**
> Yep, I'm pretty sure it has a GUI. It did in Windows.

From the package description in Synaptic:
> 
POV-Ray by itself is a command-line utility that will take scene
descriptions, written in a special easy-to-understand language, to
produce ray-traced images (or even a sequence of images, for animations).
You can either write those scene-descriptions by hand, or use external
tools to generate (parts of) the scene.


---

### Post by t0p on 2008-08-15
> **zzzonked said:**
> Err... so how do I get it running once I've located it? Nothing happens when I double click the icon. And double clicking .pov files won't enable me to open it either :( The .pov files were created when I was still using Windows, and launching them would launch POV-Ray by default, but apparently that's not the case here...

I don't know what povray is, or .pov files... but have you tried typing ```
povray
```

into terminal?  That should run it.

Also, what about what billgoldberg suggested - right-click a .pov file, then select povray from the menu or type povray in as the command to use.

If those don't work, post back and say what you've tried.

**EDIT:** In Paqman's post, above, he quotes Synaptic saying that povray is a **command line utility** - ie it does NOT have a gui.  You need to run it in terminal.  For instructions on how to use it, check the manpage by typing into terminal
```
man povray
```

or it might be **pov-ray** I suppose.

---

### Post by zzzonked on 2008-08-15
Sorry for all the confusion guys. I've tried right click > open with... > then type "povray", nothing happened. I've tried opening terminal and just typing "povray", a long list of stuff came out but nothing launched. I've tried typing "man povray" in terminal and I got a very long manual which I've never seen before and am still reading. I've tried typing the .pov file's directory into terminal but terminal couldn't read it because there's a space in the one of the folders' name. How do you type spaces in terminal?

I don't think POV-Ray uses a CLI. It *has* a CLI. But it also has a text editor, urgh how do I put this... Meaning you can achieve the same effect through two means: the Command Line, and the text editor. But most of the time you use the text editor, and most of the stuff goes in the text editor too. It uses its own language in the text editor. Then you have to export the coded image into a .png file. A .pov file is just a text file, just like a .html file. It needs to be exported into a .png image file with POV-Ray. I consider it GUI because there are buttons that achieve certain effects with point-and-click, it's not very different from Kile, most of the stuff is just text-based, but there's a graphical menu above all the text. In short, I'd say it's something like Kile that produces images.

So does this help you guys understand the program better to know what it's supposed to run in?

---

### Post by Paqman on 2008-08-15
> **zzzonked said:**
> 
I don't think POV-Ray uses a CLI. It *has* a CLI.

From the description i'd say that it definitely doesn't have a GUI. That's generally what "this is a command-line utility" means.

---

### Post by 3rdalbum on 2008-08-15
You say "a long list of stuff came out" when you typed "povray" into the terminal. Usually this stuff tells you how to use the program, sort of like a quick-start manual.

It should tell you what options it accepts. I don't know anything about Povray so I have no idea what options these might include.

My other thought is: Can Blender import and render Povray files?

---


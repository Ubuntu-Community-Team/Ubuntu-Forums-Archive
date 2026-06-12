---
title: "Compile From Source"
date: 2007-03-03
forum: Programming Talk
---

### Post by brokencrystal on 2007-03-03
I want to recompile Ubuntu (Gnome) from source because I want to remove the arrow on the 'main menu applet' (not usp) that covers my custiom icon.

1. Does anyone know where I can get the source code for Ubuntu's Gnome? I want Ubuntu's version of Gnome, as not to change my Ubuntu too much.

2. Does anyone know what part of the code I need to comment out to remove this arrow? I read how to do it before on the net, but I can't find it now.

3. Can anyone tell me how to recompile it when I am done commenting out this line of code?

4. Is there any way to make this new recompiled verison of Ubuntu as a Ubuntu Install/Live CD so I can install the modified version of Ubuntu on all my other machines?

Thanks in advance...

---

### Post by tbodine on 2007-03-03
Um, I'm sorry but I doubt that compiling GNOME from source would get rid of the arrow on the main menu, try looking in the configuration editor for something that might do it.
But to get the source code for any app that you can install via Aptitude merely use the command
```
sudo apt-get source app
```
In your case I guess it would be
```
sudo apt-get source ubuntu-desktop
```
You should be able to use Linux Google to search for how to compile software if the need actually arises.

---

### Post by brokencrystal on 2007-03-04
There is nothing in the configuration editor... (Stupid, I know)  The only way that I have heard of anyone getting rid of that arrow is to comment out a line in the code and recompile it.  I just need the details...

---


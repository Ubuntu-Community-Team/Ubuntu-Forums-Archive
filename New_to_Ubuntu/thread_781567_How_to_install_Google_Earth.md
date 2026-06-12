---
title: "How to install Google Earth?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ChildOfMana on 2008-05-04
So I've just downloaded Google Earth for Linux and now I'm left with a file on my Desktop called GoogleEarthLinux.bin

How do I install this?

Is it an image file (eg .cue/.bin)?

Do I need to burn to disc and then install?

I'm new to the Linux game so I apologise if this is really obvious.

I've searched the forum and had a quick look around the Google Earth site but can't find any answers.

Thanks.

---

### Post by MattBD on 2008-05-04
I'd use Medibuntu to get it if I were you, that way you can get it from the repositories. The link is [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by Monicker on 2008-05-04
Install googleearch-package

or 

[https://help.ubuntu.com/community/GoogleEarth]("https://help.ubuntu.com/community/GoogleEarth")

---

### Post by chemtut on 2008-05-04
right click file
go to permissions
tick box make file executable
close window
double click icon

---

### Post by mahiyar on 2008-05-04
If i remember correctly it is a .sh file (script) that gets downloaded and you have to run the same from a command line.

---

### Post by ChildOfMana on 2008-05-04
Wow, thanks guys.

Think I'll try the medibuntu repository.

Appreciated.

---

### Post by T-Virus on 2008-05-04
Installed it of repos myself, haven't encountered any problem with that. :)

---

### Post by Peterfc on 2008-05-04
Hi

After i asked for help with the same problem yesterday i found this link below. It worked fine for some things i wanted and i then spotted the install Google Earth. Hope it helps.

Just go down to 1.3.11 Utilities


[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by CoCoKnots on 2008-06-16
I know this is a dated thread & it has already answered many of my questions about installing Google Earth. It shows up on my Applications/Internet tab without any issues. When I click on the icon, the program opens, but it runs slow & jerky. I used to use Google Earth with Windows XP. It was always smooth in moving & zooming. Is there something else I'm suppose to load, perhaps another driver?

---

### Post by PseudoOne on 2008-06-16
There are many ways of installing Google Earth, including from the repository, but since you have already downloaded the linux bin file, here are the directions.

cd to the directory the file is in.
sudo chmod +x googleearthlinux.bin
./googleearthlinux.bin

and it will give you the graphical installer.

---

### Post by PseudoOne on 2008-06-16
I'm sure you don't need drivers, but possibly a graphics card that was meant to support Linux systems as well.  Just a thought, because my Ubuntu version of GE runs very smooth.

---

### Post by RomeReactor on 2008-06-16
> **CoCoKnots said:**
> I know this is a dated thread & it has already answered many of my questions about installing Google Earth. It shows up on my Applications/Internet tab without any issues. When I click on the icon, the program opens, but it runs slow & jerky. I used to use Google Earth with Windows XP. It was always smooth in moving & zooming. Is there something else I'm suppose to load, perhaps another driver?

Hi. Can you give us more details about your system--video card, processor, amount of memory? Also please run this command from the terminal (Applications->Accessories->Terminal):
```
glxinfo | grep rendering
```
and post the output.

---

### Post by CoCoKnots on 2008-06-16
It just came back with... direct rendering: Yes
I think I missed something.

---

### Post by RomeReactor on 2008-06-16
Then your card has hardware accelaration already enabled, so the problem might be if you have a low end ATI or nVidia card, or an integrated gpu--Intel, VIA, SiS. If you have desktop effects enabled, turn them off and see if GoogleEarth's performance increases.

---

### Post by CoCoKnots on 2008-06-16
I just went thru the documentation I have & couldn't find anything. The ATI sounds familiar. My notebook is a Sony VAIO VGN-FE780G . It's about a year old and has been great other than the Windows XP issues (which are now gone).

---

### Post by RomeReactor on 2008-06-16
To find out which video card you have please post the output of the following:
```
sudo lshw -C display
```

---

### Post by stchman on 2008-06-16
Post an lspci terminal output here in this thread.

ATI or Nvidia Hardy works very well with these cards.

To install GE use Medibuntu.  I have a tutorial on installing Medibuntu.

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

After successful installation of Medibuntu for your distro do the following in a terminal.

```

sudo apt-get update
sudo apt-get install googleearth

```

Assuming that the drivers for the video card are right then GE will work.

On my laptop I have to disable desktop effects.

---

### Post by markbuntu on 2008-06-16
Desktop visul effects, which XP does not have, can create issues with running google earth. So, turn them off by right clicking on your desktop and using the menu there. after using google earth you can turn them back on the same way.

Some video cards will support google earth with desktop effects set to normal so yiu can try that first.

---

### Post by stchman on 2008-06-16
> **markbuntu said:**
> Desktop visul effects, which XP does not have, can create issues with running google earth. So, turn them off by right clicking on your desktop and using the menu there. after using google earth you can turn them back on the same way.

Some video cards will support google earth with desktop effects set to normal so yiu can try that first.

I personally believe it to be related to graphics power of the card.  I can run GE with desktop effects on using my 8800GT and 7600GT with no problem.  My laptop uses an X3100 and while it will run with desktop effects enabled it is very choppy.

---


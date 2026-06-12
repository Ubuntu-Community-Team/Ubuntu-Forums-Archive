---
title: "Hack in media application..."
date: 2010-10-06
forum: Programming Talk
---

### Post by Moozillaaa on 2010-10-06
I'm trying to RESIZE a reference symbol used in GIMP when rotating images, and it's not a configuration setting.

Does anyone know where the GIMP script file is, to re-PROGRAM this function? (screenpic below of target object - bullseye-like symbol)







[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171472&d=1286395388[/IMG]

---

### Post by spjackson on 2010-10-06
I didn't realise that you had reposted and I replied to your other thread. [http://ubuntuforums.org/showthread.php?p=9932840#post9932840](http://ubuntuforums.org/showthread.php?p=9932840#post9932840)

---

### Post by Vox754 on 2010-10-06
> **Moozillaaa said:**
> I think you're right there, hhh - I thought I'd try the Programming' forum tho', since it will involve modifying code for the application.

And good for you - actually reading the question! I think it went right over the others' heads. :(
LOL. Your original post doesn't even make sense.

It's quite understandable why people mistook your question.

...wait. That is not even a question!

Learn to write better posts.

Oh, and it seems you lack the necessary background in programming to edit the GIMP's "script file", so don't even bother.

---

### Post by Moozillaaa on 2010-10-07
I found a 'Rotate' Plug-in, which is an ***executable (application/x-executable)***.

I installed a hex editor - which I'm guessing is necessary to accomplish this task???

---

### Post by spjackson on 2010-10-07
> **Moozillaaa said:**
> I found a 'Rotate' Plug-in, which is an ***executable (application/x-executable)***.

I installed a hex editor - which I'm guessing is necessary to accomplish this task???

As I read it, the source for /usr/lib/gimp/2.0/plug-ins/rotate is gimp-2.6.9/plug-ins/common/rotate.c . I'm prettty sure this is the case because running "strings" on the executable outputs text that matches what is in the this source, i.e.

"This plug-in does rotate the active layer or the whole image clockwise by multipes of 90 degrees. When the whole image is choosen, the image is resized if necessary."
"Rotates a layer or the whole image by 90, 180 or 270 degrees"

I don't think that's the tool you showed, which permits rotation by any angle around any point.

Furthermore, the strings for the dialog in your screenshot are in the the gimp executable.
```

$ strings /usr/bin/gimp-2.6 | grep _Angle; strings /usr/bin/gimp-2.6 | grep Center
_Angle:
Center _X:
Center _Y:
Center lines

```I still think that the source for that cross-hair in a circle is what I mentioned in my earlier reply. I wouldn't recommend trying to patch the executable.

---

### Post by Moozillaaa on 2010-10-14
> I'm not really familiar with the Gimp source but I have done a bit of digging.

I think the actual drawing takes place in app/tools/gimpdrawtool.c , with the 2 cases:
GIMP_HANDLE_CIRCLE and GIMP_HANDLE_CROSS.

I think the size calculation happens in app/tools/gimptransformtool.c

I hope that points you in the right direction at least.I'm having no luck finding those folders or files in any filepath Karmic / (GIMP 2.6).

Any ideas?

---

### Post by mc4man on 2010-10-14
> I'm having no luck finding those folders or files in any filepath Karmic / (GIMP 2.6)
He was referring to the gimp source code.
The best thing was prev. suggested - posting on gimp forums, maybe someone who knows the code can advise properly.

On first look changing the tool diameter would seem easy, but what other un-intended consequences, if any, don't have a clue.
screen 1 - orig
screen 2 - increased by about an apparent 35%, give or take
( done by changing the define in /app/tools/gimptransformtool.c - line 67 here

> --- gimp-2.6.10.orig/app/tools/gimptransformtool.c
+++ gimp-2.6.10/app/tools/gimptransformtool.c
@@ -64,7 +64,7 @@
 #include "gimp-intl.h"
 
 
-#define HANDLE_SIZE     25
+#define HANDLE_SIZE     35
 #define MIN_HANDLE_SIZE  6

---

### Post by Moozillaaa on 2010-10-15
I think that what you've done is what I want to do, but I do not see a file or folder anywhere with ANY names that might get me to that code file.




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=172382&d=1287119183[/IMG]


The GIMP forum got me a reply - 1 - in 9 days. Worthless.
[http://gimpforums.com/thread-increase-size-of-reference-symbol-in-rotate-function?pid=890#pid890](http://gimpforums.com/thread-increase-size-of-reference-symbol-in-rotate-function?pid=890#pid890)

---

### Post by James78 on 2010-10-15
Really? I see it..

---

### Post by Moozillaaa on 2010-10-15
Can anybody help out here?

---

### Post by saulgoode on 2010-10-15
> **Moozillaaa said:**
> I think that what you've done is what I want to do, but I do not see a file or folder anywhere with ANY names that might get me to that code file.
The file to which mc4man is referring is in [the GIMP source code]("http://git.gnome.org/browse/gimp/tree/app/tools/gimptransformtool.c?h=gimp-2-6"). You will have to recompile GIMP from the source code in order to change the HANDLE_SIZE definition.

---

### Post by Moozillaaa on 2010-10-15
I still am not understanding here...

Do I need to download additional GIMP files that I now do NOT have in my computer (or that I DO have in Synaptic?)?

If I now have the files which load the program (and the function as a part of the program) why can't I modify the function? What am I missing here???

:confused:

---

### Post by mc4man on 2010-10-15
While I'm not 100% sure this will end well or even why you wish this... - 
**and am going on that you said you're on karmic**

Do something like this (run each command after the other has finished
```
mkdir gimp_build && cd gimp_build
```
```
apt-get source gimp
```
```
sudo apt-get build-dep gimp
```

Leave terminal open and browse to gimp-2.6.7 folder in home folder -> gimp_build.

Find the file mentioned, (app/tools/gimptransformtool.c ) edit as desired and save.( line 67 - presently 25, 35 - 40 should do

Now go into the gimp-2.6.7/debian folder -> changelog and append +tool1 to latest version (top line), this will keep gimp updating back to repo package(s)
Ex. (from maverick - your version/date will be slightly lower/older, add blue
> gimp (2.6.10-1ubuntu3[COLOR="Blue"]+tool1[/COLOR]) maverick; urgency=low

  [ Sam L. ]
  * Changed the description in debian/control to be less confusing.
    (LP: #599785) 

 -- Robert Ancell <robert.ancell@canonical.com>  Fri, 27 Aug 2010 12:11:20 +1000

Back at terminal cd to the gimp source folder 
```
cd gimp-2.6.7
```
If you get to the gimp-2.6.7 prompt then 
```
dpkg-buildpackage -rfakeroot -D -us -uc
```

About 10 -20 min later if all goes well you should have 6 packages in your gimp_build folder. Only the gimp package is needed but I'd install 3 - screen 1

Make a folder in gimp_build named in and put the 3 packages shown inside (screen 2, yours will be the lower 7 version

Edit: (to avoid confusion, after creating the in folder and placing the 3 packages inside **open a new terminal and run**


```
cd ~/gimp_build/in && sudo dpgk -i *.deb
```

---

### Post by Moozillaaa on 2010-10-15
Thanks - looks like this will get me into the code.

I need a larger rotate reference symbol because as small as it is by default, it serves as nothing more than a 'point', about which rotation occurs.

Making it larger will give not only a reference point, but also reference line**S** - horizontal; for horizon alignment, or vertical, for alignment by structures in an image - lightpost, building, etc.

---

### Post by mc4man on 2010-10-15
> I need a larger rotate reference symbol because...
Then you may wish to experiment with different #'s, 40 may or may not suit.
You'll need to rebuild each time, so other than other than the time it takes to build the source should be pretty straightforward.
(still not sure if this way affects other things negatively - time will tell I'm sure.

---

### Post by saulgoode on 2010-10-15
> **Moozillaaa said:**
> Making it larger will give not only a reference point, but also reference line**S** - horizontal; for horizon alignment, or vertical, for alignment by structures in an image - lightpost, building, etc.

Change the Preview in the Tool Options dialog (double-click on the Rotate Tool's icon in the Toolbox to display this) to be "Image + Grid" or "Grid". This will add horizontal and vertical lines that extend across the entire image (there is a slider provided to adjust the number of lines).

EDIT: Here is a video tutorial demonstrating this: [http://meetthegimp.org/episode-1-preparing-an-image-for-the-web/]("http://meetthegimp.org/episode-1-preparing-an-image-for-the-web/")

---

### Post by Moozillaaa on 2010-10-16
Excellent - thanks. 

Grid function - DUH. And I saw it before, but took no thought...

Hacks ALWAYS have application (pun intended) too!

---


---
title: "I need an editor"
date: 2010-01-02
forum: Programming Talk
---

### Post by xieu90 on 2010-01-02
hi everyone.
I need a good editor for 9.10
which will automatic add code for me like visual studio or eclipse

for example:
if i write <html>
then it will automatic add </html> for me

or when I type static vo then it will show static void and then i will only have to press enter

---

### Post by lorsen on 2010-01-02
Why don't you try eclipse, see e.g. [http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910](http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910) ? ;-)

But there are lots of others, like kdevelop or anjuta.
Maybe you can have a look at this list [http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)
or the discussion here [http://www.cplusplus.com/forum/unices/4781/](http://www.cplusplus.com/forum/unices/4781/) which is more for C, I guess.

Let us know which one you found best for yourself.

---

### Post by xieu90 on 2010-01-02
> **lorsen said:**
> Why don't you try eclipse, see e.g. [http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910](http://www.h3manth.com/content/install-eclipse-galileo-35-ubuntu-karmic-910) ? ;-)

But there are lots of others, like kdevelop or anjuta.
Maybe you can have a look at this list [http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)
or the discussion here [http://www.cplusplus.com/forum/unices/4781/](http://www.cplusplus.com/forum/unices/4781/) which is more for C, I guess.

Let us know which one you found best for yourself.

Hi
I used eclipse in windows, it is great, i love it, and it has a lot of version, for java, java ee, for c and php
in ubuntu i only found its version for java (in synaptic)

now i plan on learning java script, jquery and php mysql
so i will have to write a lot of tag like <html><head></head> open then close open then close ....
that is why i cant use eclipse and forced to find another editor.
i miss this feature: when I type static vo then it will show static void and then i will only have to press enter .
it was in eclipse ^^

anjuta is only for c i guess
kdedev is a bit too big (300 or 400 mb)
eclipse is also big (around 200 in ubuntu) but it is acceptable, since it is great

until now i have installed and tried gedit,bluefish,geany
so far bluefish is the best, but compare to that feature (type something, then choose , press enter and everything goes like in eclipse)  then it is still too bad.

---

### Post by lorsen on 2010-01-02
Hi,

I have not used eclipse so far, but it seems like I should do so ...
However, have you installed the necessary plugins?
I found something here: [http://ubuntuforums.org/showthread.php?t=955733](http://ubuntuforums.org/showthread.php?t=955733)
which is not up to date but suggest to have a look for the right plugin in Eclipse's Update Manager (Help / Software Updates).

Have you tried something like this?

---

### Post by Barriehie on 2010-01-02
Have a look at geany.

---

### Post by xieu90 on 2010-01-02
> **lorsen said:**
> Hi,

I have not used eclipse so far, but it seems like I should do so ...
However, have you installed the necessary plugins?
I found something here: [http://ubuntuforums.org/showthread.php?t=955733](http://ubuntuforums.org/showthread.php?t=955733)
which is not up to date but suggest to have a look for the right plugin in Eclipse's Update Manager (Help / Software Updates).

Have you tried something like this?

I installed eclipse throught synaptic
then go to help/install new software or program in eclipse and add this link
[http://download.eclipse.org/webtools/updates/](http://download.eclipse.org/webtools/updates/)
but couldnt install anything from there.
i tried to install jigloo and it worked.
so i wonder what the problem could be, may be that link only works for eclipse from win ?
or that link is broken somewhere inside ?

---

### Post by xieu90 on 2010-01-02
> **Barriehie said:**
> Have a look at geany.

i tried it but i think i dont know how to use it.

---

### Post by phrostbyte on 2010-01-02
Another option is [bluefish]("apt:bluefish"), for HTML.

---

### Post by act28 on 2010-01-02
I use eclipse for all major project work. But I also use UltraEdit for Linux (uex) which is a commercial product. Mostly for smallish websites.

---

### Post by not_a_phd on 2010-01-02
If you are happy with it, I would recommend that you install Eclipse directly off of the eclipse.org site. I am sure that you can get at the ide options that you need. Eclipse in the repositories is typically too dated to use effectively anyway.

---

### Post by matthew.ball on 2010-01-03
Unlikely you'll be interested, but emacs does include code completion and is also fairly lightweight (though I'm sure compared to vim - which may or may not include code completion - it's behemoth).

---

### Post by xieu90 on 2010-01-03
> **not_a_phd said:**
> If you are happy with it, I would recommend that you install Eclipse directly off of the eclipse.org site. I am sure that you can get at the ide options that you need. Eclipse in the repositories is typically too dated to use effectively anyway.

I downloaded the classic version(linux 32 bit) from eclipse
then unrar or untarz it
i havent checked it yet, at least it works but i cant update software when i copy links like [http://cloudgarden1.com/update-site](http://cloudgarden1.com/update-site) or the wtp one then i cant see any box to check.
the one in repo at least show those box.
could it be that i made any mistake?

now it shows the little boxes to check (after i maximum the window)
i checked jigloo and pressed next (at least 3 times, but it does nothing )
what should I do ?
and the cancel one have to be pressed 2 times then it will exit.
????

---

### Post by Bobulous on 2010-01-03
For hand coding XHTML I use xmlcopyeditor, as it can validate XHTML against the correct schema and tell me when I've failed to use a valid element or forgotten to close an element, etc.

It's probably handy for HTML 4 too, though you wouldn't be able to use the validate tool.

Eclipse is superb for project work, but I find it too heavy handed for individual file editing. If you do want to use Eclipse, there is a web tools package that may be of use when working with HTML. I've only got experience with the web tools package through installing the PHP package for Eclipse, so I'm not sure what the web package offers on its own.

[http://eclipse.org/webtools/](http://eclipse.org/webtools/)

---

### Post by lorsen on 2010-01-03
I'm sorry that I can not really contribute,
but maybe you should think about starting a new thread
with the topic how to install extensions to eclipse.
I'm pretty sure there are some people around knowing this,
but probably they don't look in this thread.

---

### Post by xieu90 on 2010-01-04
> **lorsen said:**
> I'm sorry that I can not really contribute,
but maybe you should think about starting a new thread
with the topic how to install extensions to eclipse.
I'm pretty sure there are some people around knowing this,
but probably they don't look in this thread.

thank you very much for you effort
I really appreciate it ^^
einen guten Rutsch ins neue Jahr 
:lolflag:

---

### Post by lorsen on 2010-01-04
Danke, ich wünsche Dir auch alles Gute im neuen Jahr! 
Besonders ein funktionierendes Eclipse ;-)

---

### Post by caelestis2 on 2010-01-04
My god, the answer is:

[Aptana]("http://www.aptana.org/studio")

It is built on eclipse and can be installed as a plugin to eclipse or separately. To install it to eclipse see [http://www.aptana.org/studio/plugin]("http://www.aptana.org/studio/plugin")

I've used it to build a website and it works great. Has built in php server so you can preview work, works great with ajax frameworks, and I like the code completion and integration into eclipse.

Wait.. you are talking about web development right? You used html as an example, thats when you would want aptana, but you can install eclipse on linux for java. Just download and extract it somewhere and make a shortcut.

---

### Post by xieu90 on 2010-01-04
> **caelestis2 said:**
> My god, the answer is:

[Aptana]("http://www.aptana.org/studio")

It is built on eclipse and can be installed as a plugin to eclipse or separately. To install it to eclipse see [http://www.aptana.org/studio/plugin]("http://www.aptana.org/studio/plugin")

I've used it to build a website and it works great. Has built in php server so you can preview work, works great with ajax frameworks, and I like the code completion and integration into eclipse.

Wait.. you are talking about web development right? You used html as an example, thats when you would want aptana, but you can install eclipse on linux for java. Just download and extract it somewhere and make a shortcut.


it works just like eclipse, wonderful
thanks a bunch
i have found a great sword, now i just have to train myself enough
to be able to wield it
time to fight !!!!:lolflag:

---

### Post by Crafty Kisses on 2010-01-08
So I haven't read the whole thread but it seems like you're having troubles installing Eclipse? Am I correct? You can try one of two things. Option A would be to install Eclipse from Synaptic by running:
```
sudo apt-get install eclipse
```
Option B would be compiling Eclipse from source, which is fairly simple, you need the following package:
```
sudo apt-get install build-essential
```

---


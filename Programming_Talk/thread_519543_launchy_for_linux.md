---
title: "launchy for linux"
date: 2007-08-07
forum: Programming Talk
---

### Post by MrGreen on 2007-08-07
Hi,

I have been trying out Katapult and Deskbar applet but they do not match up to the look and feel of Launchy [Dash!]

Wondered how difficult it would be to write my own?

Do it in Python, Mono I am not much of a hacker so I could do with some help

If anyone is interested then please then let me know

MrG

---

### Post by Njall on 2007-08-13
I know very little about Python.  However I am relatively fluent in C and Perl and I am a programmer.  Alas not on Linux based systems.  All that said, I'd like to either help make Katapult much more like Launchy or write something else similar to Launchy.

---

### Post by chrisj1 on 2007-08-18
Hi, been thinking a similar thing myself... used to use deskbar, but have switched to an xfce based distro (Vector), and I can't find xfapplet in any of the repo's so can't run deskbar. I'm not quite linux literate enough to sort it out! So, I've started using the alt+f2 run dialog to launch apps, and then set about figuring out how to open files this way, so far I've just used an alias s="find * | grep ", so that to find a file, just hit  's [search term]' and it finds all your related files, in any directory underneath home (I'm experimenting with using tag-like filenames). I'm hoping to turn 's' into a script, which accepts a few search terms, so that you don't have to | grep between each one, and then gives your results in Thunar or whatever file manager you use. It's embarassingly basic I know, but I like the idea that this uses what's already there, and a few scripts to extend the functionality of the run dialog could then be useful to everyone,  (like 'google [search term]' opening a browser with your results etc.) as I think a lot of distros have the run dialog option.

Is this just a 'noob' idea, have I overlooked something obvious, or is there some distance in it??

---

### Post by MrGreen on 2007-08-18
Take a look at gmrun config file ... maybe some help [.gmrun]

Not sure about your own scripts [its a path thing!] I have alias for apt-get but there not picked up in gmrun 

Not much help to you but see how you get on

MrG

---

### Post by Nekiruhs on 2007-08-18
Great idea, am working on it now, no guarantees though, so don't hold your breath.

---

### Post by Max Luebbe on 2007-08-18
I'm presuming youre running Gnome, since you dont want to use Katapult.

Have you looked into [Gnome Launchbox]("http://developer.imendio.com/projects/gnome-launch-box")?

I've been thinking about building a Ubuntu package of this for a while, as well as extending it.

If this scratches the application itch you're experiencing - let me know and we can coordinate our efforts.

---

### Post by Nekiruhs on 2007-08-19
First update!
The GUI is in the final stages! I designed it all on Glade-3. The window has no decoration, so it floats in the middle of your screen, just like launchy. I've decided to use find as my backend, so it will support regex searches. This is shaping up to be a good project. Check out the screenshots!

---

### Post by MrGreen on 2007-08-19
Sweeet..... will it have a config file, when can we test it ;-)

---

### Post by Nekiruhs on 2007-08-19
> **MrGreen said:**
> Sweeet..... will it have a config file, when can we test it ;-)
Yes it will have a config file, in ~/.omnibar, I'll release it for testing when I get atleast 3/8 of the features implemented. That could be a few weeks.

---

### Post by Nekiruhs on 2007-08-19
New update! The normal search function now works. Next up to implement is the Regex search, the Executable search, and the Internet search.

---

### Post by Note360 on 2007-08-19
the s script sounds cool. Basically what you could do is make a temp hidden directory filled wiht aliases of the items that where found. From tehir you could launch thunar into the directory.

---

### Post by Nekiruhs on 2007-08-19
Uploaded Version 0.0.1:

Bugs:
Internet search can only handle one word
Executing search doesn't work for now.

If you want to see what it will be like when finished, open glade and make notebook1 visible.

---

### Post by MrGreen on 2007-08-20
We have seen the packaging now we want to feel the goods. ;-) 

If you need any help let us know

MrG

---

### Post by chrisj1 on 2007-09-15
@note360 - thanks! I was wandering how to approach that next step.. I actually haven't started working on this yet, but feel quite encouraged by your comment thanks.

---

### Post by HarvesterOfBeer on 2007-10-24
> **Nekiruhs said:**
> Uploaded Version 0.0.1:

Bugs:
Internet search can only handle one word
Executing search doesn't work for now.

If you want to see what it will be like when finished, open glade and make notebook1 visible.

Any progress updates for the last couple of months? Thanks.

-HoB

---

### Post by sk8dork on 2007-12-20
i found this thread while searching google for "launchy for linux", which was prompted by my installing the latest version of launchy for windows (2.0, it's nice). 

i got excited by this thread as it was something new. i too don't really care for the deskbar or gnome launch box or katapult. i hope there are more advancements like this for keystroke launchers. 

however, another search result i found was [GNOME Do]("http://do.davebsd.com/"), which looks very promising. i'm going to be installing it as soon as i get back into ubuntu (had to boot into windows since gutsy is being stupid... going to have to go back to feisty).

here's to the progress and success of both, and more, keystroke launching apps =)

---

### Post by crazybilly on 2007-12-20
fwiw, the new version of Launch (2.0) is written in QT, which means it's cross-platform.  They're working right now on getting a new Linux version working.  

As fast as the development process moved for the new version, I'd guess the new Linux version should be out soon and very soon.

---

### Post by sk8dork on 2007-12-20
> **crazybilly said:**
> fwiw, the new version of Launch (2.0) is written in QT, which means it's cross-platform.  They're working right now on getting a new Linux version working.  

As fast as the development process moved for the new version, I'd guess the new Linux version should be out soon and very soon.

oh god i can only hope

having used gnome do a bit today, it definitely works and it's pretty quick and responsive, but it's clearly still in early stages.

---

### Post by Nekiruhs on 2007-12-20
> **HarvesterOfBeer said:**
> Any progress updates for the last couple of months? Thanks.

-HoB
Not really, I stopped working on it after I tried to get a PPA from Launchpad and couldn't figure out how to upload it. Something about signing the source and letting launchpad build it tripped me up. Its in Python so I'm not sure what it means by build. I couldn't figure out how to use BZR either.

---

### Post by twright on 2007-12-22
i have also failed to work out how to use the ppa but i have used bzr in the past

i know quite a bit of C++ and java (i have been meaning to learn python) so if i can be of any help i will try :)

---

### Post by actionscripted on 2008-07-28
For those of you interested in an official Launchy for Linux...it's here!

Download it here:
[http://sourceforge.net/project/showfiles.php?group_id=132975](http://sourceforge.net/project/showfiles.php?group_id=132975)

Read about it here:
[http://www.launchy.net/](http://www.launchy.net/)

---

### Post by mtelesha on 2008-07-29
As of July 28 Launchy is now for Linux. Just installed it with Hardy and it works exactly like it does in Windows.

---

### Post by mssever on 2008-07-29
I've been using (and loving) GNOME Do for a while now. How does Launchy compare with Do?

---

### Post by onero on 2008-07-29
> **mssever said:**
> I've been using (and loving) GNOME Do for a while now. How does Launchy compare with Do?

It really depends on what you use it for. I've become used to and prefer GNOME Do on my Ubuntu box, but in my Windows work computer I use Launchy because I don't really have a choice :) 

Do will be releasing 0.6 soon (I'm running 0.5.97 from the PPA, which is the beta for 0.6), and it fixed most of the little annoyances I had in Do. Also, Do has more plugins which don't have equivalents in Launchy, at least for its current Linux version (such as the Tomboy, Session Management, Disk Mounter, etc.).

If you don't use Do's plugins though, Launchy's great; it looks nice and is very functional. To my surprise, even though it's a QT app, it uses significantly less memory than Do (but that's probably because of the number of plugins I have enabled in Do). Right now Launchy is only taking up 8 MB of Memory and 66 MB of Virtual Memory, while Do is taking up 30.9 MB of Memory and 88.8 MB of Virtual Memory. Performance-wise, though, they seem the same, and if you have a decent amount of RAM it shouldn't really matter.

I *might* switch to Launchy just to be consistent with my Windows usage, but right now there are little things I use on Do that aren't Launchy; as an example, when searching for a Folder and pressing the right arrow button, it navigates into that folder and then you can search again. It's really useful. Even so, either one is a good choice.

---

### Post by mssever on 2008-07-29
> **onero said:**
> If you don't use Do's plugins though, Launchy's great; it looks nice and is very functional. To my surprise, even though it's a QT app, it uses significantly less memory than Do.Well, I'd assume that Do would take up more memory since it's written in C# on Mono, which implies a certain overhead. Since I use a number of Do's plugins, it seems that I should just stick with it.

---


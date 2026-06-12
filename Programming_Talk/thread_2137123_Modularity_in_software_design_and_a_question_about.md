---
title: "Modularity in software design and a question about extant applications."
date: 2013-04-19
forum: Programming Talk
---

### Post by YQ002lc2 on 2013-04-19
I am a CLI fan.
This is probably because I am a hard working poor man with a wheezing 9 year old dinosaur computer. 
I prefer the efficiency and speed the command line affords. 



I wish more applications were written in the following modular way:

App Name:
1. -Core (the core input and output)
2. -Interfaces  -GUI
                     -Text based terminal interface
                     -CLI
3. -User   -Settings
             -Data


Let's suppose 'banshee' was written in this way.

mycomputer$:

mycomputer$: banshee-CLI --search:'bocelli'+'o sole mio'
   (launches banshee-core and banshee-CLI and searches within the user files)

The output displays:
1. o sole mio  andrea bocelli  album name
2. o sole mio  andre bocelli   album 2 name

mycomputer::banshee-cli$: play 2 --volume-normalizer'30-40'
(plays the second search result while keeping the volume within 30-40 decibles) 

mycomputer--banshee-cli$:exit-cli
(kills banshee-cli while banshee-core still runs playing the music. The terminal returns to the main comand prompt)

mycomputer$:

Sometime later, we decide we want to interface with banshee graphically while the music is still playing. 

mycomputer$:banshee-gui-gtk
Please choose your display manager?  (lightdm,unity...):lightdm
password:*****

The graphical interface starts and we interact graphically for a bit.

CTRL+ALT+F1 
(we are directed back to the main terminal and the banshee-gui-gtk suspends opperation momentarily since it is a separate process not integral to the core operation.)

mycomputer$:
mycomputer$: pkill banshee-gui
(kills any graphical interface computations while the core still runs)
mycomputer$: pkill lightdm
(kills lightdm)
(banshee-core continues to run)
mycomputer$: pkill banshee-core
(kills banshee-core)

Presently, the banshee application and many others do not operate independently of their graphical homes. 
It would be nice if more applications were written in this modular way. 

Does anyone know of any extant software designs like this for banshee or any software? 

Thank you and sorry if I've chosen the wrong spot to post.

---

### Post by mörgæs on 2013-04-19
> **jpinson said:**
> 
Thank you and sorry if I've chosen the wrong spot to post.

I guess Programming Talk is better, so moved. Let's see if you get a response here.

---

### Post by trent.josephsen on 2013-04-19
Depending on what you use banshee for, mpd (Music Player Daemon) might be very similar. I've never used either one so I'm basing this on your description. [ArchWiki link.](https://wiki.archlinux.org/index.php/Music_Player_Daemon)

Come to think of it, this is the kind of thing Arch users just love. wicd works essentially the same way. pidgin/finch comes to mind, although I don't know that those actually share a daemon; maybe they just use the same library. Vim can do the same thing (and, unsurprisingly, so can Emacs).

These are just a few off the top of my head; I can't think of any browsers that do it, but a wide variety of other applications have been made to operate on the client-server model.

---

### Post by r-senior on 2013-04-20
The [GNU Coding Standards]("https://www.gnu.org/prep/standards/standards.html#Graphical-Interfaces") recommend a design approach similar to that you describe:> In addition [to a GUI], please provide a command-line interface to control the functionality. (In many cases, the graphical user interface can be a separate program which invokes the command-line program.) This is so that the same jobs can be done from scripts.

Unfortunately, that paragraph is the extent of this recommendation and it gets a bit lost in the rest.

Open source being open source, there is no forced compliance of any coding standard. My view is that the GNU standards are biased toward what I assume are Richard Stallman's own preferences (C, Emacs). These are not to every programmer's taste or requirements. Anyone writing Python or C++, for example, is told that they are non-standard, so why bother reading further?> Using another language [other than C] is like using a non-standard feature: it will cause trouble for users.
 
Even C programmers disagree with them: In the Linux Coding Style, Linus Torvalds writes:> First off, I'd suggest printing out a copy of the GNU coding standards, and NOT read it. Burn them, it's a great symbolic gesture.

So perhaps it's not surprising that this recommendation for CLI/GUI duality is sparsely implemented, which is a pity, because it's a good design pattern in itself. Your description is essentially a model-view-controller (MVC) pattern:> 1. -Core (the core input and output) [CONTROLLER]
2. -Interfaces -GUI -Text based terminal interface -CLI [VIEW]
3. -User -Settings -Data [MODEL]

It's not just about following standards of course: There's nothing to stop a programmer designing an application using this pattern and *not* following the GNU Coding Standards, but that relies on the individual's own perspective on the importance of providing a unified CLI and GUI.

---


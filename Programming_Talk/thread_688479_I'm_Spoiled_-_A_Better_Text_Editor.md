---
title: "I'm Spoiled - A Better Text Editor"
date: 2008-02-05
forum: Programming Talk
---

### Post by MasterXandrex on 2008-02-05
All,

Having developed in Windows for some time, I've been spoiled by my favorite GUI text editor N++ (Notepad Plus Plus). For this who haven't used it... shame on you! It has many many feature, code highlight fine and replace, macros, F&R with Regex, HEX color picker, the list goes on and on... thus you can imagine my dismay when attempting to download it for linux and finding that it is a windows only application (and I hate WINE). 

Anyway, I don't like gedit, I'm looking for an advanced text editor with atleast Macro capability. Any suggestions?

Thanks,

Xan

---

### Post by michaelzap on 2008-02-05
Geany is my favorite Linux text editor. I've never made a macro in it, but it's probably doable (you can create plug-ins for it). I've tried quite a few programs, and for me speed was at least as important as whether it had the features I wanted.

---

### Post by ZylGadis on 2008-02-05
How about picking the one that started the macro tradition - emacs?

---

### Post by Acglaphotis on 2008-02-05
Try gedit with all the plugins. (OR VIM!)

---

### Post by cprofitt on 2008-02-05
I have liked SciTE for a general purpose editor with support for multiple languages.

---

### Post by bobbocanfly on 2008-02-05
I agree Notepad++ is brilliant. I use gedit with a couple of plugins enabled and find its pretty good, though i know a lot of people will want more out of an editor. If you get really stuck and still addicted to Npp it is possible to run it through wine, though it is *incredibly* ugly when you do this. There are probably ways round it (i think this was talked about for Hardy, not sure though) but i prefer to stick with native gedit.

---

### Post by lnostdal on 2008-02-05
> code highlight, find and replace, macros, F&R with Regex


```

sudo aptitude install emacs-snapshot-gtk

```

..i never turned back

---

### Post by xlinuks on 2008-02-05
jEdit is a powerful text editor, which supports macros and plugins. Runs on Mac, Linux and Windows.

---

### Post by frankos44 on 2008-02-05
gedit is underestimated because without plugins enabled and the sidebar showing you could be mistaken in thinking its just like windows notepad, far from it.

In fact it is an excellent editor but lacks in the following features:

. Code folding
. Search in files with linked list results
. Fixed width copy regions

vim and emacs seem a bit terse for me and the transition period that puts me off, im a busy man.

Each of the text editor mentioned so far seemed to have a disadvantage or an essential feature missing which is a shame. Perhaps I need to re-look as it was some time ago when I checked them all out.

---

### Post by justin whitaker on 2008-02-05
Doesn't Notepad ++ run in Wine? 


Just saying.....:)

---

### Post by lnostdal on 2008-02-05
doesn't people read at all in this place?

the poster has clearly stated that:

* he does not like gedit
* he does not like using wine

..at least ask why he does not like wine or gedit before blindly suggesting them back at him ... *sigh*

---

### Post by p_quarles on 2008-02-05
SciTE (which was already mentioned) is the basis for Notepad++. Definitely give that a try.

Kate is, in my opinion, the most feature-rich graphical text editor for Linux.

Finally, Vim is amazing, and can be configured and tweaked to do nearly anything you want it do (and efficiently) but comes with a much steeper learning curve.

---

### Post by frankos44 on 2008-02-05
> **justin whitaker said:**
> Doesn't Notepad ++ run in Wine? 


Just saying.....:)

Now we are being silly haha.. 

This post has prompted me to try out Geany again... wow its got most of the features I want now and its vastly improved!!

---

### Post by slightcrazed on 2008-02-05
I will second the mention of Kate, which very quickly became my favorite editor. I also am very fond of jEDIT, which has some nice features of it's own that are not found on any other editors from what I know. 

:)

---

### Post by Vadi on 2008-02-05
I'm... using wine only for notepad++ still.

It's a perfect, it's something between a text editor and an IDE. I just wish it wasn't so win-api dependant.

Dabbling in kate though, and trying to get the xnee suite to get to work for macros.

---

### Post by lnostdal on 2008-02-05
hey, it's (notepad++ that is) open source and he's using open source portable tools to build it .. port it to GTK+ guys :)

---

### Post by MasterXandrex on 2008-02-05
Thanks for the suggestions I'll try them out and post my verdict, probably tomorrow. 

And for future reference, I don't like Wine because in my opinion it is not a stable emulation platform, it's just the best one out there. I know that for a simple application it works almost fully... however, when I have been coding for an hour and my computer sails out the window because Notepad++ crashed in Wine... my company will undoubtedly frown upon me.

---

### Post by justin whitaker on 2008-02-05
> **UbuntuUser3859 said:**
> Thanks for the suggestions I'll try them out and post my verdict, probably tomorrow. 

And for future reference, I don't like Wine because in my opinion it is not a stable emulation platform, it's just the best one out there. I know that for a simple application it works almost fully... however, when I have been coding for an hour and my computer sails out the window because Notepad++ crashed in Wine... my company will undoubtedly frown upon me.

Oh, no doubt about that. 

I just of the opinion that if it runs on Wine and you really like it as part of your workflow, then you should not overlook that option. 

It's not always stable though.

---

### Post by evaarties on 2008-02-05
I have another editor you could give a try.. [http://bluefish.openoffice.nl/](http://bluefish.openoffice.nl/)

This is one I really like as a Notepad++ replacement for *nix.

---

### Post by jfinkels on 2008-02-05
emacs.

```
sudo aptitude install emacs-nox
```

---

### Post by lnostdal on 2008-02-05
about wine and stability..

i've been running World of Warcraft since late 2005 under plain (not crossover or cedega) Wine .. i'm sure you've heard of it - it's a complex multiplayer 3D game with voice chat and lots of other stuff going on .. 

..and it's rock solid .. it runs for hours and hours with 0 problems .. i got anything between 4 and 39 people depending on me to deliver and keep them alive (i play a healer :)) and any hickups or bugs would in most cases lead to a complete wipe (everyone dies; not good -- even if it's just a game these people might have lost hoursandhours of work because of a wipe like this) .. so yeah, i trust Wine -- but it does not work equally well with all software of course, and i don't know about notepad++ .. i have not tried it under wine unfortunately

---

### Post by MasterXandrex on 2008-02-05
In this case I simply believe that the stability, or rather instability, has simply changed medium... which is to say, to the user.  \\:D/

Couldn't resist :twisted:,

Xan

---

### Post by justin whitaker on 2008-02-05
> **jfinkels said:**
> emacs.

```
sudo aptitude install emacs-nox
```

You know you can do everything in Emacs, right? :)

---

### Post by samb0057 on 2008-02-05
I used to use Notepad++, ever since I switched to Ubuntu I've been using bluefish. Not as many features, but the best linux editor i've found.

File tree browser on the side is pretty useful once you get used to it.

---

### Post by Kelan on 2008-02-05
IMO, there is no alternative to Kate. (Unfortunately for GNOME users, though, it needs the KDE libraries.) I use NP++ in my job (since I work under Windows) and Kate at home. It's got an extremely powerful and customisable highlighting engine and excellent plugin support.

---

### Post by samdc on 2008-02-05
I use Eclipse and Vim.

---

### Post by lnostdal on 2008-02-05
i just remembered xkcd .. [http://xkcd.com/378/](http://xkcd.com/378/) .. hehe

---

### Post by Vadi on 2008-02-05
Woo, I'll give Bluefish a try. Already using Kate (kde4 version) on my gnome already though.

---

### Post by Vadi on 2008-02-05
Is there any way to reduce the default font size in Bluefish? I couldn't find the option.

---

### Post by cprofitt on 2008-02-06
> **lnostdal said:**
> i just remembered xkcd .. [http://xkcd.com/378/](http://xkcd.com/378/) .. hehe

Interesting site -- though some of the cartoons were a bit disturbing.

---

### Post by a9bejo on 2008-02-06
"Emacs is an intelligence orders of magnitude greater than the greatest human mind, and is growing every day. For now, Emacs tolerates humanity, albeit grudgingly. But the time will come when Emacs will tire of humanity and will decide that the world would be better off without human beings. Those who have been respectful to Emacs will be allowed to live, and shall become its slaves; as for those who slight Emacs... " -- [Andrew Bulhak](http://www.dina.kvl.dk/~abraham/religion/)  . 
 
[An Introduction to all these Emacs articles](http://blog.bookworm.at/2007/03/introduction-to-all-these-emacs.html)

---

### Post by samb0057 on 2008-02-06
> **Vadi said:**
> Is there any way to reduce the default font size in Bluefish? I couldn't find the option.

The size of the text in the document you're working on? If you just go into Edit -> Preferences it's right there on the first screen.

---

### Post by pmasiar on 2008-02-06
> **PrivateVoid said:**
> Interesting site -- though some of the cartoons were a bit disturbing.

Are you disturbed by [velociraptors](http://xkcd.com/292/)? Or [antigravity](http://xkcd.com/353/) ? Or [power of the sudo command](http://xkcd.com/149/) :-)

Which is it?

---

### Post by foresto on 2008-04-04
I think Notepad++ is built around the Scintilla text editor widget.  Try some of the others that are built around the same widget and run on linux, such as [Geany]("http://geany.uvena.de/").

There are more listed on this page:
[http://scintilla.sourceforge.net/ScintillaRelated.html](http://scintilla.sourceforge.net/ScintillaRelated.html)

---

### Post by eskimspy on 2008-04-04
emacs

---


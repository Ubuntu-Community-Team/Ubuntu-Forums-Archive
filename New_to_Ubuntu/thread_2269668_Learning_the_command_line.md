---
title: "Learning the command line"
date: 2015-03-17
forum: New to Ubuntu
---

### Post by kharrisma-j on 2015-03-17
Hey Everyone,

Can anybody recommend a really good, thick book that delves really deeply into  command line stuff, and working with user and system files and such?  I'm getting tired of being stuck with the GUI and want to get my knuckles dirty fixing things at the command line and using the text editor on the relevant files.  Like now; I managed to get rid of unity (14.04 LTS) by installing Gnome, but it comes with a window manager built in, and I want to use Compiz.  I installed Compiz, but it won't load/run.  I'm sure that some user config files being tweaked would solve the problem, if only I know a) which ones, and b) how to do it.  I'm not really asking for a how-to specifically here; I'm looking for a book that would tell me how to do such things in general, if anybody knows of one.

Thanks in advance for any ideas!

Karl

---

### Post by nerdtron on 2015-03-17
As I always recommend, an easy to read book and easy to follow about familiarizing the command line. Most lessons are generally applicable to most Linux distros.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Download the free PDF version and have fun learning!

---

### Post by buzzingrobot on 2015-03-17
"Learning the BASH Shell", 3rd edition, Cameron Newman

"Bash", 2nd edition, Karsten Guenther

"The Linux Command Line", William E. Shotts, Jr.

The first two are published by O'Reilly, the third is from No Starch Press.

Should be available on Amazon and the other ususal suspects.

That, though, won't help you use Compiz with Gnome.  Compiz is a compositing window manager. Unity is implemented as a Compiz plugin. Gnome is very tightly integrated with Mutter, also a compositing window manager. BTW, when Compiz is used with something like Mate, it replaces the standard Mate windows manager, Marco.

---

### Post by Frogs Hair on 2015-03-17
The Gnome shell has it's own window manager and won't work with compiz. Gnome-session-flashback includes a compiz session. What Gnome session are you using ?

---

### Post by kharrisma-j on 2015-03-17
Thanks for the quick replies; guess I'll start with the PDF download, and work up to the bigger books.  Walk, then Run.

---

### Post by kharrisma-j on 2015-03-17
I WAS until recently using 10.10, with the Gnome desktop and Compiz window manager, wobbly-windows and all.  Ran great.  It finally just got too unstable, and repositories moved and stuff, so I couldn't even upgrade, so I went clean install with 14.04.  I'm not sure how to tell which session of Gnome I'm running (great with the GUI... duhhhh with the command line....)

---

### Post by Habitual on 2015-03-17
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by nerdtron on 2015-03-17
I think you can still get those effects on Kubuntu 14.04 with the desktop effects enabled. Might be worth a try.

---

### Post by QIII on 2015-03-17
All the eye-candy is available in Kubuntu -- which uses kwin instead of compiz.

But that doesn't solve the user's present problem with the current DE.

@kharrisma-j:  while it is well and good to learn things on your own, asking for help is often less painful than bashing your head against a wall trying to learn something inscrutable in a vacuum.  Please feel welcome to ask specific questions!  :)

---

### Post by Tadaen_Sylvermane on 2015-03-17
A suggestion to, while not being a source such as a book. Get yourself virtual box and go crazy with it. Is how I learned almost everything I know now about linux. That way you don't have to risk your daily driver at all while testing things out. Virtualize everything while you are learning. Then once you are comfortable with it go bare metal.

---

### Post by King of Heart 4711 on 2015-03-17
The Linux Documentation Project TLDP.org is a fantastic place to start. Is where I learned a good deal of my knowledge.
I also keep a (unofficial) mirror here: [https://apps.skynet-hosting.com/LDP](https://apps.skynet-hosting.com/LDP) - warning: it's a self signed cert...

Also just using Linux on a day to day basis is a MAJOR help. Unless you are good at reading a book AND memorizing everything in the book, there is nothing like just using the CLI (even on limited knowledge) and learning / googling / visiting the forums / etc. as you go and as needed.

---

### Post by DarkSapphire on 2015-03-17
Most of the recommended sources will probably tell you this, but always be careful when using the sudo command.  I have made the mistake of not being very careful with it.

---

### Post by King of Heart 4711 on 2015-03-17
Speaking of 'sudo'.... NEVER run 'sudo rm -rf /' it looks like such a sweet and innocent command.... yet so destructive.... always be sure you fully understand the command you type in the terminal. If you don't it can and probably will have unintended consequences!!!

---


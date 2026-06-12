---
title: "[SOLVED] [Gutsy] Ugly Lazarus interface"
date: 2008-03-04
forum: Programming Talk
---

### Post by microfi on 2008-03-04
Hi folks!
I've been coming from Delphi, and I saw in Lazarus a nice alternative for Linux development. The thing it is: while I can make "beautiful" apps using MonoDevelop or Eclipse (by "beautiful" I mean using my GTK2 theme "Clearlooks"), the user interface in Lazarus (and the apps I develop) is in an old GNOME interface (I think it's called Motif). I've seen in the screenshots from Lazarus website ([http://wiki.lazarus.freepascal.org/Image:Lazarus_IDE_GTK2.png]("http://wiki.lazarus.freepascal.org/Image:Lazarus_IDE_GTK2.png")) it working beautifully on Ubuntu's main theme.
Is there anything I can do to make my Lazarus look like that?
Thanks, Filipe.

---

### Post by bruce89 on 2008-03-04
To be precise, Lazarus uses GTK+ 1.0, which is a relic of the 20th century. I'm sure they'll transition to 2.0 when they feel that their support for it is good enough.

See [http://wiki.lazarus.freepascal.org/Installing_Lazarus](http://wiki.lazarus.freepascal.org/Installing_Lazarus) anyway, but there is a warning:
> 
WARNING : The GTK2 (sic) interface is not yet complete and is only for testing purposes. 

---

### Post by microfi on 2008-03-04
Thanks dude!
I'm sorry I didn't see this site before (Google hasn't been my friend)...
But what about that screenshot that is annoying me, saying that there is a solution??
I'll try to follow the instructions there and I'll post any solutions I find. Others' solutions are welcome, too!
Thanks, Filipe

---

### Post by bruce89 on 2008-03-04
> **microfi said:**
> I'll try to follow the instructions there and I'll post any solutions I find.

Looking at that page, have fun!

---

### Post by microfi on 2008-03-04
Got it working!!!
I've found [HOWTO - compile Lazarus with GTK2]("http://forum.paldo.org/index.php?action=topic&topicnr=157&hilikeywords=a:0:%7B%7D"), which is very good, but a little incomplete (for begginers); so that's what I did:
01. In terminal, type:
> sudo startlazarus
That's really important that you launch Lazarus with "sudo", otherwise it will look like it is building but the IDE will be unable to access the "/usr/" directory
02. Tools > Configure Build Lazarus > Advanced Build Options
03. Put "Build*" for everything in the list, but "Clean+Build" for LCL
04. In "LCL interface", choose "gtk 2"
05. Ensure that the option "Restart after successful build" is checked
06. Click "Build"
07. Wait until the packages are built
08. Your IDE will be restarted

And voilla! You get a pretty shinin' Lazarus IDE!
Though, it's necessary to mention that it is not considered "stable" by some developers, and others say that some components have disappeared from the palette.
Well, that's it, I hope it solves for you too!

Thanks, Filipe.

* I don't know if it's really necessary to build everything, 'cause the text says to put "None" for the items. I put build and it worked for me. If it works with "None", you'll have saved a lot of time in building a lot of packages.
* Please edit this post for better understanding 'cause my English is "brazilian".

---

### Post by MasterProg on 2008-07-08
On Ubuntu 8.04 I had to install *fpc*, *fpc-source* and *fpc-utils* packages (probably not all of them are needed, I just installed all of them) in order to recompile Lazarus.

It seems like a little problem with Lazarus package in Ubuntu repositories.

---


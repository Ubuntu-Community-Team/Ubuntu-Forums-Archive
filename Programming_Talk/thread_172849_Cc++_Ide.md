---
title: "C/c++ Ide"
date: 2006-05-09
forum: Programming Talk
---

### Post by bhubanmm on 2006-05-09
Hi,

Can anyone suggest me a good IDE for C/C++ **COMMERCIAL** Development on *NUX.

Thanks in advance...

---

### Post by scooper on 2006-05-09
[QUOTE=bhubanmm]Can anyone suggest me a good IDE for C/C++ **COMMERCIAL** Development on *NUX.[/QUOTE]

Eclipse has the CDT C++ environment available for its excellent IDE.  Check out [http://www.eclipse.org/](http://www.eclipse.org/).

Of course there are ways to build up emacs and vim into awesome development environments.  I've used commercial IDEs for many years, including VisualStudio, Eclipse and IntelliJ.  I've found they have both advantages and trade-offs/sacrifices.  I wouldn't rule out the less bloated options if you don't mind more of a learning curve.  You can ultimately end up being more efficient.  Just a thought.

Good luck.  BTW - If you mention what you're looking for in an IDE there may be more focused responses.

Cheers,
Steve

---

### Post by ComplexNumber on 2006-05-09
try borland's kylix...(although its can be a bit buggy)

---

### Post by pedwards on 2006-05-09
you should be ashamed to suggest the c pluggin for eclipse, ive never known someone to acually get it running correctly, not even my computer science professors can.

---

### Post by cstudent on 2006-05-09
[QUOTE=pedwards]you should be ashamed to suggest the c pluggin for eclipse, ive never known someone to acually get it running correctly, not even my computer science professors can.[/QUOTE]


I've used Eclipse with the CDT plugin on several machines, Linux and Windows. Currently I'm using an IDE called [Code::Blocks]("http://www.codeblocks.org/"). I use the SVN .deb from this location: [http://www.savefile.com/projects/547711](http://www.savefile.com/projects/547711)

---

### Post by rplantz on 2006-05-09
[QUOTE=pedwards]..., not even my computer science professors can.[/QUOTE]

As a retired cs professor (taught for 21 years), I can assure you that we professors are not all experts at everything having to do with computers. I always had at least one student who was better at sysadmin stuff that I. (Not a graduate student; we only had an undergrad program.) I often asked a secretary how to do things in our word processor. I know cs professors who really don't even know how to program.

I also worked as a programmer in industry for 8 years before teaching. The two jobs require separate skill sets.

---

### Post by ZylGadis on 2006-05-09
Eclipse's IDE is far from excellent, and its C++ plugin even further. I'd suggest Code::Blocks, or vi/emacs if you are in the mood for learning.

---

### Post by ComplexNumber on 2006-05-09
[quote=ZylGadis]Eclipse's IDE is far from excellent, and its C++ plugin even further. I'd suggest Code::Blocks, or vi/emacs if you are in the mood for learning.[/quote] i agree about eclipse's IDE. personally, i think eclipse is rubbish. its also rather crashy. i wouldn't agree with emacs or vim either because, given the time spent to learn them and the associated key maps, the return isn't very muchcompared with using a lightweight-ish editor  IMO. its a bit like using a sledgehammer to crack a small nut.
may as well just use a lightweight-ish editor such as gedit or kate or bluefish, with glade, galeon, or qdesigner to do the GUI bits.

---

### Post by bhubanmm on 2006-05-10
I want an IDE for GUI development using C/C++. Please suggest.

Thanks

---

### Post by GNUrag on 2006-05-10
[QUOTE=bhubanmm]I want an IDE for GUI development using C/C++. Please suggest.

Thanks[/QUOTE]

As per the above discussion, i'd suggest  **Anjuta** is good enough :mrgreen:

---

### Post by ComplexNumber on 2006-05-10
[quote=GNUrag]As per the above discussion, i'd suggest  **Anjuta** is good enough :mrgreen:[/quote]
....with glade.

---

### Post by treak007 on 2006-05-10
u can always run visual studio in wine ;)

---

### Post by maurito on 2006-05-27
[QUOTE=treak007]u can always run visual studio in wine ;)[/QUOTE]

reallyyy???? :D 
hoooowwwww????

---

### Post by thumper on 2006-05-27
[QUOTE=bhubanmm]I want an IDE for GUI development using C/C++. Please suggest.

Thanks[/QUOTE]
Why an IDE?

I must admit for all the commercial development I do the team uses whatever editor they choose (emacs for me, vim for others, textpad... whatever), and then makefiles (or in unfortunate cases workspace projects).

IDEs often just get in the way of writing code, especially if you don't write code in the same style of the people that created the IDE.

---

### Post by tht00 on 2006-05-28
The programming I've done so far in Linux is with gedit (Ubuntu's default text editor) and gcc/g++ from the command line.

I thought I'd miss using an IDE -- I learned on VB, then used VC++ 6 for some terminal programming back in the day.

Really, after doing some Java programming with just a text editor and command line, I'm enjoying that approach about the best, at least when I'm not GUI programming. ;)

---

### Post by Meghnaad on 2008-05-28
What about  kdevelop !
although i've not used it many people suggest it !

---

### Post by dempl_dempl on 2008-05-28
Kdevelop. I believe it beats the Visual C++ and Borland C++ Builder  altogether . It has built in visual editor too, which is less intuitive than Borland's,  but easier than Microsoft's .
Kdevelop used to eat the dust behind the two mentioned, but not anymore. 

Problem, however lies in the fact that Qt framework ( GUI framework for KDE , which is used in Kdevelop )  is not free for commercial use , i.e it's dual-licenced , with GPL and Qt commercial licence. 

If you want to use Qt for commercial puproses , you'll have to pay  5000-6000 bucks [ outrageous ] .
Although , to be pedantic, GTK+ is licenced under GPL , hence you wouldn't be able to use Glade nor GTK+ at all.  But, if you would like to ignore ( break) the licence ,    TrollTech would actually  hunt you down :)  . 

About the **Code::blocks:**
It was always too bugy on Ubuntu. I always had to restart it every 15 minutes, although , this is only my experience, someone else might had better luck with it :)  . 


So... after some thinking... 
GTK + Glade + Anjuta would be the choice if you want to pass as  cheap as possible .
wxWidgets + wxGlade are good solutions too. 
GTK also has a (far) greater number of 3rd party custom components, widgets  and libraries than Qt and wxWidgets, if you really need some very fancy look.


Qt on the other hand, has a lot better internationalization support [ Qt linguist ] and can integrate in Eclipse and Visual Studio .  And it has a very simple interface for connecting to database servers [ looks a lot like Delphi and BCB ] .
But it still costs 6000$ ! 




Cheers!

---

### Post by radagast1155 on 2008-05-28
> **scooper said:**
> Eclipse has the CDT C++ environment available for its excellent IDE.  Check out [http://www.eclipse.org/](http://www.eclipse.org/).

Of course there are ways to build up emacs and vim into awesome development environments.  I've used commercial IDEs for many years, including VisualStudio, Eclipse and IntelliJ.  I've found they have both advantages and trade-offs/sacrifices.  I wouldn't rule out the less bloated options if you don't mind more of a learning curve.  You can ultimately end up being more efficient.  Just a thought.

Good luck.  BTW - If you mention what you're looking for in an IDE there may be more focused responses.

Cheers,
Steve
Eclipse is the best of what I have seen plus if you choose to learn a different programming language it can do that too!

---

### Post by slavik on 2008-05-28
> **dempl_dempl said:**
> Kdevelop. I believe it beats the Visual C++ and Borland C++ Builder  altogether . It has built in visual editor too, which is less intuitive than Borland's,  but easier than Microsoft's .
Kdevelop used to eat the dust behind the two mentioned, but not anymore. 

Problem, however lies in the fact that Qt framework ( GUI framework for KDE , which is used in Kdevelop )  is not free for commercial use , i.e it's dual-licenced , with GPL and Qt commercial licence. 

If you want to use Qt for commercial puproses , you'll have to pay  5000-6000 bucks [ outrageous ] .
Although , to pedantic, GTK+ is licenced under GPL , hence you wouldn't be able to use Glade nor GTK+ at all.  But,  TrollTech would actually  hunt you down :)  . 

About the **Code::blocks:**
It was always too bugy on Ubuntu. I always had to restart it every 15 minutes, although this is my experience. 


So... after some thinking... 
GTK + Glade + Anjuta would be the choice if you want to pass as  cheap as possible .
wxWidgets + wxGlade are good solutions too. 
GTK also has a (far) greater number of 3rd party custom components, widgets  and libraries than Qt and wxWidgets.

Kdevelop + Qt + 6000$ are the alternative.

Cheers!
Anjuta 2.x should have glade built in, no? (I have never tried it)

---

### Post by dwhitney67 on 2008-05-28
> **dempl_dempl said:**
> If you want to use Qt for commercial puproses , you'll have to pay  5000-6000 bucks [ outrageous ] .
...
I do not believe this to be true.  My previous employer uses Qt (qt-x11-free-3.2.3) and the legal advice they received is that it is ok to develop applications and include the runtime libraries on the product they develop.

Maybe what you are referring to is for new releases of Qt (rel 4)?

---

### Post by LaRoza on 2008-05-28
Who's idea was it to necromance an IDE thread?! Don't we have enough of those?

[img]http://img181.imageshack.us/img181/8060/necromancingsv7.jpg[/img]

---


---
title: "gedit.... windows????? glade ... windows???"
date: 2006-01-08
forum: Programming Talk
---

### Post by rock freak on 2006-01-08
Hi there i was just wondering if any one new a good text editor liek gedit that is compatiable as i cant always get onto a ubuntu or linux machine :(

i like the colour markup it does and the wide languages i program in c and php and do some html etc.. along the way!!

also any one know how to get glade to work in windows i have the win32 installed but it still generates the automake.sh of which i cant find a program to use!!!! tried cygwin but dont think i got all the right packages!!


cheers for any help

Ollie

---

### Post by akshoslaa on 2006-01-08
I use [http://notepad-plus.sourceforge.net/](http://notepad-plus.sourceforge.net/) under windows... I actually prefer it over gedit/kate... *briefly wonders if it'll run under wine*

---

### Post by Hanj on 2006-01-08
Or try [JEdit]("http://www.jedit.org/") or [GVim]("http://www.vim.org/"). Vim takes some time to get used to, but once you do, you'll never want to use any other editor.

---

### Post by rock freak on 2006-01-08
cheers guys just tried them all im loving jedit not sure ont ht vim it could take alot of getting used to and i also cant get it to highlight like jedit and gedit to, cheers for the link to notepad++ but didnt really like it my self!! 

any ideas on the glade at all ???

Cheers

Ollie

---

### Post by rock freak on 2006-01-08
aha dont worry about the glade after enough routing around i have found the autoconf and automake libries for cygwin :D

---

### Post by Adrian on 2006-01-08
[QUOTE=rock freak]Hi there i was just wondering if any one new a good text editor liek gedit that is compatiable as i cant always get onto a ubuntu or linux machine :([/QUOTE]

My favourite Windows editor is [UltraEdit]("http://www.ultraedit.com/index.php?name=Content&pa=showpage&pid=1"). Unfortunately, it's not free but you can download a trial version to check it out.

---

### Post by rock freak on 2006-01-08
well ok it was goin great with glade upuntill the make time the autogen worked no problem but it now runs make and it chucks this out at me

[IMG]http://www.over-the-bars.co.uk/make.jpg[/IMG]

any ideas guys???

---

### Post by serenity on 2006-01-08
i like [Notepad2](http://www.flos-freeware.ch/notepad2.html) as a notepad replacement on windows

---

### Post by Hanj on 2006-01-08
> not sure ont ht vim it could take alot of getting used to and i also cant get it to highlight like jedit and gedit toMake sure you have GVim installed, as regular Vim don't have syntax hightlighting (as far as I know). Sure, the learning curve is pretty steep, but after some training you can edit text *really* fast. Type 'vimtutor' in a bash shell and see for yourself.

---

### Post by jwenting on 2006-01-08
GVim it is for me. Only true cross platform editor (if you include VI and VIM).
Using it in some flavour or another on Windows, Linux, AIX, Solaris, and SCO (and have used in the past on HPUx, BDS, and OS/2).

Handy not to have to relearn a commandset for your editor when switching OSs.

---

### Post by DirtDawg on 2006-01-08
Yikes. Lots of suggestions. 

Scite is my favorite on both Windows and Ubuntu. Plenty of syntax color.

EDIT: Oops, forgot the link: [http://www.scintilla.org/SciTE.html](http://www.scintilla.org/SciTE.html)

---

### Post by majikstreet on 2006-01-08
[QUOTE=Hanj]Make sure you have GVim installed, as regular Vim don't have syntax hightlighting (as far as I know). Sure, the learning curve is pretty steep, but after some training you can edit text *really* fast. Type 'vimtutor' in a bash shell and see for yourself.[/QUOTE]

it must have syntax highlighting, I've seen it on my host's ssh.. but never on my own vim lol.

*pokes akurashy*

---

### Post by Lews Therin on 2006-01-08
[QUOTE=rock freak]aha dont worry about the glade after enough routing around i have found the autoconf and automake libries for cygwin :D[/QUOTE]

You may have better luck with the [Win32 version of Glade](http://gladewin32.sourceforge.net/modules/news/).

---

### Post by Azriphale on 2006-01-09
For an editor, I use emacs everywhere. I think it makes more sense than vim. It is also difficult to get used to (it has a lot of advanced function), but when you do, it makes editing files very quick.

And, as has been pointed out, there is gladewin32 available.

---

### Post by rock freak on 2006-01-09
yeah i have glade win32 but it still chucks out autogen.sh and make fuiles so you have to have some way of run them the only way i have got so far is via cygwin i have tried dev cpp as well but to no avial!!!


any help would be very much appreciated!!

---

### Post by Lews Therin on 2006-01-09
[QUOTE=rock freak]yeah i have glade win32 but it still chucks out autogen.sh and make fuiles so you have to have some way of run them the only way i have got so far is via cygwin i have tried dev cpp as well but to no avial!!!


any help would be very much appreciated!![/QUOTE]

Download and run the installer

---

### Post by rock freak on 2006-01-09
i have and selected cygwin and dev cpp on install
but still nothin!!:S

it looks like to me that it is somethign to do witht he libary files!

---

### Post by LordHunter317 on 2006-01-09
[QUOTE=jwenting]GVim it is for me. Only true cross platform editor (if you include VI and VIM).
Using it in some flavour or another on Windows, Linux, AIX, Solaris, and SCO (and have used in the past on HPUx, BDS, and OS/2).[/quote]Hardly.  Emacs runs natively on more platforms than VI ever has, I think.

---

### Post by benplaut on 2006-01-09
i haven't found a single editor i like as much as Gedit, but i need to try SciTE again... looks good

---

### Post by Azriphale on 2006-01-10
Do you have the normal win32 GTK+ devel release installed? I don't remember if GTK+ and gladewin32 are packaged separately... But you do need GTK+ development installed.

---

### Post by rock freak on 2006-01-10
well i no that i got this package from the win32glade site 2.8.8-rc2 addtiont he first one on the page!!!

---

### Post by go_beep_yourself on 2008-04-15
[http://live.gnome.org/Gedit/Windows?action=AttachFile&do=view&target=geditwindows.jpg](http://live.gnome.org/Gedit/Windows?action=AttachFile&do=view&target=geditwindows.jpg)

---


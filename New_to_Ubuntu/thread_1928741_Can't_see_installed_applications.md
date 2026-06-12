---
title: "Can't see installed applications"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by Ketman on 2012-02-20
According to the Software center I've installed many programs, but most of them seem to be hiding from me. For example, I've just installed the Grub customizer, but I can't see it. The only entry in Applications>System Tools is KpackageKit, whatever that is. No sign of Grub customizer. Anyone tell me where it is?

---

### Post by Ms. Daisy on 2012-02-20
Are you running 11.10? Ubuntu, kubuntu, etc? What desktop environment are you using? Is it the default, Unity?

---

### Post by oldos2er on 2012-02-20
If you're using KDE, type Alt-F2 and enter "grub" (without quotes). Does it show anything?

---

### Post by Ketman on 2012-02-20
I'm running 10.04. I haven't changed my desktop since it was installed, so I presume it's the default.

---

### Post by Ketman on 2012-02-21
Here's what I've got listed under Applications:


Accessories >>Calculator, CD/DVD Creator, Character Map, Disk Usage Analyser, gedit Text Editor, Manage Print Jobs, Passwords and Encryption Keys, Search for Files, Take Screenshot, Terminal Tomboy Notes

Education >> KTurtle

Games >> AisleRiot Solitaire, DosBox Emulator, gbrainy, Mahjongg, Mines, Quadrapassel, Sudoku

Graphics >> F-Spot Photo Manager, OpenOffice.org Drawing, Simple Scan

Internet >> Claws Mail, Empathy IM Client, Firefox Web Browser, Gwibber Social Client, Remote Desktop Viewer, Terminal Server Client, Transmission BitTorrent Client

Office >> Dictionary, Evolution Mail and Calendar, OpenOffice.org Presentation, OpenOffice.org Spreadsheet, OpenOffice.org Word Processor

Science >> Qalculate!

Sound & Video >> Brasero Disk Burner, Movie Player, PiTiVi Video Editor, Rhythmbox Music Player, Sound Recorder

System Tools >> KPackageKit

Wine >> Programs, Browse c:\ drive, Configure Wine, Uninstall Wine Software

Ubuntu Software Centre

Most of those were installed automatically I presume. But I did install Kturtle, Wine, and a few others myself.

But when I look in the Software Center I've got 75 items marked with a green tick:

Archive Manager
Bluetooth
Byobu Window Manager
Calculator
Compiz
Computer Janitor
Configuration Disk Utility
etc...

That's just those between A-C. I've never seen most of them. There are some I've deliberately installed myself, but can't find in my Applications menu, such as Python, 16-bit Assembler and Loader, GNU assembler linker and binary files, GNU C Compiler, GNU debugger. Those last  I can find under Development Tools and they are ticked as installed, but they don't show up on the Installed Software list.

Just as an experiment, while writing this post I installed Hex Editor from the Development Tools list, and it now shows up there as installed, and it's also listed in Installed Software. My Applications menu now has a new category, Programming, which contains Hex Editor, but nothing else. None of those I installed previously from Development Tools are there.

---

### Post by Ms. Daisy on 2012-02-21
Couple of things: The programs you're looking for are run from a terminal (but I don't know about grub customizer).  I've got unity now so I can't remember if they show up in the applications list.
edit: They should show up in the GUI.

I think Python is automatically installed along with Ubuntu 10.04. Which version of Python did you install? 

What happens when you open a terminal (ctrl + alt + t) and type
```
python
``` ?

You should get something like this if python is installed.
```
msdaisy@computer:~$ python
Python 2.7.2+ (default, Oct  4 2011, 20:03:08) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

```

---

### Post by bogan on 2012-02-21
Hi!, **ketman**,

Just a suggestion that worked for me in a similar newbie situation:

 Run Main Menu and see if the programs you have installed are listed there, but are not ticked, so do not show in the Menus displays.

Chao!, **bogan**.

---

### Post by forrestcupp on 2012-02-21
If you can't get Grub Customizer in your menus, you can always run it with this command
```
gksudo grub-customizer
```

And you can always create a launcher with that code to make it easier in the future. Grub Customizer is not a program you're going to run a lot, so you might as well just save yourself the trouble and run it from the command line.

---

### Post by Ketman on 2012-02-21
Bogan's suggestion of trying the Main Menu turned up a couple of things. I found Grub Customizer in System>>Administration, and I found Python in Programming, but unticked. So I ticked it, and now it shows up in Applications. That's those two sorted. But I can't mark this as solved,  because all the other apps I listed seem to have gone AWOL.

---

### Post by Ms. Daisy on 2012-02-21
> **Ketman said:**
> Bogan's suggestion of trying the Main Menu turned up a couple of things. I found Grub Customizer in System>>Administration, and I found Python in Programming, but unticked. So I ticked it, and now it shows up in Applications. That's those two sorted. But I can't mark this as solved,  because all the other apps I listed seem to have gone AWOL.
can you open them in terminal?

---

### Post by 3rdalbum on 2012-02-21
Most of the programs you mentioned are terminal programs with no GUI. The compiler, assembler, Python etc. Therefore they don't show up in the Applications menu. They can be run from the terminal though.

---

### Post by Ketman on 2012-02-22
> **Ms. Daisy said:**
> can you open them in terminal?

I just tried one. In Software Center>>Development Tools, there is the GNU C compiler, marked as installed, though it doesn't show up in Installed Applications. Underneath its title is the filename (presumably). So I typed "gksudo gcc-4.4" and got an error "invalid syntax".

---

### Post by Ketman on 2012-02-22
> **3rdalbum said:**
> Most of the programs you mentioned are terminal programs with no GUI. The compiler, assembler, Python etc. Therefore they don't show up in the Applications menu. They can be run from the terminal though.

Ah! I didn't think of that. Makes sense. But see my other post. I've tried running a couple from the terminal - no luck.

---

### Post by bogan on 2012-02-22
Hi!,** ketma**n,

You Posted:  > So I typed "gksudo gcc-4.4" and got an error "invalid syntax".'gksudo' is for running graphics programs from the Terminal; use just 'sudo'.

In most cases using 'man programname' will tell you the command and options that are used.

```
man gcc-4.4 
```tells you that the command is 'gcc'

Chao!, **bogan**.

---

### Post by Ketman on 2012-02-22
> **bogan said:**
> Hi!,** ketma**n,

You Posted:  'gksudo' is for running graphics programs from the Terminal; use just 'sudo'.

In most cases using 'man programname' will tell you the command and options that are used.

```
man gcc-4.4 
```tells you that the command is 'gcc'

Chao!, **bogan**.

I'm not having any luck today. I just tried "sudo gcc-4.4" and got "invalid syntax". Then I tried "man gcc-4.4" and got the same result. Nothing doing.

---

### Post by bogan on 2012-02-22
Hi!, ketman.

All I can say is I just tried 'man gcc-4.4' again, and it works on my 11.10 as it should; maybe it did not get installed.

 Have you tried 'man' with the other programs you cannot find?

Chao!, bogan.

---

### Post by bogan on 2012-02-22
Hi!, **ketman**.

I just tried 'man gcc-4.4' in 10.04 and it works there too.

I also entered 'gcc-4.4' in the Search box of  File Manager  set to the root folder, and this is what came up:
[ATTACH]213093[/ATTACH]Chao!,** bogan**.

---

### Post by Ketman on 2012-02-22
> **bogan said:**
> Hi!, **ketman**.

I just tried 'man gcc-4.4' in 10.04 and it works there too.

I also entered 'gcc-4.4' in the Search box of  File Manager  set to the root folder, and this is what came up:
[ATTACH]213093[/ATTACH]Chao!,** bogan**.

No. Just tried it again. No luck. 
Looked for it in Search for Files. Found it, and plenty of associated files too. So it's there, but can't get to it from terminal.

Also tried with GNU debugger (gdb). 
"sudo gdb" - "invalid syntax"
"man gdb" - "invalid syntax"
Looked for that with Search for Files. Found it in File System. It's there. But, again, terminal doesn't recognize it.

Remind me - what's File Manager? Can't see that one anywhere. Is that another one that's gone missing?

---

### Post by bogan on 2012-02-22
Hi!,** ketman.**

You Posted:>  Remind me - what's File Manager? Can't see that one anywhere. Is that another one that's gone missing? I meant the program that displays folder contents when one Clicks on the Home or Files Icons or Menu Items.

Its proper name is probably Nautilus, at any rate that is what you use from a Terminal; otherwise people refer to it as Desktop Manager. but that's also used for other things

 There are also other alternative arrangements, so I used 'File Manager' as a generic name for whatever is used.

Confusing, isn''t it?  Chao!, **bogan**.

---

### Post by larrypg on 2012-02-22
Hello,

You can also try things without the version number such as in a terminal type man gcc or gcc.  This applies to most programs.  You do not have to put the version number to start it.

---

### Post by bogan on 2012-02-23
Hi!,** ketman**.

Some basic queries:

Is the  'invalid syntax' error limited to 'man', or is it more general, ie is your Terminal or Keyboard  not working correctly?

Does 'man' work with other commands/programs?  For instance 'cd', 'xterm', 'ls' or 'lshw'.
```
man cd 
```should give a > " no manual entry for cd" message, the others, full details.

Do other commands work from the Terminal you are using? For instance 'cd', 'xterm', 'ls', or 'lshw'.

How are you opening the Terminal?  Application>Accessories Menu, 'Ctrl+Alt+t', or  'Ctrl+Alt+F1' or F2.
See if those give the same results.

Try also from an xterm Terminal if that command works from the Terminal you are using.

Chao!,** bogan.**

---

### Post by Ketman on 2012-02-23
> **bogan said:**
> Hi!,** ketman**.

Some basic queries:

Is the  'invalid syntax' error limited to 'man', or is it more general, ie is your Terminal or Keyboard  not working correctly?

Does 'man' work with other commands/programs?  For instance 'cd', 'xterm', 'ls' or 'lshw'.
```
man cd 
```should give a  message, the others, full details.

Do other commands work from the Terminal you are using? For instance 'cd', 'xterm', 'ls', or 'lshw'.

How are you opening the Terminal?  Application>Accessories Menu, 'Ctrl+Alt+t', or  'Ctrl+Alt+F1' or F2.
See if those give the same results.

Try also from an xterm Terminal if that command works from the Terminal you are using.

Chao!,** bogan.**

Bullseye! That did it. I closed the terminal and opened another from the Applications menu. All works fine now. 

I also figured out after typing "man gcc-4.4" that "man" stands for "manual". Something learned.

What I couldn't figure out, though, was how to exit back to the prompt. I PgDned all the way to the end but still couldn't get out. I had to close the terminal. What's the secret key?

---

### Post by Ms. Daisy on 2012-02-23
> **Ketman said:**
> 
What I couldn't figure out, though, was how to exit back to the prompt. I PgDned all the way to the end but still couldn't get out. I had to close the terminal. What's the secret key?
You exit a man page by pressing "q".

---

### Post by Ketman on 2012-02-23
^Ah, thanks.

---

### Post by bogan on 2012-02-23
Hi!, **ketma**n,

 > What's the secret key? Youcould always try>  man man Or even read the bottom line of the man/more display.

Can you now find your 'lost' programs from a terminal that works.??

Chao!, **bogan**.

---


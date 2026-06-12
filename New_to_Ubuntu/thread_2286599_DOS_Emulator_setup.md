---
title: "DOS Emulator setup"
date: 2015-07-13
forum: New to Ubuntu
---

### Post by kiko2 on 2015-07-13
anybody here who can help me how to use DOS emulator to run my ".exe" program. :/ :(

---

### Post by Dennis N on 2015-07-13
> **kiko2 said:**
> anybody here who can help me how to use DOS emulator to run my ".exe" program. :/ :(

Maybe. What is the name of the DOS emulator program?

---

### Post by deadflowr on 2015-07-13
I forget how many dos emus there are.
So which dos emu, dosbox?

I know dosbox contains a help section that explains mounting the place where the exe is, then changing into that to run it.
If I remember correctly it defaults to Z and you need to set the mount points for wherever the exe, or dos file you want is.
(The Z drive exists only within the dosbox program)

The basic mount command to run, within the dosbox, is
```
mount c /the/path/to/the/folder/for/the/app
```
The just type C: to change into the newly mounted C directory.

Also any good dos game or program will contain an easy to read, readme, file that will explain any steps you need to do to install or run it.


 as pointed out though, we know neither the dos program, nor the dos emulator you are trying to use, so...

---

### Post by Dennis N on 2015-07-13
There is a simple way to run programs without any explicit mount commands in dosbox. But before expounding on that, I would want to see first what the emulator is. Also, your title uses the word 'setup' which is going to be more than how to run a program. So it would be helpful if you pose specific questions.

---

### Post by kiko2 on 2015-07-13
I am using the "DOS Emulator" from Ubuntu Software Center.

---

### Post by Dennis N on 2015-07-13
> **kiko2 said:**
> I am using the "DOS Emulator" from Ubuntu Software Center.

There are two emulators for DOS in the software center: "DOS Emulator" (package name: dosemu) and "DOSBox Emulator" (package name: dosbox). I am only familiar with DOSBox Emulator (dosbox). I hope someone else is able to help you. Good luck.

---

### Post by kiko2 on 2015-07-19
Dennis n,

Ok. could you teach me how to setup DOSBox Emulator instead? :)

---

### Post by Dennis N on 2015-07-20
You have removed dosemu and installed dosbox? 

O.K., Here goes:

_Preparation_:

I suggest you make a folder in your home folder for your DOS programs. Since mine are all games, I called it dosgames.

Inside dosgames, I made a folder for each game. Use 8 characters or less for the names (DOS rules) + 3 more for extension on file names. All the files for each game go into its folder. These games were originally bought on 3 1/2" floppy disk or CD in the 1990s. I copied the disk for each game into its folder with a USB floppy drive I bought.

My listing of game folders:
```
dmn@Sydney:~/dosgames$ ls
Archive  brain2  brix1-2  othello  SSAE  SSSB  SSTMS
brain    brix    chess    pcft     SSO   SSTM  TCV

```

_How to start a game with a terminal command_:

First, I find the file that starts the game. Using folder TCV (contains the game Treasure Cove) as an example.

```
dmn@Sydney:~/dosgames$ cd TCV
dmn@Sydney:~/dosgames/TCV$ ls
COVE.EXE      INSTALL.EXE  TC000.DAT  TC002.DAT  TC004.DAT  TCV.ICO
DESKTOPD.CFG  INSTALL.PDM  TC001.DAT  TC003.DAT  TCV.BAT    TCV.PIF

```
Look for an .EXE file using the game name. Try the COVE.EXE file. Be sure it's executable.

Linux command in terminal to start this game ( I have to use caps where they are used, since Linux is case sensitive):

```
dosbox /home/dmn/dosgames/TCV/COVE.EXE
```

that is,  dosbox, followed by full path to game file.

When done, quit game by its normal method. You return to dosbox prompt. Type **exit** to quit dosbox.

Note: There is an important configuration file at ~/.dosbox/dosbox-0.74.conf where lots of adjustments can be made to how dosbox performs.

---

### Post by mastablasta on 2015-07-20
or oyu can install a GUI something like dbgl for example: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)

it's made with games in mind but it's easy to setup other things on it with clics (that is if you like the GUI interface)

---

### Post by Dennis N on 2015-07-20
> Note: There is an important configuration file at ~/.dosbox/dosbox-0.74.conf where lots of adjustments can be made to how dosbox performs. 

I compared my current dosbox-0.74.conf to the default. These are the only changes that I had made in the past:

windowresolution=original changed to windowresolution=800x600
output=surface changed to output=overlay
aspect=false changed to aspect=true
scaler=normal2x changed to scaler=normal3x
cycles=auto changed to cycles=fixed 3000
cycleup=10 changed to cycleup=500

I suggest you backup the original if you start making changes so you can see what the original settings were. Or you could add comment lines noting the original values.

---

### Post by Dennis N on 2015-07-24
Hi kiko2;
It's Been 5 days. I'm wondering how DosBox is working out for you. Were you able to use the instructions given?

---

### Post by kiko2 on 2015-07-24
Hi Dennis N,

Sorry If I didn't get back as soon as possible. I've been busy these past few days. Thank you for the time.

I finally figured it out how to run my software using "DOS Emulator" and I tried using "DOSBox" too, but i'm having glitches on "DOSBox".

---

### Post by Dennis N on 2015-07-25
I appreciate the report. You should of course use what works best for you. DosBox is built with games in mind and tries to support the sound card and other requirements they had. In fact, a post by a developer on the forum states that it is not suited for non-gaming applications. 

As you probably noticed, there are many adjustments in its configuration files to fine tune it's performance. It takes a little experimenting to get it right. For example, I had sound problems until I discovered the right choices.

DosBox Forum:
[http://www.vogons.org/viewforum.php?f=31](http://www.vogons.org/viewforum.php?f=31)

2069: The 312th prime number.

---


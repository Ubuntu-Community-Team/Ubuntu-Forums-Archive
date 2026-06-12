---
title: "How-to: Playing old dos games with Dosbox. Guide for newbies."
date: 2007-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Hallvor on 2007-08-15
DOSBox emulates an Intel x86 PC, complete with sound, graphics, mouse, modem, etc., necessary for running many old DOS games that simply cannot be run on modern PCs and operating systems, such as Microsoft Windows 2000, Windows XP, Linux and FreeBSD. However, it is not restricted to running only games. In theory, any DOS application should run in DOSBox, but the emphasis has been on getting DOS games to run smoothly, which means that communication, networking and printer support are still in early developement.

DOSBox also comes with its own DOS-like command prompt. It is still quite rudimentary and lacks many of the features found in MS-DOS, but it is sufficient for installing and running most DOS games. [http://dosbox.sourceforge.net/wiki](http://dosbox.sourceforge.net/wiki)

Now, let`s move to the fun part:

Dosbox is not installed in Ubuntu by default, so you have to install it yourselves. There are two ways to do this, either through System-->Administration-->Synaptic package manager (search for dosbox, mark for install and apply), or you could use the comand line interface. The command line interface - CLI for short - is located under Applications --> Accessories --> Terminal.

Now, launch the CLI as shown above. Copy and paste the following command into the black box and press enter:

> sudo apt-get install dosbox

You will now be prompted for a password. Type in the password and press enter. Dosbox should now be installed.

Now, Dosbox is nothing without good old dosgames. This page contains many abandonware dosgames, but you can also find many more on google: [http://www.abandonia.com/index2.php](http://www.abandonia.com/index2.php) Pick one and download to your desktop. Press Alt+home to enter the home directory. This is where we want to place the games. Right click and make a new folder for your game. Double click the downloaded file, and extract the contents to the correct folder.

Now, for my part I have extracted the game task force 1942 from an old computer of mine and made the folder TF1942 in my home directory. The structure on this computer looks like this:

/home/ragnhild/TF1942

Now, everything is ready. Launch the installed Dosbox by opening the terminal and typing > dosbox

You should now have this image: 

[http://img456.imageshack.us/my.php?image=skjermdumpdosbox070cpucfo2.png](http://img456.imageshack.us/my.php?image=skjermdumpdosbox070cpucfo2.png)

Next, you need to mount a virtual drive c on your hard drive. 

I use the following command > mount c /home/ragnhild/TF1942 Remember that this command is case sensitive, so type every directory excactly as they are named.

If you have done everything correctly, you should se something like this:
[http://img381.imageshack.us/my.php?image=skjermdumpdosbox070cpucsv3.png](http://img381.imageshack.us/my.php?image=skjermdumpdosbox070cpucsv3.png)

From the z: prompt, type > c:

[http://img457.imageshack.us/my.php?image=skjermdumpdosbox070cpucou8.png](http://img457.imageshack.us/my.php?image=skjermdumpdosbox070cpucou8.png)

Dosbox is now mounted inside your game directory and will respond to many of the common dos-commands. List the files in the game directory to find the executable file (usually an .exe or a .bat) by typing > dir /p


[http://img463.imageshack.us/my.php?image=skjermdumpdosbox070cpucco0.png](http://img463.imageshack.us/my.php?image=skjermdumpdosbox070cpucco0.png)

In this case, the executable is TF1942.BAT (It may also launch with TF.EXE, but I haven`t tested it.)

That means you can launch the game by typing > tf1942

Now, the game should launch, and you`ll see the game in a little box in the middle of your screen:

[http://img400.imageshack.us/my.php?image=skjermdumpdosbox070cpucml0.png](http://img400.imageshack.us/my.php?image=skjermdumpdosbox070cpucml0.png)

Toggle fullscreenmode on/off with Alt+Enter. Play the game! :)

Advanced: If you want to automount a drive or change the default settings by editing the config-file, see this thread [http://ubuntuforums.org/showthread.php?t=171970&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=171970&highlight=dosbox)

For additional settings, hotkeys and troubleshooting, see this page: [http://dosbox.sourceforge.net/wiki/index.php?page=Basic+Setup+and+Installation+of+DosBox](http://dosbox.sourceforge.net/wiki/index.php?page=Basic+Setup+and+Installation+of+DosBox)

---

### Post by Nicole on 2007-08-15
This is an excellent how-to! Thank you very much!

N

---

### Post by marenkar on 2007-10-12
when I try to mount this comes out:

admin@admin-desktop:~$  mount c /home/ragnhild/TF1942
mount: only root can do that

---

### Post by Lord Illidan on 2007-10-12
> **marenkar said:**
> when I try to mount this comes out:

admin@admin-desktop:~$  mount c /home/ragnhild/TF1942
mount: only root can do that


That command must be entered in Dosbox, not in a normal bash prompt.

So open dosbox first.

Then, you'll get a window containing a DOS like command prompt. Enter mount C /home/<username>/TF1942

Ofcourse, replace <username> with your username. From what you pasted here, it appears it is admin.

If you don't have the folder TF1942 in your /home/admin directory, then it will not work for obvious reasons..

---

### Post by Hallvor on 2007-10-12
Are you trying to mount *my* local directory on *your* computer? You are supposed to mount the directory on your computer where you put your game, e.g. /home/<yournamehere>/games/mortalkombat

It also seems like you are trying to mount the game on your root shell... You should type the command to mount your local game directory from this screen after launching Dosbox:

[IMG]http://img456.imageshack.us/my.php?image=skjermdumpdosbox070cpucfo2.png[/IMG]

---

### Post by marenkar on 2007-10-13
sorry bout that, thought it was already there.
Was able to mount already.
I'm trying to run tt.exe but it wont run as I need Win32, where will I be able to get this and use it in ubuntu?

---

### Post by Hallvor on 2007-10-13
If tt.exe is a compressed game file, then it could be a problem. I have not been able to play a couple of games myself, e.g. ROTT (Rise Of The Triad), because the only download available was an exe self-extracting archive. The installation failed. Fortunately, most of the games out there are already uncompressed (or in zip,rar), and they should be easy to run. 

A solution to your problem would be to open and install the game under Windows, and copy the game folder  to your home directory, launching it with dosbox.

---

### Post by GutsyGibbon on 2007-10-13
Great How-to. thank you very much.
never thought anyone would actually still need that, but... whatever.
:)

---

### Post by popch on 2007-10-29
Is there any marked difference between a DOS box and booting DOS in a virtual machine?

---

### Post by m_alnaanah on 2007-10-29
The caps lock does not work (dosbox version 0,71) what is the solution.:(

it's also does not work in vertual terminal (CTRL + ALT +1) does this mean it needs X-server to run.

---

### Post by paridoth on 2007-10-30
is there any way i could make a launcher for the panel that would launch the game with just the click off a button?

---

### Post by Oztazdevil on 2008-04-01
Hi!     I'm  new here and was wondering if someone could help me with the DosBox thing. I'm not very computer savvy either so please bear with me.   I was following the instructions on how to get the dosbox to work but now I.m stuck. I got it  to accept the mount c thing I think. It says mount c:windows mounts windows directory as the c drive in DOSBox and won't do anything else.  I didn't get asked for a password or anything and I don't know if I've activated it or not. I have no clue how to get the games into it either. Any help would be apprecitated. Thank you.

---

### Post by Hallvor on 2008-04-03
> **Oztazdevil said:**
> Hi!     I'm  new here and was wondering if someone could help me with the DosBox thing. I'm not very computer savvy either so please bear with me.   I was following the instructions on how to get the dosbox to work but now I.m stuck. I got it  to accept the mount c thing I think. It says mount c:windows mounts windows directory as the c drive in DOSBox and won't do anything else.  I didn't get asked for a password or anything and I don't know if I've activated it or not. I have no clue how to get the games into it either. Any help would be apprecitated. Thank you.

**After launching dosbox from the terminal**, write:

```
mount c /home/yournamehere/directory-to-game/
``` where "yournamehere" is your username, e.g. bob, and directory-to-game is where your game is located. If it is in your home directory and your name is bob, the parameter could be something like: mount c /home/bob/mortalkombat
Drive c will now be mounted in /home/bob/mortalkombat and you can now get a list of files by typing dir /p or simply dir to find the name of the .exe or .bat to run the game.

---

### Post by IsawSp4rks on 2008-04-03
> **popch said:**
> Is there any marked difference between a DOS box and booting DOS in a virtual machine?

Yes, DOSBox isn't a universal x86 emulation layer like VPC, VMWare and the rest.

DOSBox is predominantly an emulator for running DOS era games and it emulates technologies like EMS, XMS and HIMEM to allow for highest available memory - a very important thing for most DOS games.  It also integrates complete emulation of the 80486 at variable speeds (as slow as 1mhz and as fast as Pentium 200 and faster depending on the host system).

DOSBox also emulates necessary hardware that the majority of DOS games might need/use.  These include:-

[LIST]
[*]The ISA SoundBlaster range (SB, SB1.5, SBPro, SBPro 2, SB 16) except the AWE32.

[*]The Adlib FM synth.

[*]The Gravis UltraSound basic, Max and Pro soundcards

[*]MT32 and GM external synth output (there are also SVN builds that integrate MUNT MT32 emulation, you'll need the MT32 ROMs and it doesn't sound 100% accurate - harmonies are off in many cases)

[*]Various VGA chipsets including ET4000, CL and more including ModeX emulation.

[*]CGA, EGA, Hercules and IMB 8514. 

[*]Joystick and mouse input.

[*]Output scalers such as 2X, Eagle and so on (important as many DOS games run at 320x200 and so need to be scaled fill screens.  Aspect ratio is supported so you can scale a 3:2 res to something much higher and have black bars on either side - important for widescreen monitors.
[/LIST]

There are also custom SVN builds that also have 3DFX Glide and other emulated hardware (such a VR Helmets) built in.

It's teh awesome!

---

### Post by mia1dolfan on 2008-04-04
[QUOTE="IsawSp4rks"]MT32 and GM external synth output (there are also SVN builds that integrate MUNT MT32 emulation...[/QUOTE]

The following post shows to get the MT32 emulation going with DOSBOX... :)

[http://ubuntuforums.org/showthread.php?t=728989](http://ubuntuforums.org/showthread.php?t=728989)

---

### Post by semisweet on 2008-05-03
I am trying to run X-wing vs. TIE fighter in Ubuntu 7.10. I followed the how to and this is what I got:
[[IMG]http://img236.imageshack.us/img236/1838/screenshotmy9.th.png[/IMG]](http://img236.imageshack.us/my.php?image=screenshotmy9.png)

Can someone help me with this? 

Thanks,
Semisweet

---

### Post by Hallvor on 2008-05-03
You need Windows 95 or Windows 98 to run it. It does not run in Dos, it seems.

[http://www.mrhope.com/games/games/xwvstf.htm](http://www.mrhope.com/games/games/xwvstf.htm)

---

### Post by 900donuts on 2008-05-05
i've got the original x-wing game and the original tie fighter game both are on 3.5in floppies 

how do i install games that are on multiple floppies?

---

### Post by tomansc on 2010-09-09
Thanks for this! Supremely helpful and worked like a charm! Currently enjoying the over-the-top cheesy awesomeness that is Police Quest 3: The Kindred.

You made my day :)

---


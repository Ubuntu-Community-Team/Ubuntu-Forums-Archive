---
title: "[SOLVED] Gnome vs. KDE - Questions and Others"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by darksideforge on 2008-11-27
More newbie questions:

(1) In simplified terms, what is the difference (what are the differences) between KDE and Gnome?

(2) After reading voluminous posts on CLI, I'm still a little confused; If I CTRL+F2 (or F3-F6) after a clean boot from the HDD, I get asked for my login/pass info. Done. Then I get *myname-laptop:~$* This puts me in or at the shell, correct? If I type the command ls (although I prefer ls -1) I get a list of .....what, exactly? Yes, I see that those are the files under PLACES>HOME FOLDER, but what can I do from there? Anything?  For example, I've seen numerous places in the forum where members discuss installing this or that via CLI, and they give examples of what they typed for whatever fix they're referring to, but where do I start to type that code in and where do I go to see the existing code before I either type new code or replace existing code?  Do I start from > myname-laptop:~$_ or do I need to change directories (CD\) or what?

(3) I've seen lots of warnings regarding working from shells as opposed to working in the Root. Is "The Root" where I need to go to see the code(s) I was referring to in Question 2 above?

(4) Under System>Administration>HardwareDrivers, my WiFi equipment appears to be installed and operating fine; nowhere is my sound card (stock) mentioned nor do I have any sound when I attempt to play music or video (and yes, I've downloaded and installed what I believe to be appropriate codecs). I have been slowly working my way through Soundcheck's post on Asla 1.0.18...is this my answer? At one point he (she?) gives the following hint:
> Hint:
The easiest and most reliable test to verify if Alsa is working is "aplay" - the Alsa player application.

Type in a terminal:
$ aplay -l

Now, going back to part of what I asked in Question 2 above, the "stringsign" or "dollarsign" $ that Soundcheck shows in his/her example...is that referring to the $ that shows up waiting for me in (what I think is called) the shell (CTRL+F2) or do I actually need to type a $ and then type aplay -l ?  Or, before I type $ aplay -l, do I need to change directories from *myname-laptop:~$* to something else? If so, what/how?


Thank you all in advance for being patient and holding my hand; I'm very new to this; I'm running a Toshiba Satellite L45-S4687 that came with Pentium DualCore with Vista HomePremium installed. I have completely formatted and partitioned my drive so that everything belongs to Ubuntu 8.10. I've got an 80GB HDD, 1GB RAM, DVD-RW, built-in WiFi, and am operating from my home with an 8-wire/4-wire Cat6 Ethernet (hardwire) with Motorola DSL modem.

---

### Post by Kareeser on 2008-11-27
Best bet is to just try :)

The dollar sign is not part of the command.

As for the terminal, it dumps you into your home folder. Type "cd /" to access the rest of the hard drive.

---

### Post by renzokuken on 2008-11-27
1. There isnt really a short answer. They are just two different Desktop Environments. They have their own specialist apps and configuration utilities, but ultimately do the same thing. You can run Gnome apps in KDE and vice versa. Best bet is to try both DEs and see the differences for yourself.

2. You can do almost everything from the commandline if you wish. By default the shell will start in your home directory (/home/username) but you can move around with **cd** e.g.

```
cd /path/to/folder
```

you can (if you want to be a commandline junkie) edit files, copy, move, link all through the terminal as well as thousands of other things such as check hardware, mount devices....the list is endless and there are plenty of sites that explain it better and in more detail.

As for where to type code, i'll do example. Suppose someone tells you to install VLC media player using ```
sudo apt-get install vlc
``` simply type all this in after the **myname-laptop:~$ ** bit in the terminal and hit enter. of course, there are graphical apps (in this case Synaptic Package Manager) that will do most tasks for you by point and click without ever having to use the CLI.

3.  Root can mean one of two things, either the folder **/root** or the root account. you should be careful with both since root user has full access to your whole system and you might accidentally change something you didnt mean to and hose the system. what do you mean by "code" by the way?

4. you will have to find out what soundcard/chipset you have and search the forums/google for a solution to get it working.

....as for your final question, no you do not need to type the $ sign, that is simply a common notation for the terminal, meaning type this in the terminal......so all you would type is ```
aplay -l
```

---

### Post by Bucky Ball on 2008-11-27
(4) Hardware Drivers are the restricted drivers (sometimes wireless, sometimes graphics, sometimes both). Your sound card will not show up in there.

Here's some practice, 'sudo' (superuser do) makes you root for the command only (not permanantly). Copy and paste this into a terminal (ctl/v to paste in a terminal)

```

sudo lshw
```

You will find you hardware and sound card in the result.

---

### Post by m_duck on 2008-11-27
Some websites / people use the $ or the # to mean either run the command following the symbol as a regular user or root respectively. The root user is the computers administrator with access to everything (and so can potentially break everything too). In Ubuntu, the root account is disabled by default for security. You can however grant yourself temporary root privileges (for installing packages for example) by prefixing a command with ```
sudo
``` and then entering your command.

---

### Post by darksideforge on 2008-11-27
A quick note of thanks to all! Everything was VERY helpful! Renzokuken, you answered my question PERFECTLY...I didn't know that KDE or Gnome were desktop environments, so it was actually two answers in one.

As far as being a CLI junkie, I think I'll probably get there at some point, just because I like the interaction. GUI just gets "stale" after a while.

Bucky Ball, that was EXACTLY what I needed to know and see...THANKS!
And, the answers you and M_Duck gave included the description of SUDO, which would've come up in another question eventually, so THANKS! for that as well!

---

### Post by bhadotia on 2008-11-27
> **Bucky Ball said:**
> (4) Hardware Drivers are the restricted drivers (sometimes wireless, sometimes graphics, sometimes both). Your sound card will not show up in there.

Here's some practice, 'sudo' (superuser do) makes you root for the command only (not permanantly). Copy and paste this into a terminal (ctl/v to paste in a terminal)

```

sudo lshw
```

You will find you hardware and sound card in the result.
@Bucky Ball
Thats ctrl+shift+v to paste in the terminal unlike the usual ctrl+v.
@darksideforge
1 KDE is a more sophisticated DE than the simpler GNOME but in my opnion not better than it.
2,3,4 [Here]("https://help.ubuntu.com/community/UsingTheTerminal") is a good intro to the CLI with some good links for further reading.
3 You can google for your sound card problem. Typ:
```
lshw -C sound
```
for your sound card model and then google appropriately or make a new thread for the problem.

---

### Post by darksideforge on 2008-11-27
> **bhadotia said:**
> @Bucky Ball
Thats ctrl+shift+v to paste in the terminal unlike the usual ctrl+v.
@darksideforge
1 KDE is a more sophisticated DE than the simpler GNOME but in my opnion not better than it.
2,3,4 [Here]("https://help.ubuntu.com/community/UsingTheTerminal") is a good intro to the CLI with some good links for further reading.
3 You can google for your sound card problem. Typ:
```
lshw -C sound
```
for your sound card model and then google appropriately or make a new thread for the problem.  

This worked really well also and slowed it down so I could read it.  I remember seeing a CLI input so that a list on the CLI screen would show up a page at the time...when I perform the lshw, I see where there's information generated that is above my screen so that I can't read it. Isn't there a command that I can add at the end of a string to make the output show up one page at the time and then use pageup/pagedown to move around?  Or, once the info is generated and autoscrolls all the way to the bottom, is there a way for me to move up to read the add'l info? Thanks, this has been a big help!

---

### Post by bhadotia on 2008-11-27
> **darksideforge said:**
> This worked really well also and slowed it down so I could read it.  I remember seeing a CLI input so that a list on the CLI screen would show up a page at the time...when I perform the lshw, I see where there's information generated that is above my screen so that I can't read it. Isn't there a command that I can add at the end of a string to make the output show up one page at the time and then use pageup/pagedown to move around?  Or, once the info is generated and autoscrolls all the way to the bottom, is there a way for me to move up to read the add'l info? Thanks, this has been a big help!

Here:
```
lshw | less
```
What the above command actually does is to give the output of lshw to the input of less. This is called input/output redirection- when we redirect the output/input of a commandfrom standard output/input. [Here]("http://linuxcommand.org/") is another good link to learn the command line in more detail after having a little intro. There is another good link in my signature (not not well organized but surely written in an attractive style!).
A quick tip- type in the terminal:
```
man intro
```
for a brief built-in intro to the terminal.
Good Luck!:)
EDIT: When the output of the command is scrolling too fast to be read, you can just scrool up using the mouse to see the messages that you could not read. Also increase th scroll buffer of your teminal to maximum to be able to scroll up the maximum. In gnome-terminal this setting is somewhere in Edit>Current Profile menu.

---

### Post by darksideforge on 2008-11-27
bhadotia,
SUPER!  But, when I get to the end of the tutorial and it says "END", what do I type to get my cursor back? (so that I can do other things)

---

### Post by Tom--d on 2008-11-27
> **darksideforge said:**
> bhadotia,
SUPER!  But, when I get to the end of the tutorial and it says "END", what do I type to get my cursor back? (so that I can do other things)

Press Q for Quit

---

### Post by Bucky Ball on 2008-11-27
> **bhadotia said:**
> @Bucky Ball
Thats ctrl+shift+v to paste in the terminal unlike the usual ctrl+v.


Naturally. Exactly what I meant to say! lol

Thanks for that, bhadotia, it was about 4am when I was posting so half asleep. Hope I didn't confuse anyone with this instruction. You can, of course, use paste from the drop down edit menu in the terminal also.

---

### Post by bhadotia on 2008-11-28
> **darksideforge said:**
> bhadotia,
SUPER!  But, when I get to the end of the tutorial and it says "END", what do I type to get my cursor back? (so that I can do other things)

Press q. 
Some more tips regarding less command (taken from [here]("http://linuxcommand.org/lts0030.php#less")):
Keyboard commands for the less program  
[LIST=1]
[*]Page Up or b-        Scroll back one page

[*]Page Down or space-  Scroll forward one page

[*]G-                   Go to the end of the text file

[*]1G-                  Go to the beginning of the text file

[*]/characters-         Search forward in the text file for                    an occurence of the specified characters

[*]n-                      Repeat the previous search

[*]q-                      Quit
[/LIST]

---


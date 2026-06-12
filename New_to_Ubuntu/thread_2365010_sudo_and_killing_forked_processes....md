---
title: "sudo and killing forked processes..."
date: 2017-07-01
forum: New to Ubuntu
---

### Post by domarius on 2017-07-01
[COLOR=#212121][FONT=sans-serif]Hi guys, I set up Ubuntu on a living room PC to play Steam games and YouTube on the TV, and I'm super impressed!  Main reason is I wanted to try out a free operating system rather than pay another licence for windows, which would be overkill for a livingroom PC.  I'm amazed at just how many of the games I want to play on it have Linux versions and are available through steam!  They are mostly couch multiplayer games, which are fairly indie, so it figures.

However there's one awesome game that isn't compatible with Linux - DuckGame.  But I got it and the controllers all working with it via some Wine instructions I found on the net!  [Instructions here for reference.]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32876")[/FONT][/COLOR][COLOR=#212121][FONT=sans-serif]

The only problem now is automating it so it can be run with the double click of an icon.

Here's the content of my (not working) script;[/FONT][/COLOR]
[COLOR=#212121][FONT=sans-serif]
[/FONT][/COLOR]```
#!/bin/bash

sudo xboxdrv --config xboxdrv_conf --wid 0&
child1 = $!
sudo xboxdrv --config xboxdrv_conf --wid 1&
child2 = $!
sudo xboxdrv --config xboxdrv_conf --wid 2&
child3 = $!
sudo xboxdrv --config xboxdrv_conf --wid 3&
child4 = $!

wine DuckGame.exe

kill -9 $child4
kill -9 $child3
kill -9 $child2
kill -9 $child1

```
[COLOR=#212121][FONT=sans-serif]
xboxdrv is a program configured to pass Xbox 360 controller support through to the Wine emulation so Duck Game can use it.  It's only needed for games running through wine - other Linux games don't need it.[/FONT][/COLOR][COLOR=#212121][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#212121][FONT=sans-serif]Thing is, I can get this to work if I manually run the xboxdrv commands above one at a time each in its own terminal, entering my password each time, then running the "wine DuckGame.exe" command in yet another new terminal (5 open terminals).[/FONT][/COLOR]
[COLOR=#212121][FONT=sans-serif]
[/FONT][/COLOR]
[COLOR=#212121][FONT=sans-serif]I can't work out how to automate this though.  And I need to have the xboxdrv processes killed because it will ruin the gamepad input for all the native Linux games that work fine without it.

I think my 2 main problems are;[/FONT][/COLOR]
[COLOR=#212121][FONT=sans-serif]
[LIST=1]
[*]sudo seems to get right in the way of this, asking for my password while DuckGame already starts, and causes issues.  I would really like to not have to use sudo and just run the xboxdrv command without it.
[*]Those attempts at getting the process ID of the forked processes to kill them later, don't work, and I'm pretty lost about how to do that, in spite all of the stuff I've read.
[/LIST]

Hope this makes sense.  Would appreciate any advice.
[/FONT][/COLOR]

---

### Post by TheFu on 2017-07-01
Processes run with sudo don't run under your normal userid.  They run with the specified ID or as the 'root' account.  Linux is multi-user. NEVER forget that.  If you start a process with a specific userid, only that userid or root can kill it.

```
child1 = $!
```
and
```
child1=$!
```
are NOT the same things. One is a comparison and the other is an assignment.

In all shell scripts, it is a best practice to use the full path to every command. In short, do NOT trust the PATH environment variable. This is a security AND an expected outcome script thing.

Anyway, hope this is helpful.  Watch your spacing.

---

### Post by domarius on 2017-07-02
**Thank you, **that spacing issue was a critical missing piece of the puzzle.  So not only does Linux care about capitalisation, it cares about spacing as well, I have just learned.

Ok PROGRESS!  The script now correctly starts the game and all the controllers work!  The only problem now is, the controller forks are not killed off afterwards, which breaks the control pads for all the non-wine games, meaning I have to restart the computer to return everything to normal.

The weird thing is, I see no error messages.  Looking at the console output, everything starts up fine, but once the game is quit, the last thing in the console is some Wine stuff. I don't see any confirmation or errors regarding killing the child processes.

Also, how do I make a simple icon to click to run this?  Currently I open a terminal window, and type;
cd WindowsGames
cd "Duck Game"
sudo bash start.sh

(contents of start.sh)
```
#!/bin/bash


xboxdrv --config xboxdrv_conf --wid 0&
child1=$!
xboxdrv --config xboxdrv_conf --wid 1&
child2=$!
xboxdrv --config xboxdrv_conf --wid 2&
child3=$!
xboxdrv --config xboxdrv_conf --wid 3&
child4=$!


export WINEARCH="win32"
export WINEPREFIX=~/.wine-duck/
chown root /home/domarius/.wine-duck/
wineboot -u
wine DuckGame.exe


kill -9 $child4
kill -9 $child3
kill -9 $child2
kill -9 $child1
```

---

### Post by TheFu on 2017-07-02
All computers care about accurate inputs.  Garbage in, garbage out.  It isn't a Linux-thing. It is a computer-thing.  If you choose to use 'bash', then you need to learn how to script in bash to get the expected results.  There are 50+ other scripting languages you could choose. Each is a different language.

You still haven't handled the things in my first post. Please re-read it and address those things.  Using the full path to each program is important.

I am not thrilled about your chown command. Running things as root that do not require it is very poor practice - AND dangerous.  Giving a program access to root lets that program pown your system, completely. That is lazy and dangerous.  I would rather see you modify the permission on the exact, specific /dev/ driver files for the controllers than see you run these things with sudo. Don't do it on any other /dev/ files, or you could easily end up with a broken system.

You need to gain a better understanding of file and directory permissions. Make the script 'executable' using chmod. 
If you don't want to be prompted for a password, then you can modify the sudoers file to all 1 command to be run without a password prompt. Be careful, since it is easily possible to cause an error and lock yourself out of all sudo access.

As for having an icon, Linux has standardized on a .desktop file type.  It is sorta like the .PIF file from Windows. You can look up the specs.

Restarting a computer is a Windows thing.  It shouldn't be necessary on Unix-like systems unless there is a hardware-driver bug and I would be embarrassed if I were responsible for that sort of simplistic issue, had I written the driver.

How good are your backups?

---

### Post by domarius on 2017-07-03
Keep in mind that I'm posting here to learn, and that the above code represents several hours of trial and error and reading forum posts and documentation - all just to get one game running! So don't mistake the incorrectness for a lack of effort! :) 

> All computers care about accurate inputs. Garbage in, garbage out. It isn't a Linux-thing. It is a computer-thing. If you choose to use 'bash', then you need to learn how to script in bash to get the expected results. There are 50+ other scripting languages you could choose. Each is a different language.


I don't really mind discovering that bash treats i=0 differently than i = 0, however... it seems like every other language in the world doesn't  (eg. C++, C#, Java, Javscript, Actionscript, PHP, etc. etc,) and instead use = and ==, so my surprise is justified, I feel ;) You're right that computers care about correctness, however, humans set the standards that computers follow, and whoever made bash decided to deviate  from many other languages when it came to this specific convention.  No need to argue over it though - it is surprising, that is all.

> You still haven't handled the things in my first post. Please re-read it and address those things. Using the full path to each program is important.
By "things" you mean the full path, and I tried that. I used "pwd xboxdrv" and "pwd wine" to find out the location was /home/domarius/ and so I replaced all of xboxdrv with /home/domarius/xboxdrv, same with wine, and it broke the script.  "No such program file or directory" for each line in the script.


I get that there's a safer way, but for now I'm trying to get it working, and rightfully avoided tackling this specific issue till I've got the basics actually working - optimisation last!


> I am not thrilled about your chown command. Running things as root that do not require it is very poor practice - AND dangerous. Giving a program access to root lets that program pown your system, completely. That is lazy and dangerous. I would rather see you modify the permission on the exact, specific /dev/ driver files for the controllers than see you run these things with sudo. Don't do it on any other /dev/ files, or you could easily end up with a broken system.


Happy to do this, but no idea how to, so I'll leave that till later I guess.


> You need to gain a better understanding of file and directory permissions. 
That's why I'm here! :)
> Make the script 'executable' using chmod. 
I used "chmod +x start.sh", it completed without error (without any message really) but typing "start.sh" (from the local folder) doesn't run it, I still need to do it with "sudo bash start.sh".  Not sure what we're trying to achieve here though, I can already run it with bash, I'd just like to run it via an icon...


Previously I had also right clicked the file, Properties, Permissions, checked the box "Allow running as program" which I thought did the same thing.


> If you don't want to be prompted for a password, then you can modify the sudoers file to all 1 command to be run without a password prompt. Be careful, since it is easily possible to cause an error and lock yourself out of all sudo access.


Well... given all the talk about security, removing password entry across the board seems insecure, but honestly it's just a media PC under my TV and I'd just like to get my game running.


I did find some tutorials on using "sudo visudo" so I know what you mean, but without clear instructions I'm hesitant to modify this file.  


Shouldn't we be able to specifically allow xboxdrv to run without a password, instead of everything?


> As for having an icon, Linux has standardized on a .desktop file type. It is sorta like the .PIF file from Windows. You can look up the specs.


Yeah I've not had much luck with that previously.  Here's the contents of my file in /home/domarius/Desktop/Duck Game.desktop
```
[Desktop Entry]
Name=Duck Game
Comment=Duck Game under Wine
Exec=/home/domarius/WindowsGames/Duck Game/Duck Game Wine.sh
Icon=/home/domarius/WindowsGames/Duck Game/blagicons.png
Terminal=true
Type=Application
```


With both the script and the desktop file set to run as executable, all this gives me is a desktop icon with no picture (in spite of the .png path being correct) that just gives the error message "There was an error launching the application" when double clicked.


> Restarting a computer is a Windows thing. It shouldn't be necessary on Unix-like systems unless there is a hardware-driver bug and I would be embarrassed if I were responsible for that sort of simplistic issue, had I written the driver.


It's because the processes were still running and I don't know how to stop them, that's all.


> How good are your backups?
I have an "OS" partition that I make backup images of with Ping, and a "Data" partition mounted under "home" where all the games etc. are installed to.  This system is what I use on my Windows PCs for years, and I had help from a friend with mimicking the partition setup on a Linux hard drive.  I'd get help from him but trying not to overload just one person with all my questions :)


UPDATE:


I've solved my actual main problem of ending the processes, now the main problem is the "kernel drivers" are left in an unloaded state which means the gamepads won't work in any games after running this script.  The xboxdrv program unloads the kernel driver and replaces them with itself - I just need it to kindly re-load them back in so the game pads will work in native Linux games again after wine is done.


```

#!/bin/bash

xboxdrv --config xboxdrv_conf --wid 0&
child1=$!
xboxdrv --config xboxdrv_conf --wid 1&
child2=$!
xboxdrv --config xboxdrv_conf --wid 2&
child3=$!
xboxdrv --config xboxdrv_conf --wid 3&
child4=$!

export WINEARCH="win32"
export WINEPREFIX=~/.wine-duck/
chown root /home/domarius/.wine-duck/
wineboot -u
wine DuckGame.exe

kill $child4
wait $child4

kill $child3
wait $child3

kill $child2
wait $child2

kill $child1
wait $child1

```

Contents of xboxdrv_conf;
```
[xboxdrv]silent=true
**detach-kernel-driver=true**
trigger-as-button=true

[ui-axismap] 
x2=ABS_Z
y2=ABS_RZ

[ui-buttonmap]
A=BTN_B
B=BTN_X
X=BTN_A
TR=BTN_THUMBL
TL=BTN_MODE
GUIDE=BTN_THUMBR
```

---

### Post by TheFu on 2017-07-03
History of Bash: [https://www.safaribooksonline.com/library/view/learning-the-bash/1565923472/ch01s03.html](https://www.safaribooksonline.com/library/view/learning-the-bash/1565923472/ch01s03.html)
In short, bash must be backwards compatible with Borne Shell, sh, which has been around much longer than most of the languages you list. Only C may be older, and not by much.

Beginning Bash scripting guide: 
   [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)
The LDP (Linux Documentation Project) is full of great information.

Tutorial on File/directory permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
Spending 45 minutes with 5 userids, 3 groups, and a bunch of temporary directories and files somewhere under /tmp/foo will pay back at least 1000x.  Work your way through every possible chmod octal setting that you can imagine and see what it does. Mix and match some userids into a the same and different groups. See how you can make the different userids be able to work together - or completely prevent them from doing so.  The Unix permissions model is extremely elegant, but also extremely capable. Only a very few times have I needed to use more advanced methods to allow file/directory access than the good-old-standards supported by chmod.

pwd vs which: I think you wanted to use 'which', not 'pwd'.

If you want to stop a process, then you need to send it a "signal" - there are different signals to send depending on how difficult the process is being.  -15 is the normal "kill" signal, but it asks the process to close.  If that doesn't work, you can send a -9 signal that tells the OS to terminate, with all prejudice, the specific process you want dead.

You can use the sudoers to allow 1 program to run without password prompts with or without control over any allowed options.  Unix-like systems are extremely flexible.  sudoers allows controls for some amazing things beyond the bonehead "give me root" stuff.  The sudoers manpage is a work of art. 

Techniques used to backup Windows aren't usually the same as those used to backup Unix systems. When there aren't any licenses and a complete understanding of where different sorts of files are placed, it becomes very clear what stuff needs to be backed up and which things can be trivially recreated in 15-30 minutes.  My 120 day versioned backups don't actually store the OS.  I store only the things required to get the OS back to the same state.  That makes backup storage much smaller and backup times measured in seconds, not hours.

There are many things that don't work the same in Unix as people who run Windows have learned - perhaps 80% is different. All those differences take time to learn and it is a steep learning curve, as you know.

That's enough for now. Good luck.

---

### Post by TheFu on 2017-07-04
Oh ... and paths that have spaces in the name need to be quoted.
```
Exec=/home/domarius/WindowsGames/Duck Game/Duck Game Wine.sh

```should be
```
Exec="/home/domarius/WindowsGames/Duck Game/Duck Game Wine.sh"
```

I find it much easier to never allow odd characters in directories or file names.  Spaces cause issues for all shell scripts, a space is a natural delimiter.  Best to never allow spaces in filenames or directories.  Yes, you can create scripts that handle spaces, but it is a little harder.

---

### Post by domarius on 2017-07-23
I just wanted to reply quickly and thank you for your follow up.  This is a recreational venture (so I can't afford to devote too much time to it, hence the delay in my reply) but I was hoping it would be a good excuse to learn about Linux on the way and see what it's all about.  And so far I'm very impressed!  Also my backup system only takes 8 mins to restore the whole OS drive, so it's ok for now.  But I do see the value in being able to make more frequent backups by backing up smaller amounts of data.  Oh - knowing that the foundation for bash predates all the mainstream languages does go a long way to explaining its design choices :)  And I will be fleshing out my experience with Bash scripting as I go.  And going back to folders & filenames without spaces!

I only have 2 questions at the moment;

1. Could you point me to a good step by step on how to just make an Icon on the desktop that runs a script?  I'm not having any luck (as posted above).  I've followed different forum post instructions, all I get are icons that cause a "There was an error launching the application" error.

2. It'd be good to have my script re-load the default gamepad drivers that it already had loaded on system start.  The xboxdrv program unloads them and puts itself in its place.  That's great for Duck Game, but after Duck Game, when it unloads, it leaves the system without any gamepad drivers at all.  Shame it can't kindly reload them back.  They're called "kernel drivers"; any idea how I could get the script to put them back when it's done?  Currently the solution is to reboot the computer after running Duck Game :)

---

### Post by TheFu on 2017-07-23
1 - sorry. I don't work this way and don't use desktops. Make sure the permissions are set to execute? That's a guess. I don't know.
2 - lsmod, modprobe, rmmod, insmod might be helpful.

---


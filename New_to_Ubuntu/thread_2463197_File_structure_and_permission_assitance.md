---
title: "File structure and permission assitance"
date: 2021-06-06
forum: New to Ubuntu
---

### Post by zzbeakerzz on 2021-06-06
Hello!
I am in the process of trying to teach myself Linux and how to use microprocessors at the same time and am drowning a bit. I recently bought a 'Teensy 4.0" micro control and was trying to follow the instructions on their website to download theirTeensyduino software. In doing this process, I was supposed to move the downloaded file from my desktop to /etc/udev/rules.d/. While attempting to do this, I found that I did not have the correct permissions to do so. I poked around on different sites and tried to give myself permission to do this. After typing in a few commands (trying to give myself access) I found that the /etc/udev/rules.d/ file is now unreadable and has a red X on it. I believe that I typed in something like $ sudo chmod 770 /etc/udev/rules.d/. Can someone please tell me:

1. What did I do wrong to get the red x and make the file unreadble
2. Is there something that I can do to fix this?
3. How can I give myself permission to move Teensy's install file into this folder

Any help is greatly appreciated!

Thank you

---

### Post by mIk3_08 on 2021-06-06
rulles.d is a administrative folder. The folder should stay as it is as  administrative folder. I think the best way to move the file is using command  
```
sudo mv
```
as the default administrative user without  changing the administrative folder rulles.d. as an authorize root user.
1st. you cannot move the file  directly to rulles.d because again it is a administrative folder you  must have to be the "root user" administrative user to acquiring root  permissions.

1. you have to change the administrative folder to the default state which you have change the permission because changing administrate folder might take you to the uncertainty to the root admin files.
2. maybe changing the rulles.d administrative folder to the default state may fix some errors your facing with.
3.  just use the administrative user to acquiring root permissions to move  the file you need to move. again use
```
sudo mv
```  
then enter your security  password to successfully move the file from desktop to the administrative folder one.
Hope it help you then. Good Luck.

---

### Post by CatKiller on 2021-06-06
> **zzbeakerzz said:**
> In doing this process, I was supposed to move the downloaded file from my desktop to /etc/udev/rules.d/. While attempting to do this, I found that I did not have the correct permissions to do so. I poked around on different sites and tried to give myself permission to do this. After typing in a few commands (trying to give myself access) I found that the /etc/udev/rules.d/ file is now unreadable and has a red X on it. I believe that I typed in something like $ sudo chmod 770 /etc/udev/rules.d/. Can someone please tell me:

1. What did I do wrong to get the red x and make the file unreadble
2. Is there something that I can do to fix this?
3. How can I give myself permission to move Teensy's install file into this folder

The very first mistake was assuming that all Linux and Unix devs ever are idiots, and know less than you do, even though you're "trying to teach yourself Linux." The permissions that things have, they have for a reason, and brute-force changing them is entirely the wrong approach. 

As for what you've done, you've removed the execute permission which, for directories (which rules.d is), controls whether it's permissable to enter the directory. You've said that no one can enter this directory under any circumstances.

You'll want to change the permissions back to what they were before you monkeyed with them. Then you can copy the file to the directory with ```
sudo cp <name of file> <target directory/>
``` 

You can move rather than copy if you use mv rather than cp.

---

### Post by ActionParsnip on 2021-06-06
I don't suggest you go changing access to the folders outside of your user's home. You can break your system. Use sudo when you need admin access

---

### Post by The Cog on 2021-06-06
That directory should look like this:
```
~$ ls -ld /etc/udev/rules.d
drwxr-xr-x 2 root root 4096 May 12 18:47 /etc/udev/rules.d

```
and the command to put it back that way is this:
```
sudo chmod 755 /etc/udev/rules.d
```
I'm surprised that nobody else has told you this yet.

Then copy the file there again by using the sudo prefix. Copying is better than moving because then the copy will be owned by root, as most system config files should be. Simply moving the file there would leave the file as being owned by you - root copying the file makes a copy that is owned by root.
```
sudo cp filename /etc/udev/rules.d
```
They key to this is using the "sudo" prefix before using a command that needs extra permissions. Don't change the security settings on the folder, raise your own authority instead. 
sudo is rather like "run as administrator" in windows, and similarly, it needs a password. Maybe confusingly, while "run as administrator" wants the administrator's password (I think), sudo just wants you to enter your own password again to verify it's you trying to do this and not someone passing by while you're got to get a coffee. 

sudo has an inactivity timer on it so that if you use a sequence of sudo commands in quick succession, only the first use requires the password.

---

### Post by CatKiller on 2021-06-06
> **The Cog said:**
> I'm surprised that nobody else has told you this yet.
For my part, I'm typing from my phone, so I couldn't check what they were supposed to be.

---

### Post by The Cog on 2021-06-06
> For my part, I'm typing from my phone, so I couldn't check what they were supposed to be. 
Yes, that comes out as though I'm having a pop at people who replied, which was not my intent. Sorry. But these forums are normally so good at answering people's questions that I really was surprised that q2 seemed to have been missed.

---

### Post by mIk3_08 on 2021-06-06
you can also do this in moving your file
```
  sudo mv '/home/username/Desktop/file-location/filename.extension' '/home/username/file-destination/folder-destination'
```
where your: '/home/username/Desktop/file-location/filename.extension' is the file to be move from your desktop location
and: '/home/username/file-destination/folder-destination' where this is the destination of your file to the administrative folder
then enter your security password so that you can successfully move the file from desktop to the administrative folder one. Good Luck.

---

### Post by zzbeakerzz on 2021-06-06
Wow guys! This is my first post here and you guys have answered so many of my questions (plus more)!!! Thank you very much. I think that I still have to learn deeper on this whole permissions thing. But this helps clear up a lot.

---

### Post by Impavidus on 2021-06-06
Read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) -- about how we can act as the root user on Ubuntu
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) -- the basics of the permissions on UNIX-like operating systems (including Linux)
The latter article mentions access control lists. Most users will never use those.

You may also be interested in the set user ID bit and the set group ID bit. The setUID bit explains how sudo works.

Generally, when you want to perform some admin task, you use sudo to act as the root user. When you want to make some action available to non-admin users, change ownership and/or permissions to give those other users access.

---

### Post by zzbeakerzz on 2021-06-12
I think I followed everything that you guys were discussing here. I am now stuck on not being able to execute the program and it keeps saying no such file or directory. The file is on my desktop and has the proper execute permissions. Any thoughts on what is going on?

---

### Post by CatKiller on 2021-06-12
> **zzbeakerzz said:**
> Any thoughts on what is going on?
Images that aren't attached inline don't display on the mobile site, so no, not a clue.

Terminal output enclosed by CODE tags is, by far, the best way to provide information.

---

### Post by TheFu on 2021-06-12
> **zzbeakerzz said:**
> I think I followed everything that you guys were discussing here. I am now stuck on not being able to execute the program and it keeps saying no such file or directory. The file is on my desktop and has the proper execute permissions. Any thoughts on what is going on?

All Unix-like OSes use a PATH environment variable just the exact way that MS-Windows does, so there is nothing new happening.  Your Desktop isn't in the path, so if you want to run a program located there, you have 3 choices.
[LIST]
[*]Make ~/Desktop part of your PATH.
[*]Move the program to a directory that is already in the PATH.
[*]Fully specify the exact location of the program to be run.
[/LIST]

The first option isn't normally done. Typically, a Desktop is for data files and directories, not programs.  Personal programs/script are often placed into ~/bin/ - which is the same as $HOME/bin/.  This directory isn't created automatically, but you can make it and add it to your PATH in your startup files.

To check the value of the PATH, use **echo $PATH**.  This is exactly the same as on Windows, BTW. Nothing new.

The 2nd option is to move the program to a directory already in your PATH.  For something downloaded, NOT installed using the normal Ubuntu package manager, I would put into my ~/bin/ directory if it was only to be used by my userid or into /usr/local/bin/ if it was to be shared by all users on the system.  There is a "Linux File System Heirachy Standards Document" which spells out clearly what goes where on a Unix/Linux file system. All the popular distros follow this document. The wikipedia article on it has a table, which is 99% all we need to read.

The last option is to specify the exact location of the program to be run.
"program" isn't an exact location.
"./program" is or
"~/Desktop/program" or
"$HOME/Desktop/program" or 
"/home/thefu/Desktop/program"
All of those are either relative or absolute paths to programs.  The first is relative and depends on the PWD/CWD value.

You can learn all the basic stuff if seems aren't on the top of your head here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Trying to learn Linux on a microcontroller is much harder than trying to learn it on a normal desktop Linux install. The learning curve will be very steep.

File and directory permissions are core to all Unix security. Spend the 45 minutes learning that stuff now to avoid hours, days, weeks, months of frustration. There isn't any shortcut.  Just learn it now, ASAP.  Create 3 new userids and 2 groupids.  Open 3 terminals, login to each terminal with one of those new userids and create a new directory - say /tmp/foo.  cd all the userid terminals into that directory and try creating files using all three. Next work through every possible combination of permissions from 000 ---> 777 on the files and some subdirectories for each of the userids. Learn to read the permissions using ls -al.  Understand that the parent directory permissions determine access to files inside that directory. Learn about groups and what being a member of the same group can and cannot accomplish.
Doing all of this should take about 45 minutes, and that includes 15 minutes working through a file permissions tutorial first.
After about 30 minutes total, the ah-ha moment should happen, then spend the remaining 15 minutes solidifying the new knowledge, testing the limitations.  Use mkdir touch chmod chgrp chown commands.   When you fully understand the power of chmod g+s, only then should you stop.

---

### Post by Impavidus on 2021-06-13
In two of your commands in the screenshot you added a random sudo. Don't. sudo occasionally helps against "permission denied" errors, not against "no such file or directory" errors. And in any case, only use sudo when you know why you need it, not simply whenever it doesn't work without.

In your first command, you began the command with ./. This means the path is to be interpreted relative to your current directory, which is your home directory. But the path you used is relative to the Desktop directory, so you should have gone to that directory first.

In the second and third command, you write the full path, with a leading dot. The leading dot (or anything not a slash or something shorthand for something starting with a slash) indicated this is again a relative path, but this one is relative to the root directory. You should have gone to the root directory first, or simply omit the dot.

Only in your final command you get the path right, but ldd doesn't execute the file. It tells you about dynamically linked libraries, which this executable doesn't have.

So, think about absolute paths, relative paths and your current directory.

---

### Post by TheFu on 2021-06-13
And I couldn't read the image. Bad eyesight. Please post text for text output, wrapped in code tags. Make it easy for us to help.

---

### Post by zzbeakerzz on 2021-06-26
Hey guys,
I have messed around with what was stated above (and am still struggling). Please see below for a few of the lines I have tried.

nathan@thinkpad-t440p:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
nathan@thinkpad-t440p:~$ sudo mv '/usr/local/bin/TeensyduinoInstall.linux64' '/usr/bin'
nathan@thinkpad-t440p:~$ ./TeensyduinoInstall.linux64
bash: ./TeensyduinoInstall.linux64: No such file or directory
nathan@thinkpad-t440p:~$ sudo mv '/usr/bin/TeensyduinoInstall.linux64' '/usr/local/bin'
nathan@thinkpad-t440p:~$ ./TeensyduinoInstall.linux64
bash: ./TeensyduinoInstall.linux64: No such file or directory

Not sure what is going on now. Do you guys have an idea?

---

### Post by CatKiller on 2021-06-26
> **zzbeakerzz said:**
> bash: ./TeensyduinoInstall.linux64: No such file or directory

Not sure what is going on now.
"." means "this directory," so "./TeensyduinoInstall.linux64" means "run the file called TeensyduinoInstall.linux64 in this directory." But that file isn't in this directory, because you've moved it to some other directory.

---

### Post by TheFu on 2021-06-26
Seems the understanding of absolute and relative paths in poor.

At any prompt, type "pwd" to see what the current directory is if you don't understand how to read the prompt provided.

I'll take a guess:
```
nathan@thinkpad-t440p:~$
```
There is a method to that prompt.

"nathan" is your current userid.  Linux is a multi-user system, so there could be 60,000 different userids on a system.  Chances are that a normal home Linux system will have less than 100.  How many will depend on the number of programs installed and if those programs like to run under a different userid.  Multi-user. Always remember that.   My 20.04 desktop system has 54 userids, BTW.  Also, usernames should always be lower-case and begin with an ASCII character, no numbers.  There is probably a limit to how long a username can be. I just don't know it off the top of my head.  For security reasons I want my real usename to be short, but random enough.  "thefu482", for example.  This is to prevent remote connections from being able to guess the login username.  When I post here, I'll post with "thefu" as my username to simplify things.

"@thinkbap-t440p" says that the hostname is thinkbap-t440p.

":" is just a separator like the @, but those are placed in specific locations to make ssh, scp, rsync and some other programs easier to use by select/paste (We don't need copy/paste - select/paste is enough).

"~" is a shortcut for the current useids $HOME directory.  **echo $HOME** will show the value. Every userid has a HOME.

And lastly, "$" says this userid is a normal user, not root.  To show a root login, convention is to use the "#" prompt.

So, taken all together, nathan@thinkpad-t440p:~$ says
nathan on thinkpad-t440p in directory ~    Pretty slick.

What if the prompt where
nathan@thinkpad-t440p:/etc$
That tells use that the pwd is /etc/, but the user and hostname hasn't changed.

Let me grab a few prompts from my open terminals:
```
thefu@hadar:~/V/DONE$
thefu@regulus:~$
thefu@istar:/d/D1/M$
thefu@romulus:/tmp$
```

See how the information in each might be helpful?
Inside romulus:/tmp/ there was a file that I wanted in hadar:/tmp/ .  I was on hadar, so I used scp to pull it over. Here was the command:
```
$ scp romulus:/tmp/blog44-2004.xml  /tmp/
```
Because the usernames were the same on both systems, I didn't need to include them.  Don't worry if this seems complex.  The point is that those prompts have a specific reason for being the way they are, but we can completely customize them as much as we like. They are just environment variables - PS1, PS2, PS3, and PS4 are used by bash to setup the prompt in a terminal.

Does that begin to make a little more sense?

Moving on.

$ sudo mv '/usr/local/bin/TeensyduinoInstall.linux64' '/usr/bin'

Says to move a file from /usr/local/bin ---> /usr/bin/.   That is probably a bad idea, since both of those directories are already in your PATH. Further, /usr/bin/ programs should come only from APT package installations, not from stuff we download off the internet.  /usr/local/bin/ is a good location for that file, methinks.  Why move it?

```
$ ./TeensyduinoInstall.linux64
```
says to run the program/script in the PWD.  If you type pwd, does that program exist in that directory?  I bet it doesn't, which why the error _bash: ./TeensyduinoInstall.linux64: No such file or directory_ is shown.  Try it without the ./ , see if that helps. If the program is:
a) in a directory in the PATH
and
b) has execute permissions for the current userid to have execute rights, then
the program will attempt to run.

The key thing to learn is to read the output from things that don't do what you want.  Those error messages are usually clear, once you see them a few times.

**No such file or directory** says where ever you tried to run the program from, it isn't there. Figure out where it is, then run it from the correct location.  It could be that the program isn't on the system. Usually, that would mean it isn't installed or it was incorrectly installed or it was installed to somewhere NOT in the PATH.

---


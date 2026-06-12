---
title: "HOWTO: Startup/Shutdown Sounds in Openbox"
date: 2008-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by nabl on 2008-04-10
[FONT=Verdana]In this tutorial, I will show you how to add startup and shutdown sounds with Openbox, a light-weight window manager. In theory, this should work with any window manager that uses a startup script (or, if you use the[/FONT][FONT=Verdana]* startx*[/FONT][FONT=Verdana] command, .xinitrc could be used for the same effect); however, I will be focusing on Openbox, so you will have to adapt these instructions for use with other window managers.[/FONT]
    
    [FONT=Verdana]We'll start with a quick background story: I was in a "tweaking" mood today, and I figured I'd try to set up some startup and shutdown noises for use with Openbox. After a few minutes of messing around, I got it working. I searched to see if there were any tutorials like this, and since there weren't, I figured I would share my knowledge--that is the point of this board, right? :D This is my first tutorial here, as well as one of my few posts, so I hope it helps.[/FONT]
    
    [LEFT][FONT=Verdana]Now that we have that out of the way, let's get started. :)[/FONT][/LEFT]
    
**-----------------------------------------------**
    
    [LEFT][FONT=Verdana]**_Step 1: Installing the necessary application(s)._**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]First off, we will be using a commandline program called [/FONT][FONT=Verdana]*play*[/FONT][FONT=Verdana]. It is part of the [/FONT][FONT=Verdana]*sox*[/FONT][FONT=Verdana] package from the universe repository, so let's install that first (you likely have most of its dependancies already).[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]```
sudo apt-get install sox
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]If you'd like, you can [/FONT][FONT=Verdana]*cd*[/FONT][FONT=Verdana] to a directory with music in it and type [/FONT][FONT=Verdana]*play *[/FONT][FONT=Verdana]name-of-sound-file.extension to test that it is working. If you don't have any files to try it on, you can do this later after downloading your desired sound files in step 3.[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]In addition to that, I will be working with obmenu, a program for editing Openbox's menu from a GUI; howevr, it will work just as well to edit the menu by hand. I won't go into detail about installing obmenu (it's not in the Gutsy repositories), as I assume you already have a preferred method of editing your menu. If you would like to install it, there are threads floating around about it (it's not hard as long as you have the dependencies).[/FONT][/LEFT]
    
    
    [LEFT][FONT=Verdana]**_Step 2: Setting up shutdown privileges._**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]For this section, I will be adapting a section from a great guide written by urukrama [here]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/"). Adding such a message is outside the scope of this guide, so we'll just use the part we need. ;) We're going to be running a shutdown command from a script, so we need to have it set up to work without any interaction--in this case, that means removing the need for a password for the shutdown command.[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]To do this, type in the following command into the terminal:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
sudo visudo
```[/FONT][/LEFT]
    [LEFT][FONT=Verdana]This will open up the sudoers file, which is used to specifiy user permissions for actions that require root priveleges. For those of you unfamiliar with Vim (I'm with you :P), just press [/FONT][FONT=Verdana]*i*[/FONT][FONT=Verdana] on your keyboard to enter interactive mode, which allows you to edit the file. Then, enter the following line at the end of the file:[/FONT][/LEFT]
    ```
[FONT=Verdana]%wheel     ALL=NOPASSWD:/sbin/shutdown[/FONT]
```    [LEFT][FONT=Verdana]Then press escape to exit interactive mode. Lastly, type in [/FONT][FONT=Verdana]*:wq*[/FONT][FONT=Verdana] followed by pressing enter to save and exit. Now you can use the [/FONT][FONT=Verdana]*sudo shutdown*[/FONT][FONT=Verdana] command without entering a password.[/FONT][/LEFT]
    
    
    [LEFT][FONT=Verdana]**_Step 3: Getting the desired sound files._**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Now we come to the fun part of the guide--finding the sounds that we want. :)[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]There are plenty of startup and shutdown noises floating around the web; I went to gnome- and kde-look to check out theirs (the same are available at both sites). [Here's a link]("http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=25") to the System Sounds section on gnome-look. You can look through and download the ones that interest you; once you have listened to a few and found one that you like, go on. Just for reference, I chose the [Dream]("http://gnome-look.org/content/show.php/Dream?content=75398") pack. It fits very nicely with my current setup and theme.[/FONT][/LEFT]
    
    
    [LEFT][FONT=Verdana]**_Step 4: Setting up the shutdown/startup scripts._**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]If you haven't already (in the last step), extract the sound files from the package that they downloaded in. Then, look through the files and find the startup and shutdown noises. For me, they were titled [/FONT][FONT=Verdana]*Dream Intro.ogg*[/FONT][FONT=Verdana] and [/FONT][FONT=Verdana]*shutdown.ogg*[/FONT][FONT=Verdana], respectively. Move these files into their own folder. I chose ~/.startup--on my Arch install, it was empty. You may want to put it into a different folder/sub-folder, preferably in your home folder. You can now remove all the other sound files--hypothetically speaking, it probably wouldn't be too hard to get other sounds (such as minimize, maximize, etc., if provided in the sounds package you chose) working with Openbox, but that is beyond the scope of this tutorial. Now, go to the folder in which you placed the startup and shutdown noises. For simplicity's sake, we're going to place the scripts in this same folder.[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]We're going to be making two scripts here--one for reboot and one for shutdown. Open up your text editor of choice here and enter the following line (replacing the "/path/to/file.extension" with the path to your shutdown sound):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
play /path/to/file.extension && sudo shutdown -r now
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]For me, it looked like this:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
play ~/.startup/shutdown.ogg && sudo shutdown -r now
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]What this does is play the sound file specified and, once that is done, moves on to the reboot process (that's what && does). Save this as reboot.sh. Now make a new file, this time for the actual shutdown. It will be the same as the first except the shutdown command with now be [/FONT][FONT=Verdana]*sudo shutdown -h now*[/FONT][FONT=Verdana]. Here's what mine looks like:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
play ~/.startup/shutdown.ogg && sudo shutdown -h now
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]Save that one as shutdown.sh. At this point, we have completed the scripts for both shutdown commands. Next, open up your Openbox autostart script (should be in /home/<user>/.config/openbox/autostart.sh, where <user> is your username) with the text editor of your choice. You probably already have a few different things in here; if not, it doesn't really matter. Just add the following line to your autostart file (as you can see, I used quotes around this one because this file had a space in its name--you'll want to do the same):[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
play "/home/<user>/.startup/Dream Intro.ogg"&
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]Make sure you keep the ampersand ([/FONT][FONT=Verdana]*&)*[/FONT][FONT=Verdana] in tact; otherwise, the script will wait until the sound is done playing before completing the rest of the processes. I recommend that you place the sound file at the beginning of the script so that it starts first--the way I have it set up, everything is ready to go by the time the login sound ends (sooner, actually). Now that we've come this far, we're almost done.[/FONT][/LEFT]
    
    
    [LEFT][FONT=Verdana]**_Step 5: Adding the shutdown options to the Openbox menu._**[/FONT][/LEFT]
    [LEFT][FONT=Verdana]At this point, the login sound will be working; however, we still need to set up the shutdown sounds. To do this, we will add a section to the Openbox menu that runs the two scripts we made in the last step.[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]Either open up obmenu or use your preferred text editor and open up menu.xml (should be in ~/.config/openbox/menu.xml). As I said, we will be adding two items: one for rebooting and another for shutting down. In obmenu, you can add a new menu wherever you want (I chose the bottom of the menu) and name it Power (or whatever else you'd like). The first we'll add is named Restart. For the execute line, add the following:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
bash /path/to/reboot.sh
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]For me, this path is ~/.startup/reboot.sh. As for the second, name it Shut Down and for the execute command put the following:[/FONT][/LEFT]
    [LEFT][FONT=Verdana]```
bash /path/to/shutdown.sh
```[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]Again, for me this is ~/.startup/shutdown.sh. Here is what the section in my obmenu looks like:[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana][IMG]http://img132.imageshack.us/img132/6171/obmenugj6.png[/IMG][/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]As for the pure XML, here it is (I replaced my name with [/FONT][FONT=Verdana]*<user> ;)*[/FONT][FONT=Verdana]):[/FONT][/LEFT]
                                        [FONT=Verdana]```

<item label="Restart">[/FONT]
[LEFT][FONT=Verdana] <action name="Execute">[/FONT]
[FONT=Verdana]   <execute>bash /home/<user>/.startup/reboot.sh</execute>[/FONT]
 [FONT=Verdana]</action>[/FONT]
[FONT=Verdana]</item>[/FONT]
[FONT=Verdana]<item label="Shut Down">[/FONT]
 [FONT=Verdana]<action name="Execute">[/FONT]
[FONT=Verdana]   <execute>bash /home/<user>/.startup/shutdown.sh</execute>[/FONT]
 [FONT=Verdana]</action>[/FONT]
[FONT=Verdana]</item>[/FONT][/LEFT]

```[LEFT]
      
[FONT=Verdana]With obmenu, just save it and your menu will be refreshed. When hand-editing the menu.xml file, you have to remember to [/FONT][FONT=Verdana]*Reconfigure Openbox*[/FONT][FONT=Verdana] (it will be in your menu unless you've removed it).[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]**-----------------------------------------------------------------------------**[/FONT][/LEFT]
    
    [LEFT][FONT=Verdana]And with that, you should have working startup and shutdown sounds. :) You can test it by right clicking on your desktop and selecting one of your new shutdown options. You should have a sound play followed by the normal shutdown routine. Then when your computer starts back up, you will have a pleasant noise after logging on. :)

I hope that helped you! Please point out any errors that you see, and I'll correct them as soon as possible. Also, I'd like to add a FAQ for common problems that may occur; if you could help with that (even if it's by asking a question yourself), please do.
[/FONT][/LEFT]

---

### Post by nabl on 2008-04-11
I hate to bump, but... only 21 views? This needs to be on the first page for at least a little while (it was on the second page by the time it was approved, I think).

EDIT: This post will also be used for the FAQ once I type it up. ;)

---

### Post by atlas95 on 2008-11-19
Thanks man !
This was what i search ... ;)

---

### Post by matt.rebo. on 2010-10-14
thanks nabl this thread helped me a lot! i had a few issues though where reboot worked but shutdown would break and vice versa, so i wanted to add my variation incase it helps anyone else...

first up gave my user "rebo" permission to shutdown without needing a password full stop, editing visudo with

```
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/halt, /sbin/reboot

# Rebo shutdown without passwords
rebo ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS

(replacing rebo with your username...)
```

with that out the way anything in the 1 - scripts and 2 - menu entries in obmenu worked fine

```
reboot.sh
1 - play ~/.startup/shutdown.ogg && sudo reboot now
2 - bash ~/.startup/reboot.sh
```

```
shutdown.sh
1 - play ~/.startup/shutdown.ogg && sudo shutdown -hP 0
2 - bash ~/.startup/shutdown.sh
```

thanks again for the inspiration nabl.

---


---
title: "How to get './flashplayer' command to work?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by steve.klebanoff on 2008-08-12
I'm trying to get my flex builder debug working the way I'd like...and I need to have the command './flashplayer' open up /home/steve/flex/flash_player_9_linux_dev/standalone/debugger/flashplayer

In the installer I believe it mentioned editing my .bashrc file to get this to work, but i'm not sure how to do this.  Any insight? 

Thanks!

---

### Post by gjoellee on 2008-08-12
.

---

### Post by Rog-Mahal on 2008-08-12
Have you tried going to the directory and typing 
```
sh ./flashplayer
```?

Are there any errors that come up when you try to run it?

---

### Post by steve.klebanoff on 2008-08-12
A little more info on the situation:

When I tell the flex debugger to launch a .swf file after building so i can debug & test, i get the error > Flex Builder cannot load the required version of Flash Player. You might need to install Flash Player 9 or reinstall Flex Builder. Do you want to try to run your application with the current version?

When I click yes I get the error > File not found: flashplayer. 

In order to get debug working, I change flex builder to load a .HTML file to debug (which never really opens)...then I manually open /home/steve/flex/flash_player_9_linux_dev/standalone/debugger/flashplayer and manually open the debugger's .swf file and it works.  

I'm just looking to have this process work automatically...so maybe I should just figure out where the flexbuilder is looking for 'flashplayer' and to copy my debugger version there.  Or...as I was trying to get to in the first post, to get ubuntu to recognize /flex/flash_player_9_linux_dev/standalone/debugger/flashplayer as the default.  At the moment when I open up a .swf file in nautilus it tries to open it in Totem...

Any more ideas?

---

### Post by steve.klebanoff on 2008-08-15
UPDATE: I ended up just fighting with the firefox flash debugger plug-in for a while and got that to work, so I can just debug from there, and not worry about why eclipse is not finding my standalone version of flash.

---

### Post by guleesh on 2008-10-21
I found this thread through a search.
I too had this error message.

The solution seems to be making sure fdb can find the flashplayer

After unpacking FP10 debug player from here 
[http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)

there are 2 ways for enabling fdb to find flashplayer

Unpack the player somewhere and add it to you system PATH.

Or perhaps simpler option (the one I did)
just copy the flashplayer to the bin folder where fdb lives.

---

### Post by bja888 on 2009-01-09
I had this same problem. Don't over think it. *fdb* is just running the *flashplayer* command.

Download the linux debug player...
[http://www.adobe.com/support/flashplayer/downloads.html](http://www.adobe.com/support/flashplayer/downloads.html)

Move the standalone debugger to /usr/bin
(at flash_player_10_linux_dev/standalone/debugger)

Or create a symbolic link like I did.

*sudo ln -s ~/Desktop/flash_player_10_linux_dev/standalone/debugger/flashplayer /usr/bin/flashplayer*

---


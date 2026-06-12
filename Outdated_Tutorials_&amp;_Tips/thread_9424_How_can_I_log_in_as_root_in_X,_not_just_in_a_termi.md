---
title: "How can I log in as root in X, not just in a terminal?"
date: 2004-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Michael Oates on 2004-12-28
Firstly I am a newbie and I want to be able to use the graphical user interface as root, not just use commands in a terminal, which I can do from reading these forums.

I am trying to edit XF86Config-4 to try and get the screen resolution to something other then 640x480 which is terrible. I can't edit it with the text editor without being logged in as root.

I have tried [FONT=Arial]'sudo passwd root'[/FONT] put in the password, then logged out and tried to log in again, but it won't let me in, I have to use my normal user name and password to get back in. 

I also tried going through [FONT=Arial]'dpkg-reconfigure xserver-xfree86'[/FONT] but this did not help.

I am also trying to install drivers for the motherboard a ASUS A7V400-MX which has an onboard graphics set VIA/S3G CLE266 and I can't get the drivers to install. If anyone can tell me that this MB is not suitable for Linux, please say before I buy any more!

The odd thing, is that this is the second identical PC I have put together for ubuntu, one has lots of screen resolutions to choose from, and one does not. I did notice that during the install, the one I am having problems with did not come up with any options for screen resolutions. I have no idea why.

Any help appreciated. And please spell it out clearly so I can type in any commands so they work... assume I know nothing.   :confused: 

Mike

---

### Post by rbran100 on 2004-12-28
There is no default root account for UbuntU and there is little reason why you would need one. just put sudo in front of any command you would like to run as root.

IE.

sudo gedit

sudo vi /etc/X11/XF86config-4

If you must have a root user then you should create a seperate user and give it permissions to all directories.

---

### Post by rbran100 on 2004-12-28
Didn't know if that was clear enough after reading it:

"vi" is a terminal based text editor and gedit is a GUI one.

vi will be the best in this case as you will be in and out of a misconfigured X

use "sudo vi FILENAME"

in the file press "i" to turn editing ond off 
when you get done editing turn it off and type
":w" to save and
":q" to quit

Does that make sense?  It is critical that you learn how to use vi it has saved me so much time over the years.

---

### Post by rbrimhall on 2004-12-28
sudo pico filename

vim is horrid until you learn shift+: wq (that ends the edit session, writes, then quits)

---

### Post by rbran100 on 2004-12-28
No VIM is better......it is the best!     =D>

---

### Post by Michael Oates on 2004-12-29
[QUOTE=rbran100]Didn't know if that was clear enough after reading it:

"vi" is a terminal based text editor and gedit is a GUI one.

vi will be the best in this case as you will be in and out of a misconfigured X

use "sudo vi FILENAME"

in the file press "i" to turn editing ond off 
when you get done editing turn it off and type
":w" to save and
":q" to quit

Does that make sense?  It is critical that you learn how to use vi it has saved me so much time over the years.[/QUOTE]

Firstly, my appologies for posting this in the wrong section. I will be more careful in future.

Secondly, thanks for the help on how to edit a file as root.

Thirdly, I have sorted out my problems and I am now replying to this message from my ubuntu machine in glorious high resolution and flicker free thanks to a thread I found: [via km400 video supported?](http://www.ubuntuforums.org/showthread.php?t=3700&highlight=km400) Using ubuntu or any other OS is impossible at 640x480 when most of the dialog boxes go off the bottom of the screen!! I can now start to learn how to use it 

I shall take more time searching the forums before posting in future.

Thank you,

Mike

---


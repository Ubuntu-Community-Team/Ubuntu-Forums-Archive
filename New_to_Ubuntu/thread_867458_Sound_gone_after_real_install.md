---
title: "Sound gone after real install"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by whrd on 2008-07-22
I really messed up. 

Everything was going fine, until I went to the bbc site and was told that real.com had my answers. 

I downloaded it, but the instructions were vague, so I just slapped it into

/[enduser]/real

Firefox picked it up, and all the sound -- youtube, bbc, all of it, went dead. Hmmm. real showed up on the Applications - Sound & Video menu, but when I clicked on it, it said it couldn't find the executable. 

Where should I put it? Is there a quick troubleshooting tip, or is this rtfm time?

==whrd

---

### Post by Het Irv on 2008-07-22
Do you have a link to the instructions that you followed?  I havn't installed Real Player before so I am not sure.

Oh, and these are great forums, not many people with tell you rtfm without a link to the proper manual.

---

### Post by whrd on 2008-07-23
thanks for replying so quidkly. The link I found was:


[http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8902005&pageregion=A1](http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8902005&pageregion=A1)

I ran it in the terminal window, and it seemed to go okay. After I installed the realplayer module and tried 

[http://www.bbc.co.uk/bbc7/listenagain/sunday/](http://www.bbc.co.uk/bbc7/listenagain/sunday/)

and clicked on an Evelyn Waugh title, which usually pops real player. 

Now I just went back and did that, and the Totem Movie player jumped up; wrong codec, but the time is counting, as though it's playing. 

I'm thinking: kill the totem movie player (using Add or Remove), restart firefox, try again --? 

Yes, I am a seven-year-old with a hammer. 

any observations? Thanks for the help.

---

### Post by Het Irv on 2008-07-23
> **whrd said:**
> 
Yes, I am a seven-year-old with a hammer. 

any observations? Thanks for the help.

Observations?  Yeah, Two.
Seven-year-olds are scary enough without the hammer.
And those instructions suck.

You should be fine slapping the .bin in your home folder, but that is just the install file, not the program itself.  You can change the permissions by right clicking on the file and going to the third tab "Permissions" and making sure the check box is checked next to "Allow executing file as program".  You should be able to simply double click on the bin file to run it.

If you did install it try going to System -> Preferences -> Preferred Applications
Under the multimedia tab, can you change the default to Real Player?

---

### Post by whrd on 2008-07-23
Okay, I think I'm getting close to the problem. 

Another set of instructions specified that when I go the .bin to execute using su and chmod, I should send the files off to /opt/real/RealPlayer, which I did. 

Still nothing, but I noticed that the /opt/real/RealPlayer/plugin dir has a whole bunch of .so files, which I think should go to some firefox plugin dir. Is that /usr/lib/firefox-addons/plugins? That directory's empty, so I'm a little reluctant... 

Per your instructions I ran the Preferences > Preferred Applications > Multimedia tab, and sure enough, it's not there. 

Thanks. 

==Will

---

### Post by Het Irv on 2008-07-23
When you run the install, try pointing it at your /home, that is where I usually install stuff.  I am not sure about the Firefox plugin.

---

### Post by whrd on 2008-07-23
Thank you for your help, Het. 

Hmmmmm.

All plugin directories full of .so files, no sound. reloaded into /home, no sound. 
The preferences > multimedia never got around to finding RealPlayer. I even tried using "custom" to point to it. no sound. The Totem player, disabled or enabled, pops up, but doesn't play the .ram files. 

Interesting. When I actually open RealPlayer and open an mp3 file and play it, the time is reeled off, but the slider next to the speaker is blank. So  I'm thinking that the basic sound stuff is off.

I went to Administration > Hardware Testing, which sent me off to Launchpad, which told me of all the edgy toys I could load. Not helpful. 

Het, I really appreciate all the help you've given me, but I'm just not seeing a basic way I can approach this. I'm thinking: ground up. Test the basic drivers; reset the sound; troubleshoot piece by piece. But after this, and after talking to a couple of my unix-flavored friends, I'm realizing that when things break in linux, the reasons are often arcane and hard to reach. 

Maybe I'll reload the OS later today. Dunno. Back to Win 2k right now; I have to get some VOIP  going, get some work done. 

I'll keep the partition, work on it when I have time. . . .

Again, Het, thank you very, very much for your help in this.  Just happens. 

Regards, 

==Will

---

### Post by whrd on 2008-07-23
Actually, I just went through the Add/Remove section, and it refuses to find realplay, even when I point directly to it. 

Can you tell me exactly which directory applications are placed? that might help. 

thanks, 

==Will

Fixed it, sort of. Delparted the system, started over. Installed Adobe, fine. installed RealPlayer, then went to Applications, etc, RealPlayer 11, okay. Go to bbc, the Totem player keeps trying to tropm me, but I just copy the link to the RealPlayer window. I think the key is ignoring the totem player (which kicks in even if you specify real as the player. Well, it's working

thanks. Off we go.

---


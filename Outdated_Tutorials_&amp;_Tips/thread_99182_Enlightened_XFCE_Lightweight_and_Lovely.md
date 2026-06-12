---
title: "Enlightened XFCE: Lightweight and Lovely"
date: 2005-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Iandefor on 2005-12-05
After reading a poofyhairguy's [Enlightened GNOME howto]("http://www.ubuntuforums.org/showthread.php?t=54476&"), I began to ponder the possibility of applying such a method to XFCE. It took my contributions to [this thread]("http://www.ubuntuforums.org/showthread.php?t=97742") to get me experimenting, and I found, after much toil, that the it is most certainly possible. But the method used is radically different than what is in Enlightened GNOME. It took me a while to get it up and running. To ease the troubles of anyone else trying this, I've documented my steps and here is a howto.

NOTE: I'm pretty bad at explaining things. Please, please give me constructive criticism if this is too poorly written to understand- I want this to be at least readable!


** I. Getting Enlightenment**

This is the most basic part, of course. If you don't have enlightenment installed, you have two options as of the time of this writing: DR16 and E17. Simply put, DR16 is more lightweight and is stable. E17 is less stable, a little heavier, but it looks better. I went with DR16 because E17 consistently crashed. This HOWTO uses DR16, but I see no reason why it shouldn't work with E17 as well. If you want E17, may I suggest [Aboe's Howto]("http://www.ubuntuforums.org/showthread.php?t=79155&")? It installed E17 without a hitch for me. To get enlightenment DR16, open up Synaptic, search for enlightenment, and mark it for installation along with any other packages you might want for it.

** II. Setting Enlightenment as the WM for XFCE4**

This was the part of getting it working that gave me the greatest difficulty. In an environment other than XFCE, open up a terminal and type in

```
rm ~/.cache/sessions/*
``` 

Which will wipe all your session data. type in ```
cp /etc/xdg/xfce4/xinitrc ~/.config/xfce4/xinitrc
``` This isn't really necessary, but it moves xinitrc to a more convenient place for XFCE. Now, log out, and log in to an xfce4 session. As soon as it's finished logging in, kill xfwm4 (using whatever means convenient), log out, and save session; this generates a session file we can then modify.
Log back into the non-XFCE environment you were just in. open up the file ~/.cache/sessions which should be named something like xfce4-session-[hostname]:0. Open the file up, and you should see something like this:
```

[Session: Default]
Client0_ClientId=10af783ad2000113376999500000128550001
Client0_Hostname=unix/brownie
Client0_CloneCommand=xfce4-panel,--display,:0.0
Client0_CurrentDirectory=/home/ian
Client0_Priority=40
Client0_Program=xfce4-panel
Client0_RestartCommand=xfce4-panel,--display,:0.0,--sm-client-id,10af783ad2000113376999500000128550001
Client0_UserId=ian

Client1_ClientId=10af783ad2000113376999500000128550002
Client1_Hostname=unix/brownie
Client1_CloneCommand=xftaskbar4,--display,:0.0
Client1_CurrentDirectory=/home/ian
Client1_Priority=30
Client1_Program=xftaskbar4
Client1_RestartCommand=xftaskbar4,--display,:0.0,--sm-client-id,10af783ad2000113376999500000128550002
Client1_UserId=ian

Client2_ClientId=10af783ad2000113377000500000128550003
Client2_Hostname=unix/brownie
Client2_CloneCommand=xfdesktop,--display,:0.0
Client2_CurrentDirectory=/home/ian
Client2_Priority=35
Client2_Program=xfdesktop
Client2_RestartCommand=xfdesktop,--display,:0.0,--sm-client-id,10af783ad2000113377000500000128550003
Client2_UserId=ian

Count=3
LegacyCount=0
Screen0_ActiveWorkspace=0
LastAccess=1133770022

``` 
Obviously, your file doesn't have to match. Just has to look like that.
Now, what you want to do is copy and paste the last big block of text and paste it right after itself, so it looks like:

```

[Session: Default]
Client0_ClientId=10af783ad2000113376999500000128550001
Client0_Hostname=unix/brownie
Client0_CloneCommand=xfce4-panel,--display,:0.0
Client0_CurrentDirectory=/home/ian
Client0_Priority=40
Client0_Program=xfce4-panel
Client0_RestartCommand=xfce4-panel,--display,:0.0,--sm-client-id,10af783ad2000113376999500000128550001
Client0_UserId=ian

Client1_ClientId=10af783ad2000113376999500000128550002
Client1_Hostname=unix/brownie
Client1_CloneCommand=xftaskbar4,--display,:0.0
Client1_CurrentDirectory=/home/ian
Client1_Priority=30
Client1_Program=xftaskbar4
Client1_RestartCommand=xftaskbar4,--display,:0.0,--sm-client-id,10af783ad2000113376999500000128550002
Client1_UserId=ian

Client2_ClientId=10af783ad2000113377000500000128550003
Client2_Hostname=unix/brownie
Client2_CloneCommand=xfdesktop,--display,:0.0
Client2_CurrentDirectory=/home/ian
Client2_Priority=35
Client2_Program=xfdesktop
Client2_RestartCommand=xfdesktop,--display,:0.0,--sm-client-id,10af783ad2000113377000500000128550003
Client2_UserId=ian

Client2_ClientId=10af783ad2000113377000500000128550003
Client2_Hostname=unix/brownie
Client2_CloneCommand=xfdesktop,--display,:0.0
Client2_CurrentDirectory=/home/ian
Client2_Priority=35
Client2_Program=xfdesktop
Client2_RestartCommand=xfdesktop,--display,:0.0,--sm-client-id,10af783ad2000113377000500000128550003
Client2_UserId=ian

Count=3
LegacyCount=0
Screen0_ActiveWorkspace=0
LastAccess=1133770022

``` 

In the block of text you just copied and pasted, change all instances of Client2 to Client3; then, make the value of Client3_CloneCommand=enlightenment, Client3_Program=enlightenment, --display,0:0 and Client3_RestartCommand=Client2_RestartCommand=enlightenment,--display,:0.0,--sm-client-id,[Whatever Client3_ID is] . I understand that that looks pretty confusing, so here are the changes I made to that copied and pasted block of text. Compare to the original block:

```

Client3_ClientId=10af783ad2000113377000500000128550003
Client3_Hostname=unix/brownie
Client3_CloneCommand=enlightenment,--display,:0.0
Client3_CurrentDirectory=/home/ian
Client3_Priority=35
Client3_Program=enlightenment
Client3_RestartCommand=enlightenment,--display,:0.0,--sm-client-id,10af783ad2000113377000500000128550003
Client3_UserId=ian
``` 

To finish it all, change the value of count to the appropriate number (Whatever it was, add one to it). Save, logout, and log back in. Enjoy your newly enlightened XFCE! As a final note, thanks to wushumofo, mhancoc7, and karma 23, who all got me started on this mad quest of mine.

---


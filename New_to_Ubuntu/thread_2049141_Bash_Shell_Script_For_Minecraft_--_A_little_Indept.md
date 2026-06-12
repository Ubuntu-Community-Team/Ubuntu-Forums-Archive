---
title: "Bash Shell Script For Minecraft -- A little Indepth Understanding Help?"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Invectus on 2012-08-28
[SIZE=4]Hey, I'd really like to get some help understanding what exactly it is that this script is informing me, and if I can improve it all, based upon my system specs.

(Shebang, I know this already as the shell it's executing with?) 

#!/bin/bash

(Comments)

#Minecraft launcher
#This is here to solve issues with key input in linux systems&#12288;
#Kill the ibus daemon
killall ibus-daemon

(I get this part, it's killing the ibus-daemon processes)

#Launch minecraft

(No duh :P)

java -Xmx1024M -Xms512M -cp $HOME/bin/java/minecraft.jar net.minecraft.LauncherFrame &
MINECRAFT_PID=$!

(Mkay, the first part up until after -cp, I know nothing about. The directory where my 
Minecraft.jar is instaled, the net.minecraft.LauncherFrame  is obviously the launcher, and they're being launched in the background by the (&). How does the Minecraft PID get set by just adding the =$ to the end?)

sleep 1

(Why is it that with the 1 there and no time like s, m, h, [seconds minutes and hours] behind it, that it instead launches minecraft without an issue?)

#Then wait for minecraft to finish before relaunching ibus.
ibus-daemon -d
wait $MINECRAFT_PID

(What I get here is that ibus-daemon [For Japanese input] gets started up again, and then the "wait" line with $Minecraft_pid indicates that it's waiting for Minecraft to end. I'm really wondering how this part works out.)

I have a 32-bit system, with 3 gigs of ram, so I'm thinking that maybe the reason why minecraft lags so hard sometimes is because of the "limits" or "parameters" as stated in the "java" line. 

Can someone help me out?

:)
[/SIZE]

---

### Post by goldblattster on 2012-08-28
Since I know Java, I can analyze the Java command for you. The Xmx and Xms arguments define how much memory is to be allocated to the minecraft process and the maximum memory that is to be allocated.

---

### Post by Invectus on 2012-08-28
Ah, thank you, do you think you could "reduce"  the amount of Ram that is allocated for me? That would be awesome. :)

---

### Post by taras.kuzyo on 2012-08-28
> **Invectus said:**
> [SIZE=4]
sleep 1

(Why is it that with the 1 there and no time like s, m, h, [seconds minutes and hours] behind it, that it instead launches minecraft without an issue?)

[/SIZE]

One second.

---

### Post by drmrgd on 2012-08-28
In terms of the remaining, unanswered questions:

1.  The $! variable in BASH is the equivalent of the PID of the last job that was sent to the background process.  So, after executing the Minecraft java launcher and sending it to the background, the script inquires about the PID that it was assigned, and assigns that value to the variable MINECRAFT_PID.

2.  The purpose of the wait command is to stop the script running after the job with MINECRAFT_PID has finished running.  So, essentially the script keeps looking at the PID for Minecraft, and once it sees it's been terminated, the script terminates.

3.  You could allocate less RAM to Minecraft if you like.  However,  I don't think that's what you want.  As it stands now, the maximum heap size of memory that you're allocating to Minecraft is only 1 GB (minimum is 512 MB).  If you're having lag problems, it's not because you've allocated too much RAM to Minecraft, but potentially the opposite.  Really, I think 1 GB should be plenty.  But if you're doing a lot of modding and such, you may need more than 1 GB of RAM.  What I would do is press F3 while you have a Minecraft map running to bring up the debug mode and look in the top right corner of the screen.  There you can see how much RAM is allocated and how much is being used.  If you're getting huge spikes and using up all of the available RAM, you may want to allocate more.  My suspicion is that there is something else that's causing you to lag.  Maybe not enough GPU memory?

---

### Post by Invectus on 2012-09-01
Thanks, that really helped. :DDD

---


---
title: "New to Ubuntu, beginner problems"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by nefrin on 2008-05-01
Greetings everyone, just let me say that at this point I have installed Ubuntu 8.04 on my computer and am very happy with it. That being said, there are a couple of issues that I have that I would appreciate input with.

To give my system specs: HP computer, AMD 64 Dual Core 6000+ processor, 3GB of RAM, NVIDIA GeForce 8600GTS graphics card, no third party sound card. Ubuntu downloaded and installed drivers for the NVIDIA after first boot up, to make use of the 3D rendering.

I have also installed Wine to run a couple of games, such as EVE Online and NWN.

1) Boot issues. Sometimes I get a Kernel Panic error while booting my system. At other times I will get a freeze up during the Ubuntu graphics loading page.

I recently switched over from Vista, where i was getting constant BSD while booting up (ie dozens of times before the system finally booted and ran fine afterward). At first I thought this was just a Windows problem, but now that I am experiencing this same issue with Ubuntu, I am starting to think that it's a Hard Drive problem. Any inputs?

2) While running Ubuntu after it boots up fine, I get an issue sometimes where programs will just shut down on their own, such as FireFox and the RythmBox music player. Is there something I can check or do that may prevent this from happening?

3) The other computers on my network are running windows still, though I will be converting in the future. In particular, all my music is store on an XP computer, as well as most of my shared folders that I access on a regular basis. I've had an issue where I can only mount one (1) of the shared folders on my XP computer at a time to access. If I attempt to mount a second folder, I get a password prompt that doesn't accept my user password for Unbuntu (I have no password stored for the XP system). What happens is that I enter the password, make sure that I am trying to access the MSHOME group, and it just keeps popping back up over and over again.

Is there anyway that I can mount multiple shared folders from XP, or is this a standard issue?

Thanks in advance. Please note that I am new to Linux, and while I have a bit of experience with CL, I am by no means an expert.

---

### Post by Tatty on 2008-05-01
1 and 2 both suggest a hardware problem.  Run a test on your RAM by rebooting, then selecting the memtest on the grub screen.

---

### Post by rahulsharma on 2008-05-01
try sudo apt-get install linux-rt
(reboot kernel with realtime)
someone told me about this command when i ran into same problem

let us know if this helps

---

### Post by scragar on 2008-05-01
> **nefrin said:**
> 1) Boot issues. Sometimes I get a Kernel Panic error while booting my system. At other times I will get a freeze up during the Ubuntu graphics loading page.

I recently switched over from Vista, where i was getting constant BSD while booting up (ie dozens of times before the system finally booted and ran fine afterward). At first I thought this was just a Windows problem, but now that I am experiencing this same issue with Ubuntu, I am starting to think that it's a Hard Drive problem. Any inputs?

[http://ubuntuforums.org/showthread.php?t=778019](http://ubuntuforums.org/showthread.php?t=778019) <-- try disabling the splash screen, and see what it says before things start going wrong during boot, if there's a consistant message between crashes and it get's posted back there could be a fix or solution of some kind.
> 
2) While running Ubuntu after it boots up fine, I get an issue sometimes where programs will just shut down on their own, such as FireFox and the RythmBox music player. Is there something I can check or do that may prevent this from happening?
after they crash running```
dmesg | tail -n 30 | less
```will let you see the 30 most recent messages back from the system, again, posting repeated messages back here could offer a solution.
> 
3) The other computers on my network are running windows still, though I will be converting in the future. In particular, all my music is store on an XP computer, as well as most of my shared folders that I access on a regular basis. I've had an issue where I can only mount one (1) of the shared folders on my XP computer at a time to access. If I attempt to mount a second folder, I get a password prompt that doesn't accept my user password for Unbuntu (I have no password stored for the XP system). What happens is that I enter the password, make sure that I am trying to access the MSHOME group, and it just keeps popping back up over and over again.

Is there anyway that I can mount multiple shared folders from XP, or is this a standard issue?

Thanks in advance. Please note that I am new to Linux, and while I have a bit of experience with CL, I am by no means an expert.
no idea about the last problem, I personaly stopped using windows a long time ago, although I recently started dual booting to play some PC games.

---

### Post by nefrin on 2008-05-01
rebooted the system and did the memtest from GRUB. Should note that I did install the amd64 version of Ubuntu, but the memtest displayed as "memtest86+" which I thought was an intel thing.

When trying to run memtest, got the following error:

Error 28: Selected item cannot fit into memory
Press any key to continue . . .

Takes me back to the first screen when pressing the key.

Also ran the sudo apt-get install linux-rt

It installed all the files, told me that installed all the files, but I never got the prompt back in my terminal window, and the system locked up.

---

### Post by Tatty on 2008-05-01
It really does sound like a hardware problem, its annoying that even the memtest has failed.

Try booting from a live cd and choose the "check memory for errors" option.

If even that doesnt work then try swapping the ram to see if the helps.  If that doesnt fix your problem then it very well might be a hard drive problem.

---

### Post by nefrin on 2008-05-01
Went in and disabled the splash screen and rebooted, worked fine. My boot issues only seem to arise during initial boots from a cold system (ie been turned off over night or long periods of time). Now that splash is disabled, I will monitor it and look for errors on boot up, and start posting those in the forums.

I also copied the command to run when a program quits on its own, so I can easily access it and run it when this occurs. Again, I will be posting the results as I get them.

Thanks for the help, just want to say that these experiences have not soured me on using Ubuntu. I knew that there was going to be a learning curve when I decided to switch from Windows, and tbh, I was getting a lot more problems with Windows then I currently am with Ubuntu.

---

### Post by phread59 on 2008-05-01
Nefrin as others have alluded I belive you have a memory stick in your machine dying.  It has all the classic symptoms.  If both Ubuntu and Vista are giving the same results.  As in irregular lock ups,freezes and crashes.  Boot issues from cold all sound like a memory issue.  Try running the Memory test from the live CD.  If that fails try to get a copy of "The Ultimate Boot CD"  it has lots of memory and motherboard tests as well as hardware tests for drives ect.  It may point out what is at fault.

Mark Shuman

---

### Post by nefrin on 2008-05-01
I am currently running Memtest86+ v1.70 from the live CD. I am 1 hour 20 minutes into the test, have recieved no errors as of yet, and Pass=1. 

I am hoping it's not a memory problem, but I pretty much figured it would be a hardware issue. The computer was moved by a moving company from Hawaii to CO, and it's possible that in transit it got knocked around or what not. When I first got the computer from the movers, I had to system restore everything on the computer due to boot issues at that time (running Vista). Worked fine for months, now these issues.

So yeah, most likely a hardware issue, but hadn't considered Memory problems. Something that I have not done yet is open up the CPU and reseat the memory sticks, I will attempt that next once the Memtest is done running, maybe it's just a loose connection somehwere.

---

### Post by nefrin on 2008-05-02
Ok, 4 hours later, I have completed 4 passes in Memtest, with no errors. I am aware that the program keeps recycling itself over and over again, but I would think that by this time if there was a problem with the memory it would have presented itself.

At this point, should I just reboot and assume my RAM is functioning properly and move on to troubleshooting other issues?

I would assume now that it's a hard drive error that is causing problems isnce the RAM seems to be ok.

---

### Post by nefrin on 2008-05-02
I let the system run for 5 passes before I rebooted back into Ubuntu. Been having issues with firefox shutting down on its own, also had the GUI restart on me. Ran the code suggested earlier in the thread and these are the errors I came up with:

[   75.670130] jockey-gtk[6291]: segfault at 7fb064ffb5b0 rip 4b599b rsp 7fff6c8e3980 error 4
[   77.047432] gnome-panel[6216]: segfault at 18 rip 7f9f7563b031 rsp 7fff7f9b6ee0 error 6
[  165.140877] firefox[6659]: segfault at 7fc624faa038 rip 7fc626e3b1f9 rsp 7fff2f04b890 error 6

segfaults are memory errors, should I attempt another memtest (and let this one run for a lot longer). I'm kinda lost here

Follow up, more errors:

[  590.907386] firefox[6948]: segfault at 7fb5e59cd400 rip 7fb5e785446e rsp 7fffefa65350 error 6
[  649.086817] gnome-panel[6478]: segfault at 18 rip 7fe7f49bd031 rsp 7ffffed38930 error 6
[  654.277357] gtk-window-deco[6343]: segfault at 30 rip 7fddde581031 rsp 7fffe8135340 error 6
[  695.309828] glxinfo[7396]: segfault at 7f5bec5ee8c0 rip 7f5bec8251f9 rsp 7ffff4a35f50 error 6
[  695.519210] jockey-gtk[7413]: segfault at 7fa48bfc52a0 rip 7fa48e1cf1f9 rsp 7fff963d87b0 error 6
[  695.868492] python[7432]: segfault at 7f3e956ed2a0 rip 7f3e9fcbf1f9 rsp 7fffa7ec48e0 error 6
[ 1188.023336] metacity[7337]: segfault at 20 rip 7f26c4a0c031 rsp 7fffcd8b9330 error 6
[ 1248.475530] firefox[7575]: segfault at 7fa508e51da0 rip 7fa509cec1f9 rsp 7fff11efd6e0 error 6
[ 1254.164997] pidgin[7793]: segfault at ff23d0 rip 7f63a810b220 rsp 7fffb45b0040 error 4
[ 1257.364132] stickynotes_app[7434]: segfault at 41c348c4 rip 7f81ead40032 rsp 7ffffc4a35a0 error 6
[ 1670.638616] metacity[7758]: segfault at 20 rip 7f21ae78a031 rsp 7fffb7637240 error 6
[ 1670.764632] metacity[8090]: segfault at fffffffffffc5d77 rip 7f4661dbf144 rsp 7fff6e4616e0 error 4
[ 1671.596966] metacity[8091]: segfault at 20 rip 7f4a90c3b031 rsp 7fff99ae86f0 
[ 1739.759125] rhythmbox[8120]: segfault at 7f579a52c2a0 rip 7f57aadbd1f9 rsp 7fffb2fc7df0 error 6
[ 1773.514359] rhythmbox[8148]: segfault at ff0000 rip ff0000 rsp 7fff7ab5ce18 error 15
[ 1773.519757] stickynotes_app[7830]: segfault at 10 rip 7fa6af103031 rsp 7fffb92bf5c0 error 6
[ 1773.540301] metacity[8092]: segfault at 20 rip 7ffab7016031 rsp 7fffbfec3ad0 error 6
[ 1866.489429] rhythmbox[8182]: segfault at ab60 rip 7f29ad8f6de9 rsp 7fffbd9275a0 error 4
[ 1879.756875] metacity[8153]: segfault at 20 rip 7f5249fbc031 rsp 7fff52e67a70 error 6


Since they are all segfaults, unless otherwise requested, I will stop posting these errors on the forums.

---

### Post by scragar on 2008-05-02
I'm not sure how you can fix this, ut this info might help:
```

1  protection fault       0  no page found
2  write                  0  read
4  user                   0  kernel
...
```not since all your error codes are 4 or 6, they are all user programs(although that just means that it's not the kernel unfortunatly...), the ones that are 6 occcur when writing to memory, and the 4's when reading. segfault occurs when attempting to access RAM it has no permissions to use, and judging by your number of errors the most likly result is that your ram is acting up. if you have multiple sticks of ram try removing one of them, see if the errors still occur, and swapping it if they do, till you find out which has the error.

---

### Post by nefrin on 2008-05-02
Thanks scragar. I was thinking that was the last solution I had as well. It's going to take some time, as I have 4 sticks of RAM (2 1gig and 2 half gig), so I will have to take an evening or a day to play around with pulling them out and using them one at a time (or possibly pulling out one at a time and running the system to find segfaults).

I haven't yet tried to reseat them into the mother board, so I will try that first. I am still running memtest, in an attempt to find anything wrong with them in that fashion, and will be able to run it for approx 24 hours before I need to shut it down.

It seems like something got knocked around too hard while it was being shipped overseas this last move.

Ran memtest for 13 passes, still no errors. I know that memtest won't necessarily find anything, so I'm on to the next step of reseating the RAM and seeing if that works. If not, I'll be pulling it out and testing them one at a time.

Does anyone know if there is a script I can run that will quickly check for segfaults while running Ubuntu, or do I just have to load up the RAM and start playing with programs to see if I get a segfault?

---

### Post by nefrin on 2008-05-05
Problem solved!

Pulled out all my RAM sticks and popped them back in one at a time to boot up the computer. Turns out one of the 1GB sticks had the fault, wouldn't even boot up the computer, just displayed SegFault Error 4. Removed that one and replaced all the others, system is working wonderfully.

Thanks again to all who helped, saved me a lot of trouble and possible money trying to solve the issue.

---


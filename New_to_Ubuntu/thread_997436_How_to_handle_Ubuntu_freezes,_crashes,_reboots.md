---
title: "How to handle Ubuntu freezes, crashes, reboots?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by kyleryner on 2008-11-29
Hi all,

Been a new Linux/Ubuntu user for only a week now (and lovin' it!) :)

I have always heard good things about Linux even before, and one thing i always hear is how stable it was-- doesnt crash or freeze like windows, no BSOD, etc.

When i started using Ubuntu a week ago, i gushed about it in an IRC group i belong to. One chatmate told me (and he is much more of a techie than me), he did try the latest Ubuntu when it came out.. and he said he always does one simple test.. he pulls the plug off the PC running Linux to simulate a Power Failure, and checks to see if it reboots properly. He said he tied this and Ubuntu 8.10 failed.

Few days later, I encountered a freeze-up.. (I was trying Wine on some games, screen froze and had to reset). Ubuntu failed to boot properly after that.. BUT I tried again with the "Recover" option and it fixed the problem. I thought, "hey, my friend is wrong.. maybe he didnt try the recover option?"

Few more days later, another situation came up (forgot what brought it about), same thing.. freezes, couldnt reboot.. THIS TIME, even the Recover option FAILED to reboot it. Tried several times, wont boot.. (text scrolling up so fast, but i notice one said FAILED.."

No Big deal, took the opportunity to repartition the drive to hold bigger space for a fresh install, tried Kubuntu, uninstalled, and reinstalled Ubuntu again (all using wubi btw).

Last night, a near fatal crash happened again.. was trying out OPENARENA.. graphics was giberrish, i couldnt see the menu, so i couldnt exit.. i was trying to alt-tab, ctrl-esc, ctrl-alt-del inan attempt to switch programs or pop up a task manager (ala windows), no luck so i had to reset.. left my pc for a few mins, so it automatically rebooted to Vista.. restarted again to go to Ubuntu.. I noticed a text error message as Vista was shuting down .. then Ubuntu wont reboot again, even with the Recover option.

But this shows a different message than last time.. (it left a prompt > .. last time it just kept going back to the dual boot screen)
Message says something about doing a disk check in windows or something like that. Rebooted back to Vista (in safe mode to be sure), booted ok, restarted again Ubuntu in safe mode, and this time it booted properly so it was fine...

So here I am now, wondering if i should expect more of the same.. as im starting to REALLY like linux, installing more apps, etc, the idea of having another catastrophic crash is scary.. 

here's some questions:

1) Does this happen often? Are the above expreinces normal? 

2) I find most of the problems are graphics related, or when i use WINE to run a windows game, it freezes. Anything i can do about this?

3) Is there a keyboard command like windows' ctrl-esc, alt-f4 (close), ctrl-alt-del (to force task manager to close an app) etc i can use before resorting to the drastic restart/reset option?

4) is my friend right? Pulling the plug off (w/c i take it is equivalent to Power off/  reset) will cause such crashes? and when is it fatal, when is it fixable with the 'recover' option?

Thats all, my apologies for the rather windy post :)

The more i invest my time and energy to Ubuntu, the more Im scared of encountering a crash i cant recover from. Any suggestions and inputs would be greatly appreciated,  thanks.. :)

---

### Post by linuxguymarshall on 2008-11-29
I am computer enemy #1. My primary form of shutdown is to yank out the power source :)     I have not yet had it mess up although I have had a lot of problems with 8.10    If you are now I recommend 8.04

For ending non-responding programs their is Force Quit which you can assign a key to in your preferences. It is like WindBlows' End Now only Force Quit will end it right there, no questions asked.

---

### Post by faraz_k86 on 2008-11-29
Phew, long post.

Im from Pakistan and we dont have to simulate power failures we get it all the time. Due to power failures and Loadshedding my Ubuntu PC improperly shuts down atleast 10-15 times a day.

I never had any problems after.


Ctrl+Alt+Backspace may work for you in such cases. Though I would also like to know the alternative to ctrl+alt+del :)

---

### Post by faraz_k86 on 2008-11-29
> **linuxguymarshall said:**
> I am computer enemy #1. My primary form of shutdown is to yank out the power source :)     I have not yet had it mess up although I have had a lot of problems with 8.10    If you are now I recommend 8.04

For ending non-responding programs their is Force Quit which you can assign a key to in your preferences. It is like WindBlows' End Now only Force Quit will end it right there, no questions asked.

LOL. You can seriously mess up your hard drive that way. Im told it brings bad sectors

---

### Post by linuxguymarshall on 2008-11-29
> **faraz_k86 said:**
> LOL. You can seriously mess up your hard drive that way. Im told it brings bad sectors

I have a piece of crap machine if it dies, good riddance. I think my current $250 USD + Christmas money (~$800), + whatever I can get on Craigslist  or ebay for this will allow me to build a new pc.

---

### Post by Xiong Chiamiov on 2008-11-29
> **kyleryner said:**
> 
1) Does this happen often? Are the above expreinces normal?

Depends on what you're doing.  I never have problems with my computer locking up.

> **kyleryner said:**
> 
2) I find most of the problems are graphics related, or when i use WINE to run a windows game, it freezes. Anything i can do about this?

Don't use Compiz.  It's still a little buggy, and often doesn't play well with fullscreen applications.

> **kyleryner said:**
> 
3) Is there a keyboard command like windows' ctrl-esc, alt-f4 (close), ctrl-alt-del (to force task manager to close an app) etc i can use before resorting to the drastic restart/reset option?

That one depends on your desktop environment.  For certain, however, ctrl-alt-backspace will restart X, which will often do the trick.  Be aware that this will log you out.

You can also use the "killall command" in a terminal.  If you're stuck in fullscreen, you can press ctrl-alt-f1 to get a prompt.  If you're not sure what the process name is, you can use htop to get a graphical sort of task manager; select the one you want to kill, then press f9 and enter to kill it.

There's also another emergency shutdown command, which is on a sticky-note at my apartment at school.  It was something like ctrl-alt-y,s,b or somesuch.  Does anyone know what I'm talking about?

> **kyleryner said:**
> 
4) is my friend right? Pulling the plug off (w/c i take it is equivalent to Power off/  reset) will cause such crashes? and when is it fatal, when is it fixable with the 'recover' option?
If you're using a journaled filesystem (which, by default, you are) then you shouldn't have any problems.  Fdisk will probably check your disks when you start up again, but other than that, nothing should have issues, afaik.  I have no knowledge of the recover option or what it does, so I cannot comment on that.

> **kyleryner said:**
> 
Thats all, my apologies for the rather windy post :)
None needed.

> **kyleryner said:**
> The more i invest my time and energy to Ubuntu, the more Im scared of encountering a crash i cant recover from. Any suggestions and inputs would be greatly appreciated,  thanks.. :)

Really, there is no reason you should ever have to reinstall linux, unless you do something dangerous as root, like deleting your /boot.

---

### Post by kyleryner on 2008-11-29
thanks all for the QUICK and HELPFUL replies :)



> **linuxguymarshall said:**
>   If you are now I recommend 8.04

For ending non-responding programs their is Force Quit which you can assign a key to in your preferences. It is like WindBlows' End Now only Force Quit will end it right there, no questions asked.

Im using 8.10 now. I think i tried 8.04 before (or an older Ubuntu). Didn't work properly with my system and hardware (spec my wireless card). Now 8.10 works, i upgraded my mobo/cpu since then but my wireless card is the same one. I assumed it was the 8.10 that made my wireless work


I checked Preferences->Keyboard shorcuts... didnt see Force Quit as an option?  Did notice there is actually a  a ctrl=alt-del shortcut. It works now, but it didnt help when my PC was frozen

> **faraz_k86 said:**
>  
 

Ctrl+Alt+Backspace may work for you in such cases. Though I would also like to know the alternative to ctrl+alt+del :)

This is probably what i need! I just tried it, and i was logged out before i knew what hit me. LOL. good thing i didnt have any unsaved documents open :)  thanks for this.


> **Xiong Chiamiov said:**
>  

Don't use Compiz.  It's still a little buggy, and often doesn't play well with fullscreen applications.

I have no knowledge of the recover option or what it does, so I cannot comment on that.

Really, there is no reason you should ever have to reinstall linux, unless you do something dangerous as root, like deleting your /boot.

Is Compiz the one responsible for the really cool effects for Appearances-> Extra?  I really love that :)

I have dual (actually triple  :) ) boot with Vista/ XP/ Ubuntu.
Under Ubuntu, options are Ubuntu 8.10 and Ubuntu 8.10 (Recovery). choosing Recovery saved me from a failed reboot at least twice now.

For #3, Ill take your word for it, you're the experts :) . However I did encounter a failed reboot once so far.. necessiating a re-install. The other times were "close calls" (I thought i came close to a failed reboot again). In retrospect, i guess there must be a technical way to recover from events like those, so ill just come running to the forum when that happens again (hopefully it wont) :)

thanks again guys!

---

### Post by rhcm123 on 2008-11-29
I had this problem myself. You said you were using wubi? When using wubi, it creates a virtual disk (which slows down speed tremendously) for ubuntu. However, the problem arises when something locks up the system and somebody has to force a hard reboot. On a regular partition, ubuntu would bounce right back, check the file system, then carry on. On a wubi drive, the data is typically irreversibly corrupted. You got lucky that recovery mode fixed it.

You said you created a new partition. Why not install ubuntu into that? Instead of screwing around with wubi, just use your partition.

Edit:
Also, another thing happened to me, which i completely forgot about until i read this:
[http://kempj.blogspot.com/2007/09/wubi-dangers.html](http://kempj.blogspot.com/2007/09/wubi-dangers.html)

Wubi corrupted my MBR (master boot record). I had to get my winxp disk to write me a new one. (which is a pain in the butt, just for refrence). I don't know why it does this on an unclean exit, but it may have somthing to do with somthing called grub4dos ([https://gna.org/projects/grub4dos/](https://gna.org/projects/grub4dos/)) that, because windows resources are loaded in wubi (the virtual disk) may become corrupted on a bad exit.

Also, read this thread on bootloader problems:
[http://ubuntuforums.org/showthread.php?t=488740](http://ubuntuforums.org/showthread.php?t=488740)

And this one on a possible fix for them:
[http://ubuntuforums.org/showthread.php?t=478838](http://ubuntuforums.org/showthread.php?t=478838)

---

### Post by kyleryner on 2008-11-29
> **rhcm123 said:**
> I had this problem myself. You said you were using wubi? When using wubi, it creates a virtual disk (which slows down speed tremendously) for ubuntu. However, the problem arises when something locks up the system and somebody has to force a hard reboot. On a regular partition, ubuntu would bounce right back, check the file system, then carry on. On a wubi drive, the data is typically irreversibly corrupted. You got lucky that recovery mode fixed it.

You said you created a new partition. Why not install ubuntu into that? Instead of screwing around with wubi, just use your partition.

Edit:
Also, another thing happened to me, which i completely forgot about until i read this:
[http://kempj.blogspot.com/2007/09/wubi-dangers.html](http://kempj.blogspot.com/2007/09/wubi-dangers.html)

Wubi corrupted my MBR (master boot record). I had to get my winxp disk to write me a new one. (which is a pain in the butt, just for refrence). I don't know why it does this on an unclean exit, but it may have somthing to do with somthing called grub4dos ([https://gna.org/projects/grub4dos/](https://gna.org/projects/grub4dos/)) that, because windows resources are loaded in wubi (the virtual disk) may become corrupted on a bad exit.

Also, read this thread on bootloader problems:
[http://ubuntuforums.org/showthread.php?t=488740](http://ubuntuforums.org/showthread.php?t=488740)

And this one on a possible fix for them:
[http://ubuntuforums.org/showthread.php?t=478838](http://ubuntuforums.org/showthread.php?t=478838)

Ok, this explains a lot! Thanks for the reply and the helpful links.

Luckily, my long-winded post happened to mention wubi in passing (good catch, btw) It never occured to me that was the issue.

Reading your links, i get a general idea on the issues. So it seems wubi's install is more unsafe than a standard install. Meaning it might be a matter of time before i have an irreversible crash again :(

The whole point of wubi is to try out Linux in a familiar environment (windows install/uninstall). I think Im sold already so i guess im ready for a full install now.. but im still wary of messing with the MBRs and dualboots and stuff like that.

I barely managed to make a dual/triple boot with Vista/XP/Ubuntu.. using Vistabootpro and Wubi.

btw, the partition i mentioned im using is the one where i keep Windows XP.. I keep it around bec im paranoid and still a relatively new user to Vista myself. I guess I can still use a partition manager to make another SEPARATE PARTITION just exclusively for Ubuntu. (I have 2 drives, 4 partitions and 2 partitons each.. i guess another one wouldnt hurt, would it?)

Can you kindly point me to a link where i can best accomplish a fresh Ubuntu install, assuming i already have a vista/xp dual boot going on using Vistabootpro? (ill try to google for it myself, of course)

thanks again

---

### Post by rzrgenesys187 on 2008-11-30
Nobody has mentioned the [Magic Sys Req keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") :)

In short if your computer has crashed you can, pretty safely, shutdown your computer this way.  What you do is hold Alt + SysReq (generally the print screen key) and while holding those two type REISUB.  Waiting about a second or so between each keypress.  This should restart your computer (see link above for what exactly happens).  If the computer doesn't restart (B doensn't seem to work in ubuntu for me) O, not zero, should power off the machine

---

### Post by Xiong Chiamiov on 2008-11-30
> **Xiong Chiamiov said:**
> 
There's also another emergency shutdown command, which is on a sticky-note at my apartment at school.  It was something like ctrl-alt-y,s,b or somesuch.  Does anyone know what I'm talking about?


> **rzrgenesys187 said:**
> Nobody has mentioned the [Magic Sys Req keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") :)


Ah, that's it.  It's been a while since I've had to use those, so I couldn't remember much except that it was some odd key combo.

> **kyleryner said:**
> 
Is Compiz the one responsible for the really cool effects for Appearances-> Extra?  I really love that :)

Yep, you got it.  As awesome as it is, things will run smoother without it.  It's a tradeoff that you have to decide whether it's worth it or not.

---

### Post by rhcm123 on 2008-11-30
> **kyleryner said:**
> Ok, this explains a lot! Thanks for the reply and the helpful links.

Luckily, my long-winded post happened to mention wubi in passing (good catch, btw) It never occured to me that was the issue.

Reading your links, i get a general idea on the issues. So it seems wubi's install is more unsafe than a standard install. Meaning it might be a matter of time before i have an irreversible crash again :(

The whole point of wubi is to try out Linux in a familiar environment (windows install/uninstall). I think Im sold already so i guess im ready for a full install now.. but im still wary of messing with the MBRs and dualboots and stuff like that.

I barely managed to make a dual/triple boot with Vista/XP/Ubuntu.. using Vistabootpro and Wubi.

btw, the partition i mentioned im using is the one where i keep Windows XP.. I keep it around bec im paranoid and still a relatively new user to Vista myself. I guess I can still use a partition manager to make another SEPARATE PARTITION just exclusively for Ubuntu. (I have 2 drives, 4 partitions and 2 partitons each.. i guess another one wouldnt hurt, would it?)

Can you kindly point me to a link where i can best accomplish a fresh Ubuntu install, assuming i already have a vista/xp dual boot going on using Vistabootpro? (ill try to google for it myself, of course)

thanks again

Yes, wubi is, although now "technically" endorsed, still a open source project, and it isn't as, shall we phrase it, reliable, as a full defualt install.

You hit the idea right on the head. The idea of wubi is to let people with no linux/other computer experience who have heard good things about ubuntu use it with a fun gui (lacking in other distros of linux), and, because it was made by people who know what they are doing, it holds very little risk of damaging the computer. (Right? :) )

I have found if you use gparted (NOTE: THIS IS NOT RECOMENDED) to resize your windows partiton down by about 5 gigs of the end, if it is not very full, you risk losing very little data & you gain a large enough space for ubuntu and swap. (I'll walk you through that if you so desire.)

If you want a fresh ubuntu install (I'll reccomend 8.04 LTS) download the ISO here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) being sure to select 8.04 LTS. Delete your wubi partiton and then post here.

---

### Post by rhcm123 on 2008-11-30
> **Xiong Chiamiov said:**
> 
Yep, you got it.  As awesome as it is, things will run smoother without it.  It's a tradeoff that you have to decide whether it's worth it or not.

Oh, and this reminds me. Ubuntu runs terribly slowly with wubi, i've found through my own usage and the documentation. So slow, the hardware accleration was disabled by defualt when running my wubi install, but on a physical partition install, it works on normal right out of the box.

I saw you want to use vistabootpro as your boot manager. Let me warn you, ubuntu will overwrite this and install GRUB as it's boot manager. There is little to no difference, as they all acomplish the same task, but be warned.

---


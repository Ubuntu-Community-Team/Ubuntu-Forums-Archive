---
title: "my experience with ubuntu 14.04 (and elgato game capture hd help needed)"
date: 2014-04-21
forum: Recurring Discussions
---

### Post by david194 on 2014-04-21
ok so heres the situation i installed ubuntu 14.04 to try it out, i figured what the hell i have a recovery system on my laptop, 
so i partitioned my free space and moved all my important files over to it.
I installed ubuntu telling it that it could over write windows.
when i it loaded i couldnt find my backup partition....it had wiped it!
worse still it wiped my recovery partition!!!!!!!! there is no escape for me now!
ok ok im not perturbed millions like ubuntu its ok its ok
so i install playonlinux and then steam and then space engineers...... it wont load
i mess about with directx settings etc .....nothing
ok i play that on my main pc anyway np problem
i installed star wars galaxies emulator (i play on the tarkin server) 
i figure out how to add directx9 to wine (this os serously is not user friendly to suss out!)
i can play galaxies yay
ok so time to stop messing with ubuntu and do some streaming from my main pc, plug in my elgato game capture hd ....no bleep to tell me new device attached.......no popups no nothing
searched the net and cant find any way to use my game capture card with ubuntu!!!! despite it being the best and most popular game capture hardware! 

so here i am ....completly screwed cursing ubuntu if i could get the game capture card working it wouldnt be so bad (i tried using play on linux to install the windows version of the software but no go) so far though i have to say i have not found any pluses to ubuntu over windows just lots of negatives, maybe its the fact its asking me to enter my password every time i add or remove software, maybe its the fact nothing works out of the box, maybe its the fact my capture card (the main reason for the laptop) just wont work with it! 

arghhhhhhhhhhhhhhhhhhhhh

---

### Post by Vladlenin5000 on 2014-04-21
Hi, welcome.

Well, needless to say that if you choose the option to use the entire disk, _the installer will do just that._ The 'best practices' manual clearly states that backups should be done to a different drive, precisely to avoid mistakes likes yours.
Also needless to say that attempting to install software designed for another OS is seldom user-friendly. Granted, there are more sophisticated emulations environments like the (commercial) Codeweavers Crossover that make it easier, (supposedly) support more software, but it's always a hit&miss scenario. You should do your search before trying any Windows software on Linux via an emulator, namely at the WineHQ website where they have a list of software and their support status (anything below Gold forget it, it isn't worth the trouble).

Finally, regarding your capture card, I'm afraid it has no native support for Linux. You might want to read this: [https://plus.google.com/+NickHolden/posts/gfHZAuKCvGc](https://plus.google.com/+NickHolden/posts/gfHZAuKCvGc) . So, yeah... At best you can expect community support but don't keep your hopes high. Your hardware uses proprietary code at least in the firmware and reverse engineering it would be illegal. Please demand a native albeit also proprietary driver/firmware from the manufacturer.

---

### Post by Vladlenin5000 on 2014-04-21
And commenting about your last paragraph... Don't blame the OS for manufacturer unwillingness to support other platform and (this is a bug DUH...) do your homework before jumping to a different OS by checking whether or not the software you need have native versions for the said OS - or if it is supported via an emulator - and, obviously, the same goes for hardware.

---

### Post by wildmanne39 on 2014-04-21
*Thread moved to **Recurring Discussions**.*

---

### Post by david194 on 2014-04-21
> **Wild Man said:**
> *Thread moved to **Recurring Discussions**.*

if my issues are recurring issues then that has to be a flaw in ubuntu!

inregards to the drive blanking, it was my understanding that when you partition a hard drive you make two effective drives, windows even shows these as two seperate drives (c: and d: for ) example i was perfectly happy for it to use all of c drive (my windows drive) i was not happy it wiped my other partitions...frankly im amazed they would have it able to wipe a recovery partition when nearly all laptops have come with recovery partitions for the last few years. I do not accept fault there at all, i do not lay blame really either, its free software i cant really hold it to the same standard as paid for OS like windows. 

My post was deeply negative but i had spent many hours trying to get it all working and it has not only destroyed my backup data (only the most important files were backed up elsewhere) but it has also devalued my laptop (secondhand market wont touch one that cant be reset to default) the latter is mute as i payed for an expansive laptop with a view to keep using it for years to come, i have managed to get windows 8 back on the laptop and im in the process of re-setting everything up, i do still have ubuntu installed on my main pc alongside windows 8 so i may have a proper look at it when im calmer though wont be a while yet.

so my opinion on ubuntu as a new user:
pros,
it boots fast
it shuts down fast
anywindow can be made to be ontop
when wine/play on linux is more mature it will be good
multiple work spaces, man thats a cool feature, means i can have a dev enviroment for modding on one workspace and browsers etc on another and move between them very nicely, like having a very big screen

cons,
support for hardware is not good (that may be the hardware developers fault but its still a bad side to using the os)
not user friendly in the slightest (from hunting down how to have the menus actually on the windows thier ment to be to getting native windows games to work right, man it was a nightmere)
asks for my password for everything even though i already logged in with it! i use secure passwords of multiple words and numbers and case....this just encourages silly passwords
wine and play on linux at present are not good enough to play windows games on, i even had to close and reload the windows version of steam a few times to get it to work.

in short ubuntu is NOT ready for gamers, i can see it being good if you only program or if you only do office work but for gamers its a bit of a wreck

---

### Post by Vladlenin5000 on 2014-04-21
This is a recurring discussion because there are people like you whom *recurrently *spit out the same old fallacies.

This was written specially for people like you: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) . Please read and understand it for your own sake. Ignore the few outdated bits.
Now, a few corrections:
Regarding what happened to your data, I'm sorry but if you don't know what you're doing - you clearly don't - you shouldn't complain about the bad results. The option to "use the entire drive" does just that and WARNS the user about wiping the entire contents of the drive. Whenever you need to keep a partition you must select the third option, "something else" and then _proceed to manually create the partitions for Ubuntu, _select those to format (checkbox) and make sure _no other partition you want to keep is marked._ What you did was a noobish mistake but nothing to be ashamed of, everybody makes mistakes. Now that you learned how to do it it won't happen again unless you're distracted. Also I hope you've learned by now that you should always make a backup to a known good media which ISN'T the same where you want to install a new OS. Again, please don't blame the installer for doing EXACTLY what you told it to do. The warning is abundantly clear and with pages like this - [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) - there's absolutely NO EXCUSE.
Partitioning a drive doesn't make it magically into two different and separated drives (really? LOL). No, not at all! Partitioning creates partitions (sections/divisions of the same physical drive), one, two or more (up to 4 primary partitons in the now old MBR based drives). Your understanding of the subject is flawed but it really isn't your fault here because Microsoft have been dumbing down users for decades now, you're just a victim (another one in an endless list). 

Regarding the "user-friendliness" (BTW, can you define it? Naahhh...) I have nothing to add to the aforementioned article. The author presents compelling arguments against that utterly flawed logic that conflates "user-friendly" with "familiar". 

Regarding the hardware support: Linux currently has much better native support for hardware parts than anything else. In my desktop PC the only driver I install is the proprietary Nvidia graphics driver and that because I want (more of that later), not because I need; Ubuntu and all the other modern Linux distros come with a open-source driver that works fine for the most part. Installing a Windows 7 in the same machine would require additional installations of NO LESS THEN 12 (TWELVE) drivers and/or other software. 
Granted, there are a few hardware components that doesn't work *au pair* or not at all but the manufacturers are the ones you should blame for that. 
Now, the "thing" about the only driver I have (want) to install - nvidia - is because I'm also a gamer (in my spare time). What you said about Ubuntu not being ready for gamers is, at best, laughable. Don't you know the SteamOS IS a (Debian based, just like Ubuntu) LINUX DISTRO? Your complaints are entirely related with non-native games which is the same as complaining about Windows not being ready for gamers because the [insert software name] PS3 Emulator for Windows can't run most of the PS3 games you want to play. 
Granted, as of today there aren't that many _mainstream_ titles available natively for Linux but is it in any way related with the OS limitations or shortcomings? Absolutely not. Technically speaking, Linux often performs better than Windows in every single game-related detail or part of the equation, provided the computer has been correctly installed and has good video drivers (again, blame nVidia, Intel or AMD/ATI all you want). Many native games already available at Steam (and others) are as much resources hungry than mainstream Windows games and my system runs them flawlessly. It doesn't run (yet) the games you want? Too bad but I think we can agree that that is your problem. Actually it's the exact same "user-friendliness" fallacy if you think about it.

PS - A friendly advice: Ask for help politely and assertively whenever you need. We'll do our best to help you and entirely for free. Meanwhile loose the attitude, be humble, because you know next to nothing therefore you still have a lot to learn, if you want, that is.
Here's the thing about the recurring discussion you're presenting: Although we generally welcome criticism and comments such as yours we prefer a more mature perspective - the one you'll probably have after learning something about the OS. Personally I don't care much about complaints about issues with emulated silly Windows games and similar diatribes. Why? Simply because I've been hearing the same fallacies for 20 years now... I know, in you naiveness you may think you're being awesome by producing such criticism but you aren't. You couldn't be more wrong.

---


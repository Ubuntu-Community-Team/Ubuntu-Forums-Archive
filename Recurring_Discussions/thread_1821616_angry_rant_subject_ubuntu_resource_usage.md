---
title: "angry rant: subject: ubuntu resource usage"
date: 2011-08-09
forum: Recurring Discussions
---

### Post by Martiini on 2011-08-09
"linux is the new windows", that claim is absolutely correctemundo.
bloated, resource hungry, slow, junk software
Ubuntu is slow! my nokia phone runs faster than this!

This is what linux has become.
Im on Dell mini laptop.
Im running only standard kde, chromium, konsole.

running processes: 175 (!!!)
memory used: 535589k (!!!)

WFT !!!

top - 18:10:08 up  2:42,  2 users,  load average: 0.52, 1.88, 1.90
Tasks: 181 total,   4 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.3%us,  4.6%sy,  0.0%ni, 77.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1016772k total,   699032k used,   317740k free,     9648k buffers
Swap:   511964k total,   218812k used,   293152k free,   367016k cached

---

### Post by Paqman on 2011-08-09
> **Martiini said:**
> 
Im on Dell mini laptop.
Im running only standard kde, chromium, konsole.


That's your problem. Full-fat KDE is not a very appropriate DE for a netbook. There are plenty of better choices available to you.

---

### Post by uRock on 2011-08-09
You are running KDE and complaining about resources? It is probably the heaviest DE.  >600MB is nothing compared to what my HP with Vista would use. I think it was idling between 1.5 and 2 GB of RAM. The same system with ubuntu only uses more than 1GB of RAM when running a VBox.

I have 4 systems running ubuntu. I do not consider any of them slow. They came with XP or Vista. Both of which were much slower.

---

### Post by haqking on 2011-08-09
> **Martiini said:**
> "linux is the new windows", that claim is absolutely correctemundo.
bloated, resource hungry, slow, junk software
Ubuntu is slow! my nokia phone runs faster than this!

This is what linux has become.
Im on Dell mini laptop.
Im running only standard kde, chromium, konsole.

running processes: 175 (!!!)
memory used: 535589k (!!!)

WFT !!!

top - 18:10:08 up  2:42,  2 users,  load average: 0.52, 1.88, 1.90
Tasks: 181 total,   4 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.3%us,  4.6%sy,  0.0%ni, 77.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1016772k total,   699032k used,   317740k free,     9648k buffers
Swap:   511964k total,   218812k used,   293152k free,   367016k cached

Who said "linux has become the new windows" by the way ?

KDE is HUGE DE.

The "junk software" is whatever you choose to add or use.

"This is what Linux has become"?  Linux is what you make it !

---

### Post by mikewhatever on 2011-08-09
Here is mine (dell mini 1010):
```

free -m
             total       used       free     shared    buffers     cached
Mem:           993        463        529          0         39        179
-/+ buffers/cache:        244        748
Swap:         1027          9       1018


```

Hope ranting made you feel better and fixed the problem.:-\"

---

### Post by sffvba[e0rt on 2011-08-09
Well for all the "bloat", KWin performs better than Metacity, Compiz, Mutter ;)

[http://www.phoronix.com/scan.php?page=article&item=linux_desktop_managers1&num=9](http://www.phoronix.com/scan.php?page=article&item=linux_desktop_managers1&num=9)

---

### Post by ki4jgt on 2011-08-09
If you want the new windows, try ReactOS. It runs on 32 megs. The distro is only 50 megs big. As for the bloat, I can agree. I can remember when a full install of Ubuntu would run on 256. Now (at times) it has trouble with a gig. Such expansion is expected though from an OS. As time passes and it becomes more and more complex, more and more resources are used. I do think Ubuntu should try to find ways to cut back on these resources and attempt to get as close as possible to it's original 256 support, but I'm not complaining. This would allow users from all over the spectrum use it. Though, the user could install another DE, it's just not the same. The Unity feel is not there :-)

---

### Post by uRock on 2011-08-09
Asus EeePC running ubuntu 11.04 ```
uRock@uRock:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           992        445        547          0         46        237
-/+ buffers/cache:        162        830
Swap:         1951          0       1951

```

---

### Post by ki4jgt on 2011-08-09
```
jesse@Remember:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           988        744        244          0         54        286
-/+ buffers/cache:        403        585
Swap:         1010         35        975
jesse@Remember:~$ 

```

Here's mine with a gig :-)

---

### Post by dniMretsaM on 2011-08-09
KDE on a netbook and your complaining that it's too slow? Sorry, but I lol'd. KDE is one of the biggest DE's, so it runs slow. And also, your Nokia may very well be running Linux as well. Just pointing that out.

---

### Post by Bandit on 2011-08-09
Oh no. Not another "*I dont know how my system manages resources to help boost performance so I must complain like a fool thread..*"

You WANT your system to keep used programs loaded up into memory for later usage. This enables the system to reload the program faster in the future. The more RAM you have, the more resources can be allocated into RAM. Now if you open up something that is not already loaded into system RAM, dont fret because the system will quickly remove any resources already loaded to make way for the new program to load without any hurt in performance. 

Here is example from my system, it shows I am getting my moneys worth in RAM usage:

```
exodist@Aurora:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3954       3536        417          0        160       2347
-/+ buffers/cache:       1029       2925
Swap:         9535         64       9470
```

---

### Post by ikt on 2011-08-09
> **ki4jgt said:**
> Though, the user could install another DE, it's just not the same. The Unity feel is not there :-)

That's the reason why Xubuntu and Lubuntu exist, for old computers, because Unity takes to much out of them.

TBH I'd just buy a new pc, reason I say this is because I just got a new pc the other day:

cpu: AMD E350 APU Dual-Core CPU on-board 
mobo: ASRock E350M1/USB3 Mini-ITX Motherboard - $139.00 
gpu: Integrated AMD Radeon HD 6310 graphics
ram: 4G Kit 1333 G.Skill-NT - $30 
hdd: Samsung 2T - $81 
case: Silverstone SG06 Black Cube Mini-ITX Case with 300W PSU - $119.00 

Total: $369

And that's more than capable of running unity and windows 7 **at the same time** while watching a BD movie.

---

### Post by dinamic1 on 2011-08-09
windows 7 runs faster than ubuntu 11.04 (gnome classic) on my pc

---

### Post by Paqman on 2011-08-09
> **ki4jgt said:**
> Though, the user could install another DE, it's just not the same. The Unity feel is not there :-)

Sure it is. Unity-2D is just the ticket for less grunty systems.

---

### Post by ki4jgt on 2011-08-09
> **ikt said:**
> That's the reason why Xubuntu and Lubuntu exist, for old computers, because Unity takes to much out of them.

TBH I'd just buy a new pc, reason I say this is because I just got a new pc the other day:

cpu: AMD E350 APU Dual-Core CPU on-board 
mobo: ASRock E350M1/USB3 Mini-ITX Motherboard - $139.00 
gpu: Integrated AMD Radeon HD 6310 graphics
ram: 4G Kit 1333 G.Skill-NT - $30 
hdd: Samsung 2T - $81 
case: Silverstone SG06 Black Cube Mini-ITX Case with 300W PSU - $119.00 

Total: $369

And that's more than capable of running unity and windows 7 **at the same time** while watching a BD movie.

I know that's why they exist and I'm not complaining. I have a perfect amount of resources for what I want to do on my laptop. I'm just saying, it would be kind of cool to run Ubuntu on my brother's older computer. Other DEs are not the same as Unity. I mean, AFATG, there could be a stripped down version of Unity for systems running around 256. (Still not complaining) just saying that it would be great, since several users still have this technology sitting around, and it wouldn't force them to use IMO, low-functionality DEs. Don't get me wrong, they're great for what they do, but they don't provide any functions.

---

### Post by ki4jgt on 2011-08-09
> **Paqman said:**
> Sure it is. Unity-2D is just the ticket for less grunty systems.

Ahhhh So, they've already got one??

---

### Post by uRock on 2011-08-09
> **dinamic1 said:**
> windows 7 runs faster than ubuntu 11.04 (gnome classic) on my pc

Irrelevant, but nice.

---

### Post by Bandit on 2011-08-09
> **dinamic1 said:**
> windows 7 runs faster than ubuntu 11.04 (gnome classic) on my pc

Performance is heavily based on system drivers for particular hardware just as much as the operating system. Win7 could easily run faster due to having better commercial drivers at hand, but that's not because of Win7. Its the drivers. If Ubuntu is running great on 99% of the other computers, and not on another. Huge chance its a hardware/driver issue. I have Ubuntu 11.04 on my system and have ran Win7 on it as well. They fair so close to the same I would have to run a benchmark to notice any differences. But then again I also purchased my computers components individually to insure I got a solid system for both Windows and Linux. This is something you cant do with an over the shelf store bought PC.

---

### Post by uRock on 2011-08-09
> **Paqman said:**
> Sure it is. Unity-2D is just the ticket for less grunty systems.

I have Unity on my netbook. Runs great.:D

---

### Post by BrokenKingpin on 2011-08-09
Yep, KDE is a beast, but still runs faster than Windows. I would try Xfce... nice looking, and far better memory usage.

---

### Post by ikt on 2011-08-09
> **ki4jgt said:**
> I know that's why they exist and I'm not complaining. I have a perfect amount of resources for what I want to do on my laptop. I'm just saying, it would be kind of cool to run Ubuntu on my brother's older computer. Other DEs are not the same as Unity. I mean, AFATG, there could be a stripped down version of Unity for systems running around 256. (Still not complaining) just saying that it would be great, since several users still have this technology sitting around, and it wouldn't force them to use IMO, low-functionality DEs. Don't get me wrong, they're great for what they do, but they don't provide any functions.

Yeah sorry, I just looked back at my post and thought I could word it better but then I saw like 10 replys =o

But yeah I also wish Unity was a nice slim sexy beast that would run on <256MB of RAM! :(

---

### Post by kaldor on 2011-08-09
> **ki4jgt said:**
> As for the bloat, I can agree. I can remember when a full install of Ubuntu would run on 256. Now (at times) it has trouble with a gig.

I remember when computers came with <100 MB of RAM. Now, they come with at least 2 GB of RAM. RAM is super cheap and quite easy to install.

Ubuntu is trying to become a mainstream desktop OS, not an OS for people who won't add more RAM to their 10+ year old PCs.

Linux isn't bloated. Windows isn't bloated either; it's only the OEM versions with all the crapware installed. Though, I do find the Windows UI to be pretty cumbersome and overwhelming to navigate in Win7.

---

### Post by ki4jgt on 2011-08-09
> **Bandit said:**
> Performance is heavily based on system drivers for particular hardware just as much as the operating system. Win7 could easily run faster due to having better commercial drivers at had, but that's not because of Win7. Its the drivers. If Ubuntu is running great on 99% of the other computers, and not one another. Huge chance its a hardware/driver issue. I have Ubuntu 11.04 on my system and have ran Win7 on it as well. They fair so close to the same I would have to run a benchmark to notice any differences. But then again I also purchased my computers components individually to insure I got a solid system for both Windows and Linux. This is something you cant do with an over the shelf store bought PC.

I totally agree with that statement. Custom is the best thing anyone can do for their computers. I don't know how many times people have called me, and ask me why this or that wouldn't work, and it's was hardware related. Most people have no idea what hardware is. They buy a computer, and expect it to automatically just do what ever functions are stored in the OS. I have to admit, I did it a time or two LOL. :-) We need to realize that the OS, makes up 0% of how the computer actually works. It's just a set of directions for it to follow. If the hardware's compatible with those directions, then it will continue. It's kind of weird to think about. . . The one thing, that influences your computer the most, isn't even a real object :-) Changing sig now :-)

---

### Post by ki4jgt on 2011-08-09
> **kaldor said:**
> I remember when computers came with <100 MB of RAM. Now, they come with at least 2 GB of RAM. RAM is super cheap and quite easy to install.

Ubuntu is trying to become a mainstream desktop OS, not an OS for people who won't add more RAM to their 10+ year old PCs.

Linux isn't bloated. Windows isn't bloated either; it's only the OEM versions with all the crapware installed. Though, I do find the Windows UI to be pretty cumbersome and overwhelming to navigate in Win7.

I didn't say it was bloated :-) I would like it if it ran on 256. I also have a laptop from way back which runs on 64. I used it with WinME back in the day. It origianlly had Win95, but I upgraded for the fun of it :-)

---

### Post by Ric_NYC on 2011-08-09
[[IMG]http://img19.imageshack.us/img19/2329/comedyw.png[/IMG]](http://imageshack.us/photo/my-images/19/comedyw.png/)

---

### Post by dniMretsaM on 2011-08-09
> **Ric_NYC said:**
> [[IMG]http://img19.imageshack.us/img19/2329/comedyw.png[/IMG]]("http://imageshack.us/photo/my-images/19/comedyw.png/")

One word: win!

---

### Post by ki4jgt on 2011-08-09
> **Ric_NYC said:**
> [[IMG]http://img19.imageshack.us/img19/2329/comedyw.png[/IMG]](http://imageshack.us/photo/my-images/19/comedyw.png/)

Someone's got too much time on their hands :-), but WIN.

---

### Post by Martiini on 2011-08-09
haha
3 pages of replys :P

> **dinamic1 said:**
> windows 7 runs faster than ubuntu 11.04 (gnome classic) on my pc
+1
as impossible as it sounds, windows DOES run faster

> **Bandit said:**
> Performance is heavily based on system drivers for particular hardware just as much as the operating system. Win7 could easily run faster due to having better commercial drivers at hand, but that's not because of Win7. Its the drivers. If Ubuntu is running great on 99% of the other computers, and not on another. Huge chance its a hardware/driver issue. .....
+1 
actually, yes, I suspect intel driver is the culprit .. not .. kde, unity, number of processes .. etc

---

### Post by dinamic1 on 2011-08-09
> **Bandit said:**
> Performance is heavily based on system drivers for particular hardware just as much as the operating system. Win7 could easily run faster due to having better commercial drivers at hand, but that's not because of Win7. Its the drivers. If Ubuntu is running great on 99% of the other computers, and not on another. Huge chance its a hardware/driver issue. I have Ubuntu 11.04 on my system and have ran Win7 on it as well. They fair so close to the same I would have to run a benchmark to notice any differences. But then again I also purchased my computers components individually to insure I got a solid system for both Windows and Linux. This is something you cant do with an over the shelf store bought PC.

meh, i do the same thing and i have an nvidia card. a simple example will be flash/firefox on win7 vs on ubuntu. i mainly use ubuntu but meh it's just average at the best

---

### Post by christoph411 on 2011-08-09
Who runs KDE on a netbook anyway?

> **not found said:**
> *snip*
On a completely unrelated note, nice avatar! :D

---

### Post by Thewhistlingwind on 2011-08-09
top - 14:15:01 up 5 days, 19:54,  9 users,  load average: 2.24, 1.70, 1.33
Tasks: 193 total,   3 running, 185 sleeping,   5 stopped,   0 zombie
Cpu(s): 61.7%us, 16.8%sy,  0.3%ni, 21.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1478108k total,  1377616k used,   100492k free,    18784k buffers
Swap:  5079036k total,  1499932k used,  3579104k free,   278728k cached


Linux likes to use your RAM until you need it.

---

### Post by PhillyPhil on 2011-08-09
> **Bandit said:**
> You WANT your system to keep used programs loaded up into memory for later usage. This enables the system to reload the program faster in the future. The more RAM you have, the more resources can be allocated into RAM. Now if you open up something that is not already loaded into system RAM, dont fret because the system will quickly remove any resources already loaded to make way for the new program to load without any hurt in performance. 

This. Any unused memory is wasted memory.  You want as much cached as possible.

---

### Post by Frogs Hair on 2011-08-09
I run unity with Compiz effects and E17 . Unity comes in around 500 to 600 Mb and E17 is currently 308 Mb with Opera running .

---

### Post by smellyman on 2011-08-09
When I first go into linux it was fun resurrecting old machines and trying to squeeze out performance even if a system had plenty.  still is.

I have become more sane lately and it doesn't consume me any more. lol

Use up the ram if you got it.  Don't use kde if your netbook cant handle it.  pretty easy.


Arch KDE
```
             total       used       free     shared    buffers     cached
Mem:          3962       1538       2423          0         70        509
-/+ buffers/cache:        958       3003
Swap:         4220          0       4220

```

---

### Post by jerenept on 2011-08-09
> **Martiini said:**
> 
Ubuntu is slow! my nokia phone runs faster than this!


Hey, hey, hey!! My C1-01 is super awesome!! No bashing Nokia mmkay?

---

### Post by 3rdalbum on 2011-08-09
> **Martiini said:**
> "linux is the new windows", that claim is absolutely correctemundo....
running processes: 175 (!!!)
memory used: 535589k (!!!)

Linux is obviously not the new Windows if it's using 535MiB of RAM when all you've got open is Chromium.

My gf's Windows 7 computer is currently using 615 MiB of RAM on startup, with only Skype open. Skype is using 37 MiB, apparently.

Windows 7 is a lot older than Ubuntu 11.04; expect Windows 8 to use more RAM still.

Interestingly, I'm showing 218 MiB of RAM in use on Ubuntu 11.04; actual use, not including cache. This is with Chromium open, one tab.

---

### Post by 3rdalbum on 2011-08-09
Going a little bit off-topic here, why do Unity-2D and Unity-3D both exist? Unity 2D looks pretty good here, has a semi-transparent launcher and dash, and even does the workspace switcher and expose features in 2D. There's no "folding" effect on launcher icons, but the "sliding" effect also looks nice.

Unity-3D is faster for the switcher and expose, but I'd be surprised if they couldn't just implement 3D acceleration for those two things within the 2D version of Unity. And then they'd only have one real codebase to maintain. And they'd be left with more space on the CD.

---

### Post by uRock on 2011-08-10
> **3rdalbum said:**
> Going a little bit off-topic here, why do Unity-2D and Unity-3D both exist? Unity 2D looks pretty good here, has a semi-transparent launcher and dash, and even does the workspace switcher and expose features in 2D. There's no "folding" effect on launcher icons, but the "sliding" effect also looks nice.

Unity-3D is faster for the switcher and expose, but I'd be surprised if they couldn't just implement 3D acceleration for those two things within the 2D version of Unity. And then they'd only have one real codebase to maintain. And they'd be left with more space on the CD.

I haven't looked, but that may be a great idea worth sharing with the Ayatana mailing list.

---

### Post by smellyman on 2011-08-10
> **3rdalbum said:**
> Going a little bit off-topic here, why do Unity-2D and Unity-3D both exist? Unity 2D looks pretty good here, has a semi-transparent launcher and dash, and even does the workspace switcher and expose features in 2D. There's no "folding" effect on launcher icons, but the "sliding" effect also looks nice.

Unity-3D is faster for the switcher and expose, but I'd be surprised if they couldn't just implement 3D acceleration for those two things within the 2D version of Unity. And then they'd only have one real codebase to maintain. And they'd be left with more space on the CD.

I've wondered that too sometimes.

I haven't used Unity a whole lot, I give it a whirl now and again with oneiric and spent some time with natty.

I often don't know if it is 3d or 2d I am in.

of course I am blind in one eye.  maybe that is the problem.  :)

---

### Post by bradcan on 2011-08-10
Just my two-cents worth:

I, along with many old timers, am sick to the teeth with up-grades. I'm still running RedHat pre-Fedora, Fedora 6 I think, Ubuntu 8.10 (the version distributed by linuxcnc.org), WIN2K and even somewhere windoze 98 and would you believe it DOS 5. The reason... obvious all these systems have a degree of stability and some piece of software I still use.

My wife has been running Hardy Heron on an 800MHz PC which took me some pain to install after an abortive Fedora 6 (too slow) install. Now I have finally been pushed into an up-grade of that machine. Simply because the repos are long dead so installing anything has become a major problem. For my sins I decided to up to a supported version of Ubuntu. Big mistake... To get from 8.10 to 10.10 has to be done incrementally, and credit where credit is due, when I got there 2 days and 100 cups of coffee later our desktops and painful prior installations were all intact. :o Unfortunately, yes when I run anything, even a cups print, I'm 100% processor bound! :( Obviously one should read the minimum system requirements FIRST. Isn't hindsight wonderful?

The obvious solution is to archive the rops somewhere and publish how to configure them, so that people like us old farts can continue running what we know an love. (please:)

The problem now is do I switch to LUbuntu or some completely different distro?

I like Linux stability and hate Microsoft instability. Personally I think the Ubuntu trend towards windoze bloat and bling is the wrong way to go. On the other hand I recognise that I am perhaps in a minority.

---

### Post by PhillyPhil on 2011-08-10
> **bradcan said:**
> Just my two-cents worth:

I, along with many old timers, am sick to the teeth with up-grades. I'm still running RedHat pre-Fedora, Fedora 6 I think, Ubuntu 8.10 (the version distributed by linuxcnc.org), WIN2K and even somewhere windoze 98 and would you believe it DOS 5. The reason... obvious all these systems have a degree of stability and some piece of software I still use.

My wife has been running Hardy Heron on an 800MHz PC which took me some pain to install after an abortive Fedora 6 (too slow) install. Now I have finally been pushed into an up-grade of that machine. Simply because the repos are long dead so installing anything has become a major problem. For my sins I decided to up to a supported version of Ubuntu. Big mistake... To get from 8.10 to 10.10 has to be done incrementally, and credit where credit is due, when I got there 2 days and 100 cups of coffee later our desktops and painful prior installations were all intact. :o Unfortunately, yes when I run anything, even a cups print, I'm 100% processor bound! :( Obviously one should read the minimum system requirements FIRST. Isn't hindsight wonderful?

The obvious solution is to archive the rops somewhere and publish how to configure them, so that people like us old farts can continue running what we know an love. (please:)

The problem now is do I switch to LUbuntu or some completely different distro?

I like Linux stability and hate Microsoft instability. Personally I think the Ubuntu trend towards windoze bloat and bling is the wrong way to go. On the other hand I recognise that I am perhaps in a minority.
800mhz? Time for a hardware upgrade?
In absolute genuine sincerity, someone will probably give you a computer better than that for free.

---

### Post by XubuRoxMySox on 2011-08-10
I keep my old dinosaur zipping along sweetly using [COLOR="Purple"]Xubuntu[/COLOR] 10.04.

It's still supported for almost 2 more years, and the Xfce interface is easy to adapt to from the old familiar Gnome.

[COLOR="Blue"]Lubuntu[/COLOR] might seem a little less familiar and has fewer little extras, but it is even easier on resources than Xubuntu. The interface is "Windows 98-ish," according to an adult I know who uses it on a reeeeeally old computer with ease.

And I would definitely stick with the LTS edition for stability and long support.

Loving my [COLOR="Purple"]Xubu[/COLOR],
Robin

---

### Post by FlameReaper on 2011-08-10
> **Martiini said:**
> "linux is the new windows", that claim is absolutely correctemundo.
bloated, resource hungry, slow, junk software
Ubuntu is slow! my nokia phone runs faster than this!

This is what linux has become.
Im on Dell mini laptop.
Im running only standard kde, chromium, konsole.

running processes: 175 (!!!)
memory used: 535589k (!!!)

WFT !!!

top - 18:10:08 up  2:42,  2 users,  load average: 0.52, 1.88, 1.90
Tasks: 181 total,   4 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.3%us,  4.6%sy,  0.0%ni, 77.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1016772k total,   699032k used,   317740k free,     9648k buffers
Swap:   511964k total,   218812k used,   293152k free,   367016k cached

Pick one: Stop running KDE or stop running your netbook.

What use would you have for a DE which has one too many features you don't even need or know how to use and runs slowly on your hardware? Don't you know any better?

I use KDE, but even I can sense the heavyweightness it carries, which I can forgive for various reasons.

---

### Post by Paqman on 2011-08-10
> **bradcan said:**
> 
The problem now is do I switch to LUbuntu or some completely different distro?


A custom copy of a supported version of Ubuntu might run reasonably well. Start with the minimal ISO and only add the packages you want. You could try a lighter DE like LXDE, certainly.

However, I agree with PhillyPhil. You shouldn't have any trouble picking up a much better machine for free or next to free. Try Freecycle/Freegle in your local area, somebody probably has an old machine they can give you.

---

### Post by alexan on 2011-08-10
Ubuntu server.
Then:
sudo apt-get install jwm menu thunar

set thunar to manage the desktop.
Enjoy.

---

### Post by ki4jgt on 2011-08-10
> **alexan said:**
> Ubuntu server.
Then:
sudo apt-get install jwm menu thunar

set thunar to manage the desktop.
Enjoy.

QQ: wouldn't this method present some security probs?

---

### Post by XubuRoxMySox on 2011-08-10
> **ki4jgt said:**
> QQ: wouldn't this method present some security probs?

It probably *prevents* more security problems that might present themselves in a busier system.

-Robin

---

### Post by ki4jgt on 2011-08-10
> **dixiedancer said:**
> It probably *prevents* more security problems that might present themselves in a busier system.

-Robin

So, it wouldn't leave anything (server wise) open that would need to be closed?

Just asking, b/c I have a few older systems which need to run something.

---

### Post by XubuRoxMySox on 2011-08-10
> **ki4jgt said:**
> So, it wouldn't leave anything (server wise) open that would need to be closed?

I'm not sure I understand what you mean by "left open."

It's just an ultralight desktop interface with minimal stuff to steal resources from applications. JWM (Google "Joe's Window Manager") with Thunar (from Xfce) to manage the desktop would be really ultra light! I find Openbox to be "friendlier," but it depends on what you like and what you're aiming for (performance wise). Security is not an issue, and Thunar does not have to be left open in order to control the desktop.

-Robin

---

### Post by kerry_s on 2011-08-10
What I say "if your not using it, your waisting it". 
Why have lots of ram & not use it, if nothing else needs it. This is not ms where if u run to much it slows down. I think Linux manages better than that, I don't even worry about it anymore. It's simple just use your computer & let it do it's thing.

---

### Post by hhh on 2011-08-10
> **alexan said:**
> set thunar to manage the desktop.
Hee hee, how are you going to do that? :confused:

---

### Post by Rifester on 2011-08-10
AntiX

---

### Post by kerry_s on 2011-08-10
> **hhh said:**
> Hee hee, how are you going to do that? :confused:

he was probably thinking pcmanfm, since we all know that thunar can not manage the desktop. but then again he could always install xfdesktop4+thunar then he'll be good to go.

---

### Post by hhh on 2011-08-10
> **kerry_s said:**
> he was probably thinking pcmanfm...
That's what I thought too (or maybe ROX), but since Dixie repeated it I wanted to point the mistake out. There is too much incorrect information on this forum and in the Linux world .

---

### Post by Linux_junkie on 2011-08-11
I'm running Gnome 2.30 and using following system resources...

---

### Post by Paqman on 2011-08-11
> **alexan said:**
> Ubuntu server.
Then:
sudo apt-get install jwm menu thunar

set thunar to manage the desktop.
Enjoy.

Why server? Using a command line only install from the minimal or alternate image would make more sense, surely?

---

### Post by kerry_s on 2011-08-11
> **Paqman said:**
> Why server? Using a command line only install from the minimal or alternate image would make more sense, surely?

some people still don't even know there is a mini.iso, there just thinking cli install, not a big deal.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by uRock on 2011-08-11
My system hard at work running gnome 2.30 and gnome 3.```
rabbit@ronnie-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1944       1918         26          0          2        221
-/+ buffers/cache:       1695        249
Swap:         2078         17       2061

```

---

### Post by ilovelinux33467 on 2011-08-11
Fedora KDE
```

[andrew@localhost]~% free -m
             total       used       free     shared    buffers     cached
Mem:          8001       3591       4409          0        214       2312
-/+ buffers/cache:       1064       6936
Swap:        10047          7      10040

```

---

### Post by el_koraco on 2011-08-11
Is this gonna be a "post your free -m" thread? What the hell, openbox with Aurora, Dropbox, some file management going on and MOC

free -m
             total       used       free     shared    buffers     cached
Mem:     1766       1606        159          0         79       1044
-/+ buffers/cache: 482       1283
Swap:    3450          0       3450

---

### Post by kerry_s on 2011-08-11
```
             total       used       free     shared    buffers     cached
Mem:          2003       1941         62          0         48       1676
-/+ buffers/cache:        216       1787
Swap:            0          0          0

```

lubuntu 11.04

---

### Post by bradcan on 2011-08-11
> **Paqman said:**
> However, I agree with PhillyPhil. You shouldn't have any trouble picking up a much better machine for free or next to free. Try Freecycle/Freegle in your local area, somebody probably has an old machine they can give you.

Think you missed the point! It's not the hardware, more the inevitable days of research and instalation.

The definition of bloat: Systems become so big and difficult to understand they die an inevitable death.

---

### Post by XubuRoxMySox on 2011-08-11
> **hhh said:**
> That's what I thought too (or maybe ROX), but since Dixie repeated it ["Let Thunar manage the desktop"] I wanted to point the mistake out. There is too much incorrect information on this forum and in the Linux world .

I did do that, didn't I? Shouldn't have, I'm sorry. PCManFM manages the desktop. I had that setup in Openbox on Ubu 9.04 and it rocked.

-Robin

---

### Post by ninjaaron on 2011-08-11
> **dniMretsaM said:**
> Nokia may very well be running Linux as well. Just pointing that out.
As far as I know, All nokia phones until very recently run some form of Linux or another.

---

### Post by Paqman on 2011-08-11
> **bradcan said:**
> Think you missed the point! It's not the hardware, more the inevitable days of research and instalation.


On better hardware there's not likely to be any need for fiddling about with it. Just install and go.

---

### Post by bradcan on 2011-08-12
> **Paqman said:**
> On better hardware there's not likely to be any need for fiddling about with it. Just install and go.

Only if what the install does is right first time! Mostly that's only true for simple non-networked desktop installations. Actually it's never like that in my experience!

Here's just a simple example: For many years I've been using Samba to allow access from the network to Linux printers. Mostly the development of cups and samba has progressed without a significant hitch, but now an upgrade to 10.04 causes the annoyingly trivial glitch that smbd must be re-started manually before any printer shares are available to the network. So... delving under the hood I discover that the developers, for some presumably very good reason, have introduced the aptly named 'upstart' as an adjunct/alternative to the well beloved, highly stable, and most importantly understood by most admins, sysv init service start up mechanism.

Have a go at understanding cups and samba configuration then add to that upstart. Just so users can browse for printers, just like they do in windoze? I'm not complaining, just letting you know that your install and go is a total illusion. OK you did hedge with a likely. I my view most unlikely.

There is a growing trend towards making Linux do just as you suggest, 'just install and go'. Unfortunately the only happy installers are those seduced into mistakenly accepting slick installs as a substitute for stability. 

Bloat kills operating systems because, eventually, the work to understand increasing complexity becomes too great. It's a fundamental tenet of Linux that ultimately it's all understandable with effort.

---

### Post by uRock on 2011-08-12
> **bradcan said:**
> Only if what the install does is right first time! Mostly that's only true for simple non-networked desktop installations. Actually it's never like that in my experience!

Here's just a simple example: For many years I've been using Samba to allow access from the network to Linux printers. Mostly the development of cups and samba has progressed without a significant hitch, but now an upgrade to 10.04 causes the annoyingly trivial glitch that smbd must be re-started manually before any printer shares are available to the network. So... delving under the hood I discover that the developers, for some presumably very good reason, have introduced the aptly named 'upstart' as an adjunct/alternative to the well beloved, highly stable, and most importantly understood by most admins, sysv init service start up mechanism.

Have a go at understanding cups and samba configuration then add to that upstart. Just so users can browse for printers, just like they do in windoze? I'm not complaining, just letting you know that your install and go is a total illusion. OK you did hedge with a likely. I my view most unlikely.

There is a growing trend towards making Linux do just as you suggest, 'just install and go'. Unfortunately the only happy installers are those seduced into mistakenly accepting slick installs as a substitute for stability. 

Bloat kills operating systems because, eventually, the work to understand increasing complexity becomes too great. It's a fundamental tenet of Linux that ultimately it's all understandable with effort.

I have not experienced any of those problems. If you don't want a bloated system which just works, then maybe Arch or one of the other custom install distro would be better suited for you.

---

### Post by 3rdalbum on 2011-08-13
> **ninjaaron said:**
> As far as I know, All nokia phones until very recently run some form of Linux or another.

Well, no.

Nokia dumbphones and some feature phones run Series-40; a super-slim operating system for mobile devices. Proprietary, I think, and not based on Linux.

Nokia smartphones and better feature phones run Symbian; a fairly efficient mobile operating system that is open-source, but not Linux.

Only a couple of Nokia devices such as the new N9 and the N900 run Linux in the form of Maemo.

---

### Post by Martiini on 2011-09-05
follow-up to this rant I posted.
installed crunchbang-10-20110207-xfce-i686.iso
and am very happy with it right now
not sure how they've tweaked it or what they've done with debian kernel and rest of OS but
the whole system feels solid, light and responsive. 
EVERYTHING works!, including touchpad tapping and other tiny things (except broadcom wireless which I had to install obviously)
bootup is fast, apps open in instant, firefox scolling is smooth ..etc
and I found sizable Dell Mini community on crunchbang forums

root@dell:/home/martin# free +m
             total       used       free     shared    buffers     cached
Mem:       1025128     799904     225224          0      27132     639824
-/+ buffers/cache:     132948     892180

top - 00:00:55 up 55 min,  3 users,  load average: 0.08, 0.05, 0.09
Tasks: 139 total,   2 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.1%us,  2.0%sy,  0.0%ni, 94.8%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   1025128k total,   803272k used,   221856k free,    27180k buffers

---

### Post by alegomaster on 2011-09-05
alex@alex-NV52-Series:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3706        922       2784          0         39        354
-/+ buffers/cache:        528       3178
Swap:         3836          0       3836
alex@alex-NV52-Series:~$ 

Gateway nv52 4gigs of memory

---

### Post by GSF1200S on 2011-09-05
Try Arch and Openbox w/ xfce4-panel and tell us if that system is slow.

Ubuntu is not targeted at bottom-of-the-barrel systems- its targeted at the mainstream. Arch isnt targeted at anything- build it yourself and profit. Gentoo would spend too much time compiling on that system. There are also distros which target weaker systems (DSL, Puppy, etc), so...

---


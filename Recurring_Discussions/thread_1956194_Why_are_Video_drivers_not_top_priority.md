---
title: "Why are Video drivers not top priority"
date: 2012-04-10
forum: Recurring Discussions
---

### Post by ToxicBurn on 2012-04-10
I only post when I have a problem and as you can tell all my posts are about the total lack of video card drivers in Linux . My question is why are Good 3D drivers from Amd / nvidia not on the top of the list before anything else in a distro ? 

How can you ship a product that Only kind of works with very poor 3d support 

Apple ships with a fully working driver for Amd cards and it's unix 

It makes me angry every time I want to try the latest Ubuntu release only to find out I have no way to get drivers installed . This should not be hard to do . Either make sure it works like apple or let end users like me just click a few buttons and install a version of a driver that will work . 

How many years has Linux been around and hue many more is it going to take for it to understand that you are not going to ever move forward if you can not even install a simple graphics driver .

Amd has a Linux driver on the site - ubuntu's Job is to make sure it's own distro can run it. 

I almost feel I just need to give up 100% on Linux because Ubuntu only does one thing for me every release and thats make me mad I can't install a simple driver .


Feel free to defend Ubuntu if you wish but you know I am correct. 

This is something that should have been fixed the very second a kernel freeze is done 

This is why Linux can not even reach 1%

---

### Post by PhantomTurtle on 2012-04-10
(I would like to mention, before I begin, that this might not be the correct part of the forums to post this.)First of all, I use an AMD card and it works absolutely fine, but I know that a lot of AMD cards on Linux do not work well. Ubuntu and AMD are both to blame for this, since Apple seems to be doing fine with their drivers. It is mostly AMD's fault for not making the Linux drivers as good as the Windows ones. Ubuntu I thing tries much harder than AMD to get the drivers working and makes it very easy for the user to get it working the first time around. They made it easy by including the Additional drivers program which will handle it for you. I think that if AMD tried a little bit harder to get their Linux drivers on par with the Windows and Mac drivers we would not have as many problems as we do right now. Anyways that's just my opinion.

---

### Post by Mark Phelps on 2012-04-10
I'm going to try to respond to specific points you made, before I provide a general response ...

> **ToxicBurn said:**
> I only post when I have a problem and as you can tell all my posts are about the total lack of video card drivers in Linux .
"total lack" is entirely wrong.  I'm using Ubuntu 11.10 with an AMD HD 42xx series chipset, using multiple monitors, with differene resolutions, and not only does all of the work fine, I can play Blue-Ray videos realtime on my desktop with no loss of video fidelity.  And ... this is using the Radeon open-source drivers.

> My question is why are Good 3D drivers from Amd / nvidia not on the top of the list before anything else in a distro ?  Maybe ... because in many cases, the open-source drivers work just fine.  If you're trying to run MS Windows games and encountering DirectX video rendering problems -- that's entirely a different problem in that, basically, you're using the wrong OS.

But, if 2D video works OK, other things will get higher priority -- naturally.

> How can you ship a product that Only kind of works with very poor 3d support?  Because, only a small portion of the Linux community really needs hardware accelerated 3D support. Developers, like everyone else, have limited time and that tends to be focused on fixing major problems and adding new features -- not on something that very few people (relatively speaking) use.

> It makes me angry every time I want to try the latest Ubuntu release only to find out I have no way to get drivers installed . This should not be hard to do . Either make sure it works like apple or let end users like me just click a few buttons and install a version of a driver that will work . 
The "solution" (back when I used to mess around with restricted drivers) was to use Envy to do this.  But the author dropped support.  And now, I will agree that it appears to be a lot harder to do this right than it should be.

> How many years has Linux been around and hue many more is it going to take for it to understand that you are not going to ever move forward if you can not even install a simple graphics driver . Really!  You're claiming the main reason that Linux hasn't overtaken MS is the inability to easily install restricted video drivers?  This is a joke, right?

> Amd has a Linux driver on the site - ubuntu's Job is to make sure it's own distro can run it.  No argument -- should be easier than it is.

> I almost feel I just need to give up 100% on Linux because Ubuntu only does one thing for me every release and thats make me mad I can't install a simple driver ... This is why Linux can not even reach 1%

If this WERE true, back in the days when Envy made this quick and simple, we (Linux) would have DOMINATED the PC industry -- which, as we know, was not the case.  I really don't think bringing something like Envy back is going to change the Linux presence in the PC community.

---

### Post by ToxicBurn on 2012-04-10
As a windows user and a mac user coming to try Linux to install Ubuntu and not have 3d support in the year 2012 is a joke at best . This should not even be an issue these days. I would like to use linux but as you said only a few people need 3d support in Linux and I am using the wrong OS if that's what I need. 

What a joke

---

### Post by habana on 2012-04-10
I think you've answered your own question. Most people don't need 3D support so why should the developers make it a top priority?

Ubuntu does more or less everything I need but it isn't for everybody. If you find another o/s better meets your needs then go ahead and use it.

---

### Post by xedi on 2012-04-10
But Ubuntu HAS 3D support! I'm not even 100% sure what specific problems you have. I myself like the majority have an Intel GPU which accelerates 3D in Ubuntu out of the box, my father has an ATI GPU which worked immediately and Ubuntu even asked whether we would like to install proprietary drivers which you can do with a single click.

---

### Post by ToxicBurn on 2012-04-10
I have a AMD HD6870 and need full AMD 3d support because I play 3d games and the additional drivers Ubuntu says they have for my card that have been tested by the devolper fail to install and do not work and have been reported by more then 1000 people . 

I'm not waisting  any more time on this crap back to windows were I know things work - I have no idea why I keep thinking Linux will get better each year it's still the same problems as it was six  years ago. 

What a headache Ubuntu is .
people wonder why Linux is a hobby OS mark this issue as one major reason it will never see the light of day.

---

### Post by jadtech on 2012-04-10
so toxicburn

let me get this right  you have sent off email to development leader  offering your undivided attention for free to developing  these driver and freely share there source code with the world ??? 

because unless you are a part of the solution you become part of the problem ...

---

### Post by 23dornot23d on 2012-04-10
Have a read here 

[http://www.linuxquestions.org/questions/linux-hardware-18/aticonfig-fglrx-error-on-debian-with-card-radeon-hd-6870-a-888500/](http://www.linuxquestions.org/questions/linux-hardware-18/aticonfig-fglrx-error-on-debian-with-card-radeon-hd-6870-a-888500/)


Also search on your card and solved .....

[https://www.google.com/search?client=ubuntu&channel=fs&q=AMD+HD6870+solved&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=o7k&channel=fs&sclient=psy-ab&q=linux+AMD+HD6870+solved&oq=linux+AMD+HD6870+solved&aq=f&aqi=&aql=&gs_l=serp.3...29578l31460l0l31597l6l6l0l0l0l0l248l940l0j5j1l6l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=8085291c906fc915&biw=1148&bih=473](https://www.google.com/search?client=ubuntu&channel=fs&q=AMD+HD6870+solved&ie=utf-8&oe=utf-8#hl=en&client=ubuntu&hs=o7k&channel=fs&sclient=psy-ab&q=linux+AMD+HD6870+solved&oq=linux+AMD+HD6870+solved&aq=f&aqi=&aql=&gs_l=serp.3...29578l31460l0l31597l6l6l0l0l0l0l248l940l0j5j1l6l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=8085291c906fc915&biw=1148&bih=473)

Some people have success ..... 


The next release 12.04 ..... is also picking Graphics Cards of a better specification
a lot better too ..... wait till the end of the month then try ......

or look for a solution ..... from what I can see - the solution is to use the latest 
release ...... but the 12.04 is not due officially for another 2 weeks or so

---

### Post by PhantomTurtle on 2012-04-10
> **ToxicBurn said:**
> I have a AMD HD6870 and need full AMD 3d support because I play 3d games and the additional drivers Ubuntu says they have for my card that have been tested by the devolper fail to install and do not work and have been reported by more then 1000 people . 

I'm not waisting  any more time on this crap back to windows were I know things work - I have no idea why I keep thinking Linux will get better each year it's still the same problems as it was six  years ago. 

What a headache Ubuntu is .
people wonder why Linux is a hobby OS mark this issue as one major reason it will never see the light of day.

You know there are only so many developers and AMD has a lot of Radeon cards. They can only work on one at a time. You seem to want to blame Linux for not being able to run with your graphics card, when you should be blaming AMD. The drivers are made by AMD. This makes it AMD's fault for not making good drivers, don't blame Linux. Also I have an AMD Radeon 6410 and the drivers installed fine on Ubuntu, and it works amazingly well. Also about your hobby os comment, I use Ubuntu as my main OS and I am not a hobbyist. I use it for serious work and it functions fine for me.

---

### Post by jadtech on 2012-04-10
> **ToxicBurn said:**
> 

What a headache Ubuntu is .
people wonder why Linux is a hobby OS mark this issue as one major reason it will never see the light of day.

hobby ???? 

tell the group at red hat they are a hobby 


On July 27, 2009, Red Hat replaced CIT Group in Standard and Poor’s 500 stock index, a diversified index of 500 leading companies of the U.S. economy. This has been reported as a major milestone for Linux.

 Red Hat became the first one-billion dollar open source company in its fiscal year 2012, reaching $1.13 billion in annual revenue.

i wish I had a hob by like that!!

---

### Post by ToxicBurn on 2012-04-10
Non are desktop clients with needs of 3d graphics - mostly file servers

---

### Post by jadtech on 2012-04-10
no matter what about smart phones android this to is Linux driven as well Linux is far from a hobby, many many technology s are driven by Linux and the more it becomes everyday the more support for these things it will gain..

just to look  where things are heading , with mac and Microsoft pouring more of there efforts into phones and tablet and away from  desktop and lap top market could be the not to distant future most will be using and looking far more to Linux, i'm not saying  in any way windows or mac are going away any time soon over night  though the steps  they are taking are huge steps in that direction more every day..


adding all technology's together if not already in a short time there will be more  supported by linux in some varity then by windows ...

or like others have been trying to tell you  the need of the many  out weight the want of the  few ..

as for how long not nessarily Linux but the open source movement has been around  and how big it has became and how far it has came..

you would have to remember a OS know as DR-Dos original copy write i can find  on versions is 1976, DR-DOS is and was the first OS base for not Only IBM but Apple and Microsoft operating systems by today's standard this hobby seed that generated trillions of dollars  was taken for basically nothing..

long  story short DR-DOS later went to be known as MS-DOS , Gary Kildall who Developed DR-DOS went on to develop GEM the first GUI interface which was stolen by MicroSoft emulated by apple..

it all started as part of a concept since only the vision of the PC existed this is where open source and linux roots are from ..

---

### Post by Linuxratty on 2012-04-10
> **jadtech said:**
> hobby ???? 

tell the group at red hat they are a hobby 

!

Agreed...Now THIS is how Linux is made...Watch and you will see this is definitely not a hobby OS.

[http://www.youtube.com/watch?feature=player_embedded&v=yVpbFMhOAwE](http://www.youtube.com/watch?feature=player_embedded&v=yVpbFMhOAwE)

---

### Post by jadtech on 2012-04-10
moral of the story if you want something in open source and you cant find it get a group of friends together and build it for your self ..

---

### Post by CharlesA on 2012-04-10
> **ToxicBurn said:**
> Non are desktop clients with needs of 3d graphics - mostly file servers
Source?

In any case, best of luck with Windows.

---

### Post by leecheroflife on 2012-04-11
I think it kinda sad that you've felt the need to result to "Oh noes! It's broken, instead of fixing, i'm gonna complain and run away" 

Would it not be more constructive to find the workaround that works FOR YOU and then post it up so others who might struggle can get the situation resolved? Linux is very much community oriented, everyone helps everyone, We all test, we all look for solutions.

I understand you're frustation with the driver support though, I can understand that you're having an issue, but it sounds like it's a card specific issue relating to a driver, not a "linux" issue per se.

But, if you genuinely feel that you're better of taking the windows route because "it just works" than fare enough. Thats understandable.

[SIZE=1]*cough* or get an nvidia card *cough*[/SIZE]

---

### Post by terrykiwi83 on 2012-04-11
> **ToxicBurn said:**
> I have a AMD HD6870 and need full AMD 3d support because I play 3d games and the additional drivers Ubuntu says they have for my card that have been tested by the devolper fail to install and do not work and have been reported by more then 1000 people . 

I'm not waisting  any more time on this crap back to windows were I know things work - I have no idea why I keep thinking Linux will get better each year it's still the same problems as it was six  years ago. 

What a headache Ubuntu is .
people wonder why Linux is a hobby OS mark this issue as one major reason it will never see the light of day.

Linux is not currently designed with full 3D gaming in mind (The likes of COD, Battlefield 3..etc). Linux is a solid developers tool, and as you are not a developer but a gamer then you should stick with Windows and put Linux away. Problem Solved! No buts or whys......just simply pay for Windows.

---

### Post by leecheroflife on 2012-04-12
> **terrykiwi83 said:**
> Linux is not currently designed with full 3D gaming in mind (The likes of COD, Battlefield 3..etc). Linux is a solid developers tool, and as you are not a developer but a gamer then you should stick with Windows and put Linux away. Problem Solved! No buts or whys......just simply pay for Windows.

At the same time though, I'm a gamer and sure as hell not a developer, I use Linux, most things work under wine, if they don't I have a windows partition for new games and an XP virtual machine for old games.

---

### Post by jjpcexpert on 2012-04-12
Intel and the Linux devs have been working like crazy, and I have full 3D support on my desktop with an 82865G (i915) graphics chip at 128MB of VRAM - better yet, I had 32MB on my Latitude C540 (VRAM of course, RAM was 128MB) and Compiz ran fine! And that was a really old ATI. Of course, I do not use the 3D cube or any other weird Compiz effects anymore, I only use it because switching windows feels smoother with it. No fade, just use Compiz plain and simple. Also, if you use Compiz on an old desktop, disable the Movie Player, Rhythmbox and Banshee visualizers. They're unnecessary CPU load. So if you want smooth windowing, and have a 3D accelerator, use a minimalist Compiz setup. If Compiz won't run, use Mutter or Metacity w/Composite for smoother window switching. And I expect the Nouveau community have been working like crazy to reverse engineer the Nvidia driver, and many other Linux graphics developers, especially the creators of the Radeon free driver, have been working so hard. Give back something, even just a comment saying about how good the driver is and that you respect the developers' rights. It's a background top priority, as video is needed to even use the pseudo TTY.

---

### Post by TBABill on 2012-04-12
> **ToxicBurn said:**
> I have a AMD HD6870 and need full AMD 3d support because I play 3d games and the additional drivers Ubuntu says they have for my card that have been tested by the devolper fail to install and do not work and have been reported by more then 1000 people . 
 
I'm not waisting any more time on this crap back to windows were I know things work - I have no idea why I keep thinking Linux will get better each year it's still the same problems as it was six years ago. 
 
What a headache Ubuntu is .
people wonder why Linux is a hobby OS mark this issue as one major reason it will never see the light of day.Ok, I'm going to have to agree with a small piece of your claim first. Any user that tries ubuntu and does not know that the proprietary driver Ubuntu offers will not work is in for quite the struggle and a lot of frustration. It's broken and has been broken, but if someone is new and tries it there is a guarantee of failure, yet Ubuntu devs have not taken steps to either remove the capability of installing the broken driver or packaged the correct, working driver.
 
Beyond that the rest is trollish (Ubuntu is crap, going back to Windows, etc.). There are numerous websites out there with extremely simple, step-by-step instructions to download, install and activate the proprietary driver. Not only will the machine perform a bit better, but temps will drop as well. I do this regularly for my HD 4250 and it is as simple as a few lines in a terminal copied and pasted from a website. 
 
I do think if Jockey is going to tell a user a driver is available, the setup of that driver via GUI should at least work. If not, what would a new user be led to believe? Probably that their install of Ubuntu is borked, which is not the case. I also think the devs should fix this issue for the Broadcom wireless BCM4311 setup since it sets up the driver incorrectly, yet handles it correctly for the BCM4312. Ubuntu devs should either fix it or reconfigure Jockey to not offer the driver that will not setup correctly.
 
I recently bought a Macbook Pro and I can confirm the setup, use and simplicity is amazing. Very little difference between BSD-based Mac use and use of a linux distro. Made the transition simple to understand. Now I have a few windows machines, a Mac and a few Linux machines all happily co-existing and all of them running correct drivers.

---

### Post by Bandit on 2012-04-14
> **ToxicBurn said:**
> I only post when I have a problem and as you can tell all my posts are about the total lack of video card drivers in Linux . My question is why are Good 3D drivers from Amd / nvidia not on the top of the list before anything else in a distro ?...........................................

I will explain this to you the best I can.
For one, ATI and nVidia dont work for Ubuntu or any Linux distributor.
Second since they dont get paid to produce Linux drivers, they dont make producing them THEIR top priority. Although given that I feel they do a dang good job. I have yet had a modest nVidia or ATI video card not work. Now IMHO the nVidia ones have did very very well with ATI ones lagging somewhat. But still they both perform great for a non gaming OS. So if you want to complain about poor linux support, NV or ATI forums are your place to start. 
Now his is #3 reason.. Both NV and ATI drivers are NOT OPEN SOURCE although recently I think this may be changing. So what open source drivers that are out there have been backwards engineered. AKA hit and miss guesswork.
So if you feel your need to complain or rant here your wasting your time, basically your preaching to the quire. Hit the ATI and NV forums to deliver your thoughts and feedback.

Thank you and have a splendid day..

---

### Post by QIII on 2012-04-14
I have both full 3D support and full, glass-smooth HD 1080p video hardware acceleration.  Rotating cubes, stand out windows on rotation, the whole thing.

VDPAU works just fine.

AMD doesn't use VDPAU because that is proprietary to NVIDIA.

But AMD cards work just fine with VAAPI and the XvBA back end.  AMD doesn't use proprietary hardware acceleration because VAAPI is a cross hardware standard and it can be enabled on Ubuntu by adding 4 packages.

(By the way, the proprietary drivers for ATI offered by Ubuntu DO work.  In fact, ATI schedules releases to coincide with Ubuntu releases and makes sure the latest is available for the repo just prior to release. They even align their version numbers with the Ubuntu version numbers.  That alignment goes back quite a while.  Phoronix has an article about Ubuntu getting the AMD candy before anyone else does every time Ubuntu comes out with a new release.)

Gaming support?  Well, maybe we should ask the companies that make millions writing games for Windows to make sure their products work on Linux.

3D and HD are perennial complaints about Linux that have nothing whatsoever to do with Linux since no distributor is a hardware OEM -- but, strangely, they DO work.

Bottom line:  You DO have 3D support in Linux.  You DO have HD hardware acceleration in Linux.  This is a non-issue other than for trolls.

---

### Post by TBABill on 2012-04-18
> **QIII said:**
> (By the way, the proprietary drivers for ATI offered by Ubuntu DO work. In fact, ATI schedules releases to coincide with Ubuntu releases and makes sure the latest is available for the repo just prior to release. They even align their version numbers with the Ubuntu version numbers. That alignment goes back quite a while. Phoronix has an article about Ubuntu getting the AMD candy before anyone else does every time Ubuntu comes out with a new release.)That's actually a semi-false statement. I cannot say it's a fully false statement simply because I have not tried to install the driver fully from the command line. However, via Jockey the driver will not install or work properly. It's been that way for at least a couple releases now for ATi cards. I have one, I've lived it. 
 
The drivers from AMD directly DO work properly once installed via terminal. They are wonderful and far superior to the open source driver, at least in terms of heat generation. 
 
The OP wasn't trolling so much as complaining somewhat truthfully. New users who click the offered driver via the GUI that automatically pops up after install will continue to be frustrated and think Ubuntu is fundamentally broken so long as the devs leave a broken driver and/or installer in place as they have so far. I haven't found anyone yet whose system took the offered driver successfully via jockey in 11.10 (and Mint 12 and Ultimate Edition 3.2, which are based on 11.10) or the beta of 12.04.

---


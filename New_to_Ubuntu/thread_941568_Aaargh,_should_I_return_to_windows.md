---
title: "Aaargh, should I return to windows?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by thesleepymoose on 2008-10-08
Forgive me for being an absolute noob to Linux but I haven't been able to get Ubuntu Studio (Hardy 86) to install correctly on my new machine. I'm running a clean install on a dedicated hard drive (no windows!):

M2N SLI    (no on board graphics or VGA-out)
AMD PHENOM QUAD 9550
4GB DDR2 RAM
MAXTOR 500GB HDD (SATA)
NVIDIA 9500 GT 1GB        (which I suspect is the prob)

All I wanted was to try my hand at Linux due to my growing frustration with Microsoft. I am on the verge of returning to that corporate blood-sucking she-devil so please help me out.

After install, all I get is CLi. Tried lots of things on different forums but to no avail.
I'm wandering if I should have installed Hardy 64 Ubuntu Studio instead.

I'm at a loss and need someone to hold my hand in decifering this.
I think it'll be best if I uninstall this distro and then install Ubuntu 64 version. But how?

---

### Post by Paqman on 2008-10-08
> **thesleepymoose said:**
> 
After install, all I get is CLi. Tried lots of things on different forums but to no avail.


What result do you get when you try:
```

startx

```

---

### Post by Commander_Keen on 2008-10-08
If you have a 2nd pc.. all you would have to do is d/l the OS
the OS will re format the HD and install.

---

### Post by Bucky Ball on 2008-10-08
> **thesleepymoose said:**
> 
I think it'll be best if I uninstall this distro and then install Ubuntu 64 version. But how?

If you have a 64bit machine, the AMD 64 version is the one you want. That is probably not what is causing this problem though. As a previous post mentions, what do you get when you type:

```
startx
```?

If you can get on line via an ethernet cable, you could try this:

```
sudo apt-get install ubuntustudio-desktop
```... and see if that gets you up. I've found ubuntu studio to be a little quirky, but it all works out in the end.

If you just want to try your hand at Linux, I would advise you to just install the regular Ubuntu - Hardy AMD 64 desktop version. Studio is *very* specific to audio/visual/mulitmedia creation. :)

---

### Post by thesleepymoose on 2008-10-08
@Paqman
When I try startx:
The program 'startx' is currently not installed. You can install it by typing : sudo apt-get install xinit.

@Commander_Keen
D/l'd the latest ubuntu 64 studio and tried it today but it said it couldn't mount cd. MD5 was correct and I verified the dvd after I burnt it against the ISO all on this comp with xp sp3.

@Bucky Ball
Can't seem to get apt-get to work. When I installed it I had the only net connection tied to this xp machine so I could troubleshoot and read forums etc. Would that effect anything or do I just need to add repositories. How do I check?

---

### Post by Sef on 2008-10-08
Do you have the same problem if you run the Live CD?

---

### Post by Keen101 on 2008-10-08
I'd like to say try not to give up yet. I've been in a similar position about 4 years ago. But, i figured out a solution, and now i use Linux everyday. I love it.


If you decide to remove the current partitions, which you might have to... I recommend GParted Live-CD. It's a nice GUI based partition editor.

as for 64 bit it's really up to you. Both should work about the same. 64bit will have advantages in the future when programmers program for 64 bit systems better.

While i admit the ubuntu studio edition is very tempting to try myself, there really is no to. The "regular" ubuntu doesent come with all those graphics programs preinstalled, but you can easily install them later (which i have installed most of them on my regular ubuntu).

I would recommend trying the "regular" ubuntu Live-CD version too. It probably will work better, but i don't know for sure.

---

### Post by thesleepymoose on 2008-10-08
@Sef
What's the difference between a live CD and whatever you call the other thing? Couldn't see a LiveCD on Ubuntu Studio's site. 

I'm D/L'ing vanilla Ubuntu 64 and I'll see if that fairs any better. I can always add the editing programs later can't I? Can't I?

@Keen101
I'm not using a partition but the whole HDD for the install while I learn, then I'll complicate things later. A simpletons approach first for a Linux simpleton :)

Thanks everyone for your time, I'm not giving in yet so pleas stay with me.

---

### Post by Commander_Keen on 2008-10-08
64 bit ISO Question.
 Which Cd/DVD's are you using?
 Lower your Burning speed.. If possible try burning @  2x or 4x. 
I am under the impression that  9/10 times you will get better results from buring at a slower speed.

---

### Post by eternalnewbee on 2008-10-08
This is from the heart.
I've been using Ubuntu on & off since 2005 and full time since 2007.
I've had (for 95%) excellent advice from knowledgeable and patient people.
I really didn't like the title of your thread. Really, no offense meant, but it just sounded threatening... 
Sorry. Had to get that one out.
I was even more amazed, seeing responses not to give up yet! Depending on my mood I can see where they are coming from, but still..
You shouldn't be threatening or kissing A. here.
Instead you should appreciate that a lot of people make and take the time to help you, not expecting anything in return from you...
Peace.

---

### Post by SunnyRabbiera on 2008-10-08
Well maybe a Ubuntu flavor is not in your future, give other distros a try, such as Mandriva.

---

### Post by eternalnewbee on 2008-10-08
That sounded better, SunnyRabbiera

---

### Post by Nxion on 2008-10-08
what happends when you run:

```
sudo apt-get update
```

What is the error you get?

Also you mentioned that you are having network issues. Could you be more specific? Is it interment? 

Nx

---

### Post by iKonaK on 2008-10-08
no, you should install ubuntu hardy from live cd (you'll also see that way if your internet is working and also the graphics, sound, you get my point...) and then install  what part and even all studio app's you want.
```
sudo apt-get install [SIZE=2]ubuntustudio-audio
[/SIZE]sudo apt-get install [SIZE=2]ubuntustudio-video
[/SIZE]sudo apt-get install [SIZE=2]ubuntustudio-graphics
[/SIZE]sudo apt-get install [SIZE=2]ubuntustudio-plugins[/SIZE]

```
take a look at [this page ]("https://wiki.ubuntu.com/UbuntuStudio/PackageList")

---

### Post by Nxion on 2008-10-08
Another thing is if you wanted to is install a different flavor of Ubuntu. For example Xubuntu or Kubuntu. Is there a specific reason why you chose Ubuntu Studio?

Nx

---

### Post by thesleepymoose on 2008-10-08
@Commander_Keen
Have just D/L'd 
ubuntu-8.04.1-desktop-amd64.iso
I'll try this and get back to you. I always burn at 4x, I'm rarely in a rush and prefer to have a quality burn.
Thanks for the input.

@eternalnewbee
Thanks for the honesty. Sorry if the title seemed threatening, I didn't mean it like that. I am a 2-day-old in this vast and complex land of Linux and as any new born, I was frustrated. My cries for help were a heartfelt plea  because I am a Linux orphan with no parental unit to hold me steady as I take my first tentatively shaky steps. I am certain Linux is the way forward for me but I needed to vent my anguish. That said I understand now how it came across and I'll be more considerate and appreciative in the future. Thank you.
Who knows one day I'll be writing your words in a few years time to a youngling.

As for the other suggestions, thanks, if this one doesn't work I'll try them.

I'll try the new dvd and return in the morn with an update.
Happy birthpains everyone

---

### Post by thesleepymoose on 2008-10-09
Hi everyone, thanks for all your help and suggestions,
things are still bad, Ubuntu Live CD freezes at the orange bar after I select anything from the menu (Check CD, Run Live etc.) The top half of the orange bar jumps down the screen and then everything just freezes there. Left it like that for over 20 min before a reboot in case it was loading. I still think it might be a video card compatibility prob . Is there a distro that is definitely compatible with the Sparkle 9500 GT? Or is there a graphics card anyone can suggest.

I installed an old XP SP2 CD just to confirm all the hardware was intact and everything was as it should be. There doesn't seem to be any probs.

@Nixion
I'm hoping to make a v.low cost short film and was wanting all the beautiful studio software Studio offered. I thought it would be the easiest way. But now I realise I can apt-get them, I'll try to get a distro working first. One thing at a time hey.

D/L'ing Mandriva, Xubuntu, Kubuntu, LinuxMint, PCLinuxOS and Slackware. I'll try them since they've all been known to work better with temperamental hardware.

Cross fingers.

---

### Post by thesleepymoose on 2008-10-09
Finally found a distro that works : LinuxMint

Will try Fedora and Gentoo, I guess this  a big thanks to you all and off I go skipping into the wide world of Linux.

Cheers,

---

### Post by carusoswi on 2008-10-09
Not certain what mood you were in when you posted this, eternal, but I didn't take the OP's op as a threat, and I see none of that other kissing tone in the OP's post or the follow-ups.  I'm curious to know what you see as the threat in the OP's title, and who or what you feel might be threatened.  Ubuntu ain't goin' no where, you aren't personally at risk of any threat, real or perceived.  So, where's the threat.

"Depending on my mood I can see where they are coming from but still . . ."


What do you mean?  Are you suggesting that, because you take issue with the thread title, the OP doesn't deserve civil and helpful responses?

Depending on how long and how thoroughly ones computer experience is rooted in Windows, a switch to Linux can be initially quite frustrating.  We are so used to thinking and proceeding along certain paths - Windows paths - that it can be hard to accomplish that first simple task in Linux when you first try to use it.

To the OP, I hope you aren't put off by eternal's post (or by mine).  I say, hang in there with whatever flavor of Ubuntu you decide to use.  The advantage of using regular Ubuntu is that a larger group of users is available to help you when you run into problems.  Until you get things sorted out, feel free to go back to XP when you get frustrated or need to get things done.  If you are like me, your Linux expertise will grow steadily, and, little by little, you will find yourself migrating to Linux for most of your tasks.

Except that I recently upgraded to Intrepid, I probably would have dumped 8.04 - not because it's that bad, but because I recently got dusted in a thread similar to this one - but the preponderance of posts in that thread were posters who assumed that the solution I sought was to have someone wave a magic wand to make Ubuntu into Windows - "if you just gotta have this or that or can't take the time to read this or that, report this or that, then, you should just go back to Windows" was the sentiment.

Being put off like that has caused me to look in some other directions, and I used that grazing experience to moderate my anger and frustration with those posters. 

For me, Intrepid is now working smoothly, and I find it more stable on my setup than 8.04 ever was.  But, thanks to the rudeness of some of the posters I encountered, I am now investigating other distros and other operating systems, altogether.

I definitely will not go back to Windows (although I will probably always keep XP due to certain bits of software crucial to my work that only run on that OS), but if you ultimately choose to do so, there isn't anything wrong with that.  For me, I feel I will eventually end up moving to one of the Unix offerings - but maybe not, we'll see.  Any OS migration is going to be challenging at first unless you submit to one of the proprietary platforms where stability (or the perception of stability) and simplicity come at considerable expense, financially and philosophically.

I would encourage you to keep an open mind and try to be patient as you explore Linux.  It's not perfect. In fact, until you can accomplish whatever it is you need or want to do on the computer, it's not even better than XP.  But, if you can accept this from someone with fresh experience at feeling your pain, I think in time (probably a short time) the solutions will fall into place for you, and you will appreciate Ubuntu and Linux for the better computing experience they can offer you.

Good luck.

Caruso

> **eternalnewbee said:**
> This is from the heart.
I've been using Ubuntu on & off since 2005 and full time since 2007.
I've had (for 95%) excellent advice from knowledgeable and patient people.
I really didn't like the title of your thread. Really, no offense meant, but it just sounded threatening... 
Sorry. Had to get that one out.
I was even more amazed, seeing responses not to give up yet! Depending on my mood I can see where they are coming from, but still..
You shouldn't be threatening or kissing A. here.
Instead you should appreciate that a lot of people make and take the time to help you, not expecting anything in return from you...
Peace.

---

### Post by SunnyRabbiera on 2008-10-09
> **thesleepymoose said:**
> Finally found a distro that works : LinuxMint

Will try Fedora and Gentoo, I guess this  a big thanks to you all and off I go skipping into the wide world of Linux.

Cheers,

Linux mint is a good distro, I use it myself.

---

### Post by sdowney717 on 2008-10-09
linux mint is ubuntu based.
We had a Dell laptop that could not install ubuntu, always halted, on the orange loading bar. It could run the live CD, never really pursued it further.

I just setup another ubuntu PC. And discovered something. If the bios is set with floppy disk drive enabled, and there is no floppy disk drive plugged into the port, then the system totally freezes. Windows just sailed on by.

---

### Post by akelsall on 2008-10-09
Don't abandon ship yet. I've not heard of Ubuntu Studio. You and I did something very similar, but came out with very different results. I just bought a 500Gb SATA drive and installed the "regular" 32-bit version (from the link below, select the Desktop Edition, and for "Type of computer" select "Standard personal computer".  

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

I used the partition tool that came on the LiveCD (that is, I worked my way through the basic prompts--language, keyboard, etc), then the window appeared where it asked how you want to partion the drive. I selected Manual and went through creating my primary and logical partitions. If you want to try the 32-bit version, I can post the notes I kept while installing Ubuntu. To be honest, I was amazed how smooth it went for me. Maybe it was just beginners luck (as this was the first time ever installing Linux!). 

Andy

---

### Post by Nxion on 2008-10-11
> **eternalnewbee said:**
> This is from the heart.
I've been using Ubuntu on & off since 2005 and full time since 2007.
I've had (for 95%) excellent advice from knowledgeable and patient people.
I really didn't like the title of your thread. Really, no offense meant, but it just sounded threatening... 
Sorry. Had to get that one out.
I was even more amazed, seeing responses not to give up yet! Depending on my mood I can see where they are coming from, but still..
You shouldn't be threatening or kissing A. here.
Instead you should appreciate that a lot of people make and take the time to help you, not expecting anything in return from you...
Peace.


I have to ask how is the relevant to what thesleepymoose posted. We are here to help everyone out not to offend and berate them when they ask for help.

---


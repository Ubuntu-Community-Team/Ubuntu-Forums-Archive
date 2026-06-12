---
title: "Hey, all.....problems getting Ubuntu started"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by SimTech68 on 2013-07-01
Few years back I installed 8.04(I think)on an old box, didn't have any problems getting it loaded, played with it for a time, then put it away for another day. Well, after a few years, I decided to get serious about building a Unix/Linux type box for everyday use to see if I could get away from common OS's. Anyway long story short, I downloaded 12.04 iso then burnt it to a DVD. When I go to install it on my box, it starts to load(the UBUNTU name with dots underneth), then goes to a graphic screen(just huge pixel looking boxes....white and black, then flashes some text with a fail then back to graphics then, seems to lock up there). I haven't written down the failure yet, I thought it could toss this in and it be a quick load(like last time).
Now to be clear, I not looking for any specific answers, just if anyone else has had problems getting 12.04 to load??
The machine I'm trying to load it on, has XP SP3, would it be a good idea to wipe the drive first before loading Ubuntu? Or will Ubuntu install over XP? I don't want to dual boot.

There are some other things that I just need to troubleshoot before going further, I just figure I ask a few questions to see if what I'm experiencing is common, or if I have a specific problem just to my box.

---

### Post by deadflowr on 2013-07-01
> [COLOR=#000000]There are some other things that I just need to troubleshoot before going further, I just figure I ask a few questions to see if what I'm experiencing is common, or if I have a specific problem just to my box.[/COLOR]

What is the machine/cpu/ram you're trying to install it on?
Ubuntu is, for the most part, the heaviest linux distro out there.
And older machines will have troubles.

---

### Post by ryan516 on 2013-07-01
> **deadflowr said:**
> What is the machine/cpu/ram you're trying to install it on?
Ubuntu is, for the most part, the heaviest linux distro out there.
And older machines will have troubles.
He did say he was making a box for Linux/Unix specifically. I'm guessing it's got newer hardware. If anything for you, I'd try reccomending installing a Lubuntu live CD to make sure it can run Linux Drivers.

---

### Post by sammiev on 2013-07-01
You can install over windows, but why? Dual boot and have the best of both worlds. If you install over windows make sure you have a backup first. Good Luck. :)

---

### Post by deadflowr on 2013-07-01
> **ryan516 said:**
> He did say he was making a box for Linux/Unix specifically. I'm guessing it's got newer hardware. If anything for you, I'd try reccomending installing a Lubuntu live CD to make sure it can run Linux Drivers.

You see, that's the thing. Most people think of linux as light and easy to run on light machines. But Ubuntu isn't light, so it would be best to know what the machine was, and if Ubuntu was even capable of running on it.

Of course something else to consider would be a simple bad burn of the iso.
More common then you'd think.

---

### Post by newb85 on 2013-07-01
Ubuntu should have no trouble installing over XP.  

My machine is set up with Win7 and 13.04 side-by-side, and I have the best of both worlds.  I use Ubuntu, and I haven't booted into Windows in over a year.  

XP is no longer supported, so that's yet another reason not to keep it.

---

### Post by su:bhatta on 2013-07-02
Ok, here is what u goatta do....

On the first boot from the Ubuntu DVD u will find a **purple screen with a Man=keyboard** sign at the bottom of the screen ... u have noticed it right?

1)At that screen u hit **Enter**...
it gives u a next screen where by default u will get a list of languages with English selected as default..

2)on that screen select English---> hit enter... It will get u the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen u will see options underneath F1 F2 ... **Hit F6** on that screen.. 
u will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 
It should just boot up fine ....

If I couldn't explain it right.. herez how I learnt it from grahammechanical...

[http://ubuntuforums.org/showthread.php?t=2143220](http://ubuntuforums.org/showthread.php?t=2143220)

BTW, All 'nomodeset' does is, it stops installing the videodrivers at the begining...
if u r using AMD, u may hav to download proprietary drivers(Once installed) to get the right screen resolution n all....

---

### Post by SimTech68 on 2013-07-02
bhattabhishek, thanks......did not know that. I guessed I assumed that it had an auto start feature.....that's what I get for assuming!!!

To everyone that replied....thanks for your responses much appreciated.

deadflowr, I did think of a bad burn, as I have had trouble with burns and brands of disc in the past.....nice call, one of the things I was going into.
As for the specifics of the machine I don't have in front of me at the moment, it is an AMD cpu, 2 GB ram, NVidia card, on board ethernet and sound. To clarify, I did not build it specifically for Linux, it was a box I built 4-5 years ago for XP, photo stuff and light gaming. It never really had any troubles running anything on it at the time so I relatively confident that it can handle Ubuntu. I was a little surprised when I saw the requirements for 12.04 but figured it would work.

One thing I probably should have done is run the live CD version first which is what I plan to do the next minute I get.

As for the best of both world of windows and Ubuntu, I will just leave it at this, I have tolerated windows all these years, and distros like Ubuntu have finally evolved to the point where I want to find an alternative.

Again, thanks to everyone for their responses, and I hope to be helping others as you have helped me.

I will update when I get a chance to look into the problems I'm having......I will also update with specific computer parameters.....sorry I know it's frustrating to try and T/S without all the info.

---

### Post by newb85 on 2013-07-02
It does have an autostart feature, and it usually works.  For some graphics cards, though, the default graphics driver settings won't work, and need to be changed.  More on that here [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132).

You'll probably have to set your system to always boot nomodeset, which means using the open-source drivers will give you only non-accellerated drivers.  Fortunately, Nvidia has the easiest proprietary drivers to install.  (In 12.04, open "Additional Drivers".  Everything should be straight-forward from there.)

---

### Post by SimTech68 on 2013-07-02
[**[COLOR=#000000]bhattabhishek[/COLOR]**]("http://ubuntuforums.org/member.php?u=1819052") hit the nail on the head, F6 --> nomodeset did the trick......thank you very much!!!!

OK, now for the specs on my machine:

CPU - AMD Athlon 64 X2 4200+
MB - MSI MS-7325 w/ nVidia nForce4 chipset
Mem - DDR2 2GB
Graphics - nVidia Geforce GT240
 Since I built this this myself, I have all the driver discs for these things, the question I have will they work on Ubuntu or will I have to find/download drivers from Ubuntu. If it's the latter where would I find the drivers. I'd like to have things ready when I'm ready to do the install.

I have I briefly looked at Ubuntu, and it looks and feels great, very easy to navigate and find things, hats off to those to do the development!!!!! The question I have is how to I access a terminal window? Is there a terminal window. Don't get me wrong I like the icons and window pane navigation but the one thing that attracted me to a Linux version is the ability to have control over the software. I'm guessing that something not available on the "LiveCD" section but I thought I'd ask

---

### Post by su:bhatta on 2013-07-02
SimTech78; did the nomodeset work for u?

as newb85 said there is a autostart, but it doesn't always work with all configurations... Also, If u select nomodeset from the first screen not necessarily u will hav to select it on every bootup... maybe it takes that in itz stride i dont know for sure...

I dont have to select it every time... and my ATI drivers work gr8.. surely ur Nvidia will also work just fine...

Let know what happened u may have to select a combination from taht F6 menu....

---

### Post by su:bhatta on 2013-07-02
SimTech85.. Glad to be of help....thatz a gr8 configuration there was no way it wouldn't boot up 12.04 or 13.04 for that matter....

Just download proprietory drivers or u wont get gthe right display settings...
sit back, enjoy the ubuntu ride.... 

ps: also hit the top most button on the unity panel(left of desktop) and search terminal... u will be given 3 options .. i suggest terminal emulator...
also Down load, Unity Tweak n Ubuntu Tweak if u want to Play around... 
But be cautious...

---

### Post by su:bhatta on 2013-07-03
SimTech78.....

Please mark the thread as 'Solved'...
Here is how to do it:

1) Go to the Initial thread Starter n click Edit...
2) Open 'Advanced'
3) Under 'Prefix' Please mark the thread as 'Solved'

Doing so actually helps the forum.

---

### Post by SimTech68 on 2013-07-03
Done!!! BTW it's Simtech**68**.... or just Simtech would do.

Again thanks for the tips!

---

### Post by su:bhatta on 2013-07-04
sorry SimTech, mybad.... Enjoy ur Ubuntu !

---


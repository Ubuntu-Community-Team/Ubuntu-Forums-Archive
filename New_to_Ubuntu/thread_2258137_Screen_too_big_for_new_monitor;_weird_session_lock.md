---
title: "Screen too big for new monitor; weird session lock issue"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by Cleaver on 2014-12-25
Hi!

I just got a new widescreen 1080p monitor, and was able to fix the issue of the entire desktop being too big for the screen on Windows with my NVidia software by changing the settings/shrinking the dimensions there. I stupidly took some advice online to type "xstart", and now when I try to login, it just takes me to the menu where I select a desktop(I have the default Ubuntu/Unity desktop, Xubuntu, and Lubuntu installed.)

When I type my password into that window, it just seems to briefly logout or something along those lines, then returns to that *exact* screen and the cycle continues indefinitely. Any advice is greatly appreciated, as I was looking forward to using Linux with this new display.

---

### Post by chopra on 2014-12-25
Are you able to log onto a virtual terminal, (cntrl+alt+f1 through f6)?
If not, can you enter single user mode?
Chopra

---

### Post by Cleaver on 2014-12-25
Hi chopra, and thanks for the reply.

I am able to log into a virtual terminal. The display is still too big for the screen, but I can see the prompt(or most of it) and am able to type/enter commands.

I don't actually know what single user mode is--as much as I love Linux, I'm new to it and usually don't learn much unless I'm in the process of fixing things on it or setting them up. I can look it up, though.

Let me know if there are commands I might enter into the virtual terminal. I imagine it'll end up being the solution here.

---

### Post by chopra on 2014-12-25
If you can log in to a virtual terminal, that's good enough. Don't worry about single user mode. Try going through your file systems and see what was changed most recently. 

Did you install the xstart program?  It may just be a matter of deleting the files it's residing in.  It sounds like it's interfering before your normal login session has a chance to start.

 Chopra

---

### Post by Cleaver on 2014-12-26
I'm not even sure what is meant by going through one's file systems. I'm extremely new to Linux in general. Is there a general command that might show recent changes, or maybe just some way to use the GUI/file manager to have a look?

Not sure if I installed xstart, but I did type it in and press enter, and that's when the weird login issue started. Before that, I switched from my old monitor to the new one and the new one just wouldn't fit the desktop inside its screen with whatever its settings were at the time.

---

### Post by deadflowr on 2014-12-26
First things first, let's see about that problem with the login loop.
Do the process above of getting a console terminal running (ctrl+ alt + F1-6)
Login as you would.
Then first try
```
ls -la .Xauthority 
```
Does it have two entries for your username?
Or does it have two entries for root?

If it says root maybe try chmod to change ownership.
Though this will need sudo as you are not the owner, in this instance.
Something like
```
sudo chown you:you .Xauthority
```
replace you:you with your username like username:username.

If you do indeed see your username in the ls -la command
You might also try a quick move of the file.
```
mv .Xauthority .Xauthority.old
```
This will move the file and upon restart generate a fresh one.
This may help because sometimes that original file may have been corrupted.
The file is inside your own home folder, so you can move it without needing to be root.
(You should be the owner of everything in your home folder)

See if anyone that has any effect on logging in.

Sidenote: I think you would have run startx, I do not know of a command called xstart

Another quick note: If you can't remember the spelling of the file, simply run ls -la from the terminal and all the files/folders in your home folder will be listed, and you should be able to see the name.

Also you can use what is known as TAB completion. Start spelling the word and hit the TAB button, it should autofill the rest, or will output a list of possible words if more than one share the same letter/numbers that you have already typed. Luckily this one should not have any beyond the first few.

Also note the file has a dot in the beginning, this signifies that the file is normally hidden. So when typing the filename, do not forget the dot.

Hope something here helps.
Or slowly makes sense...

**Bonus Edit**: It skipped my mind but i would think you would need to restart the X server.
Normally this is done with a simple command:
```
sudo restart lightdm
```
if using 14.04.
```
sudo service lightdm restart
```
if using 12.04.

OR
simply do a full reboot
```
sudo reboot
```
works well enough.

---

### Post by Cleaver on 2014-12-27
Hi,

I used the ls-la thing, which didn't return any lines with my username in them. However, the "chown" thing seemed to at least restore my prior desktop, which is again too big, so while I'm back where I was when my screen issue began, it's better than the locked thing I was dealing with ten minutes ago. Thanks!

Anything I might do to make the display fit the screen from here? Thanks in advance. I'll reinstall Ubuntu if I must, but I want to try not to do that this time. Might as well learn more.

---

### Post by deadflowr on 2014-12-27
Hm, okay.

You stated you have nvidia stuff on Windows so I assume you have an nvidia card.(?)
Did you install any nvidia drivers?
Or are you running the system with what came out of the box?

Another note, on Normal Ubuntu(the one with the unity desktop) have you opened up the Displays program and tried to set the resolution from there?

Sorry for all the questions.
But knowing as much about what you have tried, or have available to try, makes it easier for us not to give repeatable advice which may not help.

---

### Post by Cleaver on 2014-12-27
Hi,

I have an NVidia GTX 440, which I mean to replace soon but for now am still deciding. I don't have any drivers installed on Ubuntu; only on Windows 7, which I sadly must use for some games/programs. I guess my Ubuntu system is simply running with what's out of the box in 14.10.

Displays program runs, but there doesn't seem to be any alternative. I can either keep it set to 1080 as it is now, or choose an inferior resolution.

No apologies for the questions. I'm grateful someone's answering so quickly and providing some insight.

---

### Post by Cleaver on 2014-12-29
Update: I've found what appears to be an all-purpose Linux driver on the GEForce/NVidia site, but can't seem to figure out how to run it once it's on my hard drive, likely due to my extreme novice level of knowledge. I do have to wonder if this(plus maybe some PPA stuff if that's necessary) may fix the problem. Any suggestions, deadflowr(or anyone reading this)?  :)

---

### Post by deadflowr on 2014-12-29
There are nvidia drivers built for Ubuntu (Well not exactly built for Ubuntu, but Ubuntu developers work to make sure they work well in Ubuntu, the drivers are nvidia's that Ubuntu can install without a lot of fuss)
Open up the Program called Software and Updates, or search for a program called Additional Drivers (Additional Drivers is inside of Software and Updates usually.)
when open it'll run a quick scan of the system and then list a few driver options. The normal driver's in use are the xorg drivers. You might look at installing the one marked nvidia-current; usually a good first option. 
It'll take a moment or so because it'll then download and install the driver and the little bits and pieces that Ubuntu will use to keep the driver in line with the rest of Ubuntu system, like kernel updating, etc, etc.

It'll also add the nvidia-setting program to control the card, somewhat.
You can search for it when you restart the system, after installing the drivers.

These drivers tend to be older than what you would get from the nvidia site, but they are real stable, and the do try to kepp them updated for security purposes.
And since your card does not seem too new it should be well supported with them, I would think.

---

### Post by Cleaver on 2014-12-29
> **deadflowr said:**
> You might look at installing the one marked nvidia-current; usually a good first option. 

Hmm...I see several options with the Xorg one being currently selected by default apparently, but no trace of "nvidia-current." Might another of these be relevant, or could the list be missing "current" for some other reason?

---

### Post by deadflowr on 2014-12-29
> **Cleaver said:**
> Hmm...I see several options with the Xorg one being currently selected by default apparently, but no trace of "nvidia-current." Might another of these be relevant, or could the list be missing "current" for some other reason?

Could be simply listed under a different name.
Could a take a screenshot maybe and post it, or list which options are there?( Little more painstaking but...)

(For screenshot's we prefer if you upload them as attachments(simply open a new post with either the GO Advanced option or click on the orange button marked Reply to Thread and then click on the paperclip icon in the tool bar, then upload the image)

---

### Post by Cleaver on 2014-12-29
OK, this attachment should be it!

---

### Post by deadflowr on 2014-12-29
I would try the top one, the one for nvidia-331.

---

### Post by Cleaver on 2014-12-29
Hmm. Tried that one, plus checked the newly-installed settings program. Neither has made a difference even after a reboot. I'm certainly willing to try all drivers as shown in the screenshot(trial and error,) but just wanted to ask if that's worth a shot before doing so. Thanks.

---

### Post by deadflowr on 2014-12-29
I would expect the same result for all the different drivers, in terms of screen adjustments.
Performance tweaks and changes is really the only difference you'd get, in most cases.
I was hoping you'd get more nuanced abilities to adjust the screen with nvidia xserver settings program.

I'm at a partial loss.
Perhaps a good rundown of what is what can be helpful.
What is the size of the monitor screen, and what is the size (or at least the size you think) of the current desktop screen?
Is the monitor screen more like something around 1900x1080, but the desktop is only up to something weird like 1280x1024?
Something mismatched or other like that?

---

### Post by Cleaver on 2014-12-30
It's a 27 inch screen, and the desktop itself is probably too big by an inch or so. 28-inch desktop, maybe? If my memory serves(I'm typing this from Windows) roughly the right third of the icons on the left edge of the screen in Unity were visible, if you know what I mean. The top of a given window, which is never visible when I fullscreen it, probably requires me to "blindly" move my mouse up about a half inch or so beyond where the top edge of the screen is in order to drag it down so it's entirely visible.

The monitor is 1080p. Is there a way I'd definitively find out if the desktop's only 1280x1024? I'd always thought Linux tended to auto-detect resolution really well, which is part of why I'm so puzzled--with the exception of this and joysticks, most hardware(even a Wacom tablet) basically works out of the box without all the driver hunting hell of Windows. Is there something specific you mean by "mismatched" regarding the resolution? Some bit of software that would test that?

Please let me know if any other rundown-related details of the system/monitor could be helpful.

---

### Post by Cleaver on 2015-01-01
deadflowr(and everyone else,)

There's good news and bad news. The bad is that it appears the solution may have been embarrassingly simple. The good is that this particular problem *seem* taken care of for the moment.

My new monitor had a menu function in it that wasn't immediately intuitive for me to use. However, I was able to go into it and figure out partly by dumb luck that I could switch the input mode from A/V to PC. That fixed the desktop so that it fit perfectly in the 1080p screen rather than what was happening before.

Thanks for your patience in helping with this. I did have a flicker issue after doing this for some reason, but it might also be gone now and is likely best used for another thread if it comes up again.

---

### Post by Cleaver on 2015-01-02
Hi again deadflowr,

The problem is still solved, but I was just curious as to why you mentioned earlier that I should choose the driver you suggested from that list. Anything specific about it? So far, I've been able to get the legacy driver working with most/all games that otherwise don't display properly, but I get the feeling maybe I should use something newer/proprietary. Thoughts? Thanks for all your help!

---


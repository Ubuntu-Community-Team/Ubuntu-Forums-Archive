---
title: "How many fingers does the average person have, and questions about Ubuntu 8.04 Deskto"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by SonOfOdin on 2008-07-23
Hey, just losing my virginity to Linux.  And to these forums. :)  Tried to install and use a variety of distributions and so far Ubuntu 8.04 has worked the best for me so far.  (Actually, its the only distro that got completely through installation, 32bit or otherwise...)

Have a couple of immediate problems that I cant seem to find anything helpful for on the web.  If anyone could help I'd appreciate it.

* Gnome keeps shutting down, specially when using Firefox, XChat and Pidgin in any combo.

* I have an ATI 200 Express (using an AMD64 3000+ Lappy) - how on earth do I get non-clone dual monitors established?

* How do I get the embedded stuff in documents to open using OpenOffice?  Neither .doc nor .xls will run the embedded movies/whatever that I keep receiving in my emails from friends.

TIA

Bryn

ps, the average person has 8 fingers, and two thumbs.   The answer is definitely not *wrong*.
:lolflag:

---

### Post by Gepetto on 2008-07-23
Congrats on a sucessful install!

What do you mean when you say Gnome shuts down? As in it kicks you out of Gnome and hits you back into a text mode? or does it log you out?

I can't attest to your 2nd question, as I have an nvidia card, but I'm sure someone can help.

It's quite possible that you won't be able to watch the embedded stuff, as support for .doc's and .xls's in OpenOffice isn't 100%. It's pretty close, but things like this usually don't work so well. If you have a copy of Office lying around, you can probably install it using [WINE]("http://www.winehq.org") and see if that works.

Good luck, and I hope you enjoy your stay!

---

### Post by powderhound99 on 2008-07-23
# 1 for any media movies ect try opening it with vlc if you don't have it you should open command line.... sudo apt-get install vlc
#2 it's more important to be able to stay loged in... whether it kicks you to a login screen or a terminal is important (and you should post it here) if it's a terminal I'd look more at x than gnome... if it takes you to a login window after your login then see..... well I can't find it but it's a known issue just go to sys>admin>loginwindow and select security and enable then disable auto login then restart. Kind of a weird workaround but it worked for me. For the doc I don't have any advice just keep digging w/ google.

good luck it can be a steep learning curve but it's doable and Ubuntu is typically the easiest way to go. Once you get it it'll snowball and quickly become easier.

---

### Post by Xinkill on 2008-07-23
Well done for making the step i say.

For getting dualscreen on a ati i use this command in the terminal:
sudo aticonfig --initial=dual-head --sreen="place of the second screen in placement of your first" eg: right, left, up, down, ...

for the embedded stuff (if i understand your question correctly)
Select the properties of the file you always want to open with OpenOffice.
-> Than go to the tab saying "Open with". 
-> Than click the Add-button 
-> Select the OpenOffice from the list. 
If OpenOffice is not in the list than just do:

- Down add the botom is a: "Use a custom command thingy"
- Click it
- fill in: ooffice.

---

### Post by SonOfOdin on 2008-07-23
Thanks for the replies :)

What is happening with regard to Gnome / X:
I will be using the pc, nothing overly demanding, maybe a half dozen tabs, and either XChat or Pidg.  

The system will behave as if CTRL-ALT-Backspace had been pressed and will hang as the Kernel or other processes are reset/killed.  Sometimes it will make it to the login screen, other times it will freeze with a mass of lines and colours over the screen as if the video card had died.

Either way, I can not CTRL-F7 back into X, nor can I CTRL-ALT-F1 into a console to check for errors.  Most commonly I have to hold the power button, swear a bit and then turn the pc back on.

At first I thought that it was a hot CPU, but the air flow was fine, though I cleaned it in case.

I have installed a heap of different things from the distribution, and a lot of the add-ons for Firefox.  I wondered about this last part, created a new account and give that a whirl.  When I tried to CTRL-ALT-Backspace to switch back it froze with a messy screen again.  As I had killed the Mozilla which had 0 add-ons, I thought I could pretty much eliminate it as being an issue.

Has me stumped...  not that Im a cracker of a Linux user yet, but I cant find any reasonable explanation online for it either.

Gonna try the other recommendations now.  Bring on the learning curve I say.

---

### Post by combatwombat_nz on 2008-07-23
The X crash may well be due to overheating GPU. Try the instructions here:
[http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts") to install the ATi drivers. Otherwise you may need to actually open your laptop and evict the dust bunnies.

Another thing to try is running with Live CD. Does that work?

---

### Post by Tony Flury on 2008-07-23
<pedant>wrt to the average : it depedns what you mean by average - while the vast majority of people have 8 fingers and two thumbs, a significant number of people have had amputions and birth defects which have reduced the numbers of each, and probably a very small number have birth defect which give them an extra finger. It is highly likely that Median (the central value in an ordered list) is 8 fingers and almost a certainty that the Mode (the most frequent) is also 8 fingers per person, the Mean (i.e. what most people understand to be the Average) is probably slightly under 8 fingers, and slightly under 2 thumbs - because of the impact of the amputations etc..</pedant>

---

### Post by collinp on 2008-07-23
[SIZE=2]I am getting the X crashing problem, idk when it started, but I am thinking someone pushed a bad package for updating. I also run Firefox and Pidgin in a combo most of the time, so this is a real pain for me. I would be glad if anyone could tell me a permanent fix, but for me running &#65279;[/SIZE][SIZE=2][SIZE=2]/etc/init.d/gdm stop && /etc/init.d/gdm start [/SIZE][SIZE=2]fixes the problem, at least until it does it again.[/SIZE]
[/SIZE]

---

### Post by SonOfOdin on 2008-07-23
> **Tony Flury said:**
> <pedant>wrt to the average : it depedns what you mean by average - while the vast majority of people have 8 fingers and two thumbs, a significant number of people have had amputions and birth defects which have reduced the numbers of each, and probably a very small number have birth defect which give them an extra finger. It is highly likely that Median (the central value in an ordered list) is 8 fingers and almost a certainty that the Mode (the most frequent) is also 8 fingers per person, the Mean (i.e. what most people understand to be the Average) is probably slightly under 8 fingers, and slightly under 2 thumbs - because of the impact of the amputations etc..</pedant>

Yes all well and good, but the answer is still not "wrong".

ie "The answer to the random question is wrong"... wrong isnt even an integer. :)

---

### Post by SonOfOdin on 2008-07-23
> **combatwombat_nz said:**
> The X crash may well be due to overheating GPU. Try the instructions here:
[http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts]("http://combatwombat.7doves.com/2008/03/10/gutsy_ati_efforts") to install the ATi drivers. Otherwise you may need to actually open your laptop and evict the dust bunnies.

Another thing to try is running with Live CD. Does that work?

Live CD works no problems.

Thanks for the link to the ATi instructions.  Sounds pretty full on but Im gonna give it a go shortly.  Vacuum and air compressor sorted out the dust :)

---

### Post by Dutch70 on 2008-07-23
Well the only thing I can add here is that you dont have to hold the power button in to shut it down, try this if that happens agian.

 Hold down the _Alt & Print screen_ buttons.
and slowly press r-e-i-s-u-b. one at a time, and pause for a couple seconds between each letter. That will save just about everything and shut down your machine, unless you have a kernel panic.

Dutch

---

### Post by Troll_the_Great on 2008-07-23
> **SonOfOdin said:**
> Thanks for the replies :)


Either way, I can not CTRL-F7 back into X, nor can I CTRL-ALT-F1 into a console to check for errors.  Most commonly I have to hold the power button, swear a bit and then turn the pc back on.

At first I thought that it was a hot CPU, but the air flow was fine, though I cleaned it in case.
If nothing else works, to safely shut down the PC, press and hold Alt+Print Screen with one hand and with the other hand press R,E,I,S,U,B (about a second between each letter).This is an emergency shut down command and it will work even if everything is frozen.This will allow you to shut down the PC without pressing the power button.
Cheers!

EDIT: I was too slow...

---

### Post by SonOfOdin on 2008-07-24
Hey peeps

So far I havent managed to address any of the problems to my satisfaction.  

The one thing that is bugging me is the MS Office Documents with embedded animated gifs, shockwave files or movies etc that I cant get to work in OpenOffice.

The files themselves open, without any problems - the issue isnt a recognition or extension problem.  However once launched, the object that has been embedded is still or paused.  I cant seem to find an option to run it or restart it.

Once again, much obliged for comments.

Edit: embedded file types as above.

---


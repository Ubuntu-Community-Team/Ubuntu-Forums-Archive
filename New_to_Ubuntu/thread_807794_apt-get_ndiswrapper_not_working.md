---
title: "apt-get ndiswrapper not working?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by stropyboy11 on 2008-05-26
Just got my computer back (bum hard drive) and installed ubuntu. However, I'm still kinda a nub, so when i went into the terminal and did "sudo apt-get ndiswrapper" it came up with "E: invalid operation ndiswrapper"

What should I do?

Oh, and also...where can I control compiz in 8.04? My lappy's been out for awhile and I just got around to upgrading from 7.10

---

### Post by mevets on 2008-05-26
you should be running
```

sudo apt-get install ndiswrapper

```
To configure compiz you need ccsm. Its not installed by default, so if you dont have it you need to run
```

sudo apt-get install compizconfig-settings-manager

```
ALT+F2 then type, ccsm, in order to run it.

---

### Post by shifty_powers on 2008-05-26
for the first one, try

```
sudo apt-get install ndisgtk
```

you forgot the install part. ap-get is the command, but you have to tell it waht to do, in this case install and then the package name. plus, ndisgtk will give you the graphical frontend to ndiswrapper, whihc is easier to use. it'll appear under system>administration>windows wireless drivers.

secondly, use

```
sudo apt-get install compizconfig-settings-manager
```

then go system>preferences>advanced desktop effects settings ;)

---

### Post by stropyboy11 on 2008-05-26
aww thanks a bunch...ive been out of the game for waaaay too long

damn hp lappy

---

### Post by stropyboy11 on 2008-05-26
wait...problem arose

its saying now: "E: Couldn't find package ndiswrapper/ndisgtk/compizconfig-settings-manager"

what now?

---

### Post by shifty_powers on 2008-05-26
btw, i stand by what i siad, ndisgtk is going to be easier to use ;)

---

### Post by shifty_powers on 2008-05-26
> **stropyboy11 said:**
> wait...problem arose

its saying now: "E: Couldn't find package ndiswrapper/ndisgtk"

what now?


could you post the full output from the terminal when you try those commands?

---

### Post by stropyboy11 on 2008-05-26
yeah i saw ur reply second but i tried it as soon as i could

and how would i do that?

thanks again for all the help

---

### Post by oedha on 2008-05-26
have you activate your repositories ?
system - administration - software sources
mark all boxes, close, reload
and try to install ndis and compiz again

---

### Post by shifty_powers on 2008-05-26
type in the command into the terminal, and then highlight all the text, control-c and then put in a cpost with ```

``` either side of it ;)

or just take a screenshot and post that :D

---

### Post by Xiong Chiamiov on 2008-05-26
> **shifty_powers said:**
> type in the command into the terminal, and then highlight all the text, control-c and then put in a cpost with ```

``` either side of it ;)

or just take a screenshot and post that :D
Control-C won't copy in a terminal window, since it triggers SIGKILL (SIGTERM?  I'm not really sure) - it stops whatever's currently going on in that window.  You'll have to right-click copy.

---

### Post by shifty_powers on 2008-05-26
well you learn something new everyday ;)
and it didn't show my code tags, should have tjhought of that O.o

---

### Post by stropyboy11 on 2008-05-26
Umm i wasnt quite sure what a cpost was so i just took a screenshot

wow i feel like a total noob today

---

### Post by stropyboy11 on 2008-05-26
ooo i just checked out my screenshot...coded in ajax

fancy.....

i must say i haven't been to ubuntu forums since the redesign and im liking it alot

---

### Post by shifty_powers on 2008-05-26
sorry the cpost thing was a result of my doziness ;) only got up a little while ago.

if you go to system>admin>synaptic>settings>repositories what boxes are enabled in the first two tabs?

feel free to show screenshots ;)

(and see mine ;))

---

### Post by oedha on 2008-05-26
check your repo.....update it

---

### Post by stropyboy11 on 2008-05-26
Here we are....

And can you still explain the thing to me? I don't understand...I know you copy and paste the text but how do you get it to do the thing I see all the time where it looks like a little terminal inside the post...

---

### Post by shifty_powers on 2008-05-26
coudl i see the screenshot for the thridparty tab in the repos as well please?

amd as for the second question...

you need to use code tags. use [] with code written in it and then [] with /code inbetween the brackets afterwards ;)

see the screenshot ;)

---

### Post by stropyboy11 on 2008-05-26
yeah sure

and sorry for the delay but i was installing flash and i didnt know it would take that long

---

### Post by shifty_powers on 2008-05-26
aha

right, go an click the box on the thrid party tab that says partner at the end. (make sure the box has a cross in it ;))

then go back to terminal and

```
sudo apt-get update
```

then

```
sudo apt-get install ndisgtk
```

---

### Post by stropyboy11 on 2008-05-26
ha...success!!!!!!

if you're ever in southern california let me know, ill buy you lunch....you've earned it!!

---

### Post by shifty_powers on 2008-05-26
heh, the likelihood of that is sadly minute, seeing as i'm a student mental health nurse in london, uk, but thanks ;)

and glad to help :D

---

### Post by shifty_powers on 2008-05-26
course, now you just have to figure out ndiswrapper ;)

assuming you've been having problems with your wireless then?

---

### Post by stropyboy11 on 2008-05-26
pshh havent you been reading?

hard drive got fried, had to get new one...and a friend of mine set up my linux before...but i wanted to do it all my own this time

well, maybe with a little help from the forums :p

---

### Post by shifty_powers on 2008-05-26
heh, dude, i read so many threads i completely lose track ;)

and good luck with ndiswrapper.

just remember to use the *.inf file for the wireless driver ;)

---

### Post by stropyboy11 on 2008-05-26
huh, new problem

i enabled wobbly windows, but my windows still refuse to wobble

WOBBLE YOU OBSTINATE WINDOWS!!!

any ideas?

---

### Post by sayakb on 2008-05-26
It often conflicts with Snapping windows. Disable snapping windows first and then try again

EDIT: In case that doesn't work, goto System->Preferences->Appearance->Visual Effects and select Extra. That may "force" it to Wobble ;)

---

### Post by stropyboy11 on 2008-05-26
already did...any other ideas?

---

### Post by Xiong Chiamiov on 2008-05-26
> **shifty_powers said:**
> heh, the likelihood of that is sadly minute, seeing as i'm a student mental health nurse in london, uk, but thanks ;)
I was wondering, since
> **shifty_powers said:**
>  only got up a little while ago.

> **stropyboy11 said:**
> ha...success!!!!!!

if you're ever in southern california let me know, ill buy you lunch....you've earned it!!
I'll take it. :p

---

### Post by stropyboy11 on 2008-05-26
perhaps if you help me with my more current issue

> **stropyboy11 said:**
> huh, new problem

i enabled wobbly windows, but my windows still refuse to wobble

WOBBLE YOU OBSTINATE WINDOWS!!!

any ideas?

---

### Post by sayakb on 2008-05-26
Oh, did you click Extra as I indicated. Didn't that enable Wobbly? Thats very strange. Do 1 things then, open Advanced desktop effects settings (ccsm), click preferences and click on Reset to defaults. Then try enabling Wobbly again.

---

### Post by Xiong Chiamiov on 2008-05-26
> **stropyboy11 said:**
> perhaps if you help me with my more current issue
Eh, I think I'll have to pass, as I'm pretty new to Compiz, I use KDE, and it's quarter 'til 4 and I'm going to bed...
/snore

But best of luck!

---

### Post by stropyboy11 on 2008-05-26
i tried to reset, but alas, twas to no avail

same thing happened...

anything else i need to deactivate besides snapping windows?

---

### Post by sayakb on 2008-05-26
You don't need to, I think. Perhaps, I have almost everything on on my box, plus I do have Wobble. Do one thing, start compizconfig-settings-manager from the terminal and then try to enable Wobble. See if it shows any error message there.

---

### Post by stropyboy11 on 2008-05-26
wait i didnt see your edit before...i was on none..i just have to wait for a few updates to install then im gonna restart then ill see if that was it

sry for the confusion

---

### Post by sayakb on 2008-05-26
No problem. Just restart and see if setting it to Extra works or not.. :)

---

### Post by stropyboy11 on 2008-05-26
Ha, yet another problem...this one not so major...

How do I determine what my buttons are? A macro for magnification is shift super button 4, but I dont know what my button 4 is (and I'm on a laptop so I only have two clicky buttons)...

ideas?

---

### Post by sayakb on 2008-05-26
You might magnify by pressing Super and scrolling up/down.

---

### Post by stropyboy11 on 2008-05-26
ha yeah i just figured that out right before i read that

thanks a lot anyway

---

### Post by sayakb on 2008-05-26
No problems. Remember to mark this thread as Solved if you don't have any further questions.

---


---
title: "close/minimize/maximize on wrong side?"
date: 2010-05-01
forum: Recurring Discussions
---

### Post by rocka on 2010-05-01
Hi,
 I just upgraded to 10.04 last night, and now I notice that the three little squares for close/minimize/maximize are on the wrong end of the bar at the top of the windows. I had a look through the preferences but I couldn't find anywhere to fix it.

So, I have two questions:

* how do I fix it?

* why would they do that?

:-?

---

### Post by philinux on 2010-05-01
Minimise, Maximise and Close button placement.

A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.

---

### Post by rocka on 2010-05-01
Hi Phil,
well, first, let me say thanks for your quick response.

But gee, it gives me a bit if a dilemma, and I bet I'm not the only one. Every other computer I've ever touched [since windoze 3 point something] has had the buttons up there in the top right corner. I'm forced to use XP systems at work. My two EEEs are running the default Xandros.

If I've got to stop and think every time "which computer am I using now?" I rekon that will get old real quick.

So you're saying next release there'll be something in the way and we'll *have* to change? I wonder what could be so important...

I'm reminded of a story I heard many years ago where some study was done and they concluded that the US was driving on the "wrong" side of the road, there were good reasons to change to everyone driving on the left, but it was decided by the govt at the time that it would be too hard to change.

Are they going to *force* this change on us?

---

### Post by Paul T. on 2010-05-01
Hi,

I had same concern about moving buttons, but easily fixed:

Open up a terminal, type "gconf-editor" then navigate to /apps/metacity/general and make the "button_layout"
Code:
:minimize,maximize,close

Got that from another user, worked for me :P

---

### Post by prenoob on 2010-05-01
I feel much the same as you, Phil.  Every operating system I have ever used has had those buttons on the left and the despised (not by me) Windows still does have.  I cannot see a company standing for this because it would definitely reduce productivity from computer users!  "Customising your computer" in the main Help tells you how to change it "but it aint easy".  For me it's the kind of thing I might attempt when I had nothing else at all to do.

I don't see this change increasing Ubuntu take-up at all!!!

Trev

---

### Post by philinux on 2010-05-01
Google this ;)

mark shuttleworth buttons

---

### Post by zipperback on 2010-05-01
> **rocka said:**
> Hi,
 I just upgraded to 10.04 last night, and now I notice that the three little squares for close/minimize/maximize are on the wrong end of the bar at the top of the windows. I had a look through the preferences but I couldn't find anywhere to fix it.

So, I have two questions:

* how do I fix it?

* why would they do that?

:-?

If you don't like the controls in the new left side position for Radiance and Ambiance, you can download slightly modified versions of those themes entitled Radiance_R and Ambiance_R. I have modified these thems and posted them on Gnome-Look.org for people who would like to use them.


Here are the links to the themes.

Ambiance_R (Ambiance Right Side)
[http://gnome-look.org/content/show.php/Ambiance_R+%28Ambiance+Right+Side%29?content=123927](http://gnome-look.org/content/show.php/Ambiance_R+%28Ambiance+Right+Side%29?content=123927)

Radiance_R (Radiance Right Side)
[http://gnome-look.org/content/show.php/Radiance_R+%28Radiance+Right+Side%29?content=123931](http://gnome-look.org/content/show.php/Radiance_R+%28Radiance+Right+Side%29?content=123931)


I hope you find these beneficial and enjoy them.

- zipperback
:popcorn:

---

### Post by rocka on 2010-05-01
> **prenoob said:**
>   Every operating system I have ever used has had those buttons on the left and the despised (not by me) Windows still does have.  
Trev

I think you meant: "right"...

---

### Post by ladypcer on 2010-05-01
Ubuntu Tweak has the option to move the buttons back to the right. 
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by rocka on 2010-05-01
> **philinux said:**
> Google this ;)

mark shuttleworth buttons

well.
.
.
.

so it's bigger than just us, eh?
:confused:

I can only agree with the POV I read on one of those links: "whatever the new thing is he's planning, why not put ****that**** on the left and leave the buttons where they should be?"

---

### Post by prenoob on 2010-05-01
> **rocka said:**
> I think you meant: "right"...Yes - the upgrade left me exhausted!

Trev

---

### Post by clhsharky on 2010-05-01
HI

So we have to follow Microsoft!

Sharky

You can if you want.

---

### Post by mister_playboy on 2010-05-01
I'm actually going to stick with the left-side buttons and try to get used to it... wish me luck. :lolflag:

---

### Post by Paddy Landau on 2010-05-01
> **rocka said:**
> ... I notice that the three little squares for close/minimize/maximize are on the wrong end of the bar
The "wrong" end? LOL

On the Mac, they're also on the left-hand side. I guess that Mac users would call it the "right" end, and find Windows to be "wrong".

It will take some getting used to, especially as most people in the world use Windows.

---

### Post by Elfy on 2010-05-01
This is no longer a support thread - but another "The buttons are on the wrong side" thread - moved to recurring discussions

---

### Post by whitefort on 2010-05-01
> **Paul T. said:**
> Open up a terminal, type "gconf-editor" then navigate to /apps/metacity/general and make the "button_layout"
Code:
:minimize,maximize,close

Thanks a million for this fix.  The new 'feature' has been driving everyone here NUTS.

I think it was a dumb decision to do this.  Whatever this mysterious 'something' is that they're planning to put on the right-hand side in a future release... well, couldn't they put it on the LEFT-hand side, and leave the buttons where everyone expects them to be?

rant over - but seriously, thanks!

---

### Post by godvalve on 2010-05-01
You know, the thing I really don't understand about those who design GUIs is their hubris. Why do they think that they should control what my system looks like. 

"Oh... but you can download fix x,y,z and then it will look like you want...."

What's so hard about building the choice right into the design. The designers may well be the people with the vision to get the project going, but the moment the application leaves their development machines and lands on my machine, its **_MY_** application and it should work the way I want it to. It's either their pet science project (in which case, no body cares and it should be left in the closet), or its built to be used by the public (in which case the aesthetic design considerations of the developers are irrelevant).

Its a new age... _the age of the user_.=D>

---

### Post by Foster Grant on 2010-05-01
> **rocka said:**
> Hi,
 I just upgraded to 10.04 last night, and now I notice that the three little squares for close/minimize/maximize are on the wrong end of the bar at the top of the windows. I had a look through the preferences but I couldn't find anywhere to fix it.

So, I have two questions:

* how do I fix it?

* why would they do that?

:-?

Look at it this way: Up until now they were on the side Microsoft dictated in Windows 1.0 25 years ago and refined in Windows 95 back in ... uh, 1995. I see no reason to let Microsoft dictate *anything* to me. :D

---

### Post by kaldor on 2010-05-01
> Are they going to *force* this change on us?

This is Linux. Nobody can truly force anything on you in terms of the GUI. If Ubuntu somehow forces you to keep buttons on the left, you can do one of the following:

1) Switch distros
2) Remove GNOME
3) Hack Ubuntu


I actually prefer the buttons on the left. But then again, I'm an OS X user and on occasion used OS9; I am very used to change.

---

### Post by 3rdalbum on 2010-05-01
> **godvalve said:**
> You know, the thing I really don't understand about those who design GUIs is their hubris. Why do they think that they should control what my system looks like. 

"Oh... but you can download fix x,y,z and then it will look like you want...."

What's so hard about building the choice right into the design.

Exactly right. They should provide some sort of method for changing the order to exactly how you want it. Maybe it should have a Gconf key, where you can change it to read "menu:minimize,maximise,close" to put the buttons to the way Windows does it? :-P

---

### Post by johann_p on 2010-05-02
I do not think how this change is not stupid and an insult to long-time users who are forced to change one of the most basic GUI interaction behaviors. Many people like me have been using some GUI system where the convention was to have this on the right for years. 
Mony like me have to switch between computers that run different OS or different versions of OS and then re-adapt to the changed convention every time an Ubuntu machine is involved.

And all this without giving users a choice or even telling them why it has been done. 

If there are plans where changing this is necessary, why not let us know or make the change only when they want to let us know? 
Why can't the stuff that is obviously planned go to the left side?
If we use workarounds to change the layout back now, will this clash with whatever is planned?

I do not like that change now as there is no good reason whatsoever to change it.

But I even less like the way how this change was done and how users are left in the dark about the motivations behind it.

---

### Post by Chrysantine on 2010-05-02
> **johann_p said:**
> Mony like me have to switch between computers that run different OS or different versions of OS and then re-adapt to the changed convention every time an Ubuntu machine is involved.
Seriously.. I've been reading all the crying about something as insignificant as button placement, so here's my FREE suggestion to all of you; learn how to use keyboard short cuts, that way you'll save time and don't have to move the mouse. 

I've mapped all the short cuts so I can reach all of them without moving my left hand at all. It' a whole damn lot faster.

---

### Post by Paddy Landau on 2010-05-02
> **godvalve said:**
> ... the moment the application leaves their development machines and lands on my machine, its **_MY_** application and it should work the way I want it to.
Well, yes, certainly. But just as all cars have steering wheels, not some with joysticks, so a certain degree of standardisation happens.

If Canonical had unlimited money and resources, I'm sure that they would have put choice into absolutely everything. But as Canonical provides this completely free, the company does have limited resources.

Even Microsoft with its billions doesn't provide that sort of flexibility.

> **3rdalbum said:**
> They should provide some sort of method...
There's no "should" about it. That's what Canonical does, *completely free of charge*, so I'm not going to complain. I'm grateful that I have this choice.

Of course, you can become part of the process and vote for or against the changes (as I did), which will get your voice heard.

> **johann_p said:**
> ... all this without giving users a choice or even telling them why it has been done.
...
 ... I even less like the way how this change was done and how users are left in the dark about the motivations behind it.
This has been discussed for quite some time already on the forums, in the weekly newsletter, and in the Ubuntu brainstorm. We weren't left in the dark at all.

---

### Post by johann_p on 2010-05-02
> **Chrysantine said:**
> Seriously.. I've been reading all the crying about something as insignificant as button placement, so here's my FREE suggestion to all of you; learn how to use keyboard short cuts, that way you'll save time and don't have to move the mouse. 

I've mapped all the short cuts so I can reach all of them without moving my left hand at all. It' a whole damn lot faster.

Thanks but no thanks. You are mixing up things here: it is not the users who have to justify why they want to continue doing things as they have done it for years and as they have to continue to do it on other OSs or other Linux distributions. It is for the developers to come up for a damned good reason why to change such a fundamental part of the UI without any pressing need and without even explaining and justifying it to their users.

Doing it like they did it is both lacking of a reasonable justification and disrespectful towards their user base.

---

### Post by Chrysantine on 2010-05-02
> **godvalve said:**
> The designers may well be the people with the vision to get the project going, but the moment the application leaves their development machines and lands on my machine, its **_MY_** application and it should work the way I want it to.
And you can - you can change anything about the GUI that you don't like with a few simple commands or waving the mouse around. Sounds more like people are complaining because they're lazy and want everything handed over on a silver platter.

> **godvalve said:**
> It's either their pet science project (in which case, no body cares and it should be left in the closet), or its built to be used by the public (in which case the aesthetic design considerations of the developers are irrelevant).
Developers are the people who are doing all the work for you, you should do well to grow some respect for their work. Apparently you have none, a very common trait in the open source movement nowadays. 

> **godvalve said:**
> Its a new age... _the age of the user_.=D>
More like the age of whiners who are never happy with anything.

---

### Post by Unicast on 2010-05-02
Coming from OSX I felt right at home with the new button placement. :D

Look forward to seeing what happens with the space to the right of the buttons.

---

### Post by pigphish on 2010-05-07
Thanks for the fix... 

(No thanks to the Apple fanboys that have invaded our beloved ubuntu)

---

### Post by KdotJ on 2010-05-07
I really just wish people would get over this. Yes the buttons have moved, yes you can move them back if you don't want them on the left. It frustrates me when people keep saying "wrong" side etc. I personally think the new placement makes more sense. One thing that really strikes me, is how people moan about hating windows and Microsoft, but then moan when ubuntu breaks from the windows-made standards. People moan about how ubuntu is now copying Mac, but have never in the past moaned that they are copying windows with the button placement

---

### Post by pigphish on 2010-05-07
> **KdotJ said:**
> I really just wish people would get over this. Yes the buttons have moved, yes you can move them back if you don't want them on the left. It frustrates me when people keep saying "wrong" side etc. I personally think the new placement makes more sense. One thing that really strikes me, is how people moan about hating windows and Microsoft, but then moan when ubuntu breaks from the windows-made standards. People moan about how ubuntu is now copying Mac, but have never in the past moaned that they are copying windows with the button placement

Let me first say I don't hate Microsoft and secondly that that I am lamenting ubuntu's decision to move from the Xerox standard to the (I need to be different because I am a hipster) MAC standard. 
 [IMG]http://toastytech.com/guis/starapp3.jpg[/IMG]

---

### Post by KdotJ on 2010-05-07
I do appreciate that, but I just don't think it's fair for people to call it out right "wrong"

---

### Post by Penguin Guy on 2010-05-07
Thread with information and fix [here]("http://ubuntuforums.org/showthread.php?t=1455028").

---

### Post by benjamin222 on 2010-05-14
Thanks for that reply phil!! I love the new ambiance theme, but I definitely did not love the button placement. My ubuntu is looking perfect now!

---

### Post by Astrals on 2010-05-31
> **philinux said:**
> Minimise, Maximise and Close button placement.

A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because &quot;something&quot; is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon &quot;New Wave&quot;
3. Click the button &quot;Customize..&quot;
4. Select tab &quot;Controls&quot; and select &quot;Ambiance&quot;
5. Select tab &quot;Window border&quot; and select &quot;Ambiance&quot;
6. Select tab &quot;Icons&quot; and scroll down and select &quot;Ubuntu-mono-dark&quot;
7. Select &quot;Save Theme&quot; to your choice.



Thanks this works great.

---

### Post by SunnyRabbiera on 2010-06-01
an easy fix is ubuntu tweak.

---

### Post by geoffm on 2010-06-10
The developpers should make a compromise and put them in the middle.

You could also stop using buttons and start using mouse gestures. Moving the cursor to go click a button to do basic commands is so 20th-century. Now we have mouse gestures, it makes window buttons kind of obsolete, at least for me. All you need is to install **easystroke**

Personnaly I use those gestures, which I find intuitive:
down,left = Alt+F9 (minimize)
down-right = Alt+F4 (close)
upright diagonal = Alt+F10 (maximise)
downright diagonal = Alt+F5 (restore)

there are very intuitive to learn and use. saves you 2 seconds every time.

---

### Post by Dorrax on 2010-06-29
Mouse gestures would just cause my fidgeting to mess me up all day. 

The new feature on the right hand side of the windows will be a big flashing text that says "THIS IS THE RIGHT SIDE!". It will be 1 inch by 3 inches and play the "this is your right" song from Aqua Teen Hunger Force. Somehow, critical operating system processes will be routed through it, forcing you to leave in unchanged.

---


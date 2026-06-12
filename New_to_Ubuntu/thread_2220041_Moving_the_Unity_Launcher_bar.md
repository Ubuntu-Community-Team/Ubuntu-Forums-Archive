---
title: "Moving the Unity Launcher bar"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by Sir_Ismicoo on 2014-04-26
I prefer to have launcher on the right hand side of wide screen monitors, but I can't find a way to move the Unity launcher. I hope the Googling that I did is wrong when it suggests such a thing is not possible. If the launcher cannot be moved, can it disabled entirely so I can use something like cairo-dock instead. 

I have found nothing in the system settings, Unity Tweak tool or the /etc and /usr directories but maybe there is a hidden setting?

---

### Post by Sir_Ismicoo on 2014-04-26
Never mind. Just found [this comment]("https://bugs.launchpad.net/unity/+bug/668415/comments/2") by Mark Shuttleworth which says it's not possible and that it won't be. It's a real shame, I was liking Unity but cannot get used to having the launcher on the left. I know to most people that's a minor thing but it really isn't. I think I may open a new bug on Launchpad as the Ubuntu button being on the launcher completely nullifies his reason for marking the bug as wontfix.

---

### Post by Frogs Hair on 2014-04-26
Hello and Welcome

The launcher can"t be moved , but installing the Flash-back or Fall-back session along with Cairo Dock is possible. If you are Using 13.10 or 14.10 the session is named gnome-flashback-session . Once installed, the session can be selected at login at the top right side of the greeter box where your name appears . There once was Cairo Dock session that could be selected at login ,but I haven't used the dock for a long time.

---

### Post by deadflowr on 2014-04-26
> **Sir_Ismicoo said:**
> Never mind. Just found [this comment]("https://bugs.launchpad.net/unity/+bug/668415/comments/2") by Mark Shuttleworth which says it's not possible and that it won't be. It's a real shame, I was liking Unity but cannot get used to having the launcher on the left. I know to most people that's a minor thing but it really isn't. I think I may open a new bug on Launchpad as the Ubuntu button being on the launcher completely nullifies his reason for marking the bug as wontfix.

You go and make dozens of bug reports, but it won't change anything, and any bug reports are going to simply be marked "Won't fix".
The reasoning still stands, though not in the way you think.
Changing the placement of the launcher would also require significant changes and rewriting of the dash, the hud, and the run dialog, to fit within the movable launchers design.
It would also take away from efforts to fix existing problems, and instead add more.

Frog Hairs' suggestion is a far better way to have a launcher where you want.
That or simply fork the unity codebase and make an entirely new interface, to your own liking.

---

### Post by Sir_Ismicoo on 2014-04-26
That's a real shame. It's such a big deal for me as I don't think I'll adapt to having a launcher on the left because after so may years, my muscle memory is ingrained to them being on the right side! It's had a week and I'll may give it another few days to see if I can get used to it although I'm not holding out much hope; there are only so many times you can swear at yourself while moving the mouse left before it gets old. I'm afraid that the Fall-back solution seems entirely sub-optimal given the strength of my hardware.

 It doesn't help that I'm an ornery old goat who doesn't like being told how he will use his computer!

Maybe I can get something that works as I like by using a combination of Xubuntu, kwin and Synapse. I feel an experiment coming on. Sigh, more time to be wasted playing.

[edit]I did report it as a bug. They can only say no or yes.[/edit]

[edit2]
[quote=deadflow]Changing the placement of the launcher would also require significant  changes and rewriting of the dash, the hud, and the run dialog, to fit  within the movable launchers design.[/quote]
I don't know if you know for sure that those changes would be needed and how complex they  are or if you are assuming it would be that complex but if you are  right, the implication is that the code is badly designed and / or implemented, with tight coupling and poor cohesion and *that* doesn't bode well for the long term support of the codebase. Look at what happened to openssl and truecrypt. 
[/edit2]

---

### Post by Frogs Hair on 2014-04-26
> Maybe I can get something that works as I like by using a combination of Xubuntu

I have set up a right side launcher in XFCE using just an additional panel and also with Dockbarx. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=240742&d=1364658891[/IMG]

---

### Post by vasa1 on 2014-04-26
> **Sir_Ismicoo said:**
> ...
 It doesn't help that I'm an ornery old goat who doesn't like being told how he will use his computer! ...

Equally, it's a trend that *young* developers don't like to be told what software to write ;)

So, as others have suggested here and in several previous identical threads which have been promoted to **Recurring Discussions**, if I don't like something which can't be modified easily because the creator clearly doesn't want to allow that, some options I have are:
[LIST]
[*]to live with it
[*]dig deep to figure out how to modify it the hard way (and live with the probability of odd things happening as a result) 
[*]find some other software or operating system more suited to my needs
[/LIST]

---

### Post by LastDino on 2014-04-27
Best way would be to do what frog suggested in his first post.  It will save time and produce least amount of complications.  Fallback session panel also has some nifty stuff like move buttons on side of the panel which you might like rather than going for Xubuntu just because of that and installing lot of stuff again.

---

### Post by Sir_Ismicoo on 2014-04-27
I went with Xubuntu in the end and have it set up pretty much how I like it. ([link to screenshot]("http://ubuntuforums.org/showthread.php?t=2214270&page=9&p=13004515#post13004515"))

There are times I hate my brain because it has just tapped on the shoulder and whispered "we wonder if you could use something like wmctrl to move the Unity panel" - metaphorically speaking of course. Luckily Ubuntu is still on my test rig so I think I'll have to experiment a bit later on

---

### Post by mangocats on 2014-12-01
> **vasa1 said:**
> 

[LIST]
[*]find some other software or operating system more suited to my needs
[/LIST]


Kubuntu addresses this option nicely.

---

### Post by coffeecat on 2014-12-02
Closed to prevent this old support thread from being necromanced into yet another desktop comparison discussion.

---


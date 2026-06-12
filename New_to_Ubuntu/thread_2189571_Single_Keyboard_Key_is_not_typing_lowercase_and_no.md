---
title: "Single Keyboard Key is not typing lowercase and not worKing correctly. Need a fix."
date: 2013-11-23
forum: New to Ubuntu
---

### Post by djozone on 2013-11-23
I'm going to post the rest of my post without correcting anything pertaining to the problem just to demonstrate to you the problem that I have while explaining it to you.
oKay here it goes:

FYI: I'm currently using ubuntu 12.10 

And a heads up, Sorry if some of the words are hard to read, if they looK awKward or looK misspelled, it's because their missing the lowercase K I am unable to type now because of this problem.

First off I simply don't now what I did to cause the problem in the first place.

For some reason my K (lowercase K) ey will not type a lowercase K no matter what I try. it just simply does not register anything when I tap (and yes I said tap not hold) the K ey on my eyboard  If I hold down the K ey without holding the shift ey I am able to repeat the lowercase ey  (ex:kkkkkkkkkkkkkkk...). I tried looing online for a solution, but most do nothing except how to change your eyboard layout, change eyboard language(region) ect..., or remap eyboard shortcuts. I do not want to change my eyboard layout, I just want to fix my eyboard and get the lowercase K to wor lie it is supposed to. I have my computer set up to dual boot to Ubuntu and Windows and the problem doesn't happen unless I log into MY user profile in UBUNTU. Other user profiles(Guest) in Ubuntu do not have this problem at ALL. The problem doesn't exist until I log into MY Ubuntu profile. No eyboard problem in Windows, Just MY profile when on Ubuntu.

And before you start asing me if it's a problem with my physical eyboard that's sitting in front of me, The problem still exists if I try to use virtual on screen eyboards in Ubuntu. So it has to be something within my profile in Ubuntu that got royally f***ed up to cause this to happen.

The only thing I can even possibly thin of that could even remotely connected with eyboard changes was when I was changing eyboard shortcuts in Gimp but that shouldn't even remotely caused a ey on my eyboard to stop functioning correctly. Other than that I can't thin of anything I did while using my computer under Ubuntu that could have caused my lower case K ey to stop registering when I press the ey

_IS THERE ANY WAY TO FIX THIS SO I CAN GET MY K KEY TO WORK LIKE IT IS SUPPOSED TO?_

---

### Post by tgalati4 on 2013-11-23
Open a terminal and watch the behavior of:

```
xev
```

Move the mouse into the *xev* box and start typing some letters.  You will get a keypress code for each key on both press and release.  There are several places where keymaps are defined in linux.  What you need to edit depends on what environment are you running.

You will need to do some reading about *xmodmap* and *xkb*.  Do a forum search on those terms to understand how they are used.

[https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions](https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions)

---

### Post by djozone on 2013-11-23
ThanKs for the reply but I still do not understand the information within the linK you provided. It is still as foreign to me as a language I now nothing about. I don't really need to Know all the information about xmodmap right now, it's just that all I really need is a streamlined answer that basically just includes the information that can help me fix the problem that I currently have. Lets just assume you're talKing to a person who is basically is a 100% Linux/Ubuntu Keyboard customization newbie(0% experience).

If anyone would be so Kind as to try to help me fix my problem I would greatly appreciate the help. ;)

---

### Post by Bucky Ball on 2013-11-24
Have you tried another keyboard just to confirm this is not hardware related?

---

### Post by djozone on 2013-11-24
I really want to curse right now but I won't. I spent several days with this problem and I couldn't find a fix for it. Then I decided to update my Ubuntu 12.10 to 13.10 and for some reason on 13.10(not my 12.10) when the k key was pressed yellow stars started circling my mouse. I eventually found out it was the show mouse setting in CCSM was turned on (somehow I guess I turned it on in 12.10 without knowing I did before I upgraded to 13.10) and was set to toggle on/off with the k key. The thing I'm really frustrated about right now is the fact that something so simple as a little setting in ubuntu that was ticked on could cause me to feel so frustrated and many hours spent online trying to find the solution. ](*,)

I guess that's what happens when I use an operating system I am not used to using.

Oh well, the main point is that the problem is solved :)

---

### Post by Bucky Ball on 2013-11-24
And the other point is you learned something about your new system! ;)

Please mark thread as solved by following the instructions in my signature. Thanks.

---


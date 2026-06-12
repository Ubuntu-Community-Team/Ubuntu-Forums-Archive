---
title: "I noticed linux has no native &quot;undo&quot;. Explain? What if X happens?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-11-30
I lurked a bit, and I'm really quite surprised by this- CTRL+Z, a basic thing in windows, doesn't seem to exist in any form in linux. I have 2 things to ask regarding this.

1. Why? Perhaps a blunt statement, but sheer curiosity prompts it. I am assuming it has something to do with how code works, but I don't know coding protocol. Still, this intrigues me enough to ask- what is it natively with linux that keeps this from being? I welcome any input, no matter how convoluted it may seem to me, being a novice. I'm just curious as to how this works in XP, versus what linux architechture doesn't *seem* to allow. When I imagine all the actions one can "undo" in windows with just CTRL+Z, it really stuns me, and makes me think if we could add it to linux, it would be that much cooler. None of the posts on "no undo" seem to explain WHY it doesn't exist, only that it DOESN'T.

2. I *KNOW* some of you, like me, moved from XP to linux (in my case, 8.04 Ubuntu), and found the CTRL+Z missing the hard way. I'm sure this happens to more than a lot of you- accidentally delete an important, location dependent file, and you want to restore it, but there's no undo! Plus, recyle bin doesn't seem to have a restore function, much less anything telling you where the file was deleted from. What do YOU do? With the frequency I used CTRL+Z to undo & CRTL+Y to redo stuff, especially in mass file renaming & drawing, how do you all cope with this lack, or recommend I do? Any precautions I should take/know about before I attempt something? It really feels like I'm missing a hand or something without it.

Thanks.

---

### Post by C. Wizard on 2008-11-30
Never knew of tha function in XP.
The Ctrl Z combination does work in graphic applicatons, e.g., The GIMP to undo your last change. Maybe it works in other applications also... Just checked and it does the same thing in OpenOffice, so it must be also be "native" to Linux, or, at least, the KDE desktop.
Cheers.

---

### Post by slmouradian on 2008-11-30
> Plus, recyle bin doesn't seem to have a restore function

Yes it does! Right click on the file, and 'Restore'.

> much less anything telling you where the file was deleted from

The 'Trash' or 'Recycle Bin' is found at

~/.local/share/Trash/files/

The information for where each deleted file comes from can be found in:

~/.local/share/Trash/info/

---

### Post by Elfy on 2008-11-30
> Plus, recyle bin doesn't seem to have a restore functionIntrepid does have wastebin restore - not sure whether hardy did.
> 
What do YOU do?I tend to only delete files I know I want deleted.

---

### Post by handydan918 on 2008-11-30
One of the reasons that I prefer linux is because it doesn't treat me like an idiot.

You know, the incessant stream of stupid prompts everytime you try to do anything. 

"Are you sure you want to delete this file?"

"Warning! Modifying system files can cause you system to burn to the ground!"  

"Are you REALLY SURE you want to delete this file?"


Spare me. On the reare occasions that I need to try to accomplish something wint a Windows machine, I end up walking away frustrated and remembering why I swore off MicroShaft.

---

### Post by jerome1232 on 2008-11-30
I believe it just hasn't been implemented yet, there are bug reports filed against this and I believe the capability is there now just not working yet.

edit: As much as I think this functionality should be there, you need to re-thing your file operations if you've come to rely on undo/redo that much.

[http://bugzilla.gnome.org/show_bug.cgi?id=167501](http://bugzilla.gnome.org/show_bug.cgi?id=167501)


I guess this video is with nautilus patched with some development patch
[http://www.youtube.com/watch?v=G--PBDz3hEs](http://www.youtube.com/watch?v=G--PBDz3hEs)


In 8.10 if I browse into my trash and right click a file it has a 'restore' option, which restores the file to it's previous location.

---

### Post by BastardNamban on 2008-11-30
ok, a few things:

Unlike one original poster on this subject who was quite rude to the people responding to his question, I sense an air of hostility directed at me for not seemingly knowing better than to not delete something.

Ok, I know better. But occasionally, especially moving files, I'll make a mistake (my motor functions aren't perfect all the time!), and I'll drop files into some other folder- undo in windows allowed me to unmove those and leave them highlighted to move again.

This lack of undo is very annoying to me mostly when moving around/sorting files. It doesn't work for me in 8.04.

One of you mentioned there is an undo with CTRL+Z in certain apps- until now, I've mostly been setting up parts of my linux, and haven't used much of it yet, but you are right- Open Office has an undo that works, and I assume the Gimp example works too. That's great!

Problem is, drag & drop mistakes with files can't be undone with "undo"- and I sort around a lot of files. If I accidentally drop a lot of files in the wrong folder, I have to know the folder I dropped them in, and re-find each misplaced file- very annoying. I can't undo this with a single key combo like windows.

RECYCLE BIN- If it had a restore option anywhere, I was sure I'd have found it by now. I don't know what Intrepid does- I use Hardy Heron- already posted that. Hardy for me gives me no options right clicking to "restore". Maybe something's wrong. If it was there, I'd have found it- so I don't seem to have it, or something's wrong!

Don't get me wrong- I signed up with this forum BECAUSE I left Microsoft- I hate them too! I much prefer linux, but there were just some points I found different, and wondered why. That's all! I wasn't outright complaining- I asked you all what you do.

So thanks for pointing out to me CTRL+Z does work in some places, but my version of Ubuntu isn't giving me any restore options from recyle bin. I'll try looking into your bug report tommorrow- I live in Japan, and it's almost 4am! I need sleep.

---

### Post by oldos2er on 2008-11-30
Assuming you haven't changed any of the defaults, and that you're using Gnome, right-click on the trash icon on your bottom panel (it should be at the far right--again, assuming you haven't changed this), then click 'Open.' Right-click on a file or folder in your trash, and you should see a 'Restore' option in the menu.

---

### Post by sdowney717 on 2008-11-30
restore started with Ibex, not in Hardy.
An undo move will likely make it into nautilus eventually.
There are all sorts of nice things to look forward to, and remember to be thankful to the programmers for what has come before. It is free without cost for us to use.

---

### Post by sdowney717 on 2008-11-30
If you want undo then you can use dolphin file manager. It has an undo move option.
[http://dolphin.kde.org/](http://dolphin.kde.org/)

YOU CAN use this with gnome. When you install dolphin, it will likely install kde desktop elements as well.

Edit: Screen shot deleted. Please do not post such large images directly, use thumbnails :twisted:

---

### Post by Farmer of Bricks on 2008-11-30
Just be very careful with your mouse movements when using the click+drag copy+paste. I prefer to use the keyboard Ctrl+C or Ctrl+X and the Ctrl+V to move files in Hardy, as it's less finicky and I have better control than with the drag+drop.

---

### Post by steveneddy on 2008-11-30
I would suggest moving to the distro that has those features that you require, write them yourself or living with the distro and learning to live by it's rules and parameters.

Someone said Ibex has these features, so you could use Ibex or try and run the Nautilus that Ibex uses.

This would make the system unstable but would give you the features that you require.

IMHO-I would personally be more careful when moving or deleting files.

It actually sounds as if you need the OS to be more responsible than you are.

---

### Post by sdennie on 2008-11-30
"Undo" is context specific and so application specific.  There can't be a magical "Undo" button that is implemented below the application level so, when applications don't support some sort of intelligent "Undo", it's not really the fault of "Linux", it's the fault of the application.  I'm not familiar with Windows but, it sounds to me like it's simply the case that more Windows apps have built-in "Undo" support than their Ubuntu counterparts.  If there are particular apps that you are using where you find yourself wanting to "Undo" a lot, I would file a bug against those apps and request the feature.

---

### Post by BastardNamban on 2008-12-01
@ sdowney717- Thank you for pointing out to the others that Hardy doesn't have a restore option from recycle bin. I was not crazy after all.

@Steve- I just spent the last week figuring out how to get everything working, tweaking, and everything. I can finally use my linux the way I want. Considering how much time it took for me to install compizfusion 0.76 alone, backtracking through god knows how many sites & posts to do one thing, I don't know that I feel like going through the same stuff ALL OVER AGAIN, with different directions, because of updating to Ibex. I don't have that kind of time like I did last week- I was off. Maybe, since I feel comfortable now in using linux, I might go Ibex later when I have time. But Hardy is the long term support version- I like the idea of not having to totally reinstall EVERYTHING again after 2 years. I don't know if that's a natural mindset here or not, but I didn't want to do that unless necessary. I can't code my solution like others here, I just started.

@Voz- Thanks- I didn't know I could take that route with things, I figured if an "undo" function didn't exist, it was because there wasn't meant to be one. I never thought of addressing it like a bug. Interesting.
I'm afraid dolphin looks to have a rather convoluted layout to me, but that's just me. I'll check it out.

@ EVERYONE- I guess you'd say I'm one of the idiot masses that was smart enough to get AWAY from MS. I can't code, and I'm human- I make mistakes sometimes that prompted me to use "undo" in XP. I'm sure many of you have made a slip at some point too, that's all! That said, I'm not an idiot- I only asked what was fundamentally different in linux from MS software- I wasn't whining "wah! this isn't MS! no good!"- READ my original post. I was CURIOUS. I still am. I tried to ask as nicely as I could.

I now gather that "undo", in any form, as it exists in linux, is something individually addressed in each instance of a program- I thought there was a base set of codes or something that included it in everything, and things were built on top of that. I see now that when "undo" worked in XP, it was because they had to put separate support for that function in the application. That's kinda what I was curious about.

From now on, I'll refrain from asking a "XP could do this, why can't linux?" question- because I see, it seems it just brings out aggravated replys. A shame that curiosity is treated that way here, I expected better.

---

### Post by Psykotik on 2008-12-01
Namban, don't take too personally this kind of answer. People answering "accept it or quit" (as steveneddy does) will always be loosers, whether the OS they use.

Feel you free to criticize the way Ubuntu (or any other OS) works; it is because people where blaming the lack of "restore" function, intrepid got it.

Also, do not hesitate to contribute to the GNU/Linux world, reporting bugs you found, features you want, and so on. And avoid these strange people haunting for years the GNU/Linux world, and still not understanding its philosophy.

---

### Post by jorj82 on 2008-12-01
> **Psykotik said:**
> Namban, don't take too personally this kind of answer. People answering "accept it or quit" (as steveneddy does) will always be loosers, whether the OS they use.

That's not what he was saying, read a little more carefully.  And before pointing the finger and calling people "losers", you should take into account that these people have been answering "windows does this why doesn't linux?" for many years.  And the answers are already in the forum.  The "search" function is your friend.  If you really don't like Ubuntu, there's dozens of other distros to try; that's what stevendaddy was saying.

---

### Post by Psykotik on 2008-12-01
> **jorj82 said:**
> That's not what he was saying, read a little more carefully.  

Sorry, but you should point me out where I misunderstood the stevendaddy's disdain:

"I would suggest moving to the distro that has those features that you require, write them yourself or living with the distro and learning to live by it's rules and parameters."

and 

"It actually sounds as if you need the OS to be more responsible than you are."

are not exactly very kind words.

> **jorj82 said:**
> And before pointing the finger and calling people "losers", you should take into account that these people have been answering "windows does this why doesn't linux?" for many years.  And the answers are already in the forum.  The "search" function is your friend.  If you really don't like Ubuntu, there's dozens of other distros to try; that's what stevendaddy was saying.

I'm going to be rude: I don't care the people answering in this forum had had a bad day, they are tired to answer always to the same questions, or anything else.

Keep in mind that answering is not mandatory; the volunteer may choose to answer or not. Therefore, you may choose to answer or not ten thousand time to "windows does this why doesn't linux". But don't complain if you loose your patience; you're the only culprit.

---

### Post by jdong on 2008-12-01
The question has been answered adequately, and now this is just turning into a flame war. Let's move on to more productive things :)

---


---
title: "[SOLVED] How do I install Quake 3 Arena? (warning: n00b question)"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Fazz Munkle on 2008-05-19
Backstory: Ok, I've been using Linux for the better part of 6 years now. But, BUT, I've only used the graphical part of Linux. Gnome, KDE, etc. Anything that was end-user friendly. I'll avoid using the CLI whenever possible. Especially when instructions aren't clear enough and I run into roadblocks. Often this happens when I'm asked to compile something and the instructions are obviously dated before the current release of the distro I'm using. I'll try the instructions to the best of my ability but scrap it when errors arise that I can't find a solution for. Oftentimes I'll abandon installing something and wait for a user friendly graphical installer for it to come out (in which case often means never).

I have absolutely no patience for incomplete and dated instructions for compiling programs from source. I come from a history of not using a CLI for my daily computing needs. I get the feeling that for some this is incomprehensible, but it's true. Remember, I'll avoid the CLI (ie: terminal) whenever possible. That is not to say that I haven't launched programs and installers from the CLI. The Loki Quake 2 installer was just a double click in Ubuntu 8.04 where then I clicked the Run button and it ran. I'd imagine that I'd just type ./quake2_3.21-r0.16.1-english.run in any other distro. That's fine. I can handle that. It's total automation without any Linux terms I'm assumed to know by the programmer.

Now, with that out of the way, with my level of compiling knowledge and impatience with incomplete (or Engrish) instructions is there an easy way to install ioquake3? I've tried other installers (the Loki installer, the official id installer) but I run up against various errors obviously because they're old installers and 8.04 has changed things. **I know 8.04 has changed things because I tried installing older Windows games like Starcraft through Crossover Games and WINE and keep getting errors which I'm explained, from searching Google, are security measures put into the latest Ubuntu that prevent malicious code from accessing some lower whatsiwhozit of memory. Ok, I'm fine with that. There's a workaround that apperently doesn't work on my computer because it's automatically changed back for some reason (I'm guessing more of the security thingamabobber put into 8.04), so I'll wait for updates to WINE and Crossover Games that deal with 8.04. So WINE based installs of Quake 3 Arena are out for now.** So I tried going with the only thing I've found that's up to date (ioquake3) and I'm running into problems. The only answers I get from searches in Google are RTFM. Great! Thanks! That freakin' helps a lot (no it doesn't). :roll: Double clicking on the x86.run file brings up the graphical installer but when it asks me for the CD (which is already in the drive) the Yes button just drops me back to the "put the CD in the drive" window. So I went online to look for answers, but I find that there's something wrong with the .pak files on the CD and I need to download some updated .pak files and do some compiling. Fine, I've followed directions before and compiled programs. So I try to follow the instructions for compiling this from svn (or whatever it's called, you know what I'm talking about), but I hit a roadblock I'm not completely sure I understand (yet apparently I'm expected to know :roll: ). There are no errors I can see yet nothing is done. So I give up. No results, no play.

My question is, is there an easier way to install Quake 3 Arena that doesn't involve advanced knowledge in Linux compiling that assumes you know what Linux vets are talking about? IE: graphical user interface installer like the Loki installers. That's it. That's my question. I figured all that text before would head off any RTFM BS from vets tired of the n00b influx to Linux. ;) And if you haven't guessed yet, I'm frustrated with all this.

Bolded: What's the deal on this? I can't install older Windows programs because of this (So long Oddworld: Abe's Oddysee. j/k Just needed an older game as an example). Has Canonical addressed this? If they have is there a news article I can read on it and people's reaction to it? I'm not sure what to look for on Google (what it's called what they did).

---

### Post by ZabiGG on 2008-05-19
Did you try posting this in the Gaming and Leisure section of the forum? You might get more "specialized" help over there...

And the terminal is really not that scary. You should check out the links to the basics in my signature below. The terminal how-to makes sense and will make your life much easier.

Cheers,

Z.

---

### Post by Fazz Munkle on 2008-05-19
Gah! I didn't scroll down at the index of the forums. Sorry sorry. :oops:

And yeah, I know the CLI isn't that scary. I'm mainly complaining about the advanced things to do in Linux that usually involve the CLI and how it's expected that people coming from Mac OS (any version) or Windows (any version) are expected to know what the various terms are or told not to worry about what they just typed in as long as they followed the instructions.

I guess I just wish there was something like the ring binder user guide that accompanied all older Macintoshes for Linux. Something to go to and it would explain in plain English what things did. I'll look at your links, but I don't hold out hope. I'm somewhat of a GUI purist I guess. "If it can't be done with a slider and a button, then it's not worth doing." :lol: j/k I'm not that bad.

---

### Post by ZabiGG on 2008-05-19
I know! ;) I started using linux/Ubuntu barely two months ago...

Most of those things you can achieve with the gksudo command and nautilus.

You'll have to enter

gksudo nautilus 

in the terminal and enter your password, but you'll be able to do most of your administrative tasks directly from that GUI, with your beloved mouse :p

I learned that in those links... lol

Cheers,

Z.

---

### Post by Fazz Munkle on 2008-05-19
Heh, I remember those ring binder user guides had everything from using a mouse to networking Macs across AppleTalk. I miss guides like that. Everything from soup to nuts. And it was good that they assumed the user didn't know how to use a mouse because then you knew that with the more advanced problems in the guide that you could breeze through them no problem because the explanation was written in a way that wasn't confusing, step by ever so clear step. I became quite knowledgeable of the ins and outs of the pre-Mac-OS-X Mac OS as much as a non-programmer can. Because then that lead to me using ResEdit to hack apps. :lol: Didn't know hex, but I could edit the menus and graphics of the Finder to my heart's content. Felt so good the day I figured out how to change the Apple Menu icon from a MacAddict magazine issue. Issue 5 I think.

Maybe you can answer something for me. How many Linux vets do you think have used Linux and nothing else their entire life? Mac OS and Windows have never entered their lives at any point. Could explain the impatience with n00b these days. Just a theory of mine, but I'm not sure how many people are thinking the same thing. So I'm cautious about how to phrase it for fear that it might be interpreted as a slam on Linux vets. It isn't. I just ran into one Linux vet once who had never used any other OS before (never used DOS, never used Windows, never used Mac OS 7.5 or 9 or X, never used anything that was part of the great OS wars other than Linux) and this got me thinking.

---

### Post by Awareness on 2008-05-19
I don't know...but i kinda know what u feel...i tried... and i couldnt either... so i gave up... :/

so...im stuck with open arena... hey they even had some cpm server running with ra3 maps and it works in oa :oooo

But if i play one more time one q1 map conversion i swear im gonna kill myself.... those maps are just not intended to be mp...worst maps evaaaa why ppl keep putting'em in mp servers! (for the sp its ok, coz i dont play sp ^0^)

If you find out an easy way... plz just share it with big bold letters in the subject of the post :D

---

### Post by ZabiGG on 2008-05-19
Well.. ;) 

As opposed to some other forums, you'll find people here are eager to help. Just mention you're a newbie and they'll be even more so and coach you through it to the best of their abilities. I'd say most users have mixed experiences and can think back to when they were using other OSes... 

But you have to remember that the people who answer here are volunteers and may, sometimes be tired of answering the same old questions over and over again, so -- humanly enough -- they tend to keep their answers as short as they can, hence the command lines.

Your newbie status will get you free passes with them, as long as you're candid and as specific as possible about your questions.

Cheers,

Z.

---

### Post by Fazz Munkle on 2008-05-19
Will do on both counts. :) To the "easier way of installing Q3A." Either I will post a topic specific to that or most likely I'll post about an overall easier way that works with many games at once (unfortunately that way seems to be gone for now with the WINE/Hardy problem).

This may even force me into learning how to program and make the installer myself. Mmmm... Nah... ;) I'd rather be a dumb ol' end user enjoying the fruits of labor of people who know more than I'll ever know. :D

---

### Post by Fazz Munkle on 2008-05-19
Click [here]("http://ubuntuforums.org/showthread.php?t=800028") for the solution.

Ok, how do I put the [SOLVED] tag on the title again...? ;)

---

### Post by ZabiGG on 2008-05-22
Happy you found a solution ;)

Click Thread tools (on the right, just above your first post)
Click Mark as solved


Cheers, and happy gaming ;)

Z.

---

### Post by Awareness on 2008-08-14
I cant belive how easy it was...

It took me 5 mins just get the .run from here [http://ioquake3.org/get-it/](http://ioquake3.org/get-it/)
And then copy your pak0.pk3 from your quake3 cd or even some old installation... and voila... its working with sound and everything

Ive been using open arena... and tried several methods to install q3a in linux... but ioarena was just the solution i was looking for... :)

Ive not tried mods yet tho or my old settings but it seems it will work smoothly  :)

---


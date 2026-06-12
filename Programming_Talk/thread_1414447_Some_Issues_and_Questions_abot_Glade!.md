---
title: "Some Issues and Questions abot Glade!"
date: 2010-02-23
forum: Programming Talk
---

### Post by madmax.santana on 2010-02-23
Hi there everybody. I started learning Gtk+ a few days back and it wasn't past a week fiddling with Gtk+ that someone told me that Glade is a nice RAD tool which would help me build my interface very quickly (definition of RAD :))

Anyhow, I checked a few tutorials and gave it a try... There is something there, though, which I would like to point out... Although I liked Glade overall, it is quite easy to use and files are very handy to implement, and that it saves me from getting frustrated over the Gtk+ code for interfacing while making it much of a Visual Studio thing to me.

But after I have built the Glade file, I implement it using a GtkBuilder (That is the only method known to me yet)... Using the GtkBuilder calls I take the *.glade file and then build a Window from it. Well, *ahem*, what happens if the *.glade file is not present in the mentioned directory?

- Either the program crashes
- Or, if better coded, it exits returning a very inhumane error! :)

What bothers me is, I cannot explain why, but this whole thing does bug me a lot. In my opinion, (and I honestly don't know why I have such an opinion), the interface should not be saved in a separate file. Rather it should be localised inside the application...

Well, what I want to ask is,[SIZE=2][COLOR=Red] is there a way I can get rid of the *.glade file and issues it brings with it? [/COLOR][/SIZE](Please don't tell me to follow traditional Gtk+ interfacing with codes :))...

Secondly, besides glade, [SIZE=2][COLOR=Red]is there any other RAD tool out there???[/COLOR][/SIZE] I may look for, ummm, something which[SIZE=2][COLOR=Red] combines the interfacing and the Code in the same IDE [/COLOR][/SIZE](maybe interface visually and the write function calls for events in a code editor which resides in the same IDE)

And also, I may keep working with glade if I can be assured that [SIZE=2]some other technique is available which sort of embeds the interface in the code and every time application runs, it doesn't go look for *.glade file...[/SIZE] :)

When I started with Glade, my stupid perception was, perhaps I build the interface with the glade... Then using another application, I turn it into C code and then I copy-paste the code in my application code to make it work...

Or maybe, I construct the interface with Glade, use a builder in Gtk+ code and when I compile it, the compiler looks for the *.glade file and build the executable... The executable would be independent then!!! (Certainly didn't have in mind that the application willbe dependant on *.glade file forever.)

---

### Post by madmax.santana on 2010-02-23
Well, I dunno what got into my mind and I did a

$ find / -name *.glade

on my terminal... I was amazed with the results... Like OMG, so many applications, most of the the core  of my gnome-utils are using glade for interfacing. In my /usr/share there are so many of *glade files... Like for example, Synaptics, it has a directory /usr/share/synaptic/glade which is freaking full of glade files...

So, if I think using a separate glade file to load interface every time the application is run, is a common practice... If I develop an app which is going to be distributed in a deb package, I direct the dpkg to first copy all the glades into the share folders and then install the binaries (while I have designed the binaries keeping in mind the path to glade files...) That, I guess is meant to be done while you develop an app with glad!!!

But it still bugs me... THIS IS GOING TO BE SLOW... It is ot processor friendly... The application first loads, setting the global variables, if any, then goes searches for the glade file on path and IF the file is found, load the interface from it and IF there was no problem loading the interface load the respective calls against the events and then show the window...


That's damn ages for the processor, and a lot of toil too. I am still looking for a better technique or a better IDE, or a better RAD tool :)

---

### Post by wmcbrine on 2010-02-23
> **madmax.santana said:**
> But it still bugs me... THIS IS GOING TO BE SLOW...Nonsense.

Anyway, we just had a thread about this:

[http://ubuntuforums.org/showthread.php?t=1408536](http://ubuntuforums.org/showthread.php?t=1408536)

---

### Post by madmax.santana on 2010-02-23
> **wmcbrine said:**
> Nonsense.

Anyway, we just had a thread about this:

[http://ubuntuforums.org/showthread.php?t=1408536](http://ubuntuforums.org/showthread.php?t=1408536)
Hahahahaha!!!

I understand your sentiments! But I speak only what I conceive! Maybe you can correct me?

[COLOR=Red]**Edit:**[/COLOR] *Sorry I was quick in replying and I replied before the page was fully loaded! When I replied, your message just contained a single word "nonsense" :). I was amused by that!*

Anyway, had a go at the thread, and yes, now I think (if it is not slower) keeping a separate file for interface might not be a bugging problem! :) Thanks for help! *Tada*

---

### Post by CptPicard on 2010-02-24
Don't take this as one of a "mercy killing" of mine, just another set of observations that are not "about you" personally...

> **madmax.santana said:**
> 
But I speak only what I conceive!

This is often the issue. It's often pretty easy to see what someone has been exposed to by what "they can conceive". Increasing the amount of things one "can conceive" is the goal of being educated in a matter, and this is one of those things where it might be worthwhile to see what the others conceived and why...

> 
Anyway, had a go at the thread, and yes, now I think (if it is not slower) keeping a separate file for interface might not be a bugging problem! :) 

The idea that is "slower" tends to just reveal a total lack of actual experience of coding and running applications that do this stuff -- and also a lack of theoretical understanding of how and in what form the XML-described GUI actually ends up being run on the CPU.

If this objection was actually being made in the context of, say, an embedded device or for some real reason to have the single binary (this "ideology" seems to come from Windows), I'd understand the need, but as a general goal and in the ways it got defended here recently, it's nonsensical.

I mean, consider this -- you found out that pretty much all of your GNOME apps make use of this model. Does it look like your desktop is being totally bogged down by XML GUIs? The guys who hacked up GNOME are supposedly pretty smart people... how likely is that after all the work they put into it, some relative beginner "figures out" they were going about it wrong?

I'm just suggesting that in programming there is a real meritocracy, and as technical matters can be resolved to be at least somewhat objectively "correct", there is tendency to converge to a good solution. This is not just establishment momentum. At first, best idea is always to get clued in to as to why things are the way they are, if one really is not strong enough in the Force yet to make a thoroughly reasoned break from established norm.

---

### Post by madmax.santana on 2010-02-24
First of all, Cap'n, I think mercy killing is a good thing... :) So all things aside, you do a nice job spanking my theological ideas around, once in a while! :) Do not take the comments in the other thread as any offence! I consider you my valuable comrade as far as Ubuntu forums and particularly programming goes by!

Secondly

> This is often the issue. It's often pretty easy to see what someone has been exposed to by what "they can conceive". Increasing the amount of things one "can conceive" is the goal of being educated in a matter, and this is one of those things where it might be worthwhile to see what the others conceived and why...Yes this is a problem I suppose! I have to take my surface thinking deeper! But after all, I am just another human being and I think it'll take the time it needs.. :)

> The idea that is "slower" tends to just reveal a total lack of actual experience of coding and running applications that do this stuff -- and also a lack of theoretical understanding of how and in what form the XML-described GUI actually ends up being run on the CPU.Exactly! You got me! I am inexperienced. And I do not have the mentioned knowledge on things! :) Actually, (once again maybe I am going to hurt your feelings), this was what I thought would be if the interface was separately managed than the application! :) Just what I thought. I might have been wrong, and I suppose I was wrong in this case.

> If this objection was actually being made in the context of, say, an embedded device or for some real reason to have the single binary (this "ideology" seems to come from Windows), I'd understand the need, but as a general goal and in the ways it got defended here recently, it's nonsensical.
Yes I understand totally what you mean! Maybe I shall come to UF once again when I am in my final semester designing some fancy embedded system module of some aircraft... 
And right, this ideology did come from windows! I came to know about Linux just 4-5 years ago and I was one of those compelled-to-use-windows people before that! And unfortunately, I have had some experience with Win32 apps in my past. So that ideology does come from Windows part of my brain! :) And yep, I am totally ready to adapt with the recently standardised practice of decentralising the interface!

> I mean, consider this -- you found out that pretty much all of your GNOME apps make use of this model. Does it look like your desktop is being totally bogged down by XML GUIs? The guys who hacked up GNOME are supposedly pretty smart people... how likely is that after all the work they put into it, some relative beginner "figures out" they were going about it wrong?I am afraid Cap'n you read me wrong here! I didn't mean they were going the wrong way! I just said it didn't impress me much! (But as I have pondered on the possible dimensions this innovation could give me, I am much more impressed...)
Anyway, I meant it light heartedly! Can't a man have a heart Cap'n? :)

And honestly captain, the last paragraph of your post, I haven't even read it... Your English is such Lord-ish and superior that my eyes are already going week, after a full hour of deciphering your excellent (but difficult) English!!! :) Have a nice time!

---


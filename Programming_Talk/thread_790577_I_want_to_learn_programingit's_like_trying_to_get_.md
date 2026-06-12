---
title: "I want to learn programing/it's like trying to get a drink from a firehose"
date: 2008-05-11
forum: Programming Talk
---

### Post by mhrpinca on 2008-05-11
Hi
I want to learn how to build stuff. I say stuff because i have no idea what it is i want to build or use programing for, yet. I tried visual basic in windows and there were projects like building a web browser, a Celsius converter, etc. OK that was fun....
I've gone through the beginners tutorials for python, but im having a hard time finding any project based tutorials that work or that don't assume i know more about programing than the average nob. My reference point is Photo shop and flash all the tutorials they have are Project based, which in my opinion is a great way to learn.i guess the stuff i want to build will include windows and buttons and check boxes that do things, its also important that **my stuff will look however i want it to.** 
I get the feeling that i need to learn a language which is what i want to do, but which one, and after what point am i wasting my time. python is vast the beginners tutorials only take you so far and then your options are immense and overwhelming 
a friend recommended eclipse but the tutorial doesn't work its broken and it is point and click will i learn much this way?? I've also wasted months searching through stuff that either didn't work, was to advanced, was broken, was outdated or if you down load the package and try to install it you have to compile it and blah blah blah. Oh ya i forgot to mention I'm new to Linux as well. any help would be appreciated i want to make stuff happen on my screen. one goal would be to build a browser with tabs (like fire fox or explorer 7 but for my favorite apps) with a quick launch tab at the top so i could run all my apps in one windows form and switch back and forth between apps much like i can switch pages with Firefox tabs 
So where do i stop with the nob tutorials and start building stuff????
and How?
I think my goal is to build GUI's that do STUFF. (LOL) ty

---

### Post by lswest on 2008-05-11
Well, i take Computer Science in my high school (we learn Java and later c++) and we start with the basics too, because you need the basics before you do any GUI programming.  That said, if you want to give Java a shot, there's a great book called Blue Pelican Java online that's free to download, maybe give that a look?  I find it progresses smoothly from one topic to the next.

---

### Post by nvteighen on 2008-05-11
Take a look on Gambas; it resembles Visual Basic and may suit you well... It has a "Project" wizard too, but I personally didn't like its examples. You can install it by typing the following in a Terminal:

```

sudo apt-get install gambas2

```

But anyway, it may not be the best path to follow.

---

### Post by pmasiar on 2008-05-11
OP: your problem is IMHO that you set too ambitious goals. GUI stuff is hard, and making it exactly as you want is even harder. Try EasyGUI for Python which will generate GUI the default way, or even better, skip over the whole GUI problem and learn **programming** first - programming is **much** more than just 'making the stuff look like you want' - that is graphics design. Many programmers do not care at all how the stuff looks like, if it works at all :-)

GUI requires handling events, and that means program will be executed in order of user initiated events, not in the order you  sequentially structured it. It is hard, and it is not the most important thing in learning programming - it is important for GUI only.

Try sticky FAQ or wiki in my sig for links to training task which do not require GUI magic, but will let you to learn more about  programming internals (data structure, module design, algorithms, etc).

I would not bother with Eclipse, it is very powerful IDE - way too powerful for what beginner needs. IDLE or simple editor like SciTE or anything you like is fine. SPE is Python IDE developed on ubuntu, so it should work OK.

And forget about Basic, when you become Python expert you will understand why! :-)

---

### Post by LaRoza on 2008-05-11
> **mhrpinca said:**
> Hi
I want to learn how to build stuff. I say stuff because i have no idea what it is i want to build or use programing for, yet. I tried visual basic in windows and there were projects like building a web browser, a Celsius converter, etc. OK that was fun....
I've gone through the beginners tutorials for python, but im having a hard time finding any project based tutorials that work or that don't assume i know more about programing than the average nob. My reference point is Photo shop and flash all the tutorials they have are Project based, which in my opinion is a great way to learn.i guess the stuff i want to build will include windows and buttons and check boxes that do things, its also important that **my stuff will look however i want it to.**

So where do i stop with the nob tutorials and start building stuff????
and How?

I think my goal is to build GUI's that do STUFF. (LOL) ty

Programming isn't about GUI's. GUI's are an after thought. The best programming I have seen has no interface, and is usually on backends and kernels and such. GUI's are a different ballgame. 

If you don't want to be programming, and want to design, perhaps web development is what you want. On the web, the hard stuff is already done. You can use XHTML + CSS to make the interfaces and you can use ECMAScript or something on a server to make the decisions.

It seems you don't want to programming in the sense that most programmers see it.

---

### Post by mhrpinca on 2008-05-11
my back ground is in graphic design and graphic arts, I'm the typical user, I can use flash, and the basics of action script and such, there are plenty of tutorials like building an advanced preloader that gives the file size and percent loaded etc, i use photoshop, illustrator, what if i want to build a filter from the ground up. i can use flash to build GUI's of sorts, you can also use flash to build desk top apps, alot of autoplay cds open up with user interfaces built with flash, the interface is easy. but when i click install or hit a button on a filter, some one wrote the code for what happens next? so ya i want to learn the back end.
also im using blender it uses python script as well
what i was told was to learn a language (via the forums). and the language that was suggested was python, its easy to learn correct? OK so i've gone through the basic tutorials what next? are there any tutorials that bridge the gap from nob to expert thats what i want to know? as far as guis go i just want to know how to add buttons to a standard windows form or Linux equivalent not a web page. I've gone through the beginning nob tutorials. its really frustrating
html is easy, cut and paste java script isnt what i want, same with php. i already use that stuff for server side email on my website there was some stuff i had to set up within the script same with the java script im using. but i didnt do the code.
the only reason im messing around with python is because that was what i was told to try by someone who knows what there talking about? bottom line is i want to learn programing, a language. and im looking for ways to apply it so i can learn more via project based tutorials. simple.

---

### Post by pmasiar on 2008-05-11
> **mhrpinca said:**
> bottom line is i want to learn programing, a language. and im looking for ways to apply it so i can learn more via project based tutorials. simple.

Not so simple :-) Seems to me like you want to find simple graphic GUI IDE, it has hardly anything in common with programming as commonly understood. Glade?

Free software requires higher level of dedication and self-study than more common proprietary legacy software, because there is no company to finance writing the boring stuff -- in Free Software, all the tutorials, docs is mostly work of volunteers, like you and me. If it is not good enough, learn the stuff and improve it. :-) The whole point is to be self-reliable, helping the next guy.

---

### Post by mhrpinca on 2008-05-11
wow im sorry i gave that impression, i guess web portals and such don't use, any sort of programing to make them work, and you don't need the pretty pictures and the little buttons that make a user interface work. i guess theres no script or programing to any of that ha, its all little elves doing the work using magic and such. (Jeez my buddy's building web portals for 3com using a hell of a lot of python and building the interface as well(but hes not at my beckon call). maybe no one knows and its just another mystery of the internet.
i just want a language to learn and some some tutorials that go beyond the basic nob stuff that don't make me fell like beating on the authors head with a hammer, jeez seems simple enough to me.
if this post seems a bit sarcastic I've been at this for a while now looking for some good tutorials other than the absolute beginners guide to python programing, so i guess project based tutorials that teach you the how and why of programing that go into some kind of detail as to what your actually doing, that actually work and don't drag you through the entire library of python and teach you stuff you'll never use.am i supposed to give up now???
or is it possible that there are guided tutorials that teach you by applying python programing (insert whatever language you like) to some task? i was hopeing for something geared towards my interest but seeing how programing has no application to what im interested in. i guess i can stick with address books and the like (although it would be nice to give my address book a nice little window to live in, and to assign a launcher to it)
so i guess there is no solution and i should just Google some bread recipes and spend some time learning how to download music files?????

But any way thanks for taking the time to define what it is i really want to do (i think i mentioned learning programing in there somewhere).....
and actually you guys gave me some links so i sincerely thank you but its all stuff i have tried thanks!

---

### Post by Can+~ on 2008-05-11
Programming has no bridge between being a noob and being an expert. You:

1.- Learn the language syntax, concepts.
2.- Learn some of the typical modules, the others are learnt on need, by using the documentation mostly.

That's all what the tutorials will teach you, the real job becomes when you need to solve problems with programming, and for that you use Algorithms and data structures, for instance, there's another discussion on how to simplify a mathematical equation to get to a more optimal program.

I also came from the easy world of flash. Where you could do a movie Clip and assigning a name, and it was automagically linked into the AS section. In terms of programming, it isn't about building graphical interfaces; it's about solving problems, later, you can add a GUI over it for users to use it, but that's the tip of the iceberg, it's basic to do once you learn the toolkit (GTK in my case).

You're just confused, you think that applications are graphical things, so do I used to think. Well, for that matter, programming existed long before user interfaces, even before computers as you know them.

---

### Post by WW on 2008-05-11
> **mhrpinca said:**
> ...
what i was told was to learn a language (via the forums). and the language that was suggested was python, its easy to learn correct? OK so i've gone through the basic tutorials what next?

Specifically which Python tutorials have you gone through?  Terms like "noob" and "expert" are subjective.  It might help the Python enthusiasts here if they knew how much you actually already know.
> **mhrpinca said:**
> 
 are there any tutorials that bridge the gap from nob to expert thats what i want to know? as far as guis go i just want to know how to add buttons to a standard windows form or Linux equivalent not a web page. I've gone through the beginning nob tutorials.

Again, *which* tutorials?
> **mhrpinca said:**
> 
 bottom line is i want to learn programing, a language. and im looking for ways to apply it so i can learn more via project based tutorials. simple.

I agree with those who recommend python.  I don't know if any of these are "project based", but there is a big list of python tutorials here, broken down by subject area, including dozens about GUI programming: [http://www.awaretek.com/tutorials.html](http://www.awaretek.com/tutorials.html).  Find a subject that interests you, and dive in.  If you get stuck, ask here!  There are a lot of people here who love to answer questions about python.

---

### Post by pmasiar on 2008-05-11
Those are not tutorials, but you might find useful videos about using Python (many free, some paid): [http://www.showmedo.com/videos/python](http://www.showmedo.com/videos/python)

---

### Post by CptPicard on 2008-05-11
There is no [royal road]("http://en.wikipedia.org/wiki/Royal_Road#Cultural_references_to_the_Royal_Road").

You will set up your own projects as you go, and you essentially need to be able to know how to program in general before you will be able to do what you want to do. If there were such a way as you seem to imagine there should be, you would end up being just some sort of a code monkey who doesn't understand what he's doing anyway, so be there isn't.

Programming is far more rewarding in the general case, and GUIs are just a subset. You won't be able to actually make your GUIs do anything interesting anyway without learning to be a real programmer :)

---

### Post by esaym on 2008-05-12
Yea I feel you.  I have been trying to learn either C or ruby for many months now.  I have read all the ruby books out there but I just can't make everything come together.  Yea it really sucks.  You just got to dedicate the time and keep trying.  Many community colleges have courses in different languages also.  Might be worth a shot.

---

### Post by mhrpinca on 2008-05-12
Thanks WW thats what I was looking for.... i was realllly frustrated
that link looks good direct and to the point tutorials where i dont have to search through miles of stuff. thank you

---


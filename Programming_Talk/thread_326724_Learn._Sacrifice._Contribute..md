---
title: "Learn. Sacrifice. Contribute."
date: 2006-12-28
forum: Programming Talk
---

### Post by phossal on 2006-12-28
While the overall popularity of Ubuntu will always be defined by the total number of its users, the overall value of Ubuntu will always be defined by those resilient, tenacious, inspired, knowledgeable programmers who make it what it is. The real *value* of Ubuntu is still what it was when linux was just beginning. It isn't the ability for a million users who have a problem to post blogs about it, it's in the ability of the few hundred people who can and will provide solutions by sacrificing their own time and energy.

There are a lot of bad sources of information out there, but enough good ones that a discerning individual will get along okay.

For those users (like me) who benefit from all of the time, energy and determination of the people who came before us, who use the products like the OS, compilers, music players, and browsers for free, it's time to give something back, and it goes beyond solving the simple problems related to installation and use. 

Learn c. Learn assembly. Solve a real problem. Write a device driver. Add a feature. Give something *real* back.

Learn. Sacrifice. Contribute.

---

### Post by coder_ on 2006-12-28
Well, helping back doesn't have to be by code.

I'm encouraging everyone to try to help answer more threads than ask.  If you might know, state you might know what the problem is, and try it out.  That is the easiest way to participate in an open source project:  Help out your peers.  Also, take the extra minute if an application crashes due to a bug to submit a bug report.

---

### Post by phossal on 2006-12-28
Helping in an open source project doesn't require submitting applications, patches, drivers or utilities. As you mentioned, there are a lot of ways for even a novice user to relate previous experience - no matter how limited - in order to assist another. 

In general, those people who can really solve problems opt not to because of the tremendous sacrifice it requires. Quite frankly, they could be spending time with their families, or simply making money. Those people - the ones who truly recognize the value of powerful open-source software - need to reinvest.

---

### Post by slavik on 2006-12-28
writing a driver is sometimes not so easy ... especially when you have to reverse-engineer things.

---

### Post by amo-ej1 on 2006-12-28
writing a driver is sometimes not so easy ... especially when the hardware companies are not willing to share specification of the hardware they're using.


have you tried google, isn't it by any change supported by ndis ? Google: [http://www.google.be/search?hl=nl&q=WG111+linux&btnG=Zoeken&meta=](http://www.google.be/search?hl=nl&q=WG111+linux&btnG=Zoeken&meta=) showed some results of people getting it to work with ndis (which would require to roll back to a 32 bit version, since the hardware vendor doesn't supply 64 bit drivers).

I'd say chances are pretty big you'll be able to get it to work in a 32 bit work.

But for any hardware you ever buy, FIRST use google to check for linux support, THEN buy. This 'll save you a lot of head aches in the future.

---

### Post by phossal on 2006-12-28
[Edited]

---

### Post by tseliot on 2006-12-28
> **phossal said:**
> It has been a relatively pain free experience, with the exceptions due to the troubles caused by the AMD64 platform incompatibilities. Because I use my machine for programming more than anything else, I haven't been crippled by the web browser issues. My biggest complaint has been the pathetic support for the WG111v2 wireless dongle. In short, it doesn't work (on AMD64).
Why do you use Ubuntu 64bit?

---

### Post by amo-ej1 on 2006-12-28
On one point I agree with you, it sucks that have that one piece of unsupported hardware, and all those talented people out there refusing to do anything about it. 
BUT, take a look at what _is_ supported, you can't say people are sitting around and doing nothing. Browsers have been writting, database systems, reverse engineering _is_ being done, high performance filesystems are developed.

But I still stay fixed to my point. The reason why you wireless dongle is not supported is because the industry, (you know the people _you_ supported by buying that dongle, to whom you made the statement 'carry one, here's my money') is refusing to cooperate with all those talented individuals.

---

### Post by phossal on 2006-12-28
[Edited]

---

### Post by The Noble on 2006-12-28
If you want a 32 bit system, just use the i386 installer. You don't have to "force" anything.

---

### Post by Tomosaur on 2006-12-28
I can understand the frustration behind wireless dongles myself - since I spent virtually a whole weekend getting one to work. Luckily for me, there were drivers available (although they don't have full functionality atm). The problem turned out to be Ubuntu itself - certain things were just 'different' from how the developers had expected, which created a whole bunch of problems which I had to work before the drivers would load.

That being said - I think it a poor solution for the FOSS community to have to write these drivers themselves anyway. It would be much better for everyone if the device creators would just write Unix/Linux drivers in the first place. However, since this clearly isn't happening - then yes, the only way to get these things working is to reverse engineer or create completely new drivers using whatever documentation is available. I don't think your attitude towards this is helping matters though. I'm not attacking you or anything, but I just think your 'learn, sacrifice, contribute' statement is a bit patronising to say the least. I have better things to do with my time than to write device drivers from scratch, and I'm sure many programmers will tell you the same. Until enough people have a vested interest in getting a particular driver sorted, nothing is going to happen - so unless you sit down yourself and write the drivers, you're pretty much just going to have to put up with it. No, it's not a great situation, and yes, it's irritating, but you know deep down that I'm right. If there isn't enough demand, nobody is going to waste time on it when there are bigger fish to fry. The best idea would be to create your own demand. If you started the project yourself, I'm sure other developers would be willing to contribute their time. Many great 'ideas' never come to fruition because people just don't want to take the helm and get things going, which is perfectly understandable when you consider that they're not getting paid, and that it takes time. When you consider that you could buy a supported dongle, and then earn back the money - in the time it would take to get your own device driver up and running, you begin to see the real problem. There's just no real incentive to do it unless there is a big demand.

---

### Post by tseliot on 2006-12-28
> **The Noble said:**
> If you want a 32 bit system, just install the i386 installer. You don't have to "force" anything.
Exactly. Just install Ubuntu 32bit.

I use Ubuntu 32bit on my AMD64 CPU (among my other OSes)

---

### Post by slavik on 2006-12-28
helping an open source projects requires only 2 things = learning and relaying your knowledge to others

---

### Post by phossal on 2006-12-28
[Edited]

---

### Post by phossal on 2006-12-28
[edited]

---

### Post by Tomosaur on 2006-12-28
> **phossal said:**
> 
However, no demand? You're kidding, right? One of the most popular wireless devices on one of the most widely available architectures isn't supported? Ever heard of Best Buy? Of course there is demand. To say there isn't is ridiculous - that is, if you're serious about creating an open-source OS for the masses.

That's open for debate. Until you can come up with some figures for the kind of demand you're talking about, you're just going to be spouting nonsense. The problem with stuff that 'sounds' like it has demand is that it frequently doesn't, precisely because that kind of thing is pretty much unique, especially when it's from a well known manufacturer and suchlike. Therein lies the rub, I'm afraid. Not many people have my specific wireless dongle, but TONS of wireless dongles use the zydas technology, which is what my dongle uses. This means there's TONS of demand for zydas drivers - and lo and behold - zydas is (kind of) supported. This is really a situation where you're better off paying for something flimsy than the 'quality' stuff - because more often than not, the manufacturers have reinvented the wheel and ignored the fact that there will be no support for their new technology, no matter how awesome it is. So yes - lots of people may have your dongle, but many, MANY more people have a dongle which contains MY chip, which is really what you need drivers for.

---

### Post by kinson on 2006-12-29
> **tseliot said:**
> Why do you use Ubuntu 64bit?

I suppose this isn't quite directed at me, but I'll answer it anyways, since I'm using Ubuntu 64bit :P

I'm using it cause I was stupid, and since it said "for AMD64" or something like that(obviously I'm using AMD64(athlon 64) ), I thought it was the only thing I would be able to install(compatible) :p

Admittedly it wasn't the smartest thing to do, me being a linux noob and all that. It wasn't a walk in the park seeing all the apps out there "for i386 only" and no idea how to force it or find something else (Flash anyone? :P ). I'm honestly thinking of formatting my hard disk and reducing the size of the windoze partition and installing Dapper i386, it'll probably be a better learning platform for me.

Anyways, back to the topic :p

I think people should give back too(thats why I love community :) ), but not necessarily in terms of code. As it was mentioned earlier, advise and tips are also contribution :) I'm a fresh grad, working as a programmer now(struggling with btrieve, bleh), I hope to be able to contribute in the future, but right now, I'll have to start slow :(

Cheers,
Kinson

PS: Hardware that only supports windows is so irritating ](*,) :evil:

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by Wybiral on 2007-01-02
The issue with compatibility for Linux is a toughy...
It's not that OS's like windows and mac are better at supporting other hardware...
It's that hardware companies are writing the drivers/firmware and making the hardware to work with those OS's... Not Linux.
The Linux  guy's have a real problem because there are just so many devices and such little compatibility, considering the vast support that Ubuntu already has, I'd say they are doing great. Linux will continue to improve hardware support, but I don't think it will ever reach the simplicity level that other OS's have, until hardware companies begin developing hardware to be Linux compatible. Unfortunately, thats kind of a cycle because Linux has to get big for hardware companies to care, but for linux to become as BIG as the other OS's for home use, hardware companies will have to start taking the effort of making Linux compatible stuff.

---

### Post by rolando2424 on 2007-01-02
There are several ways of helping Open Source program, for example translations or creating artwork (either for the program (if it's a game for example) or for the website), become a webmaster, or just give moral support (it's important too :D).

Also help in the program's forum... Well, there are a lot of things you can do to help

---

### Post by Cirdan7 on 2007-01-02
I'd love to contribute. Its jsut trying to find something to contribute. I can't write a Text Editor because there are thousands of them. So finding something that the community needs and doesn't already have is hard. But I am learning python so I can write software faster then I could in C++, and more specifically to help out Ubuntu.

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by rolando2424 on 2007-01-02
I have also started to learn Python as my first language (what can I say? I just love the way it works) but I still don't have enough knowledge to do some of the real important and complicated stuff :D

I just wrote a little English - Albhed (a language from the game Final Fantasy X) script, that doesn't even has a GUI mode... Yet :D

And even there, it's mode a couple of if statements and the maketrans mothod from the string module :rolleyes: 

And I belive that it's important for Ubuntu :D

(I'm also trying to write a little binary - digital converter, just for the heck on it... The binary - digital convertion is easy (just use the int(nunber ,2)) the real problem is the digital - binary convertion... Oh well ^_^)

---

### Post by pmasiar on 2007-01-02
> **phossal said:**
>  I *love* Python. ... It's a super cool language - easy, packed with cool features, *cool name.* The practical, pragmatic side of me loves it. Computers are tools to solve problems, my brain says, and Python makes that process easier. I can solve a problem, and move on.

The other side of me - the curious side that enjoys computers as a hobby - drives me in the other direction though. I love C, and C++. I love looking at Assembly. IDA Pro is my friend. Because, if I'm not just going to do my job and then move on, I don't want things to be so easy. I want them to be fun, and interesting - even challenging. I am working on a pet project currently, but I hope to jump into the fray relatively soon, and help write device drivers. To me, that sounds like fun. 

LOL your definition od "fun" matches my definition of "pain". You are free to inflict as much pain on you as you want, but I believe you are aware by now there is only a small minority of  people willing to share pain with you. :twisted: 

When *I* want more challenging problem, I tackle bigger problem. You prefer to use harder-to-use tools. Funny.

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by Mirrorball on 2007-01-02
> **phossal said:**
> **Python is great,** but it isn't always the right tool for the job.
Absolutely. I love C and C++. C is simple, C++ is object-oriented, both are very fast and let you know what's going on. Writing a C++ program is not painful at all. When you have a whole month of running a number-crunching app ahead of you, you will wish you had spent that extra day writing a C++ program instead of a Python script.

---

### Post by pmasiar on 2007-01-02
> **phossal said:**
> Can you comprehend a situation where Python isn't the answer? 

Sure. When you need raw speed, C,C++, Forth is great on devices. Fortran for calculations, Lisp and Prolog are traditionally used for AI, I understand when people like ruby, PHP, etc. 

But if someone says, paraphrased "you need to enjoy pain to become programmer and learn C++ as first language" - well, next time it will disagree less, or even let it pass.

I was making fun of you enjoying pain, maybe it was not so wise. :-( I pass next time

---

### Post by kinson on 2007-01-02
Lol, this looks a bit like its going towards a C/C++ VS Python thread ;)

---

### Post by phossal on 2007-01-02
[edited]

---

### Post by Wybiral on 2007-01-02
Every time someone brings up C/C++ and python it turns into a debate. I'm not saying it's a bad thing, I wouldn't call it a "flame war" or anything.

Here's my opinion...
I learned C++ before python, true, but C++ wasn't my first language... I've only met a couple of people who actually dove straight into C++ as a first language.

Anyway, I like them both... I even like ASM, Javascript, even BASIC from time-to-time. They're all different, neither is BETTER.

About fun vs pain... Sometimes I do like the challenge of writing in ASM, for fun... Some people would call it painful... But when I do, it is just as a toy, I don't ever set out to write some awesome program in ASM, I just tinker with it.

So, I guess fun starts to sink below efficiency as far as priority goes when you're working on a real project, and that's the difference.

BTW, C/C++ aren't all that painful... Maybe C, but C++ isn't much more painful than python in my opinion. Once again, I did learn C++ before python so I've been using it a lot longer.

---

### Post by Wybiral on 2007-01-02
Yes, eventually, but jumping straight into ASM or C++ can really scare the crap out of people. I think they need to slide in... Python/BASIC/Javascript are gentle, I recommend learning them. And not only is python easy to learn, I've seen it match speed and functionality with C++ a number of times.

BTW... Python can be used for device stuff too, just remember that any functions that C/C++ have can be written into a module for python.

One more note... I'm not saying don't learn ASM/C/C++... I like them a lot, but I am saying they might not be the best to jump into for newbies.

---

### Post by phossal on 2007-01-02
Totally agree with you. I was just approaching it from the other side: You don't *have* to start easy. Lots of us didn't.

---

### Post by Cirdan7 on 2007-01-03
Just FYI, I know C++. I jumped into c++ when I was like 13/14 right after learning a little "LibertyBasic" Tho I never took C++ seriosuly until recently. I am learning Python becuase it seems a bit easier to write gui apps in, but it is hard for me to read Python after knowing C++'s syntax. I like C++'s Syntax but usually c++ programs have to be so complex to be able to under stand whats going on exacly. Then again, the only other source code I've seen other then examples was the Quake3 source...which is messy beyond comprehension.

---

### Post by lloyd mcclendon on 2007-01-03
> **phossal said:**
> While the overall popularity of Ubuntu will always be defined by the total number of its users, the overall value of Ubuntu will always be defined by those resilient, tenacious, inspired, knowledgeable programmers who make it what it is. The real *value* of Ubuntu is still what it was when linux was just beginning. It isn't the ability for a million users who have a problem to post blogs about it, it's in the ability of the few hundred people who can and will provide solutions by sacrificing their own time and energy.

There are a lot of bad sources of information out there, but enough good ones that a discerning individual will get along okay.

For those users (like me) who benefit from all of the time, energy and determination of the people who came before us, who use the products like the OS, compilers, music players, and browsers for free, it's time to give something back, and it goes beyond solving the simple problems related to installation and use. 

Learn c. Learn assembly. Solve a real problem. Write a device driver. Add a feature. Give something *real* back.

Learn. Sacrifice. Contribute.

... nevermind

i'm not sure how to respond to that without getting banned

---

### Post by kinson on 2007-01-03
> **phossal said:**
> Nah, it isn't true. pmasiar  is hell bent on following me to every post to make the point that Python is the "language of choice" ever since I made the suggestion that a person learn a c-syntax language first. He was persistent at first; now he's graduated to complete idiocy. I love Python, but there are definitely occasions where using it isn't appropriate, and one of those is in conversation with pmasiar.

He won't let up - doesn't seem to "get it".

The whole point of this thread was to convey this thought:
The people who possess the deep knowledge of topics *traditionally thought of as difficult* like kernel and device driver programming, proprietary software reversing, and others that have a unique time requirement and/or economic value, are often talented enough to dip into online resources and recover answers to their questions with fairly little effort. Those people who have a full tool belt are best able to contribute and help out in the "difficult" areas of the open-source community - but they don't always take the time.

When a person is just getting started with linux and/or programming, it's not a bad time to look forward and consider some of the really difficult tasks - and how he or she might be the one to learn those skills and solve those problems. Although it's hard, and not always worth it, learning low-level languages is still a practical objective. That's all. 

lol It doesn't seem that difficult of a concept to grasp. I don't believe any part of that encourages anyone to *avoid* Python, does it? A few "new" programmers are going to invest the time and effort to become elite, and hopefully they'll still find it rewarding to contribute.

Lol, I do think his first reply to your post was a little out of the blue, but I'm not trying to side anybody here :)

I'm doing a little C++ currently, and its interesting, but I don't like coding the interface part(especially if you have to do it in windows). I've seen a lot of people suggesting Python around here (especially for Linux), so I'm planning to give it a try, just need to find some time.. :P

I'm hoping I can get into the whole Open Source thing and contribute back to what this great community :)

Cheers,
Kinson

---

### Post by phossal on 2007-01-03
[edited]

---

### Post by Wybiral on 2007-01-03
> **phossal said:**
> [edited]

Why so many edited posts?

---

### Post by pmasiar on 2007-01-03
> **Wybiral said:**
> Why so many edited posts?

To prevent me from quoting him :-)

Sorry I could not resist.

---

### Post by Wybiral on 2007-01-03
> To prevent me from quoting him

lol

I mean... I could understand someone correcting a post or something, maybe they feel it was a waste of space... But I've been checking post updates today and like half of his say "[edited]"

Do what you want, but it kindof clutters up the board ("[edited]" is a waste of space, if it's SO important, post for a mod to delete it or something)

---

### Post by phossal on 2007-01-03
I deleted them for two reasons: 

1. I don't want them showing up in Google. I would *actually delete* them, but I can't, obviously.
2. They really were just useless. I refuse to discuss any more 'philosophy' with pmasair. Check his reponses to me - in fact, all of his posts in general -  they're almost 100% "opinion". I much prefer to stick to the advice. When I post any kind of 'opinion' at all, the guy responds to it in exactly the same way. I love being quoted, I just don't want to read a pro-python sales pitch in every thread. Talk about a waste of space. I'm not sure he's actually helped anyone with any problem, other than convincing me he's ... not worth the points the moderater gave me for reminding him he's an idiot. 

In fact, here it is....

The guy is an idiot. Ban me. I actually helped a few people. All he did was voice his "opinions". That's fantastic, and perfectly *tolerable*. I just hate the guy. He's worthless. lol I haven't gotten any questions answered. But I've read a lot of idiotic, useless, repetitive opinions.

If the forums were filled with guys like *him*, offering their opinions, everyone would speak of the virtues of python, and nothing would get done. All this because *he* couldn't accept the fact that a guy might learn *java or c* first. Oh, the audacity of such a suggestion. *IDIOT.*

---

### Post by Wybiral on 2007-01-03
> **phossal said:**
> I deleted them for two reasons: 

1. I don't want them showing up in Google. I would *actually delete* them, but I can't, obviously.
2. They really were just useless. I refuse to discuss any more 'philosophy' with pmasair. Check his reponses to me - in fact, all of his posts in general -  they're almost 100% "opinion". I much prefer to stick to the advice. When I post any kind of 'opinion' at all, the guy responds to it in exactly the same way. I love being quoted, I just don't want to read a pro-python sales pitch in every thread. Talk about a waste of space. I'm not sure he's actually helped anyone with any problem, other than convincing me he's ... not worth the points the moderater gave me for reminding him he's an idiot. 

In fact, here it is....

The guy is an idiot. Ban me. I actually helped a few people. All he did was voice his "opinions". That's fantastic, and perfectly *tolerable*. I just hate the guy. He's worthless. lol I haven't gotten any questions answered. But I've read a lot of idiotic, useless, repetitive opinions.

No offense to anyone, you or him... But I don't see that calling him names is any less of a waste of time than him selling python. He is at least promoting a good language, calling people names doesn't do anything.

---

### Post by phossal on 2007-01-03
You know what this is... 

It's my own failure. I owe the forums an apology. I have a character flaw. I'm practical. I'm pragmatic. I want things to work. I want solutions. I want good information. I offer an opinion when I think there is some practical benefit to it, and then I drop it if the people around me don't see the value in it.

I don't like a lot of talk. The guy irritated me because he *wanted* a debate. I'm not the kind of guy for that. He voiced his opinion to me 30+ times, *in every thread*. I only needed to hear it once. It wasn't valuable to me. I reviewed his posts, and they are *mostly* opinions. He's all opinion, and, worse, it's a bad one - because his opinion doesn't allow for an alternative which absolutely exists. Why does he have to follow me around? lol

I shouldn't have called him names. I should have ignored him. *I* was wrong. But my failure doesn't make him any less annoying, any more helpful, or me any less irritated.

---

### Post by lloyd mcclendon on 2007-01-03
> **phossal said:**
> You know what this is... 

It's my own failure. I owe the forums an apology. I have a character flaw. I'm practical. I'm pragmatic. I want things to work. I want solutions. I want good information. I offer an opinion when I think there is some practical benefit to it, and then I drop it if the people around me don't see the value in it.

I don't like a lot of talk. The guy irritated me because he *wanted* a debate. I'm not the kind of guy for that. He voiced his opinion to me 30+ times, *in every thread*. I only needed to hear it once. It wasn't valuable to me. I reviewed his posts, and they are *mostly* opinions. He's all opinion, and, worse, it's a bad one - because his opinion doesn't allow for an alternative which absolutely exists. Why does he have to follow me around? lol

I shouldn't have called him names. I should have ignored him. *I* was wrong. But my failure doesn't make him any less annoying, any more helpful, or me any less irritated.

you are acting pretty f'ing weird mang

relax before i e-slap you


and editing your posts for google?  seriously wtf is that about?  stop it.

---

### Post by kinson on 2007-01-03
Maybe we should all just chill and just let the matter drop :| I mean, there's no point us arguing about this anyways...lets just "agree to disagree" :p

Cheers,
Kinson

---

### Post by lloyd mcclendon on 2007-01-03
word

---

### Post by pmasiar on 2007-01-03
> **lloyd mcclendon said:**
> and editing your posts for google?  seriously wtf is that about?  stop it.

Just for fun I checked top google post with my nick. yes, 1st and 2nd is  [me]("http://www.ubuntuforums.org/showthread.php?p=1911505") - i am good :-)

Someone must linked to that post (bunch of links about tomcat). Of course phossal is there, His single post must be quite surprise for the forum (server admin questions, no flamewars between us before). Post is less abusive than phossal standard - for some reason he did not edited out that one. maybe he forgot. :-)

Google for phossal gives this thread at 2nd place. There is also [http://www.phossal.net/](http://www.phossal.net/) (rated less than this thread) -- maybe that is main phossal's concern.

---

### Post by tseliot on 2007-01-04
> **kinson said:**
> Maybe we should all just chill and just let the matter drop :| I mean, there's no point us arguing about this anyways...lets just "agree to disagree" :p

Cheers,
Kinson

You're right.

Let's we all take a step back, please.

This discussion is not going anywhere.

---


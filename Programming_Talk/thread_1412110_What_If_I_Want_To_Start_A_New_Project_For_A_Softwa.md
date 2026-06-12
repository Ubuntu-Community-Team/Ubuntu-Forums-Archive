---
title: "What If I Want To Start A New Project For A Software"
date: 2010-02-20
forum: Programming Talk
---

### Post by madmax.santana on 2010-02-20
Say I have something in mind which Ubuntu doesn't have yet, and I want to develope it. I am not much of a programmer, but I know C++ quite a bit. I have recently had a tutorial on using GTK+ and interfacing with Glade. But just that much, I am not a pro or something.

I don't have buddies around me who are programmers... I shall definitely need help of some programmer pals!

Where do I find people who are expert programmers and interested in programming software for Ubuntu, who will join me and we shall make a little team and work on that thing!!! (Nothing in return except the sense of satisfaction and name in Credits dialogue of the program:))

Is there a special place to find such people? And will they appreciate the idea? What do I do? 

There is something that I want to do, desperately, a software which Ubuntu doesn't have yet. Well there are many in that category but not that good! I think that program will be quite an advance in Ubuntu experience! But see, the problem is, no matter how desperately I want to programme it, I can't do it alone, not with this limited knowledge and experience. It could take ages before I can have a beta release ready!

I see credits of software like VLC and there are lots of people in there. Maybe they were all friends who lived close to each other, maybe worked at the same place, maybe were all professional programmers! I dunno! But I don't have such resources, so I need people, maybe in some other continent, but people who can help me in achieving that software of my dream!

I think I have said enough! Maybe many readers still don't understand my point but I have tried my best. If there is a specific place where I can find such people, please let me know! Or if "this" is the place, please tell me what do I have to do to (except howling at moon:)) to call out programmers to join me!

---

### Post by Tibuda on 2010-02-20
Whats your idea? You could already had some feedback if you have told it.

---

### Post by Simon17 on 2010-02-20
You probably need to get some code working before other people will take interest and jump on. Even if it isn't very good. You just need to get something started.

---

### Post by matthew.ball on 2010-02-21
> **madmax.santana said:**
> There is something that I want to do, desperately, a software which Ubuntu doesn't have yet. Well there are many in that category but not that good!
Surely it makes more sense to help an existing project?

Chances are there is already a team behind the aforementioned projects - you can just sign up and offer some help.

---

### Post by wmcbrine on 2010-02-21
I'm always baffled by these kinds of posts. However, I notice that there are also a lot of equally puzzling posts by (new) programmers who are looking for something to do. So you should have no trouble getting together.

---

### Post by heamaster on 2010-02-21
I myself have written a post like this a couple of months ago and I'm in the same situation. The answers are always as boring and useless: "join an existing team". 
However it is not that simple if you've never been in a team and dont have much of self confidence.

So, what is your project idea?:popcorn:

---

### Post by madmax.santana on 2010-02-21
Hi all! Actually I really am absolutely "NEW" and was just hoping to get a few ideas regarding "where do I get the people"... Your replies are encouraging enough to unveil my idea.

Actually, the idea is a downloader. Here is a link to another post by me...
[http://ubuntuforums.org/showthread.php?t=1393331](http://ubuntuforums.org/showthread.php?t=1393331)

As is obvious from the post there, there are a lot of programmes available in this category. But no one as good as Internet Download Manager which is available only for Windows. I get these remarks all over the internet that there are many downloaders, D4X, Wget, DownThemAll, lots of them... But there is rarely one having all the qualities that the best downloader could have.

In my opinion, the best downloader might have the following attributes...

1- Multi threading : Main motivation behind all this project is multi-threading. See, a download manager has to be fast! And multi threading does it.

2- It should be capable of pausig, resuming downloads.

3- It should have a nice integration with a lot of browsers available in Linux.

4- It should have a charming interface.

5- Ultimate goal is to build it through GTK+ or related libraries to make it easy to upgrade and modify.

Now I have these top download managers in front of me, but all of them appear to have a flaw.

1- D4X is good, but it is not multithreaded. It uses wget as backend and  download a single file in a single thread like wget does... Quite slow and unreliable... It doesn't even supports multiple downloads at the same time. Also, it is very very difficult to get it working through a proxy wall... And above all, it has a slacky interface.

2- JDwonlaoder is another download manger which I have used. It is very good. Except that it is actually a JAVA binary which has to be run through JAVA every time and it is not integrated with browsers, not easily. And it is quite slow as well. Even if there is multi-threading, not affective!

3- DownThemAll is a very powerful extension for Firefox and some other browsers. It is so far the best I have encoutered. But it still has many problems... It provides upto 4 threads per file, whereas it could have been 7 or 8. And it is just an extension for Firefox , whereas in my opinion, the download manager should run as a separate process so that when the browser is not open, it continues downloading. It should be able to minimize to tray like D4X does. There is probably a option in DownThemAll, which enables the tray thing in Windows, but not for Linux. So, I have already downloaded the source code for dTa but I am at loss understanding it. I was hoping that might another programmer tell me as much as in which language is this written, lol. Anyway, the idea is to take the DownThemAll code and implement in GTK+, extend some of its features and join the characteristics of many other download managers to produce one perfect download manager for Linux, you know, all-in-one!

I dunno as [wmcbrine]("http://ubuntuforums.org/member.php?u=10826") said in the post above, this might look dumb, maybe pointless but I don't mean to change the views of many other users on this topics. I just want to ask if there is someone who has my opinions.

And I must particularly mention that my purpose behind this step is not to establish myself as a programmer, have my name flashing in About box or even take the credit of any project. Honestly, I can remain anonymous throughout and after completion of this thing. I just though that there is something missing in my Ubuntu experience and I should do something to bring it in here. No personal benefits at all, honestly.

---

### Post by Tzah on 2010-02-21
That's a great idea, but the pausing and resuming thingy all depends on the server hosting the file and thus you can't control that through a download manager, am I right?

---

### Post by CptPicard on 2010-02-21
One of the fundamental issues in these kinds of threads is that there are unlimited ideas, and limited man-hours, and those having the man-hours don't really have any need to have a technically incompetent person lording it over in a project they're actually working on. So therefore these are often doomed, and also why the "show us the code" is such a common response.

One of the major things you can help in selling your idea to someone who might be interested in taking it up is not to speculate too much on the technical specifics like you already seem to be doing, although you admit to being new. For example multithreading is not necessarily a holy grail -- I/O can be asynchronous. GTK+ is probably necessary on Gnome, not so on KDE... (KDE has KGet by the way)... just focus on the features issues...

---

### Post by madmax.santana on 2010-02-21
@[@Tzah]("http://ubuntuforums.org/member.php?u=1011792") Actually, I am focusing on the performance of IDM on Windows as well, if anyone has used it? Actually IDM automatically determines whether the server supports resuming file or not. It then adjust the download specs accordingly.

@[CptPicard]("http://ubuntuforums.org/member.php?u=148462") I am not actually getting your point. If you mean to imply that I am technically incompetent,  must say that I don't think anyone is technically incompetent at all. All those hi-fi programmers, who are on working on something mega once started from zero. And for me, it's never too late to start anything.

If you mean to say that knowing C or GTK+ is not enough for me to start on something that serious, maybe then you have better ideas on where should I start. What else do I have to learn. See the point is, I am not at all scared of being undermined or neglected in a group of technically more knowledgeable people. I have already mentioned that I am not doing it to earn any name or fame, I am doing it just to enhance my "technical competence" as well as introducing something in Ubuntu which I think is lacking in it.

Anyway, I am not taking all your comments as an offence, no sir, not at all. I just mean to say that I speak English as a second language and I usually do not understand the tenor of difficult English words, so I am not getting your point on the whole.

---

### Post by madmax.santana on 2010-02-21
And there is something else here too, I did not say that I want to sell my ideas to some programmers. I just mean to say that I want to so something,considering you people as my fraternity in subject, I came here for help. Maybe to some senior members it looks like a bugging pointless talk, but being a member of this community and a devoted Linux user / supporter, I demand to be taken seriously!

---

### Post by CptPicard on 2010-02-21
Those were all quite sincere observations, no offense meant.


> **madmax.santana said:**
> If you mean to imply that I am technically incompetent,  must say that I don't think **anyone** is technically incompetent at all.

I would respectfully have to disagree with that notion, based on my experience of "everyone"...

> 
 All those hi-fi programmers, who are on working on something mega once started from zero. And for me, it's never too late to start anything.

Sure, but by definition if you're asking for experts to code your project for you and haven't been at the point where you could get it off the ground, then by definition you are not competent enough for that particular project.

> 
If you mean to say that knowing C or GTK+ is not enough for me to start on something that serious

I guess you're the judge of whether you can start on whatever you want to start on. You can always try, and if you fail, you've learned where your abilities are lacking.

> I am not at all scared of being undermined or neglected in a group of technically more knowledgeable people.

Maybe, but the more knowledgeable people still need to consider it worthwhile to be working on your project -- which is one where it may well be possible that you're just dead weight. So you at least need to be able to provide lots of good ideas in the right places.

> I just mean to say that I speak English as a second language and I usually do not understand the tenor of difficult English words

Oh, likewise. I like difficult words, they make me sound like such a pompous *** :D

> **madmax.santana said:**
> And there is something else here too, I did not say that I want to sell my ideas to some programmers.

Take "sell" figuratively. You need to get them interested in what you want to achieve as you're not able to provide useful code to begin with that would pull in more developers.

>  but being a member of this community and a devoted Linux user / supporter, I demand to be taken seriously!

Everyone gets exactly as much of a fair hearing as others are willing to give them, and I'm just trying to suggest you ways to make the most of it and avoid the pitfalls. "Demanding" in general is rather difficult in the FOSS world.

---

### Post by Vox754 on 2010-02-21
> **madmax.santana said:**
> And there is something else here too, I did not say that I want to sell my ideas to some programmers. I just mean to say that I want to so something,considering you people as my fraternity in subject, I came here for help. Maybe to some senior members it looks like a bugging pointless talk, but being a member of this community and a devoted Linux user / supporter, I demand to be taken seriously!

I couldn't pass the opportunity to post old threads of people who had brilliant ideas too.

**Stacks**
[LIST=1]
[*][I need help...............](http://ubuntuforums.org/showthread.php?t=526722) (15 August 2007)
[*][The next generation search engine](http://ubuntuforums.org/showthread.php?t=547359) (9 September 2007)
[*][Stacks](http://ubuntuforums.org/showthread.php?t=548096) (10 September 2007)
[*][one last chance..........](http://ubuntuforums.org/showthread.php?t=552655) (16 September 2007)
[*][semantic web logic](http://ubuntuforums.org/showthread.php?t=556137) (20 September 2007)
[/LIST]

**Automatic Kernel drivers**
[LIST=1]
[*][Development advice: Kernel API](http://ubuntuforums.org/showthread.php?t=1380710) (13 January 2010)
[*][Programmers needed in new project I created](http://ubuntuforums.org/showthread.php?t=1383015) (16 January 2010)
[*][Launchpad code uploads](http://ubuntuforums.org/showthread.php?t=1383317) (17 January 2010)
[/LIST]

Good stuff.

Simple suggestion: start developing; if it's good, it will attract other people.

---

### Post by CptPicard on 2010-02-21
Oh wow... it was better than I remembered. There is almost a surreal literary quality to cubytes' "visions". I wonder what came of his plans to "buy Novell and create his legacy" after he finally got tired of our dimwittedness...

---

### Post by madmax.santana on 2010-02-22
Oh boy!!! [SIZE=4][COLOR=Red]I really did sound dumb!!![/COLOR][/SIZE] I am embarrassed... :P Hahaha!!!

[SIZE=3][COLOR=SeaGreen]But I am getting the picture here![/COLOR][/SIZE] Thanks a lot all of my learned comrades!!! 

I think I would start it alone then!!! Of course during programming I can ask for small help here on forums!!! Please don't deny that!!! :) :) :) (Lightly intended)

Yes you people are absolutely right! If am to do it, I will do it no matter what! And if I can't do it, well, we'll know in some time! Hahaha!!! Have a nice time all!

---

### Post by love to learn on 2010-02-22
Just ignore comments from people like old picard there.
There are always a few high and mighty twats who post im sure just to add to their post counts or take pleasure in degrading other people and their ideas.
Most of the time if not all the time they are useless programmers themselves.
Your idea is great, but as mentioned,you will have to start working on it yourself to plant a seed for others to comment on or add to.

---

### Post by pokebirdd on 2010-02-22
I hope I'm not hijacking this thread but since I didn't really want to start another one of these, could someone answer my question?

> 
You need to get them interested in what you want to achieve as you're not able to provide useful code to begin with that would pull in more developers.What exactly constitutes useful code? I have a working program that seems alright when I run it but I have absolutely no idea whether my code is well structured and well written since I lack experience in writing anything remotely large. Is there any point in posting it onto any sites like Freshmeat or Launchpad?

---

### Post by nvteighen on 2010-02-22
> **love to learn said:**
> Just ignore comments from people like old picard there.
There are always a few high and mighty twats who post im sure just to add to their post counts or take pleasure in degrading other people and their ideas.
Most of the time if not all the time they are useless programmers themselves.
Your idea is great, but as mentioned,you will have to start working on it yourself to plant a seed for others to comment on or add to.

Uh... you never seen any CptPicard's code, I guess. Just search a bit and you'll see really advanced stuff like [http://ubuntuforums.org/showthread.php?t=749965](http://ubuntuforums.org/showthread.php?t=749965)

@OP:

Free Software programming works under pure meritocracy. You have to show you're good if you want to be at the top... and to show you're good, you have to be good.

A good idea is to start a personal project... When I mean personal, I don't mean you keep it in secret... No, publish it, but just forget about the idea of creating a massive contributing community for it; make the code be your priority and there might be chances someone kicks in occasionally and helps you with some bits. That's why I have two projects... I just want to code them and like to do it... I release them and don't care about how many people downloaded it or not. I just want to practice.

(Also, using a project hosting service and caring about releases teaches you about version controlling systems and deployement... This week I was taught an interesting lesson about how to deal with resource files, for example)

So, just don't hurry; enjoy learning!

---

### Post by love to learn on 2010-02-22
Well that explains the pompous attitude then  it sucks.
One should motivate not criticise and down others.
Its plain bad manners.
I personally dont give a fly what code hes written.

---

### Post by CptPicard on 2010-02-22
> **pokebirdd said:**
> 
What exactly constitutes useful code?

The problem is that you won't know until you try -- it's the other people who can judge the usefulness. :)

And you guys can nip what is brewing in the bud -- the OP seemed to approve of my statement that it was not meant offensively. I may "say what I mean" but I have no need to denigrate anyone -- they might not like what is said though. (Then there are the *genuinely funny* cases but... you understand :) )

I rarely post code here simply because it's mostly a collection of "Hello World" and the millionth implementation of the Sieve of Eratosthenes anyway, and more interesting stuff requires more implementation, time for which I do not have if I already understand how I'd do it. Plus, I don't have dwhitney67's charitable tendencies to fix people's broken homework... 

> **nvteighen said:**
> 
(Also, using a project hosting service and caring about releases teaches you about version controlling systems and deployement... This week I was taught an interesting lesson about how to deal with resource files, for example)


Mind you, if you took my suggestion (I have not checked the thread for further responses), that's just how I'd do it... in C you could also have preprocessor flags that hardcode paths depending on some flag.

EDIT:

I guess I'll just comment on this a little as there is something to contribute:

> **love to learn said:**
> 
One should motivate not criticise and down others.


In matters like this, just simply purely "motivating others" on their own terms, even when one sees they're wrong and going down a doomed path, really achieves nothing. Of course I could just be patting people on the back regardless and telling them to go for it as it is, but I would not be *communicating anything of value* back to them. The entire exchange would be meaningless -- just a booster, not carrying "bits of difference" in an information theory sense.

For an extreme example, look at the "Stacks" threads. That guy was full of motivation, and also of hot air -- and only that. The faster he realized how clueless he was, the better.

---

### Post by madmax.santana on 2010-02-23
People, why are we discussing somebody else's credibility as programmer? You know, for me, I don't care if anyone who is posting replies on my thread is a dental sergeon or something. He must convey something meaningful...

Well CptPicard did so... Although his attitude was whatsome people might look upon as discouraging, but of course that is how geeks with tons of knowledge are... No complaints about the CptPicard issue. I am happy with what he tried to pass me... Actually, the theory of CptPicard is somewhat similar to mercy killing.
> The faster he realized how clueless he was, the better.
And the BLUNT AXE might hurt someone, but everyone is not someone. So I didn't go for the tone of Cap'n but the message in it. 

@CptPicard, thank you, sir! But all said, I humbly request you to please consider just this that your intentions might not be bad, but your tone counts much more in conveying the people. That might be why someone could think that you are being pompous! I do not mean any offence but first time, your posts looked a bit harsh to me even... :)

@love to learn:
Actually, I must apologize if I am going to hurt your feelingss. Of course your opinion does count and you were actually favoring me in your post! But I must say that we should not take upon anyone personally because of his arrogant attitude.
> There are always a few high and mighty twats who post im sure just to add to their post counts or take pleasure in degrading other people and their ideas.
That wasn't meant to be said man... Well, I didn't say I was demotivated, pal. Should have been a problem if I was.
> Most of the time if not all the time they are useless programmers themselves.
Well, even if he isn't a good programmer, that doesn't mean he can't give me any advice. Actually my question wasn't related to programming at all, was only related to finding programmers. :)
> Your idea is great, but as mentioned,you will have to start working on it yourself to plant a seed for others to comment on or add to.
Well, I thinks that is what Picard meant to say. :)

Settle it, amigos... There is nothing more disastrous that a battle on the same front. :) We are all on one front, the Ubuntu front!

Mods, please close this thread... I suspect it is going the wrong way!!! *Already marked it solved... Thank you!

---

### Post by CptPicard on 2010-02-23
> **madmax.santana said:**
> 
@CptPicard, thank you, sir! But all said, I humbly request you to please consider just this that your intentions might not be bad, but your tone counts much more in conveying the people. That might be why someone could think that you are being pompous! I do not mean any offence but first time, your posts looked a bit harsh to me even... :)


Well, I'm not a "sir" and there is no need for a "humble" anything. I just prefer being to the point sometimes instead of confusing the communication with fluff :)

(I was going to post the "He's not the Messiah" video clip from Life of Brian, but considering there's material there the mods will consider not suitable here, let's forget about it :) )

---


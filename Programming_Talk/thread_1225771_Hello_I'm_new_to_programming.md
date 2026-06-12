---
title: "Hello I'm new to programming"
date: 2009-07-28
forum: Programming Talk
---

### Post by emptycan on 2009-07-28
Hello all I am new to programming, and new to the Ubuntu/Linux world. Lately I have had an itch to learn to program, my job does not require it however, I would like to learn the basics. My friend has given me his old C book (he dropped out of CS in college but still had the book), and I just installed the Ubuntu Netbook Remix on my new MSI-Wind u100. Now I just need to know where to start, I heard learning C, C++ and Java are all quite similar so I decided to learn C first. My question is what program do I need to install to start my merry way? I was reading the stickies but it seemed to skip step 1, starting off with what I acentually need to program. Please help me out, I'll be scouring through the older posts but there are so many I decided to to just start a new one. Thanks and sorry for all the noob questions, but I really don't know jack about programming and linux at all.

Edit - I decided to use VIM as an editor because my friend told me that's what he used way back in the days, can someone explain how I install it?

---

### Post by JordyD on 2009-07-28
> **emptycan said:**
> Hello all I am new to programming, and new to the Ubuntu/Linux world. Lately I have had an itch to learn to program, my job does not require it however, I would like to learn the basics. My friend has given me his old C book (he dropped out of CS in college but still had the book), and I just installed the Ubuntu Netbook Remix on my new MSI-Wind u100. Now I just need to know where to start, I heard learning C, C++ and Java are all quite similar so I decided to learn C first. My question is what program do I need to install to start my merry way? I was reading the stickies but it seemed to skip step 1, starting off with what I acentually need to program. Please help me out, I'll be scouring through the older posts but there are so many I decided to to just start a new one. Thanks and sorry for all the noob questions, but I really don't know jack about programming and linux at all.

Edit - I decided to use VIM as an editor because my friend told me that's what he used way back in the days, can someone explain how I install it?

In a terminal:
```
sudo apt-get install vim-full
```
or in Add/Remove Programs, search and install vim.

Besides that, the stickies do cover it: [http://ubuntuforums.org/showthread.php?t=689635]("http://ubuntuforums.org/showthread.php?t=689635").

Vim has a steep learning curve, but you should be able to make it if you keep a cheat sheet of basic commands nearby when using it.

---

### Post by emptycan on 2009-07-28
Thank you I just installed VIM, and I'm googling for some VIM cheat sheets, there seems to be plenty out there, I'll just dl any one of these.

---

### Post by JordyD on 2009-07-28
> **emptycan said:**
> Thank you I just installed VIM, and I'm googling for some VIM cheat sheets, there seems to be plenty out there, I'll just dl any one of these.

Good luck with it.

When you can do the basics (of vim) without thinking about it, you should look for other things that slow you down, or are annoying. There is generally a faster/better way to do it.

---

### Post by Dill on 2009-07-29
Here's a [ViM tutorial]("http://www.cs.grinnell.edu/~walker/lubinski/vim.html") I started with and a [good presentation]("http://http://video.google.com/videoplay?docid=2538831956647446078") by Bram Moolenaar, the creator of ViM.

Much like the previous poster, the best ViM advice I can give is: if you're doing something that you feel could be done faster, see if there's a faster way! Google as much as you can and get the muscle memory down... your finger will begin to fly.

Cheers,
Dill

---

### Post by Mirge on 2009-07-29
> **emptycan said:**
> Hello all I am new to programming, and new to the Ubuntu/Linux world. Lately I have had an itch to learn to program, my job does not require it however, I would like to learn the basics. My friend has given me his old C book (he dropped out of CS in college but still had the book), and I just installed the Ubuntu Netbook Remix on my new MSI-Wind u100. Now I just need to know where to start, I heard learning C, C++ and Java are all quite similar so I decided to learn C first. My question is what program do I need to install to start my merry way? I was reading the stickies but it seemed to skip step 1, starting off with what I acentually need to program. Please help me out, I'll be scouring through the older posts but there are so many I decided to to just start a new one. Thanks and sorry for all the noob questions, but I really don't know jack about programming and linux at all.

Edit - I decided to use VIM as an editor because my friend told me that's what he used way back in the days, can someone explain how I install it?

Have you decided yet what type of software you're looking to create?

---

### Post by StunnerAlpha on 2009-07-29
ViM is great and all but you will find that there will be times where you need to indent a block of code or do something that involves a GUI, that is why I would recommend you don't devote your full attention to ViM, but look at some IDE's. I like to use Geany personally, really lightweight, simple and easy to use. Learning ViM is still a good idea nonetheless, I just think that once you really get down to business you should start using an IDE. ViM is a great tool when programming on a remote machine via ssh. Just my 2 cents.

---

### Post by anzac1942 on 2009-07-29
I would also recommend that you try out a little bash scripting too... just to help you get a feel for how linux works:D I know when I switched over to linux that bash scripting helped me learn my way around the system, and I've never looked back! At least until windows 7 comes out... then I'll have to give it a spin...

---

### Post by TheStatsMan on 2009-07-29
> **StunnerAlpha said:**
> ViM is great and all but you will find that there will be times where you need to indent a block of code

This is extremely easy to do in Vim.

---

### Post by JordyD on 2009-07-29
> **StunnerAlpha said:**
> ViM is great and all but you will find that there will be times where you need to indent a block of code or do something that involves a GUI, that is why I would recommend you don't devote your full attention to ViM, but look at some IDE's. I like to use Geany personally, really lightweight, simple and easy to use. Learning ViM is still a good idea nonetheless, I just think that once you really get down to business you should start using an IDE. ViM is a great tool when programming on a remote machine via ssh. Just my 2 cents.

= will indent it for you according to c indentation, > will just plain indent. If you want to indent a block use v to select multiple lines and press which kind of indentation you want. I've mapped ggVG= to my F6 key. gg is 'go to top line', then V is 'line selection', then G is 'go to bottom line' and = was already explained. Most of what IDEs can do, VIM can do. You just need to figure out how.

---

### Post by hessiess on 2009-07-29
> **thestatsman said:**
> this is extremely easy to do in vim.

+1

All you need to program in C is an editor(Vim), A shell (BASH) and a compiler(GCC).

---

### Post by wrtpeeps on 2009-07-29
Wouldn't bother with C myself.

---

### Post by Copernicus1234 on 2009-07-29
Ok, im going to be honest. You guys give the worst advice to someone new to programming.

You not only want this guy to start with C, but to use Vim as well? Are you on drugs? :)

No. Listen. Start with Python. Its a excellent language for writing basically everything you want, and its easy to learn.

Type ipython at the prompt and get started, while checking the web for python tutorials. Ipython lets you type in commands and get the result right away. Its excellent for learning.

Then when you have tasted it, start making real programs in python using Eclipse and pydev as the editor.

Thats my 2 cents, and thats the 2 cents you should listen to in this thread filled with masochists. :)

---

### Post by loomsen on 2009-07-29
> **Copernicus1234 said:**
> Ok, im going to be honest. You guys give the worst advice to someone new to programming.

You not only want this guy to start with C, but to use Vim as well? Are you on drugs? :)

No. Listen. Start with Python. Its a excellent language for writing basically everything you want, and its easy to learn.

Type ipython at the prompt and get started, while checking the web for python tutorials. Ipython lets you type in commands and get the result right away. Its excellent for learning.

Then when you have tasted it, start making real programs in python using Eclipse and pydev as the editor.

Thats my 2 cents, and thats the 2 cents you should listen to in this thread filled with masochists. :)

+1

:lolflag:

well said

---

### Post by hessiess on 2009-07-29
IDE's only overcomplicate everything, Vim is simple and efficient, its just different (which is a good thing, `common' `word processor' like editors are extremely inefficient).

C is nowhere near as complicated as its often made out to be.

---

### Post by monraaf on 2009-07-29
You should definitively learn Vim, regardless if you are going to use it as your main editor for coding. Vi is the _de facto_ standard Unix editor. If you need to edit a file on a remote server through SSH, or even locally when you don't have X running for some reason, and you don't know how to use Vi you are handicapped.

---

### Post by Dill on 2009-07-29
> **Copernicus1234 said:**
> 
You not only want this guy to start with C, but to use Vim as well? Are you on drugs? :)

> Edit - I decided to use VIM as an editor because my friend told me that's what he used way back in the days, can someone explain how I install it?

The OP asked, and we answered. I'm not experienced enough to give an in-depth comparison of editors, but I do use ViM, so I thought I'd throw my two cents in, as well : )

Cheers,
Dill

---

### Post by Mirge on 2009-07-29
> **Copernicus1234 said:**
> Ok, im going to be honest. You guys give the worst advice to someone new to programming.

You not only want this guy to start with C, but to use Vim as well? Are you on drugs? :)

No. Listen. Start with Python. Its a excellent language for writing basically everything you want, and its easy to learn.

Type ipython at the prompt and get started, while checking the web for python tutorials. Ipython lets you type in commands and get the result right away. Its excellent for learning.

Then when you have tasted it, start making real programs in python using Eclipse and pydev as the editor.

Thats my 2 cents, and thats the 2 cents you should listen to in this thread filled with masochists. :)

I agree. Start with a higher level language (ie: Python), not because "C is so super difficult", but because you'll be able to get more results, quicker. It's a lot easier to stay enthusiastic about programming if you can see that it's not difficult, and that you can get great results quickly. It will help you wrap your mind around programming concepts a bit easier as well, imho.

Vim is just going to add to the learning curve. Sure, it can be used when ssh'ing into a remote server, but so can pico/nano (which is a lot easier).

Start with Geany for a text editor and Python or a different higher level language. When you're more familiar with programming concepts and decide that you actually enjoy programming.. take a look at C again or even several other languages and really dig in. Learn vim too if you want. Some people (as you can see in this thread) swear by it.

---

### Post by emptycan on 2009-07-29
> **Copernicus1234 said:**
> Ok, im going to be honest. You guys give the worst advice to someone new to programming.

You not only want this guy to start with C, but to use Vim as well? Are you on drugs? :)

No. Listen. Start with Python. Its a excellent language for writing basically everything you want, and its easy to learn.

Type ipython at the prompt and get started, while checking the web for python tutorials. Ipython lets you type in commands and get the result right away. Its excellent for learning.

Then when you have tasted it, start making real programs in python using Eclipse and pydev as the editor.

Thats my 2 cents, and thats the 2 cents you should listen to in this thread filled with masochists. :)


Thanks for the comment, I'm pretty set on learning C then C++ then Java and C#. Every time I see job openings for programmers those are the 4 languages that seem to dominate. Personally I never programmed and this is my first time, I'm not doing a career change or anything but just thought that it would be useful to add onto my resume and all. Maybe later on I'll learn python as well, but as for now C seems to be the basic one so I'll go with that. I know it's not the best language but I'm going to make that my foundation.

---

### Post by chancekang on 2009-07-29
> **emptycan said:**
> Thanks for the comment, I'm pretty set on learning C then C++ then Java and C#. Every time I see job openings for programmers those are the 4 languages that seem to dominate. Personally I never programmed and this is my first time, I'm not doing a career change or anything but just thought that it would be useful to add onto my resume and all. Maybe later on I'll learn python as well, but as for now C seems to be the basic one so I'll go with that. I know it's not the best language but I'm going to make that my foundation.

Just a thought you should put in your mind.... Once you get through C++, Java and C# is just a toy...

---

### Post by Mirge on 2009-07-29
> **chancekang said:**
> Just a thought you should put in your mind.... Once you get through C++, Java and C# is just a toy...

How's that?

---

### Post by hessiess on 2009-07-29
> **chancekang said:**
> Just a thought you should put in your mind.... Once you get through C++, Java and C# is just a toy...

Wrong, I know and use C++ as my main language, but commonly use Lisp for trying stuff out and PHP/BASH for general system scripting.

---

### Post by monraaf on 2009-07-29
> **Mirge said:**
> Vim is just going to add to the learning curve. Sure, it can be used when ssh'ing into a remote server, but so can pico/nano (which is a lot easier).

What part of "Vi is the de facto standard Unix editor" didn't you get?

```

$ pico
pico: not found
$ nano
nano: not found
$ which vi
/usr/bin/vi
$ uname -s
FreeBSD

```

---

### Post by ibuclaw on 2009-07-29
Vi and C definitely a +1

I didn't really understand much about programming languages until I started thinking in C mode.

Currently, my main writing language is D, it's such a refreshing and fun language coming from a C background. Perl is awesome for quick hacks too. :)

---

### Post by JordyD on 2009-07-29
I have nothing against learning Python as a first language, but honestly there is nothing wrong with learning C as a first language either. It doesn't matter what your first language is, as long as you learn from it. Text editor is really not that important. The important part is programming. I think vim helps understand exactly what's going on, and at the same time getting out of your way and letting you work most efficiently, once you get the hang of it.

---

### Post by CptPicard on 2009-07-29
> **tinivole said:**
> 
I didn't really understand much about programming languages until I started thinking in C mode.

I always found it interesting how hard it was to actually *break* the "C mode" at the exposure to, say, Lisp. It puts certain assumptions into your head that are hard to get rid of when it's time to realize that those things are not necessary... I would say I didn't understand much about programming languages before I moved out of the C-based languages ;)  (This is not to diss C-based languages per se...)


> **JordyD said:**
> It doesn't matter what your first language is, as long as you learn from it.

That's the important point; getting an understanding of the lay of the land ASAP. C is actually a far better first language than, say, C++ is because it's so much simpler, but it doesn't exactly volunteer a lot of the ideas you want to be learning, either...

---

### Post by hessiess on 2009-07-29
```

I didn't really understand much about programming languages until I started thinking in C mode.

```
Same.

> 
I always found it interesting how hard it was to actually break the "C mode" at the exposure to, say, Lisp.

Personally I dident have much problem learning Common Lisp, Though my lisp is still sort of `c like'.

---

### Post by soltanis on 2009-07-29
> **tinivole said:**
> Currently, my main writing language is D, it's such a refreshing and fun language coming from a C background. Perl is awesome for quick hacks too. :)

Please teach me then. I come from a C background but D is just incomprehensible (lack of any resources fails to help).

---

### Post by Mirge on 2009-07-29
> **monraaf said:**
> What part of "Vi is the de facto standard Unix editor" didn't you get?

```

$ pico
pico: not found
$ nano
nano: not found
$ which vi
/usr/bin/vi
$ uname -s
FreeBSD

```

Did my dog **** in your yard & piss you off or something? Just wondering why you're after me all of the sudden, with your "baiting" remark and now this.

```

$ which pico
/usr/local/bin/pico
$ uname -s
FreeBSD
$

```

```

mike@mike-kubuntu:~$ which pico
/usr/bin/pico
mike@mike-kubuntu:~$ uname -s
Linux
mike@mike-kubuntu:~$

```

What's your point?

---

### Post by CptPicard on 2009-07-29
> **monraaf said:**
> What part of "Vi is the de facto standard Unix editor" didn't you get?


Actually, [**ed**]("http://en.wikipedia.org/wiki/Ed_(text_editor)") is the standard editor.

---

### Post by JordyD on 2009-07-29
> **CptPicard said:**
> Actually, [**ed**]("http://en.wikipedia.org/wiki/Ed_(text_editor)") is the standard editor.

You have the wrong link, *[this]("http://www.gnu.org/fun/jokes/ed.msg.html")* is the correct one.

**EDIT:** It was very funny my first time reading it, because I had the same ed session as the one on that page.

---

### Post by monraaf on 2009-07-29
> **Mirge said:**
> Did my dog **** in your yard & piss you off or something? Just wondering why you're after me all of the sudden, with your "baiting" remark and now this.

Dude, take a chill pill. No need to take it personal.

> 
```

$ which pico
/usr/local/bin/pico
$ uname -s
FreeBSD
$

```


Programs in /usr/local/bin are not part of the FreeBSD base system, the stuff from ports goes there.  Vi is part of the FreeBSD base system and is guaranteed to be found on any FreeBSD system. Nano, pico, or any other text editor is only there if the administrator has explicitly installed it. 

And it's not only FreeBSD, don't assume that because Ubuntu comes with nano that it can be found on any other Unix system, it's not. A while ago there was some emacs user here asking a question about Vi. Why? Because that was the **only editor** found on his embedded system.

If you don't want to use Vi that's fine, don't use it. But you shouldn't discourage other users from learning the **de facto standard Unix editor** when you know nothing about it, except that you think it has a 'steep learning curve'

---

### Post by Mirge on 2009-07-29
> **monraaf said:**
> Dude, take a chill pill. No need to take it personal.



Programs in /usr/local/bin are not part of the FreeBSD base system, the stuff from ports goes there.  Vi is part of the FreeBSD base system and is guaranteed to be found on any FreeBSD system. Nano, pico, or any other text editor is only there if the administrator has explicitly installed it. 

And it's not only FreeBSD, don't assume that because Ubuntu comes with nano that it can be found on any other Unix system, it's not. A while ago there was some emacs user here asking a question about Vi. Why? Because that was the **only editor** found on his embedded system.

If you don't want to use Vi that's fine, don't use it. But you shouldn't discourage other users from learning the **de facto standard Unix editor** when you know nothing about it, except that you think it has a 'steep learning curve'

A person new to programming is really going to be ssh'ing into other servers to write/edit software? Unlikely it would seem to me.

And why should I _not_ recommend against adding onto a **beginner's** learning curve when he/she is just learning how to start programming? As far as vi being the **de facto standard Unix editor**, see the earlier posts.

If you've got a hard-on for vi/m, that's fantastic... but no need to push more difficulty onto a beginner than is necessary. I don't feel that it's necessary.

As far as it being installed in Ubuntu:
> 
Hello all I am new to programming, and new to the **Ubuntu**/Linux world. Lately I have had an itch to learn to program, my job does not require it however, I would like to learn the basics. My friend has given me his old C book (he dropped out of CS in college but still had the book), and** I just installed the Ubuntu Netbook Remix** on my new MSI-Wind u100. Now I just need to know where to start, I heard learning C, C++ and Java are all quite similar so I decided to learn C first. My question is what program do I need to install to start my merry way? I was reading the stickies but it seemed to skip step 1, starting off with what I acentually need to program. Please help me out, I'll be scouring through the older posts but there are so many I decided to to just start a new one. Thanks and sorry for all the noob questions, but **I really don't know jack about programming and linux at all**.


---

### Post by monraaf on 2009-07-29
> **Mirge said:**
> A person new to programming is really going to be ssh'ing into other servers to write/edit software? Unlikely it would seem to me.

And why should I _not_ recommend against adding onto a **beginner's** learning curve when he/she is just learning how to start programming?


Actually he decided for himself to use Vim, so why tell him he shouldn't use it when you know nothing about Vim. Vim is **not difficult**, it's different.

> 
If you've got a hard-on for vi/m,


Can you keep the childish personal attacks out of this?

---

### Post by Mirge on 2009-07-29
> **monraaf said:**
> Actually he decided for himself to use Vim, so why tell him he shouldn't use it when you nothing about Vim. Vim is **not difficult**, it's different.



Can you keep the childish personal attacks out of this?

Wasn't an attack by any means. But I'll leave it alone, I'm not going to be sucked into a pointless argument by a forum troll. Have a nice day!

At OP, I don't think vi/m is a bad editor by any means. It's quite powerful when you figure it out and become accustomed to it. I simply meant that it _does_ have a learning curve to it, and if you are new to programming, you might find it easier to wrap your mind around one thing (programming in itself) before trying to tackle too much at once. Best of luck in your endeavors, and be sure to post again if you run into any snags!

---

### Post by monraaf on 2009-07-29
> **Mirge said:**
> At OP, I don't think vi/m is a bad editor by any means. It's quite powerful when you figure it out and become accustomed to it. I simply meant that it _does_ have a learning 
curve to it

LOL, you don't even know Vim.

---

### Post by CptPicard on 2009-07-29
Well, I'm an Emacs guy myself, but as nifty a tool it can be, I'm not particularly pushing it on beginners, as I understand that editors like Kate and gEdit also work just fine. Whatever old skool editor they may learn eventually is not really a very relevant question to the actual programming issue... I would suspect vim is the same here.

---

### Post by monraaf on 2009-07-29
> **CptPicard said:**
> Well, I'm an Emacs guy myself, but as nifty a tool it can be, I'm not particularly pushing it on beginners,

Nobody here is pushing the OP to use Vim Captain ;) The OP decided for himself and was already getting started enthusiastically googling for Vim cheat sheets. Then who are we to say: "sorry you can't use Vim, that's too difficult for you" ?  Sounds a little condescending to me. It's especially strange that some of these remarks came from somebody who hasn't even bothered to learn Vim.

---

### Post by emptycan on 2009-07-29
Thanks for the help guys, I don't want this topic to become a debate on what editor is the best. I just simply chose VIM because that was the only one that I knew of. I don't know of any other text editor (until yesterday I thought VIM was a program writing tool only). I mean by all means please post other editors that are out there that are easy to learn. I already learned a things in VIM but I would like to know what you guys use besides vim. Thanks.

---

### Post by ibuclaw on 2009-07-30
> **soltanis said:**
> Please teach me then. I come from a C background but D is just incomprehensible (lack of any resources fails to help).

IRC is probably a better place to discuss this.

I'm usually in #ubuntu-beginners-dev on FreeNode, name is ibuclaw, if you don't see me, I'm at work. ;)

---

### Post by TheStatsMan on 2009-07-30
> **emptycan said:**
> Thanks for the help guys, I don't want this topic to become a debate on what editor is the best. I just simply chose VIM because that was the only one that I knew of. I don't know of any other text editor (until yesterday I thought VIM was a program writing tool only). I mean by all means please post other editors that are out there that are easy to learn. I already learned a things in VIM but I would like to know what you guys use besides vim. Thanks.

If you are comfortable with vim keep using it. The only thing people were debating about is to use vim correctly you may have to spend some time learning commands (rather than learning to program), where as other editors like Gedit you can just start typing. In the end though Vim is much more efficient than editors like Gedit, so if you are already used to it stick to it.

---

### Post by hyperAura on 2009-07-30
well as of my experience i use nedit for Java and Gedit for C.. Nedit is what i started with but ive also started from Java as my 1st language.. I will give Vim a try as every1 seems to be so enthusiastic about it..

---

### Post by wrtpeeps on 2009-08-01
> **hessiess said:**
> IDE's only overcomplicate everything, Vim is simple and efficient, its just different (which is a good thing, `common' `word processor' like editors are extremely inefficient).

C is nowhere near as complicated as its often made out to be.

Ha. You mustn't write anything with any sort of complication at all.

Try managing projects with hundreds of source files in VIM. It's a load of old crap and it doesn't do the job.

> **chancekang said:**
> Just a thought you should put in your mind.... Once you get through C++, Java and C# is just a toy...

If the OP is looking employment, learn C#, C++ and Java, in that order.

Everything is a bonus and not required. Python etc, whilst being "fun" (if one can even consider programming fun) are not much use to large scale corporations and you'll struggle to find languages like those used in any real capacity.

---

### Post by JordyD on 2009-08-01
> **wrtpeeps said:**
> Ha. You mustn't write anything with any sort of complication at all.

Try managing projects with hundreds of source files in VIM. It's a load of old crap and it doesn't do the job.

Is he learning to program or is he jumping into a hundred-file project with a week's experience?

That said, what is it you think vim is missing, specifically?

> **wrtpeeps said:**
> If the OP is looking employment, learn C#, C++ and Java, in that order.

Everything is a bonus and not required. Python etc, whilst being "fun" (if one can even consider programming fun) are not much use to large scale corporations and you'll struggle to find languages like those used in any real capacity.

[http://python.org/community/jobs/]("http://python.org/community/jobs/")

---

### Post by Dad1985 on 2009-08-01
why not just use vi, cant really see any need for vim.  while most kernel developers just use vi, for basic programming I see absolutely no reason to do this for non kernel programming.  We do have X and the op should be using a app like gedit or kate.  There really is no reason to use archaic software like VI or VIM.  Is this the same crowd which frowns on IDE's.

---

### Post by wrtpeeps on 2009-08-01
> **JordyD said:**
> Is he learning to program or is he jumping into a hundred-file project with a week's experience?

That said, what is it you think vim is missing, specifically?



[http://python.org/community/jobs/]("http://python.org/community/jobs/")

Vim is missing so many things it'd be pointless to list them all.

People who use vim tend to be the elitist sort, the "look at me I'm smart enough to use vim" sort.

---

### Post by JordyD on 2009-08-01
> **wrtpeeps said:**
> Vim is missing so many things it'd be pointless to list them all.

I'd like to hear them. A few at least.

---

### Post by wrtpeeps on 2009-08-01
> **JordyD said:**
> I'd like to hear them. A few at least.
Here's an absolutely fecking HUGE one:

Mouse support

2. Better file support.

1 file at a time? meh
2 at a time, meh

What about when you have 20 open? It's total pish. 

It's old and outdated and it's only suited to really quick edits. 

If you're going to learn on something, at least use an ide that is "advanced" (snigger) enough to allow mouse support, lets you see ALL your files that are currently open in a nice, neat wee tab bar, and also uses industry standard keyboard shortcuts.

Edit:

yes, I know gVim solves a lot of these issues, but then, why use vim at all?



And it lacks something that a LOT of editors lack, and should be considered an absolute sin:

Autocomplete.

Should be against the feckin law to release an editor without autocomplete support.

---

### Post by JordyD on 2009-08-01
> **wrtpeeps said:**
> Here's an absolutely fecking HUGE one:

Mouse support

2. Better file support.

1 file at a time? meh
2 at a time, meh

What about when you have 20 open? It's total pish. 

It's old and outdated and it's only suited to really quick edits. 

If you're going to learn on something, at least use an ide that is "advanced" (snigger) enough to allow mouse support, lets you see ALL your files that are currently open in a nice, neat wee tab bar, and also uses industry standard keyboard shortcuts.

Edit:

yes, I know gVim solves a lot of these issues, but then, why use vim at all?



And it lacks something that a LOT of editors lack, and should be considered an absolute sin:

Autocomplete.

Should be against the feckin law to release an editor without autocomplete support.

Tabs? :tabe filename
gVim solves mouse problem, gVim is just graphical vim, so why would you not use vim because of it?
Autocompletion can be achieved by C-p, C-n, or C-x C-o

Honestly, there is very little that vim doesn't support. And if there is, there is probably a plugin for it.

---

### Post by JordyD on 2009-08-01
> **wrtpeeps said:**
> Here's an absolutely fecking HUGE one:

Mouse support

2. Better file support.

1 file at a time? meh
2 at a time, meh

What about when you have 20 open? It's total pish. 

It's old and outdated and it's only suited to really quick edits. 

If you're going to learn on something, at least use an ide that is "advanced" (snigger) enough to allow mouse support, lets you see ALL your files that are currently open in a nice, neat wee tab bar, and also uses industry standard keyboard shortcuts.

Edit:

yes, I know gVim solves a lot of these issues, but then, why use vim at all?



And it lacks something that a LOT of editors lack, and should be considered an absolute sin:

Autocomplete.

Should be against the feckin law to release an editor without autocomplete support.

Tabs? :tabe filename
gVim solves mouse problem, gVim is just graphical vim, so why would you not use vim because of it?
**EDIT:** *And* most terminal emulators support mice, so you only need to enable it in your .vimrc. The example which comes with vim is what I base my .vimrc off of. It enables a lot of useful things, like mouse support.
Autocompletion can be achieved by C-p, C-n, or C-x C-o

Honestly, there is very little that vim doesn't support. And if there is, there is probably a plugin for it.



**EDIT2:** Sorry for the double post. If a moderator wants to delete the above since this one includes it all, that would be great.

---

### Post by wrtpeeps on 2009-08-01
> **JordyD said:**
> Tabs? :tabe filename
gVim solves mouse problem, gVim is just graphical vim, so why would you not use vim because of it?
Autocompletion can be achieved by C-p, C-n, or C-x C-o

Honestly, there is very little that vim doesn't support. And if there is, there is probably a plugin for it.

Yea, so you missed my point.

:tabe is fine if you can remember every single file you have open and the name for it.

What about if you have 20-30 files open. You can't see whats open at a quick glance, you can't QUICKLY (ie ctrl-tab) through them. 

As for this autocompletion, if I turn that on, does it automatically do it for functions I create then? Does it pop up with a tool tip and all to tell me what the parameters are expected to be? Can it figure out functions I write in other files? Do I need to hit c-whatever every time? 

As for the gVim question, the only reason to use vim is if you have this strange, weird hatred for GUI's or IDE's. If you don't mind IDE's, there are much better ones than gVim.

---

### Post by JordyD on 2009-08-01
> **wrtpeeps said:**
> Yea, so you missed my point.

:tabe is fine if you can remember every single file you have open and the name for it.

Dunno about you, but I can open up gVim, :e test.c :tabe test.cpp, and see two tabs with the names of my files open.

> **wrtpeeps said:**
> What about if you have 20-30 files open. You can't see whats open at a quick glance, you can't QUICKLY (ie ctrl-tab) through them.

:ls

> **wrtpeeps said:**
> As for this autocompletion, if I turn that on, does it automatically do it for functions I create then? Does it pop up with a tool tip and all to tell me what the parameters are expected to be? Can it figure out functions I write in other files? Do I need to hit c-whatever every time?

Yes. No. Yes. Yes.

Admittedly, vim needs to see some work here.

> **wrtpeeps said:**
> As for the gVim question, the only reason to use vim is if you have this strange, weird hatred for GUI's or IDE's. If you don't mind IDE's, there are much better ones than gVim.

I don't mind IDEs. I don't hate GUIs. Whether you like to use an IDE vs a text editor is a matter of personal preference, not elitism.

---

### Post by Neheb on 2009-08-02
@OP: If I where you I would avoid using any IDE or code auto-completion of any sort, at least in the beginning. This greatly helps you in actually learning the syntax of whatever language you are learning and also remove much of the "helpful" features of IDE lik having lots of code in your files when you create them.

though you should try to get an editor that does syntax highlighting/colouring as it is really useful.

As for what language to start out with, I think all of the 4 are good/ok languages, though C++ (and probably C, but I haven't touched it) have some features that makes them a bit hard to start out with.

all of this (what editor/language to use/start with) have been discussed a lot and searching the forums and looking at the stickies should sort you out if there is anything you are still uncertain about.

EDIT: depending on how old that book are, I would suggest either getting a new book or following online tutorials instead.

---

### Post by Mirge on 2009-08-02
These "what language should I start out with?" threads pop up so often now that I'm just going to stop reading them :P.

---

### Post by measekite on 2009-08-02
> **emptycan said:**
> Hello all I am new to programming, and new to the Ubuntu/Linux world. Lately I have had an itch to learn to program, my job does not require it however, I would like to learn the basics. My friend has given me his old C book (he dropped out of CS in college but still had the book), and I just installed the Ubuntu Netbook Remix on my new MSI-Wind u100. Now I just need to know where to start, I heard learning C, C++ and Java are all quite similar so I decided to learn C first. My question is what program do I need to install to start my merry way? I was reading the stickies but it seemed to skip step 1, starting off with what I acentually need to program. Please help me out, I'll be scouring through the older posts but there are so many I decided to to just start a new one. Thanks and sorry for all the noob questions, but I really don't know jack about programming and linux at all.

Edit - I decided to use VIM as an editor because my friend told me that's what he used way back in the days, can someone explain how I install it?

I would not recommend C, C++, or Java for your first language and also having to learn an editor and other programming concepts as well.

I would buy the book "Programming Python 3" sold at Amazon at a good price.  I initally would use gedit which you already have.  It is a text editor.  Setup the preferences for color coding that is good for programming.  After you know this language you will be able to do many things.  Then if you desire I would take a look at Java or what ever else interests you.

---

### Post by napsy on 2009-08-02
If you're opening 20+ source files in *any* IDE or editor, you're probably doing something wrong.

Unix/Linux user can use grep for quickly finding stuff. And vim users have the cscope tool which is a powerfull extension for vim to quickly browse a source tree.

---

### Post by wrtpeeps on 2009-08-02
> **napsy said:**
> **If you're opening 20+ source files in *any* IDE or editor, you're probably doing something wrong.**

Unix/Linux user can use grep for quickly finding stuff. And vim users have the cscope tool which is a powerfull extension for vim to quickly browse a source tree.
What a load of absolute nonsense. 

Try developing programs on enterprise scale. Programs that take 3 days to compile and therefore you have to make sure that nothing is going to screw up. Hence the need to continually cross reference files.

---

### Post by credobyte on 2009-08-02
> **wrtpeeps said:**
> What a load of absolute nonsense. 

Try developing programs on enterprise scale. Programs that take 3 days to compile and therefore you have to make sure that nothing is going to screw up. Hence the need to continually cross reference files.

3 days of pure compiling ?? :o Don't mind in giving an example ( open-source application of course ) ?

---


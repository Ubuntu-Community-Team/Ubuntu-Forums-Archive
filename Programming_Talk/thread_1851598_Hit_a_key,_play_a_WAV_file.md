---
title: "Hit a key, play a WAV file"
date: 2011-09-28
forum: Programming Talk
---

### Post by kline on 2011-09-28
I want to write a C or C++ program  where, basically, using getchar(), whenever I hit a key, one of my .WAV files plays.  So far I've been going in circles.  Can anybody help me?

---

### Post by Senesence on 2011-09-29
As I see it, you have two options:

[LIST=1]
[*]Run an existing program from your C program (like a player) that will play the WAV files.
[*]Use an audio library that provides WAV playback functions that you can call directly from your program.
[/LIST]

The first option is probably the fastest to implement, and it could even be done in a few simple lines of BASH. The second option will provide more flexibility, but it will require more work on your end (you'll have to learn about the library in question, and how to use it to do what you want).

There is an OpenAL tutorial here that may be helpful: [http://www.devmaster.net/articles/openal-tutorials/lesson1.php](http://www.devmaster.net/articles/openal-tutorials/lesson1.php)

There's a Linux version of the code at the bottom of the page.

---

### Post by nvteighen on 2011-09-29
In my opinion, it'd be great for you to use OpenAL, so that you get familiar with reading APIs and using libraries. Opening a new process is almost like cheating, when done in a general programming language... Ok, sometimes you have to do it, but that's more the way bash scripts are meant to work, not C++ (or any of the general programming languages).

---

### Post by kline on 2011-09-29
> **Senesence said:**
> As I see it, you have two options:

[LIST=1]
[*]Run an existing program from your C program (like a player) that will play the WAV files.
[*]Use an audio library that provides WAV playback functions that you can call directly from your program.
[/LIST]

The first option is probably the fastest to implement, and it could even be done in a few simple lines of BASH. The second option will provide more flexibility, but it will require more work on your end (you'll have to learn about the library in question, and how to use it to do what you want).

There is an OpenAL tutorial here that may be helpful: [http://www.devmaster.net/articles/openal-tutorials/lesson1.php](http://www.devmaster.net/articles/openal-tutorials/lesson1.php)

There's a Linux version of the code at the bottom of the page.

The OpenAL library does just about what i want.  it fits into what will be a much larger program.  I"ve got a bunch more questions about things in general, but the most noteworthy is "ai" or "AI"??  Elsewhere on this forum i found a program that seems to be an older version of the audio library that has its headers in /usr/include/AL.  Can you [or anybody else ] confirm.

One thing I discovered is that the alutSleep() call takes times in fractions of a second.  One of my wav files seems to be around 0.15sec.
Is there any way I can tell the exact length and built this in? :)

---

### Post by Senesence on 2011-09-29
> **nvteighen said:**
> Opening a new process is almost like cheating, when done in a general programming language... Ok, sometimes you have to do it, but that's more the way bash scripts are meant to work, not C++ (or any of the general programming languages).

"Which one will reach the other side of the river: The one who dreams of a raft, or the one that hitchhikes to the next bridge?"

;)

[quote=kline]
The OpenAL library does just about what i want. it fits into what will be a much larger program. I"ve got a bunch more questions about things in general, but the most noteworthy is "ai" or "AI"?? Elsewhere on this forum i found a program that seems to be an older version of the audio library that has its headers in /usr/include/AL. Can you [or anybody else ] confirm.

One thing I discovered is that the alutSleep() call takes times in fractions of a second. One of my wav files seems to be around 0.15sec.
Is there any way I can tell the exact length and built this in? :) 
[/quote]

You should consult the OpenAL documentation. Also, looking at this OpenAL programmers guide could be of some use, so take a look at that too: [http://docs.google.com/viewer?a=v&q=cache:PLYMXNc1hggJ:connect.creativelabs.com/openal/Documentation/OpenAL_Programmers_Guide.pdf+openal+documentation&hl=en&gl=us&pid=bl&srcid=ADGEESgaTtAV_fqiaPPzn0_BDLNVGNBQPJj5oAvyZZcJrkmQzE9TxeIg89NtOG_FnDCtF-d6B6jC1AxOeeIHFKqQy1QYga6YF5drkmtnMrsu1330fzM1cVcmonaBKSIEDOHJozX59es3&sig=AHIEtbSrofpRZNxRxc8NbOi55XHwB5ZWxA](http://docs.google.com/viewer?a=v&q=cache:PLYMXNc1hggJ:connect.creativelabs.com/openal/Documentation/OpenAL_Programmers_Guide.pdf+openal+documentation&hl=en&gl=us&pid=bl&srcid=ADGEESgaTtAV_fqiaPPzn0_BDLNVGNBQPJj5oAvyZZcJrkmQzE9TxeIg89NtOG_FnDCtF-d6B6jC1AxOeeIHFKqQy1QYga6YF5drkmtnMrsu1330fzM1cVcmonaBKSIEDOHJozX59es3&sig=AHIEtbSrofpRZNxRxc8NbOi55XHwB5ZWxA)

If you have any OpenAL specific questions, you should probably ask them on OpenAL mailing lists/forums.

---

### Post by nvteighen on 2011-10-01
> **Senesence said:**
> "Which one will reach the other side of the river: The one who dreams of a raft, or the one that hitchhikes to the next bridge?"

;)


I see your point.

My point against using system() or stuff like that is not just justified with the silly argument I gave, which I do recognize as a very weak argument.

Mostly, it's about controlling I/O to/from the child process... or rather than I/O, interfacing with it in general. system() works by opening a new shell, so all you get to communicate with the child is command line arguments and the returned error code. You can't interact with it, actually. popen() allows you I/O-based interaction... but as you surely know, libraries gives you interfaces that are far beyond that: you share data using the library's data structures, procedures, etc.

Yeah, I guess I should have thought my post a bit better.

---

### Post by kline on 2011-10-01
well, believe it or** else** {MAD magazine}, somewhere in my ~/devel directory, i found a bunch of popen() code that i wrote back in the early 90's.  so, when i'm farther along with my program, i can dig into that.  as for now, i discovered how Much more there is to do.  

still, considering all the benefits if this is as useful as i think it will be--hey--a few days'  worth of hacking is nothing.

---


---
title: "what to practice for kernel engineering jobs"
date: 2010-11-17
forum: Programming Talk
---

### Post by jamesbon on 2010-11-17
Hi,
I was going through a job profile mentioned here
[http://webapps.ubuntu.com/employment/canonical_KD%20PG3/]("http://webapps.ubuntu.com/employment/canonical_KD%20PG3/")
I recently did some network programming and developed a character driver (basic it takes text from userspace and then displays it back)
and have got a good understanding of network driver (leaving the PHY device part of it) you can see my past posts on the same forum.
I have been reading more on Kernel and related stuff time to time since my college time.

I want to know what do I need to practice so that I can be the best person for the jobs similar to mentioned above.I have been reading and reading a lot of stuff about kernel timers,spin locks,polling of data for CMOS drivers.But I do not have practiced it enough.
I do not want to read any further but I want to actually do some thing on some real stuff.
What should I be doing that is not clear to me can some one help me to understand as where do I begin with.I watch kernel mailing list also I am right now not sure as how much would I be able to fix the bugs in current kernel.I don't find myself heading to any where if I do not actually do some thing.The problem is I am not aware as what should I do so that I can be the right person for Kernel Engineering jobs.
If some one can point me to some thing that I should be developing that can at least satisfy my hunger for technology even that would be great.
I don't feel myself as a novice for kernel development but I am not practiced enough also.
The situation is without practice I don't find myself any where.But what to practice I do not know as I have no idea as what do people in such jobs do.

---

### Post by worksofcraft on 2010-11-17
> **jamesbon said:**
> Hi,
I was going through a job profile mentioned here
[http://webapps.ubuntu.com/employment/canonical_KD%20PG3/]("http://webapps.ubuntu.com/employment/canonical_KD%20PG3/")
I recently did some network programming and developed a character driver (basic it takes text from userspace and then displays it back)
and have got a good understanding of network driver (leaving the PHY device part of it) you can see my past posts on the same forum.
I have been reading more on Kernel and related stuff time to time since my college time.

I want to know what do I need to practice so that I can be the best person for the jobs similar to mentioned above.I have been reading and reading a lot of stuff about kernel timers,spin locks,polling of data for CMOS drivers.But I do not have practiced it enough.
I do not want to read any further but I want to actually do some thing on some real stuff.
What should I be doing that is not clear to me can some one help me to understand as where do I begin with.I watch kernel mailing list also I am right now not sure as how much would I be able to fix the bugs in current kernel.I don't find myself heading to any where if I do not actually do some thing.The problem is I am not aware as what should I do so that I can be the right person for Kernel Engineering jobs.
If some one can point me to some thing that I should be developing that can at least satisfy my hunger for technology even that would be great.
I don't feel myself as a novice for kernel development but I am not practiced enough also.
The situation is without practice I don't find myself any where.But what to practice I do not know as I have no idea as what do people in such jobs do.

This kind of job is for people with **a lot of experience**. Many years ago I worked as an electronics engineer and to make our hardware work efficiently I needed a reasonable understanding of device driver requirements. I received support from experienced people with similar knowledge but for Microsoft operating systems.

Your "bond driver" was indeed good experience, but you will have to know about writing interrupt handlers, virtual memory management, task switching etcetera to be able to give Linux specific guidance to engineers who are developing drivers for new products like next generation graphics cards.

I think the only way you can get there is to actually get a job as a more junior team member possibly by finding an existing project and joining to contribute and you will learn what you need as you go. Also I would be interested to read about what you find :)

---

### Post by DangerOnTheRanger on 2010-11-17
Hey, I know a lot of that stuff! :)
What I did to learn all that(and put it into practice) was to develop my own mini OS.
It's actually not too hard, just tedious...

---

### Post by jamesbon on 2010-11-17
Hi,many thanks to both of you for replying to this message.

> **worksofcraft said:**
> This kind of job is for people with **a lot of experience**.

I understand your point that is why I asked here.My situation is not as yours.I do not have such a job.
> **worksofcraft said:**
> 
Your "bond driver" was indeed good experience, but you will have to know about writing interrupt handlers, virtual memory management, task switching etcetera to be able to give Linux specific guidance to engineers who are developing drivers for new products like next generation graphics cards.
I am actually reading this stuff only which you mentioned.Not got my hands dirty on the code the books I am following are Linux Kernel Development Robert Love and [ELDD.]("http://books.google.co.in/books?id=Boo57V0IOq0C&pg=PA139&lpg=PA139&dq=xf86WriteSerial(pInfo-%3Efd,+s,+1);&source=bl&ots=pwIuaSV5T2&sig=6bRJwFeFeHjPLwVPdwYQDbI_B3k&hl=en&ei=ypLkTJ2uBZCevgPLqYW4DQ&sa=X&oi=book_result&ct=result&resnum=1&ved=0CBYQ6AEwAA#v=onepage&q=xf86WriteSerial(pInfo-%3Efd%2C%20s%2C%201)%3B&f=false")

> **worksofcraft said:**
> 
I think the only way you can get there is to actually get a job as a more junior team member possibly by finding an existing project and joining to contribute and you will learn what you need as you go. Also I would be interested to read about what you find :)
Very correct I do work but my current job does not involve any Kernel Development and is just a way of earning my living rather than doing some thing I really like.
I am keen to join any open source project which involves kernel development I am not looking for big money at this point. I want to learn but I am not sure as how do I get into one such job.
I recently gave an interview at a very good company which is known for its technology world wide (the company does not exist any more) the panel there had asked me some question which I feel I had answered correctly.
In one question on a written paper I had marked a piece of code as wrong.I have forgotten the logic as why did I mark a cross or error on that.They coincidentally asked the last question which was nothing but the answers I marked in written test which I just mentioned.Now at the time in interview they gave me a similar problem as was in the written test.Which I had cross marked.The answer I gave in interview was different than what I gave on written exam for same type of question.That was basically some sort of macro defined in C ( I do not remember the question now)
and they asked why my answer in interview and written test are different I even after thinking for long in interview could not recall the logic as why did I mentioned the options in the written test as that day (which I feel was correct) so they said I am not good at programming and even though I was not suited for the job they had called me looking at the resume since they felt there could be some substance which they did not found.So they said if you are still interested for the job do not loose hope and apply here after three months and practice programming more.
I am not sure what message they wanted to convey me on one side they were rejecting and on the other side they were saying to apply again also.I left heart broken that time.

Irrespective of the fact that I get or not such jobs at least for myself I want to work on such things.
So do let me know if you have any other suggestion other than working in a small team (I doubt it to be possible) I would keep working as I am doing now for myself.
I am giving my full time to stuff on internet such as kernel development device drivers etc to be honest I enjoy this thing more than any thing I have done till date.


> **DangerOnTheRanger said:**
> Hey, I know a lot of that stuff! :)
What I did to learn all that(and put it into practice) was to develop my own mini OS.
It's actually not too hard, just tedious...
Can you suggest me where you began with and what you did I will surely practice what you mention.Even I had that idea and I came across Linux From Scratch project share some thing that you might have done some relevant links I am interested to do them.

---

### Post by worksofcraft on 2010-11-18
> **jamesbon said:**
> ...
I am not sure what message they wanted to convey me on one side they were rejecting and on the other side they were saying to apply again also.I left heart broken that time.


Yes it is sad, but a lot of people who learn computing just do it for a job. They aren't interested in exploring beyond what they are taught and so your interviewers quite likely think that you hadn't paid much attention in class as opposed to actually exploring alternative approach to a question that you felt you had already answered for them.

What you are looking for comes under the term "real-time" or "embedded" systems programming. Sadly I don't think there are quite as many small companies making innovative computer equipment as there used to be so there are fewer opportunities, but I do know that there are versions of Windows being embedded in hand held devices and also that companies like Nokia are investing in Linux technology.

My suspicion is that the next big thing will be the Linux answer to Microsoft's direct-X and thus bring high performance 3D into the open source domain ;)

---

### Post by trent.josephsen on 2010-11-18
The day Linux gets anything resembling DirectX is the day I buy a Mac.

</facetious>

---

### Post by worksofcraft on 2010-11-18
> **trent.josephsen said:**
> The day Linux gets anything resembling DirectX is the day I buy a Mac.

</facetious>

AFIK currently on non Microsoft platforms most of your rendering is being done by your main processor in memory image buffers and then bit blitted to the display.

Meanwhile many of us have a high-spec 3D graphics engine in our top of the range graphics card running **nop** instructions :shock:
OTOH, 3D is seriously going to happen whether you like it or not.

---

### Post by Reiger on 2010-11-18
You meant to say that you want proper support for hardware acceleration in OpenGL. Bit complex on Linux as the concept of “driver” exists for hardware/X/mesa/what_have_you.

---

### Post by DuneSoldier on 2010-11-18
> **worksofcraft said:**
> Yes it is sad, but a lot of people who learn computing just do it for a job. They aren't interested in exploring beyond what they are taught and so your interviewers quite likely think that you hadn't paid much attention in class as opposed to actually exploring alternative approach to a question that you felt you had already answered for them.

What you are looking for comes under the term "real-time" or "embedded" systems programming. Sadly I don't think there are quite as many small companies making innovative computer equipment as there used to be so there are fewer opportunities, but I do know that there are versions of Windows being embedded in hand held devices and also that companies like Nokia are investing in Linux technology.

My suspicion is that the next big thing will be the Linux answer to Microsoft's direct-X and thus bring high performance 3D into the open source domain ;)

OpenGL & SDL & OpenAL.

Next.

DISCLAIMER: I've only done a very, very small amount of work with Direct3D in college. DirectX 9 I think it was and I made a very poor Asteroids clone using C#. It's about the same level of work to do the same thing using SDL and OpenGL with C++. Oh and Boost I rely on that just as much as I rely on STL.

---

### Post by worksofcraft on 2010-11-18
> **DuneSoldier said:**
> OpenGL & SDL & OpenAL.

Next.

DISCLAIMER: I've only done a very, very small amount of work with Direct3D in college. DirectX 9 I think it was and I made a very poor Asteroids clone using C#. It's about the same level of work to do the same thing using SDL and OpenGL with C++. Oh and Boost I rely on that just as much as I rely on STL.

The point is about opportunities for kernel level programming. It isn't about how easy it is to code graphics apps.

If you think OpenGL is the perfect and complete solution and doesn't need any further kernel level development to better utilize high performance 3D hardware capabilities... then suggest something else :P

---

### Post by NathanB on 2010-11-18
```
Quoting DangerOnTheRanger:
Hey, I know a lot of that stuff!
What I did to learn all that(and put it into practice) was to develop my own mini OS.
It's actually not too hard, just tedious...

```
> **jamesbon said:**
> 
Can you suggest me where you began with and what you did I will surely practice what you mention.Even I had that idea and I came across Linux From Scratch project share some thing that you might have done some relevant links I am interested to do them.

Some excellent places to start:

OSDev Wiki:

[http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

AOD (alt.os.development) FAQ wiki:

[http://aodfaq.wikispaces.com/](http://aodfaq.wikispaces.com/)

---

### Post by DangerOnTheRanger on 2010-11-23
> **jamesbon said:**
> 
Can you suggest me where you began with and what you did I will surely practice what you mention.Even I had that idea and I came across Linux From Scratch project share some thing that you might have done some relevant links I am interested to do them.

Sure!

[http://wiki.osdev.org]("http://wiki.osdev.org/")
[http://forum.osdev.org]("http://forum.osdev.org/")

OSDev is full of information concerning how to build your own x86 OS.
There's even some info on the PowerPC architecture.

---

### Post by DangerOnTheRanger on 2010-11-23
> **NathanB said:**
> ```
Quoting DangerOnTheRanger:
Hey, I know a lot of that stuff!
What I did to learn all that(and put it into practice) was to develop my own mini OS.
It's actually not too hard, just tedious...

```
Some excellent places to start:

OSDev Wiki:

[http://wiki.osdev.org/Main_Page](http://wiki.osdev.org/Main_Page)

AOD (alt.os.development) FAQ wiki:

[http://aodfaq.wikispaces.com/](http://aodfaq.wikispaces.com/)

Oopsie... :redface: ...

---


---
title: "License for an open-source project"
date: 2009-04-22
forum: Programming Talk
---

### Post by adamitj on 2009-04-22
I am a newbie when talking about licenses. I read the terms and conditions of GPL, LGPL and some others licenses, and I still need help to understand which one is the best for my needs.

Months ago, I started a new project in Java/AJAX/DHTML to create web pages dynamically. The company I work for is now very interested in this project, so I need to put it on a license because I will be paid to maintain and add new features in the project if we can have a deal.

So, the terms and conditions I need are:

1) The source code is hidden to everyone (until it becomes mature and stable I will left it this way. Then I'll create an open-source "branch" with a BSD license);
2) Everyone can use the binaries for free, except for commercial purposes (these one must acquire a license);
3) Everyone can distribute the binaries respecting the items #1 and #2;

Is there a license which contains the terms above?

---

### Post by cb951303 on 2009-04-22
> **adamitj said:**
> I am a newbie when talking about licenses. I read the terms and conditions of GPL, LGPL and some others licenses, and I still need help to understand which one is the best for my needs.

Months ago, I started a new project in Java/AJAX/DHTML to create web pages dynamically. The company I work for is now very interested in this project, so I need to put it on a license because I will be paid to maintain and add new features in the project if we can have a deal.

So, the terms and conditions I need are:

1) The source code is hidden to everyone (until it becomes mature and stable I will left it this way. Then I'll create an open-source "branch" with a BSD license);
2) Everyone can use the binaries for free, except for commercial purposes (these one must acquire a license);
3) Everyone can distribute the binaries respecting the items #1 and #2;

Is there a license which contains the terms above?

I think you need dual-licensing.
[http://en.wikipedia.org/wiki/Commercial_open_source_applications](http://en.wikipedia.org/wiki/Commercial_open_source_applications)
[http://en.wikipedia.org/wiki/Dual-licensing](http://en.wikipedia.org/wiki/Dual-licensing)

---

### Post by wmcbrine on 2009-04-23
Basically there are two kinds of licenses: Open source, and proprietary. Since you're not planning to distribute the source, you can't use any kind of open source license; and there is no standardization among proprietary licenses, nor TTBOMK are there any that you can just take and reuse. And after all, why would there be? Proprietary licenses are about *not* sharing.

It's possible that one of the Creative Commons licenses could be made to work for you, though.

BTW, this idea of keeping the source private "until it's mature" is something I see a lot among newbies, but it's quite bizarre. For one thing, your source is never going to be mature. Code that isn't changing is code that's dead. In fact, I'll go out on a limb here and say that it probably won't even reach the "less embarrassing" stage. And it shouldn't -- because you should always be pushing the limits of what you know how to do. Second, there's no better way to improve bad code than to publish it and get feedback on it. That's kinda the whole point of open source.

P.S. Good luck trying to enforce "free except for commercial purposes". I've been there, and I didn't get one single buyer for my commercial license, though I knew for a fact that I had commercial users. This is much different from the typical dual-licensing situation, because that's based on *distribution* rather than simple *use*, and it only works for open source.

---

### Post by shadylookin on 2009-04-23
> **adamitj said:**
> I am a newbie when talking about licenses. I read the terms and conditions of GPL, LGPL and some others licenses, and I still need help to understand which one is the best for my needs.

Months ago, I started a new project in Java/AJAX/DHTML to create web pages dynamically. The company I work for is now very interested in this project, so I need to put it on a license because I will be paid to maintain and add new features in the project if we can have a deal.

So, the terms and conditions I need are:

1) The source code is hidden to everyone (until it becomes mature and stable I will left it this way. Then I'll create an open-source "branch" with a BSD license);
2) Everyone can use the binaries for free, except for commercial purposes (these one must acquire a license);
3) Everyone can distribute the binaries respecting the items #1 and #2;

Is there a license which contains the terms above?

Since open source requires that it be free for **EVERYONE** to use(even commercial businesses) what you're asking for is not open source and there is no standard(that I'm aware of) for such a thing. You should ask your company to have a lawyer draft you an appropriate license.

---

### Post by adamitj on 2009-04-23
> **wmcbrine said:**
> P.S. Good luck trying to enforce "free except for commercial purposes". I've been there, and I didn't get one single buyer for my commercial license, though I knew for a fact that I had commercial users. This is much different from the typical dual-licensing situation, because that's based on *distribution* rather than simple *use*, and it only works for open source.

I have no intention to start a strike against opensource iniciative, but, even using this king of software I never understood how to survive, in other words, how to earn money by declaring all software I maintain as opensource.

When you have time, and do it for hobby, it is very appreciable to join some opensource communities and contribute with them, offering part of your time to work in their source codes.

However, how can I, a single and lonely software developer, who depends of software programming to live, can survive in this capitalist world working 100% of time in opensource projects?

Some people say me: "Oh! Man! It's easy! Just make support contracts with your customers!" or "sell trainings to your users!" and stuff like that... but it is a different reality, which can be reached only by not-so-small corporations.

These are the reasons I just can't free my own softwares in opensource world - *not the ones created and maintained by the company I work for*. I am very minded to change them if I can find a "magic" solution...

---

### Post by shadylookin on 2009-04-23
> **adamitj said:**
> I have no intention to start a strike against opensource iniciative, but, even using this king of software I never understood how to survive, in other words, how to earn money by declaring all software I maintain as opensource.

When you have time, and do it for hobby, it is very appreciable to join some opensource communities and contribute with them, offering part of your time to work in their source codes.

However, how can I, a single and lonely software developer, who depends of software programming to live, can survive in this capitalist world working 100% of time in opensource projects?

Some people say me: "Oh! Man! It's easy! Just make support contracts with your customers!" or "sell trainings to your users!" and stuff like that... but it is a different reality, which can be reached only by not-so-small corporations.

These are the reasons I just can't free my own softwares in opensource world - *not the ones created and maintained by the company I work for*. I am very minded to change them if I can find a "magic" solution...

I don't really have any statistics to back it up, but I'm fairly certain most open source software comes from hobbyist who enjoy it and major corporations who have a vested interest in an open source project

It may not be RMS's dream world, but closed source definitely has it's uses. Though you are asking for a proprietary license and as such there is no open source license that meets your needs. You should really consult your companies legal department and have them assist you.

---


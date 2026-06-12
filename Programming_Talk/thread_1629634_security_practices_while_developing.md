---
title: "security practices while developing?"
date: 2010-11-24
forum: Programming Talk
---

### Post by minsf on 2010-11-24
Hi all,

I recently joined an open source project, so I was wondering if other developers here could recommend some security practices they use.

_Motivation:_ It is a small project (3-5 developers) and I kind of trust them, but you know how they say trust no one... Plus, I consider this as a jump board to bigger projects, so I wonder what one does when they do not know all the other developers...

_More Details:_ the project is mainly written in java, which means I need to run ant in order to build my code, but the build.xml file is so long, so I am not yet sure what it really does... Then, I need to run the jar file (java -jar blahblah.jar) to test it. I am using git for revision control, even though the repository is svn, but I doubt that source code management creates any big security risk, so it's probably just the ant and the jar.

_Some Ideas:_ Should I run "ant" and "java -jar" as a different user? something like

```

su -c "java -jar blahblah.jar" differentUser

```

or should I chroot?
or maybe some other (better) idea?

I usually google this stuff online, but this time I have no clue what to search for, so I guess I just need some direction.

ps. I should mention this has been posted on the security forum, but I got no replies, so I assume it is fits better in this programming forum; sorry for the double post (is there a way to merge?)

---

### Post by worseisworser on 2010-11-24
Do you know what the 324 million lines of code in Debian "really does"?

( [http://en.wikipedia.org/wiki/Source_lines_of_code#Example](http://en.wikipedia.org/wiki/Source_lines_of_code#Example) )

What's the real problem or danger here? Perhaps you should think of some other way to deal with it.

---

### Post by shadylookin on 2010-11-24
Once you trust the original source you only have to check new commits. 

Though generally you only allow trusted people to make commits to a repository. 

if you're really paranoid you could do all the building and testing on a separate user account.

---

### Post by minsf on 2010-11-24
> **worseisworser said:**
> Do you know what the 324 million lines of code in Debian "really does"?

What's the real problem or danger here? 

Well, the difference is that Debian's code is reviewed by many developers. You can argue that it is still possible to sneak in some malicious code - some will agree with you and some will not -  but you'd probably agree it is certainly easier to sneak in some code in a project which is reviewed by 3 others at best. In fact, each of us has different responsibilities, so I doubt anyone had time to look at my code at all, except for testing; and, likewise, I don't have time to look into all the details of their code, except for testing. So the bottom line is that most of the code is probably not reviewed by more than one person...

in other words, anyone can sneak in some <exec...> task in the build.xml.

---

### Post by minsf on 2010-11-24
> **shadylookin said:**
> Once you trust the original source you only have to check new commits. 

In general, you are right, but, unfortunately, the code is too long, so this is never going to happen... i simply have to test new commits without trusting anything.

> **shadylookin said:**
> 
Though generally you only allow trusted people to make commits to a repository. 


Yes this certainly eliminates some of the problems in theory.
But in practice, I cannot really know what they are doing...

---

### Post by Arndt on 2010-11-24
> **minsf said:**
> In general, you are right, but, unfortunately, the code is too long, so this is never going to happen... i simply have to test new commits without trusting anything.



Yes this certainly eliminates some of the problems in theory.
But in practice, I cannot really know what they are doing...

Maybe one could go look for anecdotes (or rather real stories) of where something went wrong, but I don't know where to look for that. When it happens on a small scale, it's probably not reported anywhere.

There is a mailing list which deals with computer risks in various forms: [http://catless.ncl.ac.uk/risks](http://catless.ncl.ac.uk/risks). Maybe you can find something there.

One piece of advice might be to keep what you consider really valuable on another computer, and protect that one with a firewall, so even if the development one blows up or posts its whole content on twitter, you haven't lost anything. If it's practical, I don't know.

In the end, this is going to be a program others will use, who are not programmers, I suppose? And you will recommend it to people you know? If you won't be able to do that with a clear conscience, maybe that is the scenario you should think about. I haven't been in your situation, so I can't say how I would think, myself.

---


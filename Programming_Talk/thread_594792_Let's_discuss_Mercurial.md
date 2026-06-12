---
title: "Let's discuss Mercurial"
date: 2007-10-28
forum: Programming Talk
---

### Post by kentl on 2007-10-28
Hi,

I've been messing around with Mercurial for a while. And I must say that it seems really interesting. My previous experience is with CVS and SVN, even though I'm not THAT experienced with those either. ;)

I thought that we would discuss Mercurial in this thread. If all you have to contribute is a rant about why Mercurial should not be used, that's fine too! :)

To kick start a discussion, you might want to answer some/all of these questions:

Do you use it? How do you use it? (Which technologies do you use, like: SSH, Apache web server + CGI. Which model do you use? Do you sync to a central repository, or in a ring, or whatever?) Have you tried working together with users of non-Linux platforms using it? Did it work well? Do you use the Ubuntu package of Mercurial, or do you install it manually to get the latest version?

---

### Post by kentl on 2007-10-29
Doesn't anyone use Mercurial? What do you use? :popcorn:

---

### Post by pmasiar on 2007-10-30
SVN, pyworkbench and TRAC :-)

---

### Post by kentl on 2007-10-30
What's pyworkbench? I tried Googling it but the only hit is your post in this thread. :-)

---

### Post by pmasiar on 2007-10-30
Sorry, proper name is pysvn workbench, my bad: [http://pysvn.tigris.org/](http://pysvn.tigris.org/)

It is GUI frontend to SVN client. Neat and easy to use!

---

### Post by hecato on 2007-10-30
I have little experience with SVN and CVS, and after try in a place to people get used to version control systems. But some random person formatting the server (in Windows.. thought this is not a blame :P, who use the server for introduce virus!.. lol) and losing little of our work, I decide to look for alternative.

I have tried darcs, and also bazaar (bzr), also I take a little look at mercurial and other like git and perhaps others, haven't used it much, still think that is nice thing, but I guess that I pass it, because I already have been trying to get basic usage of darcs and bzr.

Hehe, not much information about subject, also isn't a rant why mercurial should not be used, but a little of why I not used it (I have already get used to others, in fact I get  first darcs, then watching launchpad, I select to take a look at bzr).

Don't remember if is the one used in kernel, anyway, searching I found this [mercurial project]("http://video.google.com/videoplay?docid=-7724296011317502612") a video presentation at google.

---

### Post by kentl on 2007-10-30
I started by looking at Darcs as well. What got me looking at Mercurial instead was the exponential time commits, which I hear happen for Darcs users. And also that I'd like Windows developers to be able to use it, and I hear Darcs isn't that focused on platform independence.

I hear two things that is. What's your feeling about those? Any problems?

---

### Post by hecato on 2007-10-30
mmm, havent used darcs on Windows but I think there is exe there, it is write in Haskell (IIRC) thus somewhat portable via GHC I guess.

About the exponential, yes is something that I care, but I don't have such large projects hehe or large history, also the workaround I gues will be make checkpoints (I guess), and being something know by the nature of the program, I guess people is trying to solve that. Is only enought for me ;).


What I care most when developing with windows users is to use the same coding (UTF-8), and also follow some rules of indentation, spaces and things like that, if not you will get some extra nonsense differences (specially when you not only use ASCII characters in comments, being the program write in other lang).

---


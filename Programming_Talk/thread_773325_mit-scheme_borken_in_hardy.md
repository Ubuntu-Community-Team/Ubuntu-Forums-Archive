---
title: "mit-scheme borken in hardy?"
date: 2008-04-28
forum: Programming Talk
---

### Post by the2ndgenesis on 2008-04-28
Hey everyone, I have a brief question on my inability to run mit-scheme since upgrading to Hardy. It's one of the few issues I've had since the upgrade, so I'd love to get it solved as soon as possible...

Running from the console yields the following results:

```
administrator@#######:~$ mit-scheme
Largest address does not fit in datum field of object.
Allocate less space or re-configure without HEAP_IN_LOW_MEMORY.
```

And emacs:
```
Largest address does not fit in datum field of object.
Allocate less space or re-configure without HEAP_IN_LOW_MEMORY.

Process scheme exited abnormally with code 1
```

Googling has done nothing to help the issue or enlighten me about its cause. Could anyone shed some light on what might be causing this to happen? I'd love to get back to working on SICP...

---

### Post by LaRoza on 2008-04-28
I will check it out. What version of mit-scheme is it?

It does it for me also. Scheme43 works though. (I know, not exactly the same, but if you don't need mit-scheme, it may be a suitable replacement until mit-scheme is fixed)

Bug Report: [https://bugs.launchpad.net/ubuntu/+source/mit-scheme/+bug/217792](https://bugs.launchpad.net/ubuntu/+source/mit-scheme/+bug/217792)

---

### Post by the2ndgenesis on 2008-04-28
> **LaRoza said:**
> What version of mit-scheme is it?

I got rid of my old version and did a fresh install from here:
[http://packages.ubuntu.com/hardy/devel/mit-scheme](http://packages.ubuntu.com/hardy/devel/mit-scheme)

Hope that helps.

---

### Post by LaRoza on 2008-04-28
> **the2ndgenesis said:**
> I got rid of my old version and did a fresh install from here:
[http://packages.ubuntu.com/hardy/devel/mit-scheme](http://packages.ubuntu.com/hardy/devel/mit-scheme)

Hope that helps.

I editted my post, there is already a bug report on this (I just found it)

Did that version work?

---

### Post by LaRoza on 2008-04-28
I am build it from source. It will take a while. I'll let you know.

---

### Post by the2ndgenesis on 2008-04-28
> **LaRoza said:**
> It does it for me also. Scheme43 works though. (I know, not exactly the same, but if you don't need mit-scheme, it may be a suitable replacement until mit-scheme is fixed)

Scheme48 installed fine. Now the only issue is to get it running in emacs, which I can figure out on my own.

Thanks for the help LaRoza :)

---

### Post by LaRoza on 2008-04-28
> **the2ndgenesis said:**
> Scheme48 installed fine. Now the only issue is to get it running in emacs, which I can figure out on my own.

Thanks for the help LaRoza :)

No problem. I recently installed Hardy, and forgot to install Scheme. Thanks for reminding me. I used scheme48 though, and only installed mit-scheme for the first time now.

It says the building of it takes about an hour (on fast hardware and lots of ram, which I have). 

Emacs is evil, use Vim.

EDIT: thanks for the 600th thanks. I only noticed because someone made a thread about me and my beans in the Cafe...

---

### Post by the2ndgenesis on 2008-04-28
> **LaRoza said:**
> Emacs is evil, use Vim.
Somehow I knew editor wars would creep into this thread... :)

> **LaRoza said:**
> thanks for the 600th thanks
No problem.

---

### Post by LaRoza on 2008-04-28
> **the2ndgenesis said:**
> Somehow I knew editor wars would creep into this thread... :)


No war. Statement of fact.

---

### Post by CptPicard on 2008-04-28
> **LaRoza said:**
> 
Emacs is evil, use Vim.


Writing Lisp outside of an appropriate Lisp environment is useless, you lose half the sense of doing Lisp in the first place. I doubt vim has suitable Scheme or Lisp modes like Emacs does... try out SLIME on Emacs to get a feel of what I'm talking about.. :)

---

### Post by LaRoza on 2008-04-28
> **CptPicard said:**
> Writing Lisp outside of an appropriate Lisp environment is useless, you lose half the sense of doing Lisp in the first place. I doubt vim has suitable Scheme or Lisp modes like Emacs does... try out SLIME on Emacs to get a feel of what I'm talking about.. :)

Never.

---

### Post by CptPicard on 2008-04-28
> **LaRoza said:**
> Never.

[SIZE="6"]**-1**[/SIZE]

:(

---

### Post by LaRoza on 2008-04-28
> **CptPicard said:**
> -1

:(

We all have standard and areas where we won't budge. Logical or not, that is life.

Like you not admitting that the Borg are supreme...

(It is still compiling...)

---

### Post by Glaxed on 2008-04-28
Geany FTW!
Down with the vims and macx!
[http://geany.uvena.de/images/geany_main.png](http://geany.uvena.de/images/geany_main.png)
[http://geany.uvena.de/images/geany_plugins.png](http://geany.uvena.de/images/geany_plugins.png)

It's fast (way faster than gedit for shure, what a terrible default text editor), full of features, and easy... Try it!

---

### Post by LaRoza on 2008-04-28
[http://www.gnu.org/software/mit-scheme/liarc-build.html](http://www.gnu.org/software/mit-scheme/liarc-build.html)

I did this, and it works.

It takes a while, it just finished.

Good luck!

Run with: /usr/local/bin/mit-scheme

---

### Post by cphmit on 2008-05-03
See [http://ubuntuforums.org/showthread.php?t=778034]("http://ubuntuforums.org/showthread.php?t=778034") for an explanation and workaround for the mit-scheme problem.

---

### Post by LaRoza on 2008-05-03
> **cphmit said:**
> See [http://ubuntuforums.org/showthread.php?t=778034]("http://ubuntuforums.org/showthread.php?t=778034") for an explanation and workaround for the mit-scheme problem.

Thank you for the assistance. You are a developer of this project?

I will add it to the sticky for future users.

---

### Post by cphmit on 2008-05-03
> **LaRoza said:**
> Thank you for the assistance. You are a developer of this project?

I will add it to the sticky for future users.

Yes, I'm the primary author of MIT/GNU Scheme, as well as the GNU maintainer for the project.

---

### Post by LaRoza on 2008-05-03
> **cphmit said:**
> Yes, I'm the primary author of MIT/GNU Scheme, as well as the GNU maintainer for the project.

Thanks for the help :-)

Glad to have you on the forum.

---


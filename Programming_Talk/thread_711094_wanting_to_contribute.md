---
title: "wanting to contribute"
date: 2008-02-29
forum: Programming Talk
---

### Post by miesnerd on 2008-02-29
Ive been using Ubuntu and other various forms of Linux for the last two years. Now, as an intermediate user of linux, I'd like to add a hobby-- I want to give back in ways more than testing. Nothing wrong with testing, but I have ideas, and I dont want to suggest them and hope someone does them for me. I want to undertake a project to learn.

What project?
I want to add modules to network- manager (this is one idea, but just an example).
Specifically, I want to have a mix of wicd's features and stability, with scripts, but with network manager's look and usability.  Additionally, I want a script that  monitors wifi connections, and when stats go below a certain threshold, automatically retries to reconnect continually until this is accomplished.

I realize that is a whole mouthful, but tell me, where do I get started-- I have been playing with python the last few days. 

Also, can someone give me a run-down of how this process were to work?

Thanks
Miesnerd

---

### Post by miesnerd on 2008-02-29
and btw, yes, I understand Wicd has a tray applet. I want to focus on network manager because I prefer the interface, as well as it being what comes as default for many distros.

---

### Post by mssever on 2008-02-29
You didn't say how much programming experience you have, but you'll need a fair bit before you can delve into NetworkManager. Some of their documentation is flatly wrong (I got burned by that), and NM isn't in Python. I have no idea what's involved in extending NetworkManager like you propose. You'll have to look at the source code and see.

Once you've gotten started, try sending patches to the mailing list.

---

### Post by imdano on 2008-02-29
You'd need a pretty good working knowledge of C to contribute to NetworkManager.  Wicd, on the other hand, is written entirely in python.  If you don't have much experience coding, you might find it difficult to start making the kind of changes you're talking about.  NM's codebase is pretty large, so it will probably take a little while to get familiar with where stuff is and what it does.  You're probably better off trying to change/fix/add something small until you get comfortable with it.  Check out [this page](http://www.gnome.org/projects/NetworkManager/developers/) for information about NM developement.

If you change your mind, maybe look into helping out with wicd.  The project is a lot younger, so there's more work to be done, and there's considerably less code to work through.  Plus you know python.  (And we could use some help on the development end :)).

---


---
title: "Is there a GUI find&amp;grep tool?  Should I make one?"
date: 2010-08-11
forum: Packaging and Compiling Programs
---

### Post by tbrminsanity on 2010-08-11
After another annoying attempt to try search my system for files, I had to open up the terminal and use a combination of find and grep to get what I want.  Every time I go to the terminal to do what I perceive is a fundamental task to the OS (ie searching for a file), I feel there has been a failure in usability.  I don't think the GUI search should be this inept and slow.

Is there a utility in the repos that utilizes find and grep (or at the very least has similar speed as find and grep)?  If so what is it's name?
If not, would people be interested in a project that utilized find and grep but has a GUI front end for usability?

---

### Post by cj.surrusco on 2010-08-11
What's wrong with the file search under the Places Menu? I just tested it and it seems just as fast as find and grep.

---

### Post by Nick_Jinn on 2010-08-11
Hmmm. It might be redundant, but if you are looking for something to build, do you think you could make a generic 'GUI' that can be customized and any button can be programmed with commands of your choice and labeled, all through the GUI without using the command line.?

That would make it really easy for people to build GUI tools for people....if it could pack itself into a deb file, that would be even better. If somebody cant figure out hot to fix something with the command line, just spit out a GUI for it and send it to them via email.

---

### Post by Paddy Landau on 2010-08-12
> **Nick_Jinn said:**
> ... do you think you could make a generic 'GUI' that can be customized and any button can be programmed with commands of your choice and labeled, all through the GUI without using the command line.?
Well, the repository does have zenity, which is a GUI front-end for scripts. It's not brilliant, but it's usable.

You can write a script, use zenity for the GUI, and it can be run using Alt-F2 or from a launcher.

---

### Post by NFblaze on 2010-08-12
If you make one, do make sure that the program lets you see the exact CLI equivalent that was used somewhere in the GUI.

---

### Post by tbrminsanity on 2010-08-16
> **cj.surrusco said:**
> What's wrong with the file search under the Places Menu? I just tested it and it seems just as fast as find and grep.

It is not just as fast.  Maybe if you have a small computer, but I have a server and it takes 3-8 times the length to use the GUI search bar instead of Find and Grep.

---

### Post by MrQuincle on 2010-08-20
> **tbrminsanity said:**
> It is not just as fast.  Maybe if you have a small computer, but I have a server and it takes 3-8 times the length to use the GUI search bar instead of Find and Grep.

1. You have a X on the server?
2. If people go for speed, they use the CLI anyway.
3. To go for speed you should use locate (and regularly run sudo updatedb), why searching through the entire system all the time?

---

### Post by tbrminsanity on 2010-08-20
I love my GUI.  Every time I have to open up a terminal to do something that should be easy to do in the GUI, there has been a failure of usability.  I really don't care how the GUI searches through my system (via indexing, or just a direct use of the Find command) I just expect to have similar performance benchmarks.  Is this too much to ask for?

---


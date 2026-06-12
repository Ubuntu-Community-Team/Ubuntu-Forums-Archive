---
title: "code monkey question!"
date: 2011-05-09
forum: Programming Talk
---

### Post by jadedcritic on 2011-05-09
So, hey, I'm going to be upfront.  I'm a ridiculously amateur programmer, but what can I say, one attempt at a time!   

Honestly, I LOVE the concept of your programming challenge, and I'm probably going to start lurking those threads, but for the moment I'm kinda banging my head against a brick wall on a shell script I'm trying to do, so I thought I'd ask for advice.

I've been trying to piece together a bash shell script to organize my music library.  (3 or 4 distinct file types in various directories).   The problem such as it is, is it has to be able to fetch *.mp3 files recursively from any location in the filesystem, and move them.  I was experimenting with using ls -laR, but ended up rejecting that because it doesn't return relative path, so I suspect what I need to do is set up some sort of for/while loops that takes the results of find . -name '*.ogg' -print.

Honestly, if it weren't for that ***recursively*** part, I'd just do, for tmp in *.ogg; mv $tmp /home/me/Music/Ogg/; done

(Yes, I know I could just do a GUI search, and cut/paste the results, but that would kind of defeat the point.  Kinda sick of staring at someone else's code which I don't understand, want to write some of my own which I don't understand.)

Anyway, all advice is welcome, but my own skills are modest at best, I don't know much about anything yet outside of bash & python, so I'd appreciate it suggestions could be made in one of those two forms.  Thank you :)

---

### Post by jadedcritic on 2011-05-09
Quick apology for what amounts to an extraneous post.  I was a little brainfried this afternoon - wasn't seeing the forest for the trees.  Got home and found a one-line solution to what I want to do in a bash cookbook.

---


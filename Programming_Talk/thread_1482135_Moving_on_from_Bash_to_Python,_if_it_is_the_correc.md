---
title: "Moving on from Bash to Python, if it is the correct language to use"
date: 2010-05-13
forum: Programming Talk
---

### Post by prupert on 2010-05-13
Hi

As the topic say, I was thinking of moving from bash programming to Python, to further my knowledge of programming. I did a bit of googlywoogling but haven't found much, apart from this post: [http://ubuntuforums.org/showthread.php?t=978218](http://ubuntuforums.org/showthread.php?t=978218) which seemed to get into some god awful argument about what was and what was not asked, rather than the actual topic in hand. I also found this: [http://magazine.redhat.com/2008/02/07/python-for-bash-scripters-a-well-kept-secret/](http://magazine.redhat.com/2008/02/07/python-for-bash-scripters-a-well-kept-secret/) which indicates that it is something that isn't that hard to do.

Basically, I know a fair bit of bash now, after writing simple scripts for a year or so. I was thinking I would like to learn, what I perceive to be, a more powerful and flexible language and from what I have read, Python is the way forward (especially because it is supported on my Android phone, and my two favourite apps (Boxee and XBMC) use Python plugins).

Whilst a number of my bash scripts perform lots of system shenanigns (like automatically updating to the latest SVN / GIT versions of ffmeg and x264) which I believe Python isn't very good at and bash is best at, my main bash script that I am keen to program in Python is intended to be a frontend (via the CLI at first) to ffmpeg. So far, the bash script simply runs ffmpeg on a specified file and then manipulates the stdout output from ffmpeg to show you a nice easy to understand progress indicator and ETA. Since this mostly involves processing stdout output (which is first passed to a text file) I am assuming Python should be fairly good at this, since from what I understand, Python is very good at manipulating data and text. Once I have this working in Python, I would then like to add more features, like the ability to chose from various pre-sets for ffmpeg, and to run it on a whole directory of files and then finally to have a nice GUI that I can use in Ubuntu, so there is no need to use the CLI if you don't want to...

So, on to my question. Does this sound like the kind of thing Python is good for? If not, then what should Python be used for and what would be a better language to use to make such a program as described above (and why) bearing in mind I am still a noobie programmer am doing this for a hobby?

Cheersio for your views.

---

### Post by roccivic on 2010-05-13
It really looks like you've already made up your mind...

As far as GUI for python goes, you might want to look at PyGTK.

---

### Post by prupert on 2010-05-13
Oh, I only chose Python since I have heard it is fairly easy to learn and quite flexible. I am totally open to all options. 

I suppose my question should be, what is Python good for and what is it not so good for?

---

### Post by roccivic on 2010-05-13
Since it's interpreted rather then compiled, it's slow and therefore not good for raw number crunching. A _properly written_ C program will outperform a Python program every time.

In your case the number crunching will be done by ffmpeg, so it's a good option for writing just the GUI.

---


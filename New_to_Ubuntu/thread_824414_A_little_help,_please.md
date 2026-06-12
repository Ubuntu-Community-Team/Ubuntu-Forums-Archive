---
title: "A little help, please"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Saturn357 on 2008-06-10
Well, I've been using Linux for a few months now, and I have to say that I enjoy it, except for all the CLI prompt things, as they seem to never work with me.

But, long story short, there are some things I am having trouble with. For instance, why can't I find a decent Movie Maker. All I want to do is use some of my .gif and .jpeg files to make movies to the background of music and maybe add some .mpg files along with them. I've tried Kino, Pitiviti, Open Movie Editor and 5 others and none of them can do what I wanted. With Windows Movie Maker, I was able to use it instinctively. With the others, it seemed like you had to learn how to program.

Downloading things are a challenge for me, as I know nothing about source code, compiling or anything like that. And, when I cut and paste from the website, it usually gives me some error message that I don't know how to fix.

I think that's it for right now. That, and the fact that the program names look totally random, so it's hard for me to tell what does what. Other than that, I'm learning. Maybe one of these days I'll learn that shell. 

So, can anyone help me?

---

### Post by rockerphil on 2008-06-10
in your case my suggestion for movie making is to dual boot your machine or at least keep a Windows machine around so that you can make your movies the way you're use to. but as far as Linux being harder to use it's proven to be false for me, it's not harder, you just have to learn how to do things differently.

now, on to installing software. the easiest way is to install from the Ubuntu repositories using sudo apt-get install in the command line. so say i wanted to install the instant messanger client Pidgin. i'd simply open up a terminal and type this

sudo apt-get install pidgin

and it will download and install the program for me from the cental ubuntu repositories. if you can't seem to find the program in the repos then try to find a .deb file for the program you wish to install. i.e. FrostWire comes in a .deb format. you can install these files in the terminal with the command "sudo dpkg -i <nameoffile>"

i hope this information proves usefull. much luck to you,




Phil

---

### Post by hyper_ch on 2008-06-10
Use a descriptive topic title and not a generic "noob here" or "need help". You know, most people posting here want to get some help and you should support those, that provide help by indicating what the problem is about in the title.

---

### Post by marufaberlin on 2008-06-10
I know this problem pretty well, and would recommend the console program [ffmpeg]("http://ffmpeg.mplayerhq.hu/"), which, even though it is not intuitive, provides a powerful movie editor. Sadly, it has no GUI, but I am currently writing one.

I know that there's always the rule that no program should shoot ahead of it's goal, but the 3D renderer/modeler blender also includes powerful features, such as a title editor, as well as a sequence editor, which would be ideal for your purposes. You just need a little time to get aquainted with the GUI.
[]("http://ffmpeg.mplayerhq.hu/")

---

### Post by Xiong Chiamiov on 2008-06-10
Movie editing is rather weak on Linux currently.  There's nothing we can do about that, except make it better (for those of us who can program at a level that's useful for that sort of thing, meaning, not me).  Dual-booting is a perfectly acceptable solution; we won't lynch you if you use Windows.

Installing software can be either very easy or rather difficult.  If something is in the repositories, then you just have to use Synaptic - it even downloads the packages for you (yay!).  Installing .debs is also rather simple, just requiring a double-click and press install.
When you're looking at software that you need to compile, you should determine whether or not it really is for you.  There are many applications available for Linux that are not for other platforms, but that perhaps are a bit difficult to get working properly.  If you're using Linux casually, then avoid those.  If you enjoy a good trouble-shooting session of silently (or perhaps not!) cursing something or the other, but silently thanking them for giving you this cool new toy, then go ahead and play with things.  I'm one of the latter, but most people aren't, and end up just getting frustrated.  My advice is to just ignore the fact that said application exists in the first place.

Now, that said, compiling from source isn't really that difficult.  If you're interested, [here's a well-written guide]("http://monkeyblog.org/ubuntu/installing/#source").

---


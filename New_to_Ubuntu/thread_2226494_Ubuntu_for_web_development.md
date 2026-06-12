---
title: "Ubuntu for web development"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by websquad on 2014-05-27
I'm a Ubuntu novice.  Background is Windows (and DOS's prior to that) starting with Windows 286.  Running Windows 7 on my main production machine, which is used for website creation & maintenance.

**Objective:** Configure my Ubuntu 14.04 LTS system for website work (I particularly like the "LTS" aspect of this Ubuntu release).

**What I have:** Dell Optiplex 745, Core 2 CPU 6400; 4GB RAM (could be upgraded to 8GB), one 19" monitor (I would add two more -- it's just the way I work).  *Machine is "snappy" -- I like the performance.*

**Apps:**  So far, FilZilla and jEdit (I'm a hand coder).  I just discovered that gEdit was loaded.  Yikes.  Maybe I found the editor I want... [COLOR="#8B4513"][SIZE=2]I'd like a text editor that supports the HTML/CSS syntax (syntax highlighting).[/SIZE][/COLOR]  I'd also like a photo editor that will do the basic stuff I do in Photoshop CS5.

**Questions: **

[LIST=1]
[*]1 Am I on the right track?  Any suggestions.
[*]2 Do I really need to learn all this command line stuff?  I'd rather not!
[/LIST]

***(This is my first post.  I hope I've not broken any forum protocols!)***

---

### Post by gijs2 on 2014-05-27
> **websquad said:**
> I'm a Ubuntu novice.  Background is Windows (and DOS's prior to that) starting with Windows 286.  Running Windows 7 on my main production machine, which is used for website creation & maintenance.

**Objective:** Configure my Ubuntu 14.04 LTS system for website work (I particularly like the "LTS" aspect of this Ubuntu release).

**What I have:** Dell Optiplex 745, Core 2 CPU 6400; 4GB RAM (could be upgraded to 8GB), one 19" monitor (I would add two more -- it's just the way I work).  *Machine is "snappy" -- I like the performance.*

**Apps:**  So far, FilZilla and jEdit (I'm a hand coder).  I'd like a text editor that supports the HTML/CSS syntax (syntax highlighting).  I'd also like a photo editor that will do the basic stuff I do in Photoshop CS5.

**Questions: **

[LIST=1]
[*]1 Am I on the right track?  Any suggestions.
[*]2 Do I really need to learn all this command line stuff?  I'd rather not!
[/LIST]

***(This is my first post.  I hope I've not broken any forum protocols!)***

I am also a web developer and I love linux to work with, and i've also made it my main engine.

Your questions:
    1. You are, although i suggest using Sublime Text 3 it is a light weight program that supports a bunch of programming languages including HTML/CSS.
    2. You don't need to, but i suggest to learn alteast the basics such as ls, ls -l, chmod cd and maybe vim.

One last suggestion for programming, linux is sensetive about upper and lower cases if you don't use them right your code won't work.

---

### Post by pfeiffep on 2014-05-27
> 2 Do I really need to learn all this command line stuff? I'd rather not!

The command line is not essential, however I suggest familarizing yourself with it to some degree. You have the technical background to grasp CLI.
Many times instructions are provided using CLI - if in doubt of the exact syntax provided use google. 
Essentially don't try to learn the entire Linux command structure learn the commands as you need them!

---

### Post by Impavidus on 2014-05-27
1: Many text editors support syntax highlighting. I have used nedit and gedit, nowadays mostly vim for writing TeX, PostScript, C, bash. Try it, you'll either hate it or love it. For image editing there is gimp. The experts say it's not as good as photoshop, but most people won't notice.

2: You don't *have* to use the command line, but it gives direct access to many components of the system normally hidden under the GUI. As a result, the command line often provides a faster way to the solution of your problems, if you know the way.

---

### Post by ritwikraghav14 on 2014-05-29
You may use gedit or bluefish editors for syntax highlighting and of course GIMP (as Impavidus suggested). But get used to command line for the reasons in above posts. I don't think it will be any tough for you as you said:
> (I'm a hand coder).

---

### Post by jakke1975 on 2014-05-29
+1 for bluefish. It's completely free software. Sublime Text may be free as well, but for me it kept nagging for registration even though it worked.
I always liked bluefish, but, I had to get used to it a bit.
Sublime and Bluefish are a little bit different in concept (bluefish more dreamweaver-like whereas Sublime looks more like a regular editor like Notepad++)

---

### Post by mastablasta on 2014-05-29
there are many text editors.default ones are preety good. there are also IDE for more programing projects

what command line stuff do you think you need to learn and why?

---

### Post by mcduck on 2014-05-29
You'll probably want to add the LAMP stack to your list of software, if you haven't done that already.

For editors, use what you like. This far I've used Gedit of rmost of my web development, but recently I made the move to Atom (while gedit has plenty of great plugins avalable, Atom has even more and since it's based on web technologies it's quite easy for a web developer to customize it even more...)

What comes to learning command-line, it really depends on what you want to do. However learning how to do the server management side of things from CLI makes sense, as command-line is what you'd most commonly use on a real-life production server, and CLI access through SSH is by far the most common way to manage remote servers... Any other command-line use (outside of the very absic stuff) is really up to you and while it might help, it's not really relevant from we development point-of-view.

For Photo/bitmap editor, Gimp does excellent job. I would also recommend picking up Inkscape for any graphics work, it gives you cleaner and more scalalbe vector graphics which is often handy. Plus SVG files are part of the web standard, and can also be scripted and edited with common web tools like Javascrpt and PHP for some interesting and useful results. And learning some Imagemagick might come handy, even though it's a command-line tool, it's abilities to batch process loads images with quick commands has saved me hours and hours of manual work..

(For FTP, I actually prefer just using the built-in server connection with Nautilus, as that uses Fuse to mount the remote location making all the files available to me to edit on any program just like if they were local files.)

---

### Post by ramzes2 on 2014-05-29
[COLOR=#000000][FONT=Arial][COLOR=#222222][FONT=Arial]I use Sublime Text. Fast and convenient


[/FONT][/COLOR]
[/FONT][/COLOR]

---


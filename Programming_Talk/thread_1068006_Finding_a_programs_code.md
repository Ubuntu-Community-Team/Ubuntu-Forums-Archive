---
title: "Finding a programs code"
date: 2009-02-12
forum: Programming Talk
---

### Post by swappo1 on 2009-02-12
Hello,

I have been studying C for a while and would like to start looking at code for other programs to see how they work and further my studies.  Since linux is open source I would assume that we would have access to the code for all the open source programs.  If this is allowed, is there a way that I could take a program that I use on my computer, like a cd player, and get the code to study it?  If so, how would I go about doing it?  What are some simple types of programs written in C that I could start with?  Thanks for any advice.

---

### Post by Caduceus on 2009-02-12
If you go to a website like sourceforge you can download the code. The program itself doesn't often contain its own source (if you download it the 'traditional' way, you often have to compile it yourself so the source is there)

---

### Post by lykwydchykyn on 2009-02-12
In Ubuntu the easiest way is to use apt-src.  Assuming you have source repositories enabled (they are by default, I believe), you just type:
```

apt-src install packagename

```

And the sourcecode for "packagename" will be downloaded and extracted to its own folder in the current directory.

Not everything is written in C, in fact the repos contain stuff written in just about every language out there.  The kernel and most of the system software is written in C, if I'm not mistaken.

What kind of software are you wanting to study?  System stuff, GUI apps, utilities, services?

---

### Post by swappo1 on 2009-02-12
Hi,

Thanks for the replies.  I am interested in programs that are fairly small and not too complicated to learn how they work.  I was thinking maybe something like a cd player/ripper or some systems type stuff.  At this point I am just trying to learn from programs that are being used by people.  From there I will be able to find put what really interests me.

---

### Post by lykwydchykyn on 2009-02-12
Thinking further about it, you might want to start with examining source for basic console commands; the thing about simple gui programs is that they tend to be mostly glue code to pull together various components from external libraries.  It's harder to make sense of unless you understand those libraries and what they provide.  Of course it takes only a few seconds to download a nominal source package and open it in a text editor, so don't just take my word for it.

---

### Post by geirha on 2009-02-12
coreutils contain many of the small programs you find on unix-systems; ls, mv, cp, cut, chmod, etc.
```
apt-get source coreutils
```

---

### Post by ch0d3 on 2009-02-12
You could try browsing launchpad.net as well.

---

### Post by ssam on 2009-02-12
most projects use a source code manager/revision control system to manage all thier code and all the changes to it. common ones include subversion (svn), bazaar (bzr) and git.

some of them have web access so you can easily look through.

eg
gnome [http://svn.gnome.org/viewvc/](http://svn.gnome.org/viewvc/)
kernel [http://git.kernel.org/](http://git.kernel.org/)

you can also use the the tools to get the latest (or any old) version of the code.

---

### Post by phrostbyte on 2009-02-13
apt-get source hello 
is probably the simplest :o

but you can the source of any package in universe/main very easily using the "apt-get source" command (no sudo)

---


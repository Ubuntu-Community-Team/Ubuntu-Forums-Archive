---
title: "Need help running a perl app."
date: 2007-01-07
forum: Programming Talk
---

### Post by jimw on 2007-01-07
I'm a writer, and I'd like to have a name generator.  Rather than learn programming and re-invent the wheel, I went looking for one on the net.  I'd rather have something that I can run on my own machine, without having to reconnect to the internet every time.

I found one likely-looking app at:

[http://www.ruf.rice.edu/~pound/](http://www.ruf.rice.edu/~pound/)

It's done in perl, and I have perl working on my machine (Dapper).

Unfortunately, I can't seem to make this thing run.  

It was put together way back in 1993, and I wonder if perhaps changes in computers, or even languages, have made it obsolete.

I'd really appreciate any advice anyone can give me on this.

JimW



Unfortunately, the only way I can think of to run it is to load it ito the terminal from a text editor.  When I do that, it gives me a bundle of error messages

---

### Post by phossal on 2007-01-07
This program may not do what you think.

Whether or not this is the right program for you, getting it running should be fairly straight forward. Try to run the program, and then copy and paste the output - the errors - in your next post. It's likely the program expects to use modules that aren't installed on your machine. We need the error messages to help you address those dependencies, or any other problems.

---

### Post by po0f on 2007-01-07
jimw,

I'm assuming you downloaded this file to your Desktop.  From a terminal:
```
[FONT="Courier New"]$ cd ~/Desktop
$ chmod +x perl_script.pl
$ ./perl_script.pl[/FONT]
```

---

### Post by pmasiar on 2007-01-08
> **jimw said:**
> name generator: 
[http://www.ruf.rice.edu/~pound/](http://www.ruf.rice.edu/~pound/)

Thanks for the link. It looks like really easy to be reimplemented in Python. I added it to tasks page to [learn python]("http://learnpydia.pbwiki.com") wiki - maybe someone will have time... Nice task for programming apprentice.

---

### Post by kj1h234lkj1234 on 2007-01-08
> **po0f said:**
> jimw,

I'm assuming you downloaded this file to your Desktop.  From a terminal:
```
[FONT="Courier New"]$ cd ~/Desktop
$ chmod +x perl_script.pl
$ ./perl_script.pl[/FONT]
```

Or just:

perl scriptname.pl

:)

---

### Post by jimw on 2007-01-08
Thanks for the quick replies.  Since the first post, I've spent a few hours on Google, and found out how to run a perl script.

However, it still doesn't work.

Here's what I put into my Terminal:

/usr/bin/perl /home/jimw/Desktop/Desktop_data/lc-namegenerator

And here's the result:

usage: /home/jimw/Desktop/Desktop_data/lc-namegenerator -[s|#] filename

It seems I've got some little part of it working, but apparently not everything.

As for lacking the modules, yes, unfortunately, the page is done in very small script, and my tired sixty-two-year-old eyes missed an important part of it.

Unfortunately, I can't get any further on it tonight.  I'd have thought there'd be an error message to say that the modules werent available, in whatever wording it used.

Ah, well, I'll look into it further tomorrow evening, between all the other things I have to do.

Thanks again,

JimW

---

### Post by po0f on 2007-01-08
jimw,

Looks like you need to download one of the [datasets](http://www.ruf.rice.edu/~pound/#datasets) for using this script.  Just specify the filename of the dataset you choose to download when you run the script:
```
[FONT="Courier New"]$ perl /home/jimw/Desktop/Desktop_data/lc-namegenerator english[/FONT]
```

(Assuming you downloaded the [english](http://www.ruf.rice.edu/~pound/english) dataset.)

---

### Post by pmasiar on 2007-01-08
> **jimw said:**
> the page is done in very small script, and my tired sixty-two-year-old eyes missed an important part of it.

One of main reasons I use Firefox is Ctrl+ which will increase font size from ridiculously small used by web designers with perfect sight to size I can comfortably read. Hit Ctrl+ couple times, and almost any page becomes readable :-)

---

### Post by jimw on 2007-01-09
Thanks to everyone who pitched in.  I've got it working, though it needs a lot of sorting out afterwards to pull out things that might make names from all the rest.  (Not a complaint, a comment).

Some years back, someone did a langmaker program for Windows which had several settings as I recall, for various types of languages, those that allowed multiple-consonant clusters, those that didn't, and everywhere between.  

Unfortunately (sort of:) ) I run a Windowless machine now.  I'd love to see someone do a program like that for Ubuntu, sometime.

Thanks again,

JimW

---


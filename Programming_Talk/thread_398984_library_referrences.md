---
title: "library referrences"
date: 2007-04-01
forum: Programming Talk
---

### Post by doddi on 2007-04-01
Hi People,

I am need of a little newbie help.
I am (like most people) converting from windows to linux and I am a keen programmer in C and C++, but I am used to the point and click of visual studio.

Is there an easy way to find a referrence to a function I am looking for, a simple help /search facility similar to what you find in visual studio.

As an example I am going through the serial port howtos found on various websites and they are referrencing printf/fprintf with file open/close. In visual studio if I want to find out how to open a file I will search for open file and eventually it will take me to the appropriate function(s) with usage example.

I know I could google but I am having to sift through the countless links until I find the answer I am looking for.

Is the a man/info facility for this type of thing? 

Sorry for the long message but I found it hard to get my point across. I just hope some can help.

*edit: From the only response I got I decided to change the title (and rightly so...thanks), I was wondering if there is a command line version to find function referrences as I am starting out just trying to use gedit. I am doing this so that hopefully I will learn more rather than using the big IDE's ...again

thanks

doddy

---

### Post by pmasiar on 2007-04-01
As you just noticed, having your question answered is not simple - there is an art of naming your post in a way that people will understand what you want. You have rather poor name for your post. What you want to ask is, IIUC, which C IDE has good integration with documentation and references, right?

If you named your post like "Advice for C/C++ IDE", it would have better "information smell" and more people would be tempted to read it. :-) All is not lost, is sunday night and action is slow... 

Check stickies for this forum, "how to start" and "favorite IDE"... Well I just checked "how to start" and no advice about IDE beyond VIM - and VIM is not an IDE I would inflict on someone used to VS. :-( After you find your answer, you may want to PM C/C++ authors and ask them to add IDE info - helping the next guy.

Anjuta and Kdevelop are popular choices IIRC - I use Python and Java, did not programmed in C for about 15 years... you need to install also build-essentials. Synaptic is your friend ... :-)

[http://www.google.com/search?q=linux+C%2B%2B+ide](http://www.google.com/search?q=linux+C%2B%2B+ide) suggests also Eclipse - it might be good choice if you plan to play with Java too. Eclipse if bloatware, huge and slow, I know - but has all the features you may ever need and lots of free and proprietary plugins.

Good luck!

BTW when you need small little language to parse some files, generate test datafiles, quick website, or script your test, my favorite language is Python: [http://learnpython.pbwiki.com/HowToStart](http://learnpython.pbwiki.com/HowToStart)

---

### Post by lnostdal on 2007-04-02
```

sudo aptitude install manpages-dev

man -k some_term_here

```

tap q to close man

---

### Post by lnostdal on 2007-04-02
also see: [http://www.gnu.org/software/libc/manual/](http://www.gnu.org/software/libc/manual/)

(you can use aptitude to download an offline version in /usr/share/doc)

---

### Post by samjh on 2007-04-02
> **doddi said:**
> As an example I am going through the serial port howtos found on various websites and they are referrencing printf/fprintf with file open/close. In visual studio if I want to find out how to open a file I will search for open file and eventually it will take me to the appropriate function(s) with usage example.

I know I could google but I am having to sift through the countless links until I find the answer I am looking for.

Fear not!

**[http://www.cppreference.com/](http://www.cppreference.com/)** is the best free reference for standard C and C++ commands, directives, and libraries.

To directly answer your queries regarding printf, fprintf, and file open and close:

printf: [http://www.cppreference.com/stdio/printf.html](http://www.cppreference.com/stdio/printf.html)
fprintf: [http://www.cppreference.com/stdio/fprintf.html](http://www.cppreference.com/stdio/fprintf.html)
fopen: [http://www.cppreference.com/stdio/fopen.html](http://www.cppreference.com/stdio/fopen.html)
fclose: [http://www.cppreference.com/stdio/fclose.html](http://www.cppreference.com/stdio/fclose.html)

Good luck! :)

---

### Post by doddi on 2007-04-03
Thanks for all the replies guys that manpages-dev looks just like what I am looking for. I will give it a go tonight.

Cheers,

doddi

---


---
title: "perl online"
date: 2007-03-10
forum: Programming Talk
---

### Post by evaristegalois on 2007-03-10
I don't know a lot about code and especially not about doing anything online. But I have a little perl script that I wrote (let's say of the "hello world" type) and that I would like to make available online. I have a website and can upload files. Is there something like an online shell where someone else who doesn't know perl could download the .pl file and run it? Any advice?

--evaristegalois

---

### Post by phossal on 2007-03-10
Every Ubuntu user has perl on their system. If they download your program - to their desktop, for example - wouldn't they be able to run it by typing (?):
```
perl ~/Desktop/your_program.pl
```

---

### Post by LotsOfPhil on 2007-03-10
Are you talking about them being able to run it online?

Meaning, they go to [http://yoursite/perl/script.pl](http://yoursite/perl/script.pl) and it shows some output (not the innards of the file)?

If so you need to set up CGI on your server. I forget how to do the details, but you need to tell the server it is okay for people to execute files on it.

---

### Post by pmasiar on 2007-03-10
> **evaristegalois said:**
>  But I have a little perl script that I wrote (let's say of the "hello world" type) and that I would like to make available online. I have a website and can upload files. Is there something like an online shell where someone else who doesn't know perl could download the .pl file and run it? Any advice?

Not sure what you want to accomplish. There are  [many repositories of hello world programs](http://en.wikipedia.org/wiki/Hello_world), not sure if world need one more, but you can try - it certainly will not hurt anyone.

If you publish source code in web page, anyone can download it and run using her owl Perl shell.

> I don't know a lot about code and especially not about doing anything online.

Maybe you may want to learn more before trying to suggest your advice :-)

---

### Post by phossal on 2007-03-10
It just occurred to me that he might mean, quite literally, an *online shell*, much like the one for python. I can't remember the link to the site, but a guy has implemented a python interpreter using Ajax, or something. It's like using the command line from a web page.

The problem, of course, is that most of what you want to do with scripts involves manipulation of files and such, which is impossible in such a fashion. So, while the code might "execute", it would strictly be for show.

[EDIT] This is an example of the [Python Interpreter]("http://www.mired.org/home/mwm/try_python/")

---

### Post by pmasiar on 2007-03-10
> **phossal said:**
> It just occurred to me that he might mean, quite literally, an *online shell*, much like the one for python.

IMHO Perl is more "dangerous" language - in a sense that is is rather simple to create powerful scripts doing dangerous things. Perl is not called "swiss army chainsaw" for nothing :-) You would need to filter out some too powerful operators, like <>. My feeling is that making online shell like that would be way beyond a nice learning project for someone who wants to share his "hello world" program in Perl :-) And sandboxing it to restricted area to make it secure would be another challenge - some jails or chroots or something.

BTW evaristegalois: where is the code you want to share? Can we see it?

---

### Post by phossal on 2007-03-10
> **pmasiar said:**
> IMHO Perl is more "dangerous" language - in a sense that is is rather simple to create powerful scripts doing dangerous things. Perl is not called "swiss army chainsaw" for nothing :-) You would need to filter out some too powerful operators, like <>. My feeling is that making online shell like that would be way beyond a nice learning project for someone who wants to share his "hello world" program in Perl :-) And sandboxing it to restricted area to make it secure would be another challenge - some jails or chroots or something.

BTW evaristegalois: where is the code you want to share? Can we see it?

I agree. The whole idea makes me shudder. Horrible. ;) Maybe he has a lot of free time to do nothing, and wants to create a system for teaching beginners perl?

---

### Post by slavik on 2007-03-10
ssh in a chrooted environment ...

---

### Post by evaristegalois on 2007-03-10
just to clarify: yes, you are right. I have a perl script and want people (in my class) to be able to run it online. They probably have windows machines and know nothing about perl. It's a bit more involved than "hello world" and has to do with posterior probabilities calculated from outcomes of coin tosses. In the meantime, the cgi idea sounds most promising to me. Or should I learn python? Is there a simpler way to do this in python?

--evaristegalois

---

### Post by pmasiar on 2007-03-10
> **evaristegalois said:**
> just to clarify: yes, you are right. I have a perl script and want people (in my class) to be able to run it online. They probably have windows machines and know nothing about perl. It's a bit more involved than "hello world" and has to do with posterior probabilities calculated from outcomes of coin tosses. In the meantime, the cgi idea sounds most promising to me. Or should I learn python? Is there a simpler way to do this in python?

now we are talking business.:-)  You want web front-end for your simple program so other people can *use* it easily without downloading (or even much understanding). 

Doing it in Perl is not harder than Python - easier even, if you already know Perl. CGI is new module you need (on top of modules you already use, if any), and some HTML for forms. Looks like you need only one script and one form: get params if any, calculate and print results, and ask for more input - then resubmit to self. Straightforward.

There are many Perl/CGI tutorials, I have one for Python [here](http://ubuntuforums.org/showthread.php?t=332041), you can use it as inspiration - adapting it for Perl should be trivial.

You can even make your "calculating" code into separate module and make it accessible (publish simply as webpage text), so people can save the page, download/install Perl and try it. But they will try it on their own computers, not yours. Or they can use your copy without ability to tweak it (beyond parameters you provide).

---

### Post by evaristegalois on 2007-03-11
thanks! i'll have a stab at it.

--evaristegalois

---


---
title: "packaging doesn't work in ubuntu"
date: 2014-10-23
forum: Packaging and Compiling Programs
---

### Post by baltic on 2014-10-23
According to the [guide]("http://packaging.ubuntu.com/html/packaging-new-software.html"), the lines 
```
$ sudo apt-get install dh-make
$ bzr dh-make 
```
should lead to something else than:
```

bzr: ERROR: unknown command "dh-make"

```
So, how is packaging really done?

---

### Post by thibaud-ecarot on 2014-10-24
hello baltic,

The command with dh-make package is dh_make.

You have to use this command :
```
dh_make -e [EMAIL="yourmailaddress@email.tld"]yourmailaddress@email.tld[/EMAIL]
```

And this command return :
> Type of package: single binary, multiple binary, library, kernel module or cdbs?
[s/m/l/k/b]
[FONT=arial]
[SIZE=2]I **ho[B]pe th[B]at [B]thi[B]s answers y[B]our question**[/B][/B][/B][/B][/B][/SIZE][/FONT]

Have a nice day.

---

### Post by baltic on 2014-10-24
I don't really get it. I have a source code, and would like to make a package from it. The official guide shows the way which does not work.
Is there any other guide, how to do that on ubuntu? what is that dh_make suppose to mean and how my email related to packaging at all?

---

### Post by thibaud-ecarot on 2014-10-25
Hello baltic,

So i will write an example for you. You have a little program with executable, simple HelloWorld. Before, the packaging, you must check your program with simple command that you already have :
Simple example, Helloworld, example of compilation of your program
```

./configuremake
make install

```

Then you have a simple "Hello" that is your executable. Good, you have a very beautiful program.

After that, it's more difficult. You must install dh-make package and create simple archive
```
sudo apt-get install dh-make bzr-builddeb

bzr dh-make hello 2.7 hello-2.7.tar.gz[COLOR=#222222][FONT=Verdana]
```When your computer ask you for type of package (simple binary, etc...), you can choose, in my example, simple binary.Maybe, you must delete example file like this :```
[/FONT][/COLOR]cd hello/debian
rm *ex *EX[COLOR=#222222][FONT=Verdana]
```
[/FONT][/COLOR]
And after, you can create your package with ubuntu guide.

But this guide doesn't work ?
[http://packaging.ubuntu.com/html/packaging-new-software.html](http://packaging.ubuntu.com/html/packaging-new-software.html)

Explain your procedure, please.

Thanks.

---

### Post by baltic on 2014-10-25
```
sudo apt-get install dh-make bzr-builddeb
```
oh, so it's bzr-builddeb in addition to dh-make, ffs!
Srsly ppl, having bad guides is worse than not having them at all. In the latter case ppl will simply search elsewhere and find a good one. Instead of having frustrating experience with that misguide. And the fact that it is called "official" is a shame really.
 
```
bzr dh-make hello 2.7 hello-2.7.tar.gz
```[COLOR=#222222][FONT=Verdana]
this only leads to:
```
bzr: ERROR: Either run the command from an existing branch of upstream, or move hello aside and a new branch will be created there.
```
[/FONT][/COLOR]

---

### Post by thibaud-ecarot on 2014-10-26
Good morning baltic,

No problem, i try to help you. 

So for this problem, maybe you have to init a bazaar branch with :
```
bzr init
```

Try it and say me.

Thank baltic

---

### Post by baltic on 2014-10-26
> **thibaud-ecarot said:**
> 
No problem, i try to help you. 


Thanks, but that's not the point. I can help myself. I do know how to google and found a guide at debian wiki which actually is comprehensive and works!
If some1 from ubuntu team actually read this, please either rename [this]("http://packaging.ubuntu.com/html/packaging-new-software.html") into "**official misguide**" so ppl will at least be warned and wont waste time on it, or better yet delete it altogether, and only describe there the minor differences between ubuntu and debian packages.

---

### Post by thibaud-ecarot on 2014-10-26
Ok baltic, help you yourself.

Have a nice day.

---

### Post by ian-weisser on 2014-10-26
Well, "some1" should really be you,the person who discovered the problem (and solution). 
That's how open software and documentation works.

Here's how:
> We are always looking to improve this guide. If you find any problems or have some suggestions, please [report a bug on Launchpad]("https://bugs.launchpad.net/ubuntu-packaging-guide"). If you&#8217;d like to help work on the guide, [grab the source]("https://code.launchpad.net/%7Eubuntu-packaging-guide-team/ubuntu-packaging-guide/trunk") there as well.
Source: [http://packaging.ubuntu.com/html/index.html](http://packaging.ubuntu.com/html/index.html)

---

### Post by baltic on 2014-10-26
> **ian-weisser said:**
> Well, "some1" should really be you,the person who discovered the problem (and solution). 
That's how open software and documentation works.


From my experience reporting bugs never works in ubuntu. Already reported dozens of them. Not even one was fixed.
And if for some reason you can't keep up with quality, why not to make the guide smaller? Only describe the differences between debian and ubuntu. Which are minor. The smaller the set, the easier it is to maintain it.
Because again, having such misguides is worse than not having them at all.

---

### Post by ian-weisser on 2014-10-26
> **baltic said:**
> From my experience reporting bugs never works in ubuntu. Already reported dozens of them. Not even one was fixed.

Well, I'm sorry you had that experience. My experience, in both Debian and Ubuntu over the past nine years, has been quite different.
Most of the bugs I filed were fixed. Several were rather low priority and took a few years, but surely fixed they were.
And the couple patches I worked up when I figured out a fix were quickly used. Even on my first try when I got the patch made all wrong - someone helped me do it right, and then accepted it same day.

If you open a new thread in this forum on the new topic, I'm sure many of the gurus here with Ubuntu Bug Squad experience can help you get those bug reports in motion again.

I have found both the Debian and Ubuntu communities to be welcoming,  helpful, and responsive...as long as you approach them constructively.

---

### Post by /ADM on 2014-10-26
> **baltic said:**
> ```
sudo apt-get install dh-make bzr-builddeb
```
oh, so it's bzr-builddeb in addition to dh-make, ffs!
Srsly ppl, having bad guides is worse than not having them at all. In the latter case ppl will simply search elsewhere and find a good one. Instead of having frustrating experience with that misguide. And the fact that it is called "official" is a shame really.
 
```
bzr dh-make hello 2.7 hello-2.7.tar.gz
```[COLOR=#222222][FONT=Verdana]
this only leads to:
```
bzr: ERROR: Either run the command from an existing branch of upstream, or move hello aside and a new branch will be created there.
```
[/FONT][/COLOR]

Wow, just wow..  I checked the official guide:

"bzr-builddeb includes a plugin to create a new package from a template. The plugin is a wrapper around the dh_make command. You should already have these if you installed packaging-dev. Run the command providing the package name, version number, and path to the upstream tarball:

$ **sudo apt-get install dh-make bzr-builddeb**
$ cd ..
$ bzr dh-make hello 2.7 hello-2.7.tar.gz"

What is so complicated about following a terminal instruction?  Of course it is in addition to dh-make, what else does it look like?

---

### Post by baltic on 2014-10-27
> **/ADM said:**
> Wow, just wow..  I checked the official guide:
$ **sudo apt-get install dh-make bzr-builddeb**


Wow they've fixed it! Wow indeed!

> **/ADM said:**
> 
What is so complicated about following a terminal instruction?  Of course it is in addition to dh-make, what else does it look like?

Well make a guess why does it look like that now.  And why in my original post it is cited as:
[B]$ sudo apt-get install dh-make
[/B]Any ideas, Sherlock?

---

### Post by baltic on 2014-10-27
> **ian-weisser said:**
> 
I have found both the Debian and Ubuntu communities to be welcoming,  helpful, and responsive...as long as you approach them constructively.
You seem to be right. If you approach them with caustic comments at ubuntu forums, something may finally get fixed! 

Thanks!

---

### Post by Elfy on 2014-10-27
Closed

---


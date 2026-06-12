---
title: "Easiest C++ compiler/intepreter?"
date: 2007-02-13
forum: Programming Talk
---

### Post by tjtansey on 2007-02-13
What is the easiest C++ compiler/interpreter to learn on?  I've tried to use the KDE stuff, but I can't figure out which one is for what.  I know I can use any text editor to write, but from there I'm lost.

---

### Post by haricharan on 2007-02-13
gcc is a good one...u can download build-essential to get all the dependencies...
```
sudo apt-get install build-essential
```

---

### Post by SuperMike on 2007-02-13
The tool 'g++' is your answer. You can apt-get for it or use Synaptic. Then, pick up a handy little O'Reilly pocket reference guide called C++ Pocket Reference. Also, the Schildt book (McGrawHill Publishers) is a big standard C++ book people refer to.

Also, if you're just learning C++ and have installed g++, perl, and gcc, this handy little download (see link below) will help you run C++ as if it were a script rather than having to worry about compiling all the time. It's great for learning C++.

[http://www.ubuntuforums.org/showthread.php?t=351973](http://www.ubuntuforums.org/showthread.php?t=351973)

---

### Post by tjtansey on 2007-02-13
Where can I get gcc?

---

### Post by Wybiral on 2007-02-13
> **tjtansey said:**
> Where can I get gcc?

[QUOTE=haricharan]
gcc is a good one...u can download build-essential to get all the dependencies...
Code:
sudo apt-get install build-essential
[/QUOTE]

Enter that in the command line...

---

### Post by haricharan on 2007-02-13
i m sorry i didnt read ur post properly....g++ is the one for C++......type this in terminal to get the g++ and other dependencies.....
```
sudo apt-get install build-essential
```

---

### Post by tjtansey on 2007-02-13
I've downloaded all of them but the only ones I can find are the KDE app's.  What the heck does it take to get Synaptic to put this stuff in the menus?

---

### Post by psychicdragon on 2007-02-14
You seem to be a little bit confused. A compiler is not a graphical application, thus no menu entries. It's a command line tool that you need to specify a file for it to compile and it will give you a binary. You can write your code in whatever editor you like. Ubuntu comes with gedit installed, which is good enough.

When you've written some code you can compile it like this (simple example):
```
g++ my_file.cpp -o my_binary
```

You now have a binary file called my_binary (provided there were no compile errors), you can now run it like this:
```
./my_binary
```

If you've never written any C++ before, you should follow a tutorial and then compile the code like this.

---

### Post by tjtansey on 2007-02-14
thankyou I couldn't get that anywhere

---

### Post by po0f on 2007-02-14
tjtansey,

Maybe you are referring to an IDE?  Browse through the sticky at the top of the forum for some suggestions.

---

### Post by tjtansey on 2007-02-14
No it was just one of those things I couldn't find clarification on.  There's loads of tribal knowledge on this forum, but I'm a mere papoose:D  I will say this though, I haven't had this much fun with a computer since I got a trash80 coco for my 10th bday

---

### Post by lnostdal on 2007-02-14
hi, see [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) .. the first writing contains how to get started with plain gcc/g++ under Ubuntu .. while the second writing tells how to get started with an editor and a build-environment ..  any feedback/corrections appreciated (they where written in kind of a hurry) :)

---

### Post by Klipt on 2007-02-14
For books, I'd recommend in addition to those mentioned Bruce Eckel's "Thinking in C++". It's available free on the web.

---

### Post by hod139 on 2007-02-14
> **tjtansey said:**
> I haven't had this much fun with a computer since I got a trash80 coco for my 10th bday
Can I ask a personal question, and feel free to ignore me, but how old are you?  Maybe I'm just getting old (25), but I didn't even get a computer until high school and didn't really start programming until college.

As for your thread title, the standard C++ compiler for linux is g++ which can be installed by the meta-package build-essential (as others have said).  Note however, that you probably don't mean C++ interpreter, they exist but I'm guessing that's not what you want.  Typically with C++, the source code you write is compiled into a machine specific language, not interpreted like other languages.

As for IDEs (if you are looking for a graphical enviroment), I have been using nightly builds of [codeblocks]("http://www.codeblocks.org/") lately, which is still in active development but coming along nicely.

---

### Post by tjtansey on 2007-02-14
[QUOTE=hod139;2155094]Can I ask a personal question, and feel free to ignore me, but how old are you?  Maybe I'm just getting old (25), but I didn't even get a computer until high school and didn't really start programming until college.

I'm 36, and a TRS-80 (trash 80) Color Computer was no picnic.  There was no software to speak of so you programmed everything you wanted in BASIC.  The original BASIC.  1981 did not have many affordable computer options.  Still if I remember right it was under $300.  It, the Commodre64 and the Apple IIe were the bleeding edge for someone who didn't count thier net worth in the 7 digits.

Which package of codeblocks do you recommend?  Keep in mind, it's been close to 25 years since I wrote anything other than a simple script.

And this is a loaded question, should I download "Thinking In C++" as source or HTML?

---

### Post by hod139 on 2007-02-14
For codeblocks. I suggest downloading a [nightly build]("http://forums.codeblocks.org/index.php?board=20.0").  The "stable" builds are years old.  For instance, the most recent nightly is the Feb 11th build, and the [announcement page]("http://forums.codeblocks.org/index.php?PHPSESSID=55933950432b8ff5a67d066c4a112f38&topic=5155.0") contains links to various builds.  The ubuntu package direct link for Feb 11th is [here]("http://prdownload.berlios.de/codeblocks/CB_20070211_rev3592_Ubuntu6.xx.deb").

As for the thinking in C++ book, why download it at all?  Unless you plan on referring to it on a machine without internet access.

---

### Post by tjtansey on 2007-02-15
hod139,  
I tried installing codeblocks today, but tell me what act of god does it take to do it?

---

### Post by hod139 on 2007-02-15
God doesn't have to get involved to install code blocks.  It should be as simple as downloading the latest ubuntu built nightly (as of this posting the [Feb 14th nightly]("http://prdownload.berlios.de/codeblocks/CB_20070214_rev3607_Ubuntu6.xx.deb")) and then double clicking the deb file when the download completes.  That should be it.

---

### Post by tjtansey on 2007-02-15
Oh my God, I just spent the last 2 hrs fighting with everything I could find and missed that!  Any other nuggets you can fill me in on?:lolflag:

---


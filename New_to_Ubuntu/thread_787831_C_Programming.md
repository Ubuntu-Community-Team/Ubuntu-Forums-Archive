---
title: "C Programming"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Oddrey on 2008-05-09
Fair warning: The following post's stupidity may pose a hazard to your brain cells.

I started reading K & R and chugging away on Dev-C++ on windows. I wanted to learn how to do this with ubuntu and without an IDE though, so I figured I'd give it a try. I'm a complete newbifite to ubuntu and all things non-windows, non-pretty gui's, and no hand holding.

I googled around and read a bunch of different replies. One person wrote that I just need to type sudo apt-get libc6-dev into my terminal, someone else said sudo apt-get install build-essential, and someone else said something about a manpages-dev package??? Since I didn't understand any of what these people wrote, I didn't try any of them because I was afraid of blowing up my computer by typing something weird.

What do I type to install what I need and how do I compile and run programs? For that matter, uhh, where do I type and save my code - this text editor application? If so... does the character coding matter?

---

### Post by kpkeerthi on 2008-05-09
You need build-essential. To install, run this command in a terminal window
```
sudo apt-get install build-essential
```

To see what this package offers, see [this]("http://packages.ubuntu.com/hardy/build-essential")

---

### Post by y-lee on 2008-05-09
you definitely need build-essential

```
sudo apt-get install build-essential
```

The other packages you mention might be handy, but build-essentials is necessary.

About any text editor will work, use gedit if you like it. (many programmers use vim or emacs but these are complex so takes time to learn). Save the files wherever ya want to, i usually create folders under my home directory for code.

BTW there are many [IDEs]("http://en.wikipedia.org/wiki/Integrated_Development_Environment") for linux.

---

### Post by Google Spider on 2008-05-09
What kpkeerthi and y-lee said. You need build-essential

If you also want an IDE, then I suggest geany.

```
sudo apt-get install geany
```

---

### Post by spiderbatdad on 2008-05-09
Hi. You can graphically browse to synaptic package manager for build-essential. System>>Administration>>Synaptic Package Manager. Any time you see 'sudo apt-get install (or sudo aptitude install) the program can be found in synaptic. Build-essential is a small suite of programs primarily used for building deb packages, however it also contains some c compilers, and the package is usually necessary to easily handle ./configure files.

The text editor is a fine place to write your code. Then run the terminal to compile ```
gcc your_c++.C -o your_compiled_program
```

Or just running gcc your.C will genereate a file called a.out as the compiled program. The program still need to be made executable ( I believe ) with a chmod a+x command ```
chmod a+x your.C
```

---

### Post by Canis familiaris on 2008-05-09
> **kpkeerthi said:**
> You need build-essential. To install, run this command in a terminal window
```
sudo apt-get install build-essential
```

To see what this package offers, see [this]("http://packages.ubuntu.com/hardy/build-essential")
You need build-essential as kpkeerthi suggested and I assure you that it will not blow your pc. Some people say it is a security risk but still billion times secure than Windows.

---

### Post by Google Spider on 2008-05-09
> **Anurag_panda said:**
> Some people say it is a security risk but still billion times secure than Windows.



build-essential a security risk? who says so? :confused:

---

### Post by TeraDyne on 2008-05-09
> **Anurag_panda said:**
> You need build-essential as kpkeerthi suggested and I assure you that it will not blow your pc. Some people say it is a security risk but still billion times secure than Windows.

A security risk? Could you please explain that? I've never heard anyone say that about build-essential

---

### Post by y-lee on 2008-05-09
build-essential is **NOT** a security risk. The person using the computer could be a security risk and compiling code you found somewhere but have no real clue what it does could be a security risk but build-essential is just a tool to allow you to compile code. No more and no less.

---

### Post by pedro_orange on 2008-05-09
Lol how is build essential a security risk?

It's compilers and libraries.....

You don't need an IDE. Use your favorite text editor to crack on with the coding, and use the command line to compile/link it. Easy.

I tend to use -Wall & -pedantic flags when I compile; but thats it.

K&R is a great old book if you want to learn C.
If you're going to learn C++ and take advantage of the STL; get involved in Koering & Moo "Accelerated C++"

Also check the Programming Talk section for very thorough threads covering most programming FAQs.

---

### Post by Google Spider on 2008-05-09
flash is more dangerous than build-essential

---

### Post by Joeb454 on 2008-05-09
Well we've all decided that build-essential is **not** a security risk. So lets just get back to the topic at hand (i.e. installing it to compile C code :))

---

### Post by Canis familiaris on 2008-05-10
> **TeraDyne said:**
> A security risk? Could you please explain that? I've never heard anyone say that about build-essential

To say the truth I do not really know the details but this I have gathered from the following thread.
[http://ubuntuforums.org/showthread.php?t=635752](http://ubuntuforums.org/showthread.php?t=635752)

---

### Post by Canis familiaris on 2008-05-10
> **Google Spider said:**
> flash is more dangerous than build-essential

+1

---


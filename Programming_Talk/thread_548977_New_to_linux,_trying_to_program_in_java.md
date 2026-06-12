---
title: "New to linux, trying to program in java"
date: 2007-09-12
forum: Programming Talk
---

### Post by Bootes87 on 2007-09-12
Hi all,

I am relatively new to Linux, and trying to migrate to Linux completely. I am taking a Data Structures class that uses java for our programs. Therefor being able to write java programs is a MUST. In Windows I used Textpad to write/compile/run everything worked nice all in one little application. 

Is there some program I can get for Linux that will be comparable to Textpad on Windows??

---

### Post by AlexThomson_NZ on 2007-09-12
Firstly- welcome to the forum! :)

A few suggestions here...

If you indent to stick with Linux (and why wouldn't you!), would pay to learn vi/vim at least enough to be able to edit files, also has syntax highlighting for every type of file, etc.  This might be enough to at least get you started

For 'proper' Java development, there are a couple of options- mainly Eclipse or Netbeans, both are very stong, but might take a little work getting comfortable with, so just start with vi/gedit at least until you are happy enough compiling simple programs and running.

Good luck!

---

### Post by Bootes87 on 2007-09-12
Thanks Alex!

I am familiar with both vi and gedit as far as editing and writing my programs. Now, how do I compile and run my program, I cant find an option for that in ether program

Thanks again!

---

### Post by Lux Perpetua on 2007-09-12
```
$ javac MyClass.java    # compile
$ java MyClass    # run
```By the way, make sure you've installed the Sun Java platform so you're using that, not the inferior GNU implementation. (The package is sun-java6-jdk.)

---

### Post by dwhitney67 on 2007-09-12
> **Bootes87 said:**
> Thanks Alex!

I am familiar with both vi and gedit as far as editing and writing my programs. Now, how do I compile and run my program, I cant find an option for that in ether program

Thanks again!

And you probably won't.  Vim and Gedit are not true IDEs.  They are merely editors.  If you require an IDE, as mentioned previously, Eclipse is probably the most widely used for Java development.

If you want to compile from the command line (and I encourage you to learn this), then a command like the following would do the trick:

[FONT="Courier New"]$ javac myProgram.java[/FONT]

To run it:
[FONT="Courier New"]
$ java myProgram[/FONT]

Of course substitute the .java filename as appropriate for your needs, and when you run the program, ensure that you run your main class.

If you have multiple java files in a directory and they all make up a package, you can compile all using this statement:

[FONT="Courier New"]$ javac *.java[/FONT]

---

### Post by Bootes87 on 2007-09-12
Thanks for all the help so far guys, I wrote a simple Hello World and it seemed to compile fine, but i get errors when trying to run:

jeffrey@Emily:~$ javac JavaTest.java
jeffrey@Emily:~$ java JavaTest
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found

i did as it says and installed 2 from that list already but still nothing.

Thanks again!

---

### Post by glok_twen on 2007-09-12
have you tried installing the sun-java* packages in synaptic?

then type "which java" and it should say i think /usr/bin/java which if you ls will point to the sun jre.

also i'd suggest netbeans. very easy to use and to me in coding java, the ctrl-space function to provide completion options is truly must-have to be productive.

---

### Post by pmasiar on 2007-09-12
very simple and quite powerfull programmer's text editor is SciTE - works on Windoze too.

---

### Post by aitorcalero on 2007-09-12
> **Bootes87 said:**
> Hi all,

I am relatively new to Linux, and trying to migrate to Linux completely. I am taking a Data Structures class that uses java for our programs. Therefor being able to write java programs is a MUST. In Windows I used Textpad to write/compile/run everything worked nice all in one little application. 

Is there some program I can get for Linux that will be comparable to Textpad on Windows??

You need to install java sdk (because you need to compile) and also I would suggest an IDE for java (eclipse), all you need to to is:
```

sudo aptitude install sun-java5-jdk eclipse

```
Then you need to point to the correct java version. By default Ubuntu comes with an GNU Java compiler (not the Sun one) so you need to configure it properly:
```

sudo update-alternatives --config java

```
and select the correct java version (java5 in this case)

Finally if you want to use a lighter java editor, you can use Geany (Homepage: [http://geany.uvena.de](http://geany.uvena.de))

---

### Post by Ramses de Norre on 2007-09-12
> **aitorcalero said:**
> ```

sudo update-alternatives --config java

```

javac will still be the old version after this, you'll want to use **update-java-alternatives** instead, read the man page, I think you need the -l and -s switches (I can't check because I'm not on ubuntu).

---

### Post by bubbalouie on 2007-09-12
I usually use Kate, though I recommend you look at the following "IDE", I used it when I did java at uni', it is fairly light weight, so for a fundamentals course you don't have to spend half your time learning an IDE.

[http://www.jgrasp.org/](http://www.jgrasp.org/)

It is fully cross platform and installed on my Gutsy machine right now, a word of warning with java and ubuntu (I apologize if this is not the case with earlier distros). There is a GNU Java which you should remove using the package manager when you install the sun JDK.

Try the following:

**sudo apt-get remove gcj**

I also removed the other bits that came with it, though a:

**sudo apt-get autoremove**

Should sort you out there.

Good luck, with Ubuntu, and the course, java is a great foundation, though I recommend exploring other languages too when time permits.

---

### Post by steve.horsley on 2007-09-12
You may also want ot look at an editor called geany. It's in the repos, and it's just one step up from a plain text editor.

---

### Post by Coyote21 on 2007-09-12
You could also download the latest version of java from sun's website and convert it into an *.deb package [use this [http://www.debian-administration.org/articles/142](http://www.debian-administration.org/articles/142) it's debian, but ubuntu is based on debian (and you will also use many debian packages if you want to keep your system on the "bleeding-edge" like I do :-D)]. 
For IDE, you could use eclipse, which is multi-platform (java based), and features an excelent support for java and even other languages through plugins. P.S. You will never need to use java console tools again, with eclipse.

---


---
title: "From Borland C/C++  to GCC: where is the help ?"
date: 2009-03-05
forum: Programming Talk
---

### Post by alaya.zied on 2009-03-05
[SIZE="4"]Good morning every one,
I'm a teacher in a high school.
I teach some C/C++ and I wanna to encourage students to work with GCC under Linux (Ubuntu).

I prepared a CD for the software ,using aptOnCd (Geany + build_essential), and I still have a problem.

In Borland C/C++, same in Turbo C, we have a very nice and useful help. This is very important because we can't count on the online (internet) help.

I'm looking for the same functionality under Linux: do we have a help for C/C++ like it's in Borland C/C++ IDE or Turbo C ?[/SIZE]

solution:
I find this package:man2html
browse man pages in your web browser

---

### Post by sujoy on 2009-03-05
man pages

comes preinstalled, example, 
```
man scanf
```

---

### Post by alaya.zied on 2009-03-05
thx sujoy,
I test but:
 man scanf
No manual entry for scanf

I installed gcc-doc

but still have the same response.

using the console is not bad but for new user :/
is there other solution ? 
I remember  ,one time ago under KDE, I found man pages in html. is there any think similar.

---

### Post by rjmoerland on 2009-03-05
The GCC C library (libc) is documented here: [http://www.gnu.org/software/libc/manual/]("http://www.gnu.org/software/libc/manual/"). You can find downloadable documentation in a couple of formats there.

You could also install the glibc-doc package, I believe.
HTH

---

### Post by sujoy on 2009-03-05
err, i am on a different system (not ubuntu) but it seems like

```
sudo aptitude install manpages-dev
```

fixes the manpage issue

---

### Post by alaya.zied on 2009-03-12
to install help , I typed this command:
> sudo apt-get install manpages-dev

so to have the help for printf for example:
> man 3 printf

Do you thing that a beginner student can deal with this ?
With my experience I can say: most of them can't.
any idea please to have a more simpler way.

---

### Post by dwhitney67 on 2009-03-12
I think that a beginner student, can handle typing "man scanf" or whatever in a terminal.

I think that you would be doing a disservice to your students if you encourage them to use an IDE, such as geany.  Teach them the command line; then once they have a grasp of the low-level interface for s/w development, then migrate to an IDE.

I started using Unix when I was 20 years old (back in 1987), and sometimes I had no choice but to rely sometimes on a console (not an x-terminal) to do s/w development.

P.S.  I have noticed that with Ubuntu 8.10, along with "manpages-dev", I also had to install "glibc-doc" to obtain man-page information for library functions such as pthread_create().

---

### Post by jimi_hendrix on 2009-03-12
> **dwhitney67 said:**
> I think that a beginner student, can handle typing "man scanf" or whatever in a terminal.


+1 to that and the learn the terminal stuff...its very easy

---

### Post by jespdj on 2009-03-12
> **alaya.zied said:**
> Do you thing that a beginner student can deal with this ?
With my experience I can say: most of them can't.
any idea please to have a more simpler way.
Hmmm... Select Applications > Accessories > Terminal, and then type in "man scanf". How much simpler do you want it?! If those students are smart enough to learn a complicated programming language like C or C++, don't you think they would be smart enough to type in "man whatever"... :confused:

Otherwise, look at rjmoerland's suggestion: download the [documentation of the GNU C library](http://www.gnu.org/software/libc/manual/).

---

### Post by wmcbrine on 2009-03-12
The other half of the man page system is the "apropos" command. When you don't know quite what you want, try "apropos" first:

apropos -s 3 print

Ah-hah! There it is -- "printf".

---

### Post by CptPicard on 2009-03-12
Are these students beginning programming in general? There may be better approaches than C/C++ (which isn't a language, and teaching it as such will just confuse the beginners more).

Personally, I'd say Python... but any higher-level language would do.

---

### Post by alaya.zied on 2009-03-16
Yes they are.
They study some Algorithmic then C language for the rest of the year.
These are not my choices.
I can add that some of this students didn't touch a PC before.

---

### Post by SeanHodges on 2009-03-16
There is a help utility in Gnome that gives you a graphical view for manpages:

System -> Help and Support

You can type "scanf" into the search box and avoid having to use the terminal altogether.

By default, this utility (called "yelp") opens to a basic Ubuntu user guide; however you can create a application launcher on the student's desktop that provides a shortcut straight to the man page index section. The command you will want to put in the launcher is: 

```
yelp x-yelp-toc:#Man
```

---

### Post by Krupski on 2009-03-16
> **sujoy said:**
> man pages

comes preinstalled, example, 
```
man scanf
```

Not all of them. One must also install "manpages-dev".

---

### Post by sujoy on 2009-03-16
> **Krupski said:**
> Not all of them. One must also install "manpages-dev".

yea well, i realised it and mentioned it in #5 :)

---

### Post by Krupski on 2009-03-16
> **sujoy said:**
> yea well, i realised it and mentioned it in #5 :)

Woops... sorry. Note to self: Read posts first, then reply!  :D

---

### Post by alaya.zied on 2009-04-02
OK, I finally find it :)

I find this package:man2html
browse man pages in your web browser

which allow me to see the help here: [http://localhost/cgi-bin/man/man2html](http://localhost/cgi-bin/man/man2html)

thanks every body.

---


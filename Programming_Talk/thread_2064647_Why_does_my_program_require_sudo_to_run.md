---
title: "Why does my program require sudo to run?"
date: 2012-09-29
forum: Programming Talk
---

### Post by WinterMadness on 2012-09-29
I made a very simple application in QT, all it does is read text from a text box and then transfer it to another text box.

I want to run it by clicking on it, upon finding out that does not work, I went into the command line to run it only to find out that i needed sudo... How can I make it so my applications just run? more importantly, how can i make it so my applications run by clicking on them(kind of like how gui applications are started in windows)?

---

### Post by xb12x on 2012-09-29
Since nobody has answered you yet, I'll try:

Check the owner of the app and its permissions:
If I remember correctly, on Ubuntu running Gnome: with the mouse, right-click your application and select 'properties'. Select the 'permissions' tab. Then click the 'it's executable' box. Also make sure you are the owner (not root). If root is the owner you'll have to use sudo or root to change it. For that see the chown and chgrp commands.

---

### Post by WinterMadness on 2012-09-30
> **xb12x said:**
> Since nobody has answered you yet, I'll try:

Check the owner of the app and its permissions:
If I remember correctly, on Ubuntu running Gnome: with the mouse, right-click your application and select 'properties'. Select the 'permissions' tab. Then click the 'it's executable' box. Also make sure you are the owner (not root). If root is the owner you'll have to use sudo or root to change it. For that see the chown and chgrp commands.

Yeah, I know how to do that. Im just curious as to make sure that a deployed program that I develop does not need super user access in the future. If I make something and send it to them, I want them to be able to either double click it to run it, or just simple type ./myprogramhere

---

### Post by whatthefunk on 2012-09-30
Where is your program located?  Does it have any dependencies that require sudo?

---

### Post by hakermania on 2012-09-30
I'm developing in Qt and I never had problems like this.

Be sure that you have read/write access to the parent folder of your application's executable!

---

### Post by WinterMadness on 2012-09-30
> **whatthefunk said:**
> Where is your program located?  Does it have any dependencies that require sudo?

It was in my downloads folder, I sent it over email to my other computer just to see how it worked.

It was the most basic Qt application you can think of aside from hello world

---

### Post by spjackson on 2012-09-30
You haven't said what happens when you try to run your program without sudo. How are you trying to run it? Do you get an error message? If so what is it?

---

### Post by WinterMadness on 2012-09-30
if I try to click it to run, I get an "open with" dialog

in the terminal i get permission denied

    4096 Jul 18 19:06 vlc-2.0.3                                                                                                                             
joe@kjoe:~/Downloads$ ./"untitled (1)"                                                                                                                                             
bash: ./untitled (1): Permission denied
joe@kjoe:~/Downloads$

---

### Post by Vaphell on 2012-09-30
show *ls -l "untitled (1)"* output

---

### Post by cwsnyder on 2012-09-30
Where do you specify your text box temporary data is located?  If it is unspecified, your program will try to store the data in the /tmp folder, which requires root access.

---

### Post by rai4shu2 on 2012-09-30
/tmp requires root? That's news to me.

---

### Post by cwsnyder on 2012-09-30
.

---

### Post by cwsnyder on 2012-09-30
I should correct myself, I haven't done much programming in Linux.  /tmp itself doesn't require root access, but ownership is root's.  A normal user has read & write access to that folder.

In general, the type of problem reported normally points to a permission error on where the data is attempting to be written, either the temporary file or the 'text box' is in an area where the user does not have permission to write.

---

### Post by StephenF on 2012-09-30
> **cwsnyder said:**
> Where do you specify your text box temporary data is located?  If it is unspecified, your program will try to store the data in the /tmp folder, which requires root access.
```
stephen@tmb /tmp $ echo hi >/tmp/hi
stephen@tmb /tmp $ cat /tmp/hi
hi

```
Wrong

---

### Post by WinterMadness on 2012-10-01
Why would it need access to the TMP folder? Im not saving anything on disk, it should just be ram. Its like if I have a program with two text boxes, text box a says "hello", and when I press the buttom, text box b says "hello"

---

### Post by dwhitney67 on 2012-10-01
> **WinterMadness said:**
> Why would it need access to the TMP folder? Im not saving anything on disk, it should just be ram. Its like if I have a program with two text boxes, text box a says "hello", and when I press the buttom, text box b says "hello"

Can you please answer Vaphell's question?

Here, let me ask again... what are the permissions on the file you are attempting to execute??

----

Edit:

From a terminal, run these two commands:
```

ls -l <prog>

file <prog>

```
where <prog> is the name of the file you are trying to execute.

---

### Post by WinterMadness on 2012-10-01
```
joe@kjoe:~/Downloads$ ls -l "untitled (1)"
-rw-rw-r-- 1 joe joe 28054 Sep 29 21:10 untitled (1)
joe@kjoe:~/Downloads$ file "untitled (1)"
untitled (1): ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=0x2e8549405593f1d696b925d842f06442ce5d70f5, not stripped
joe@kjoe:~/Downloads$ 


```

I can esily change the permissions with chmod, but I dont want a deployed program to force the user to do something like that. when I start getting more into linux development I want everything to be as user friendly as possible

---

### Post by Vaphell on 2012-10-01
let's say that executing non-executable file is non-trivial. That executable bit is not exactly for kicks and giggles ;-)
If you want to distribute your programs in a pleasant form, whip up .deb package with everything set up or something like that.

---

### Post by WinterMadness on 2012-10-02
> **Vaphell said:**
> let's say that executing non-executable file is non-trivial. That executable bit is not exactly for kicks and giggles ;-)
If you want to distribute your programs in a pleasant form, whip up .deb package with everything set up or something like that.

well, I have my reasons for wanting the user to not have to do anything other than point and click, is there any way I can make it so my programs are able to be ran without any terminal stuff? Debs make sense, but I dont always want to go that way. Often times, its easier to just distribute the executable and associated files to avoid package manager issues

---

### Post by Vaphell on 2012-10-02
i don't think you can override the executable bit. That's a layer of security that disallows random crap downloaded god knows from where to be run without explicit permission. Yes, i know that users detest security when it stands in the way of convenience but that does not mean that they should be encouraged in their ignorance.

Besides you don't have to use terminal, ticking the checkbox in rightclick/preferences should be mousy-gui enough for the taste of average user.
You can also explore the subject of tar archives preserving permissions.

---

### Post by lisati on 2012-10-02
If you've copied the program to another computer, it's possible that some permissions or ownership settings need adjusting. Please run the following and post its output:
```
ls -l "untitled (1)"
```

---

### Post by dwhitney67 on 2012-10-02
> **WinterMadness said:**
> ```
joe@kjoe:~/Downloads$ ls -l "untitled (1)"
-rw-rw-r-- 1 joe joe 28054 Sep 29 21:10 untitled (1)
joe@kjoe:~/Downloads$ file "untitled (1)"
untitled (1): ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, BuildID[sha1]=0x2e8549405593f1d696b925d842f06442ce5d70f5, not stripped
joe@kjoe:~/Downloads$ 


```

I can esily change the permissions with chmod, but I dont want a deployed program to force the user to do something like that. when I start getting more into linux development I want everything to be as user friendly as possible

You should be asking yourself how the program came to have those permissions.  Are the permissions the same on the source system as they are on the destination system?  Did you ever store the program on a drive that does not support permission levels?

Here's another question in order to eliminate "suspects"... what is the umask setting on the destination system?  From a terminal, run:
```

umask

```

---

### Post by trent.josephsen on 2012-10-03
He said he sent it to himself by email, which would do it. Attachments don't recognize or care about Unix permissions.

---

### Post by nvteighen on 2012-10-04
Apart from the emailing issue, which indeed erases permissions...

You really don't need to worry about permissions when deploying the program, if you know what you're doing, of course. If you use tarballs (.tar.gz archives), permissions can be kept by using tar with the -p option (both at archiving and extraction). Of course, a .deb package will do this automatically (dh_fixperms)... but I really find this an overkill for a case like yours...

The best solution, IMO: create a normal **source** tarball and recompile "at destination". That will create an executable with the correct permissions.

---


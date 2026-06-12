---
title: "Jubler - a subtitle editor for Java"
date: 2006-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by sakis on 2006-07-30
**_[COLOR="RoyalBlue"][SIZE="2"]Information[/SIZE][/COLOR]_**

Jubler is a tool to edit text-based subtitles. It can be used an an authoring software for new subtitles or as a tool to convert, transform, correct and refine existing subtitles. The most popular subtitle formats can be used. Preview of the subtitles in realtime or in design time, spell checking, translation mode and styles editing are some of the main features.

It is open source under a liberal (GNU) public licence. It is written in Java 5.0  (a.k.a. Java 1.5.0 ) in order to be really multi-platform. It has been tested under Linux, Windows XP and Mac OS X.
Requirements

[LIST]
[*]Latest version of JRE
[*]MPlayer to view subtitles
[*]ASpell to spell-check the subtitles
[/LIST]

Link: [http://www.panayotis.com/jubler/](http://www.panayotis.com/jubler/)

---

### Post by brallan on 2010-02-07
the download

Jubler-4.0-linux_i386.sh

is a shell script, and I have set it in properties as an executable(-rwxr-xr-x), but I am not sure how to get it to execute. Gedit gives me the error:

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

anyone know if there's a .deb file?

strange that after years this is still not in the repos. Maybe there's some other program that folks are using to do subtitling which I don't know about?

---

### Post by noup on 2010-02-07
You should execute the script from a terminal.

There are other subtitling applications:
Gnome Subtitles
Gaupol
Subtitleeditor

---

### Post by brallan on 2010-02-07
Thanks for the answer. 

There are indeed [a bunch of subtitle programs]("http://ubuntuforums.org/showthread.php?t=1121593"), but I have heard little from folks about what they are using and are happy with, that's why I asked.

Jubler came recommended though, so i like to see if it meets my needs.

Could something be wrong with the download? after all, isn't a shell script NOT a binary file, but a text file? At the very least I would expect gedit to be able to show me the contents.

And I AM trying to execute it, but here's what it gives me:

```
eeepc@eeepc:~/Desktop$ Jubler-4.0-linux_i386.sh 
Jubler-4.0-linux_i386.sh: command not found

```

I do have it set as an executable:

```
eeepc@eeepc:~/Desktop$ ls -al Jubler-4.0-linux_i386.sh 
-rwxr-xr-x 1 eeepc eeepc 3290794 2010-02-07 12:57 Jubler-4.0-linux_i386.sh
```

odd eh?

---

### Post by noup on 2010-02-07
> **brallan said:**
> 

```
eeepc@eeepc:~/Desktop$ Jubler-4.0-linux_i386.sh 
Jubler-4.0-linux_i386.sh: command not found

```

Unless you have "." in your path (which isn't by default), you should execute it this way:
```
$ ./Jubler-4.0-linux_i386.sh 
```

---

### Post by jasonclark10 on 2010-07-30
Jubler is a tool to edit text-based subtitles. It can be  used as an authoring software for new subtitles or as a tool to convert, transform, correct and refine existing subtitles. The most popular subtitle formats can be used. Preview of the subtitles in real-time or in design time, spell checking, translation mode and styles editing are some of the main 
 features.

---

### Post by Georges_ on 2010-08-02
Hi, same problem, I don't manage to execute jubler. I follow this thread.

---

### Post by scheeri on 2011-02-16
Hi!

I mean the solution is:

sh Jubler-4.0-linux_i386.sh

---

### Post by gcramer789 on 2011-03-13
Thanks I was having the same problem but now  I have the solution of  it ...

---


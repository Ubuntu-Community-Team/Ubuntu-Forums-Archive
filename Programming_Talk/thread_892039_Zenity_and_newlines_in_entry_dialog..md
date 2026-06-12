---
title: "Zenity and newlines in entry dialog."
date: 2008-08-16
forum: Programming Talk
---

### Post by rmflagg on 2008-08-16
Hi everyone,

   Here is a test script to make sure that I am not insane.  I have the newline escape sequence in the text of the Zenity entry dialog, but it doesn't print a newline, it just prints the \n.  It seems to work just fine in other dialogs.

#! /bin/bash

testdialog=`zenity --width 600 --height 100 --entry --title "Zenity Test" --text "For some reason the Zenity dialog\n doesn't want to linefeed.\n Any suggestions?"`

   Does anyone know if this is a bug or if there is a way to print newlines in the entry dialog?

Thanks,
RMFlagg

---

### Post by jinksys on 2008-08-17
I don't think that is supported for **--entry**.  I believe its purpose is to provide a quick one line message and text box.  For example, "Enter Password."

Although it doesn't support \n natively, you can inject your own newline characters using printf.

```

zenity --entry --text="`printf "Line one.\nLine two."`"

```

You can use echo or whatever you are more comfortable with, as long as it does the text processing before being handed off to zenity.

---

### Post by rmflagg on 2008-08-17
Well I just tried to use the print in the example that you gave and it didn't work.  I changed it to the following and I get an substitution error among other things including with an EOF error and it tried to execute the text line that I wanted to print.  Here's what it looked like:

testdialog=`zenity --width 600 --height 100 --entry --title "Zenity Test" --text="`printf "For some reason the Zenity dialog\n doesn't want to linefeed.\n Any suggestions?"`"`

   Might there be a problem since the entire zenity command is already enclosed in ` because it's being assigned to "testdialog"?

RMF

---

### Post by caljohnsmith on 2008-08-17
Rmflagg, here is an easy fix for your problem:
```
testdialog=$(zenity --width 600 --height 100 --entry --title "Zenity Test" --text="`printf "For some reason the Zenity dialog\n doesn't want to linefeed.\n Any suggestions?"`")

```

---

### Post by jinksys on 2008-08-17
> **caljohnsmith said:**
> Rmflagg, here is an easy fix for your problem:
```
testdialog=$(zenity --width 600 --height 100 --entry --title "Zenity Test" --text="`printf "For some reason the Zenity dialog\n doesn't want to linefeed.\n Any suggestions?"`")

```

Correct.

---

### Post by caljohnsmith on 2008-08-17
> **jinksys said:**
> Correct.

If you are going to use a variable you'll need to use $( ) and not backticks in your script.
I posted that solution using the var=$(...) syntax because to me it is the "cleanest" looking solution, but if rmflagg wants to he can still use backticks. He just needs to escape them:
```
testdialog=`zenity --width 600 --height 100 --entry --title "Zenity Test" --text="[COLOR="Red"]\[/COLOR]`printf "For some reason the Zenity dialog\n doesn't want to linefeed.\n Any suggestions?"[COLOR="Red"]\[/COLOR]`"`
```
There's always many choices in Linux. :)

---

### Post by jinksys on 2008-08-17
> **caljohnsmith said:**
> I posted that solution using the var=$(...) syntax because to me it is the "cleanest" looking solution, but if rmflagg wants to he can still use backticks. He just needs to escape them:
```
testdialog=`zenity --width 600 --height 100 --entry --title "Zenity Test" --text="[COLOR="Red"]\[/COLOR]`printf "For some reason the Zenity dialog\n doesn't want to linefeed.\n Any suggestions?"[COLOR="Red"]\[/COLOR]`"`
```
There's always many chois in Linux. :)

DOH! I forgot about the two sets of backticks.  You're right. :)
For the life of me I couldn't figure out why it wouldn't run, so simple.

---

### Post by dtmilano on 2008-08-18
As you mentioned, there's always choices in Linux.
Let me introduce the latest [autoglade]("http://autoglade.sf.net") and solve this problem, easily, not having some of the zenity's limitations.

1) install latest autoglade (there's an Ubuntu package in SF)
2) create a glade GUI, using glade-3

[URL="http://picasaweb.google.co.uk/dtmilano/DiegoTorresMilanoSBlog/photo#5235844608064766306"]
[IMG]http://lh4.ggpht.com/dtmilano/SKl07irYQWI/AAAAAAAAAKU/fUR8eFearPs/s144/Screenshot-entry.glade.png[/IMG][/URL]

2.1) create a dialog box
2.2) add OK and Cancel buttons
2.3) add a vertical box (size 2)
2.3.1) add a label
2.3.2) add an entry

3) add autoglade hints (that's the way autoglade understand our needs)
3.1) name the label [FONT="Courier New"]**label:auto:init:env**[/FONT]
3.2) name the entry [FONT="Courier New"]**entry:auto:init:env**[/FONT]
3.3) set Response ID: [FONT="Courier New"]**-6**[/FONT] for Cancel button
3.4) set Response ID: [FONT="Courier New"]**-5**[/FONT] for OK button

4) save it as [FONT="Courier New"]**entry.glade**[/FONT]

We told autoglade to use the environment to look for initial values.
Let's set them:

```
$ export label="this is <b>my label</b>
with more than one line:"
$ export entry="enter a value"
$ autoglade entry.glade

```

[IMG]http://lh4.ggpht.com/dtmilano/SKl5gJ3KhRI/AAAAAAAAAKc/BRnx9E3c_pk/s400/Screenshot-autoglade-entry.png[/IMG]

after entering some value and pressing OK, this is written to stdout
```
entry='123456'
autoargs='$entry'

```
and can be further passed to eval.
Of course you are not limited to a single entry and forms can be created, and you are not limited either to use autoglade from the command line as it is a python module too.

There are some other interesting examples in [http://autoglade.wiki.sourceforge.net/]("http://autoglade.wiki.sourceforge.net/")

Feel free to test autoglade and post you comments, critics, challenges, suggestions, ideas, bugs, fixes, etc.

---

### Post by rmflagg on 2008-08-20
These posts solved all my problems and I will *definitely* look into autoglade!

Thanks again!,
RM Flagg

---


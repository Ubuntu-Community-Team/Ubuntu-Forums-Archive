---
title: "Would like some help with simple coding"
date: 2009-11-25
forum: Programming Talk
---

### Post by firstEncounter on 2009-11-25
Hi there,

I am wanting to create a simple program in C/C++ or Qt (whichever would be best for this) that runs a few commands async and can display the commands' output in a text box.

More specifically, I'm wanting to create a GUI (for my own purposes) for Aircrack-ng. (Please don't tell me "there's other guis out there" because I'm extremely interested in programming and I want to make my own.) So, in theory, I'll have a GUI with three text boxes displaying the commands' output.

So, I need to know how to run the commands and capture their output, and put the output inside a text box. (Also, possibly read from the output? Like when Aircrack succeeds, it says "KEY FOUND! [00:00:00:00:00]" somewhere in the output. I would like to be able to remove the colons and display the key elsewhere on the GUI.)

If anyone could help me, I would greatly appreciate it. I know this sounds n00bish, but I've been attempting to learn more about programming and I haven't been able to find specific functions/examples on what **I** want to do.

Thanks in advance.
Luke

---

### Post by ib.lundgren on 2009-11-25
Since you are into learning and want it simple I'd say avoid C/C++ and QT and go for some fun with bash + zenity.

Bash allows for excellent text management and you can send the output to a fancy dialog with zenity. 

A simple example is:

```
ls | zenity --list --title="Directory Listing" --column="Filename"

```

That prints the files of the current working directory as a list in a dialog. Piping information from log files or whatever aircrack-ng might produces should not be a huge step up from that simple example. However, if you intend to view live data zenity will not allow for the dialogs to be updated.

Read more in the **_[bash manual]("http://www.gnu.org/software/bash/manual/bashref.html")_** and **[B]_[zenity manual]("http://library.gnome.org/users/zenity/stable/")_**[/B]

---


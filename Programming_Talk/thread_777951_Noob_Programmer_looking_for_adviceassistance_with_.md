---
title: "Noob Programmer looking for advice/assistance with Python"
date: 2008-05-01
forum: Programming Talk
---

### Post by isaacj87 on 2008-05-01
Hey all,

I'm a noob when it comes to programming (I'm actually a nursing student!), but I've taken it upon myself to learn how to code and contribute something back to the open-source world! I have this script that I use to aid me in compiling Compiz Fusion from GIT. It happens to be written in python. I'm trying to make a GUI for the script because I'm tried of looking at the terminal when using the script. I've already started, but I need some advice/assistance. Plus, I want to know how to code *properly*. I know that copy and paste is generally a "No No" in the programming world and you should always try to reuse as much code as possible. 

The script basically presents the user with options and asks for the user input (numberical values in this case). I wish to have the GUI cover for that.

Here's the script and my gui code (what little I have). If anybody could lead me in the right direction, I would be most appreciate!

Here's my GUI code:

[http://pastebin.com/m1641559b]("http://pastebin.com/m1641559b")

and the script:

[http://pastebin.com/m28e50a11]("http://pastebin.com/m28e50a11")

For those who know of the script, I realize I'm using an older version of it. I've actually made corrections to the script so that it functions *properly* (i.e. Show if updates are actually available). The image path in the GUI code is also hardcoded and that will change obviously.

and for kicks I've included a shot of the GUI

---

### Post by imdano on 2008-05-01
Heres a small tip.  I noticed this in the script code:
```
#
elif package == "ccsm" or package == "libcompizconfig" or package == "compizconfig-python" or package == "simple-ccsm":
```You can shortcut that by doing this instead:
```
elif package in ["ccsm", "libcompizconfig", "compizconfig-python", "simple-ccsm"]:
```I'll take a closer look at it a little later and see if there's anything else I can suggest, and I'm sure the other posters here will have some good tips as well.

---

### Post by lapubell on 2008-05-01
I'm not a great programmer, but I have some home brew scripts that I use the xdialog package for.  This is a simple package that lets you draw GTK windows using simple script commands.  I usually use it in my bash commands, but I have put it in python scripts too.

Check it out, it may make your life easier.

---

### Post by isaacj87 on 2008-05-01
Thanks for the replies guys!

Where can I find these scripts that you mentioned?

---

### Post by LaRoza on 2008-05-01
> **isaacj87 said:**
> Thanks for the replies guys!

Where can I find these scripts that you mentioned?

[http://xdialog.free.fr/](http://xdialog.free.fr/)

For Python, EasyGUI is an easy to use (duh) GUI (duh) package. It isn't the prettiest though, but it works. (See my wiki)

---

### Post by lapubell on 2008-05-01
here is a script that i wrote to group all pdf files into one if you have pdftk installed.

```

#! /bin/sh
DIALOG=Xdialog

$DIALOG	--title "pdfme" \
	--inputbox "Name dat pdf foo..." 0 0 2> /tmp/inputbox.tmp.$$

retval=$?

input=`cat /tmp/inputbox.tmp.$$`
rm -f /tmp/inputbox.tmp.$$

case $retval in
  0)
    pdftk *.pdf cat output "$input.pdf";;

  1)
    echo "Cancel pressed.";;
  255)
    echo "Box closed.";;
esac

```

this is a bash script, like i said.

---

### Post by isaacj87 on 2008-05-02
Thanks for the suggestions guys :)

I have another question (I forsee there will be many questions...)

Now the GUI is somewhat functional (woot!), but I was wondering something. As I mentioned before, I'm not a programmer, so I'll try to say this as best as possible. See the screenshot? How would I get what's appearing in Terminal, appear in a dialog?

---


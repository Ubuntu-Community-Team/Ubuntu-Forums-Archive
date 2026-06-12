---
title: "Need to create program with checkboxes to run other programs"
date: 2009-12-01
forum: Programming Talk
---

### Post by seanmadi on 2009-12-01
I am doing a project for my operating systems class where I created several different SH files to run.  I want to be able to make a graphical program where you can check which SH files to run, click ok, and then they run.  Can anyone point me in the direction of how to do this?  I don't have much graphical programming experience, but I should be able to figure it out, though I'd like something a little on the easier side if possible.  Thanks!

---

### Post by ib.lundgren on 2009-12-01
If you only want to choose the script(s) from a list and run it/them, and nothing fancier than that, you don't even need to leave the shell.

* Collect the scripts you want to run in some manner, file, array etc.
* Display that collection graphically with zenity.
* Use the returned (selected) value to run the script(s).
* If several values are returned, you need to split the returned ones and run them in a loop.

[PHP]$ zenity --help
$ output=$(ls -l) # Saves the output from ls -l in variable output
$ input="comma,separated,list,of,values"
$ IFS=","; for word in $input; do echo $word; done # Prints the words on a line each[/PHP]

If you are into something more fancy then this tutorial on glade with c or python is very helpfull for getting started with GUIs.

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by kerry_s on 2009-12-01
grab 1 of my scripts here:
[http://ubuntuforums.org/showthread.php?t=1273899&highlight=zenity+logout](http://ubuntuforums.org/showthread.php?t=1273899&highlight=zenity+logout)

and just tweak it.

example:
```
#!/bin/sh
read=`zenity --height=250 --list --title='A+ Please!' --column=Action command-1 command-2`

if [ $read = "command-1" ]; then
	/path/to/command1
fi

if [ $read = "command-2" ]; then
	/path/to/command2
fi


```

---

### Post by seanmadi on 2009-12-01
Thanks! That works great, except I have one problem:

```

#!/bin/sh
read=`zenity --height=250 --list --checklist --title='Selection' --column=Boxes --column=Selections TRUE a TRUE b TRUE c --separator=':'`

if [ ???? ]; then
	do something
fi

if [ ???? ]; then
	do other thing
fi

if [ ???? ]; then
	do other thing
fi


```

If the user checks a and c, it will return "a:c".  So I need a way to say "if $read contains a, then do this," or some other way accomplish the same thing.

---


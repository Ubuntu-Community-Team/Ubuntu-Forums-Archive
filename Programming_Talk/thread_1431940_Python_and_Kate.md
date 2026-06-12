---
title: "Python and Kate"
date: 2010-03-17
forum: Programming Talk
---

### Post by K.L. on 2010-03-17
Hello everyone!

 I'm learning Python programming language and using Kate editor. I know it has plugin called External Tools which allows to run various scripts easily. I'd like to write a script which would run currently open Python script by pressing F5 key.

 I've tried this (and lots of other commands), but it doesn't work.

 ```
konsole --hold -e 'python -i "%filename"'
```Can anyone help me out?

 P.S. I'm using KDE 4.4.1

---

### Post by K.L. on 2010-03-18
Anyone?

---

### Post by HalfEmptyHero on 2010-03-18
You should already have 'Run Script' under external tools, and this will do what you want. The only problem is it opens a new terminal and not the one in the bottom pane, so you have to make sure you add an input() command at the end of your script so you can see what it does before it closes the terminal.

---

### Post by K.L. on 2010-03-19
I have tried it with very simple Python script and it works, thanks. To keep terminal open I had to change External Tools Script from this :

```
cd "%directory" && chmod u+x "%filename" && konsole -e "./%filename"
```to this:

```
cd "%directory" && chmod u+x "%filename" && konsole **--hold** -e "./%filename"
```There is game engine called [Panda3D]("http://www.panda3d.org/"), it uses Python and is very easy to learn. I've tried to run Panda's Python script, but it doesn't work, it just opens blank terminal window with no error messages.

It works with Geany, tho. Its execute script command looks like this:

```
python "%f"
```I'll mess around with Kate a bit more, if nothing helps, I'll have to stick with Geany...

Anyway, any help would be appreciated.

---

### Post by abalter on 2012-04-12
I'm trying:

```
cd "%directory" && chmod u+x "%filename" && konsole --hold -e 'python -i "%filename"'
```

to run the current file which is a python script.  What I get is a konsole window and a python command prompt, but the script does not run

```

Python 2.7.2+ (default, Oct  4 2011, 20:03:08) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

hello.py:
```
print("hello from python")
```

which, of course, runs fine.

Thanks!

---


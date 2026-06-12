---
title: "Install TaskUnifier by &quot;running&quot; TaskUnifier.sh?"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by gigenieks on 2013-06-09
Hello!

[http://www.taskunifier.com/index.php?page=howto]("http://www.taskunifier.com/index.php?page=howto")
> 
In order to run TaskUnifier on Linux, download the linux zip file. Once downloaded, unzip it and finally run "TaskUnifier.sh".

What is meant by *running*? 
Double clicking opens it in gedit.

---

### Post by 3rdalbum on 2013-06-09
> **gigenieks said:**
> Hello!

[http://www.taskunifier.com/index.php?page=howto]("http://www.taskunifier.com/index.php?page=howto")

What is meant by *running*? 
Double clicking opens it in gedit.

Make it executable:

```
chmod a+x <drag the file into the terminal and press Enter>
```

Then run it in the terminal by dragging the file into the terminal and pressing Enter.

If, and **ONLY IF** this fails with a Permission Denied error, then the script you downloaded is actually an installer, and you'll need to "chmod" it with 'sudo' and then run it with 'sudo':

```
sudo chmod a+x <drag the file in>
sudo <drag the file in>
```

I'm assuming it will create an entry in the Dash when it gets installed.

---

### Post by newb85 on 2013-06-09
Actually, sudo is only necessary to chmod the file if the user running chmod is different than the file owner.

And of course, you should only do this if you trust the source of the file.

---

### Post by gigenieks on 2013-06-09
It worked. Thanks, 3rdalbum.

---

### Post by gigenieks on 2013-06-09
Installation was successful. But I can't find this program anywhere. It doesn't even show in Dash search. Therefore I can't launch it.

Why Dash doesn't find it? And more importantly, how can I make it *searchable*?

---

### Post by 3rdalbum on 2013-06-09
> **gigenieks said:**
> Installation was successful. But I can't find this program anywhere. It doesn't even show in Dash search. Therefore I can't launch it.

Why Dash doesn't find it? And more importantly, how can I make it *searchable*?

So this was an installer? You can probably start the program by typing this command in the terminal:

```
taskunifier
```

If that's not correct, you can try running:

```
whereis taskunifier
```

to figure out where it has gone.

If this doesn't yield any information, try looking in /usr/bin, /usr/local/bin and /opt.

Dash doesn't really "find" programs, it's up to the program's installer to add a ".desktop" file to one of the places it looks. Once you've found where there program actually is (or know how you can launch it in the terminal), you can use the "Main Menu" program in the Dash to add a menu item for the program.

---

### Post by gigenieks on 2013-06-09
Unfortunately, terminal doesn't start the program. And I didn't find anything named taskunifier (or close to that) in directories you mentioned.

Edit: I can start it by opening terminal dragging TaskUnifier.sh and pressing Enter, but that is really inconvenient! 
So what I need to do to access it via Dash or Unity Launcher??

---

### Post by 3rdalbum on 2013-06-09
Use the Main Menu program to create a Dash entry for it.

---

### Post by gigenieks on 2013-06-09
Sorry, I have no clue what are you asking me to do. 
Main Menu program??? Can you explain it a bit more, please?

---

### Post by MG&amp;TL on 2013-06-09
> **gigenieks said:**
> Sorry, I have no clue what are you asking me to do. 
Main Menu program??? Can you explain it a bit more, please?

There is a program (actually called *alacarte*) that shows in the Unity Dash as 'Main Menu'. You'll need to install it via the software centre or via terminal:

```
sudo apt-get install alacarte
```

---


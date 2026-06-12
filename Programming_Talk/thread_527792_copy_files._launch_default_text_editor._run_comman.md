---
title: "copy files. launch default text editor. run command in terminal"
date: 2007-08-17
forum: Programming Talk
---

### Post by nzadLithium on 2007-08-17
Hey

I'm using c. 

I'm trying to launch a text editor in linux and make it open a file. How do i do this??

I want this program to work over all linux distributions. So i need a way to find out any installed text editors and open a file using it.

Also i need to make a copy of a file as a backup. How do i do this? 

Is there a function or something i can use to run a command in the terminal? like on windows you can use shell(command).

I spent the last half hour searching in google and haven't found anything useful :(

---

### Post by PaulFr on 2007-08-17
1. AFAIK, there is no standard way to call an editor (unless you bundle or implement your own editor). You could have a standard environment variable or setting that the user can set to point to an editor of her/his choice. For example, **crontab -e** uses the environment variable EDITOR if it is set, otherwise uses /usr/bin/vi.

2. If you want to do file copy in pure C, and you only need it to work in Linux variants, then you can look at **sendfile** which is not POSIX. Otherwise, you have to roll your own using **read** and **write**. If you are okay with running a **cp** command, then the **system** call will do, using **cp** as the command.

3. See **system**. You can also use **popen** if you are interested in the output of the command.

Of course, **man system**, **man sendfile** and **man popen** for more details.

---

### Post by nzadLithium on 2007-08-17
thx. hopefully i can get this to work now.

---

### Post by kalikiana on 2007-08-18
In fact it is not very difficult to make this work on at least the major desktops.

[http://portland.freedesktop.org/wiki/](http://portland.freedesktop.org/wiki/)

Look at xdg-open which is a small shellscript doing what you want in Gnome, KDE and XFCE. :)

---

### Post by nzadLithium on 2007-10-05
if you right click on a text file and press properties then goto open with it says text editor.

That value must be stored somewhere and i'd say most linux distros must have it.

Is there a command i need to run to get that value?

Or maybe its stored in a text file somewhere??

that xdg-utils package would work perfectly but i want to stay away from extra dependencies if possible.

Also I created another thread that was asking about opening another program from within my program. It was said that fork and exec are my friends :)

I had a look at the man entries for these and wrote this as code:
```

	pid = fork();
	char *winearg[] = { GTK_ENTRY(txtwolfPath) };
	execvp("wine", winearg );
	//system(xfireLaunchCommand);

```

txtwolfPath contains the path to RTCW (a game to be run by wine)

theoretically this should launch wine with the argument /usr/local/games/wolf/wolf.x86

but when i execute this code the program goes laggy. Then i get this in the terminal:
Xlib: unexpected async reply (sequence 0xc17)!
now i read somewhere that my program is meant to handle the requests of the child program. How?

also i want wine to be launch completely seperately from my program. So if i close my program the game will still run. i'm thinking i've done this all wrong. but i don't know what to do.

---

### Post by nzadLithium on 2007-10-08
got the program launching to go using system command and sticking an & on the end :) 

still interested in knowing how i can get that default program to launch text files going.

---

### Post by j_g on 2007-10-09
I'm not sure why you're doing what you're doing. (ie, You haven't said why you're launching a text editor from your C program). But, just in case you aren't aware, I should note that you can easily use GTK+ from a C app, and GTK has controls (ie, widgets) that let you display text to the enduser and let him edit it (ie, GtkTextView). If that's what you want to accomplish, and you want it to work on many distros, I think that your best bet is to use a GTK GtkTextView in your C program.

See [http://library.gnome.org/devel/gtk/2.8/TextWidget.html](http://library.gnome.org/devel/gtk/2.8/TextWidget.html)

---

### Post by nzadLithium on 2007-10-10
that looks like it could work well. I'll try it. Thx

---


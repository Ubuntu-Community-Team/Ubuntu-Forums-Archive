---
title: "How do I use GTK+"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Adam Jensen on 2012-01-25
I'm confused:confused:

How do I use GTk+? I understand that Ubuntu has it pre-installed but I have no idea how to use it. I followed the "Hello World" tutorial here [http://developer.gnome.org/gtk-tutorial/2.90/c39.html](http://developer.gnome.org/gtk-tutorial/2.90/c39.html) and cannot get the code to compile. I used synaptic to make sure that gtk and the development libraries are installed. Please help me. I've been trying to figure this thing out for nearly 2 weeks. It's very frustrating ](*,)

---

### Post by amauk on 2012-01-25
you'll need to post what code you're trying to compile, and the errors output by the compiler

---

### Post by Adam Jensen on 2012-01-25
> **amauk said:**
> you'll need to post what code you're trying to compile, and the errors output by the compiler

Oh, sorry. Here is the code:

```
//Hello world GTK tutorial
#include <stdio.h>
#include <gtk/gtk.h>

int main(int argc, char *argv[])
{
    GtkWidget *window;
    
    gtk_init (&argc, &argv);
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_show (window);
   
    gtk_main ();
    
    return 0;
}
```

And here is the output by the terminal:

adamjensen@ubuntu:~$ gcc -Wall -g helloworldgtk.c -o helloworldgtk 'pkg-config --cflags' \ 'pkg-config --libs gtk+-3.0'
gcc: error: helloworldgtk.c: No such file or directory
gcc: error: pkg-config --cflags: No such file or directory
gcc: error:  pkg-config --libs gtk+-3.0: No such file or directory
gcc: fatal error: no input files
compilation terminated.

I'm new to Ubuntu and Linux in general, so you have to break things down and explain them in simple terms for me lol. I forgot to mention that this is only the first part of the GTK tutorial. All I am trying to do right now is to get a window to open. Once I get that done I will have it display the "Hello World" message later on.

---

### Post by amauk on 2012-01-25
> **Adam Jensen said:**
> gcc: error: helloworldgtk.c: No such file or directory
gcc: error: pkg-config --cflags: No such file or directory
gcc: error:  pkg-config --libs gtk+-3.0: No such file or directory
gcc: fatal error: no input files
compilation terminated.It's complaining that your source file doesn't exist
have you saved the code above into a file named "helloworldgtk.c" in the current directory?
Maybe better to specify the complete path to the source file

Also, the pkg-config bit is wrong
It's using command substitution (the output of "pkg-config" is processed and used as an argument in the "gcc" command)
you're using single quotes, when you need either backticks (key above tab) or the "$()" form for command substitution

It needs to be something like this

```
gcc -Wall -g helloworldgtk.c -o helloworldgtk $(pkg-config --cflags --libs gtk+-3.0)
```

---

### Post by Adam Jensen on 2012-01-25
> **amauk said:**
> It's complaining that your source file doesn't exist
have you saved the code above into a file named "helloworldgtk.c" in the current directory?
Maybe better to specify the complete path to the source file

Also, the pkg-config bit is wrong
It's using command substitution (the output of "pkg-config" is processed and used as an argument in the "gcc" command)
you're using single quotes, when you need either backticks (key above tab) or the "$()" form for command substitution

It needs to be something like this

```
gcc -Wall -g helloworldgtk.c -o helloworldgtk $(pkg-config --cflags --libs gtk+-3.0)
```

I tried out the code you provided and it removed all complaints except one: it keeps on saying that there is no such file as "helloworldgtk.c". I tried including the direct path to the file: home/adamjensen/Documents/helloworldgtk.c and it still says that it does not exist. Something tells me the mistake I am making is incredibly simple, but I'm just too inexperienced with gtk and ubuntu to figure it out.

---

### Post by QIII on 2012-01-25
Recheck the file name carefully.  Case matters.  If you see the file in the directory you expect it to be in but the case of any character in the name is different from what you are instructing to be compiled, you'll get an error like that.  Seems silly, but we all make frustrating mistakes like that (and if you show me someone who says he doesn't I'll show you a liar!) and spend hours missing them while looking right at them.

---

### Post by Adam Jensen on 2012-01-25
> **QIII said:**
> Recheck the file name carefully.  Case matters.  If you see the file in the directory you expect it to be in but the case of any character in the name is different from what you are instructing to be compiled, you'll get an error like that.  Seems silly, but we all make frustrating mistakes like that (and if you show me someone who says he doesn't I'll show you a liar!) and spend hours missing them while looking right at them.

Thanks for answering QIII. The case and spelling is correct, but the terminal is still saying that the file does not exist. Maybe I am entering the incorrect code? I tried two different codes; one from gnome's developer site and one from amauk. Check them out and tell me what I am doing wrong:

gnome's code without directory
```

gcc `pkg-config --cflags gtk+-3.0` -o  helloworldgtk helloworldgtk.c `pkg-config --libs gtk+-3.0`
```

gnome's code with directory
```

gcc `pkg-config --cflags gtk+-3.0` -o helloworldgtk home/adamjensen/Documents/helloworldgtk.c `pkg-config --libs gtk+-3.0`
```

amauk's code without directory
```

gcc -Wall -g helloworldgtk.c -o helloworldgtk $(pkg-config --cflags --libs gtk+-3.0)
```

amauk's code with directory
```

gcc -Wall -g home/adamjensen/Documents/helloworldgtk.c -o helloworldgtk $(pkg-config --cflags --libs gtk+-3.0)
```

No matter what code I enter I always get one of these error messages:

```

gcc: error: helloworldgtk.c: No such file or directory

```

OR

```

gcc: error: home/adamjensen/Documents/helloworldgtk.c: No such file or directory

```

What went wrong? :confused:

---

### Post by QIII on 2012-01-25
Just for giggles and grins, could you post the output of 

```
cat /home/adamjensen/Documents/helloworldgtk.c
```

There should be a slash in front of "home".

---

### Post by Adam Jensen on 2012-01-25
> **QIII said:**
> Just for giggles and grins, could you post the output of 

```
cat /home/adamjensen/Documents/helloworldgtk.c
```

There should be a slash in front of "home".

I read that the "cat" command combines files. How will that remedy my problem? I put the slash in front of "home" but no dice. I watched a few vids on youtube of people compiling their gtk apps without using directories; they only typed in the name of the source file. Getting this thing to work has not been a pleasant experience lol.

---

### Post by QIII on 2012-01-25
In this case, giving the name of a single file only, cat will just display the standard output in the terminal.  Quick way to view the contents of a relatively small file.

So, what happened exactly?

---

### Post by QIII on 2012-01-26
Geez!  Hold on!  Dur!  I'm sorry.  I think I see it now.

When you are at the command line under your account, the "default"  directory you are working in is /home/adamjensen.  Is your file saved in /home/adamjensen/Documents?  If so, you are trying to compile  something in /home/adamjensen/Documents and the file does not exist where "you are" in /home/adamjensen.

The reason it wasn't compiling with the full path is that you were missing the leading "/", I believe.

Move the thing to the /home/adamjensen directory (that is, move it out of /Documents) or 

```
cd Documents
```

and try to compile it without using the fully qualified path.

---

### Post by mcduck on 2012-01-26
> **QIII said:**
> Geez!  Hold on!  Dur!  I'm sorry.  I think I see it now.

When you are at the command line under your account, the "default"  directory you are working in is /home.  Is your file saved in /home/Documents?  If so, you are trying to compile  something in /home/Documents and the file does not exist where "you are" in /home.

The reason it wasn't compiling with the full path is that you were missing the leading "/", I believe.

Move the thing to the /home directory (that is, move it out of /Documents) or 

```
cd Documents
```

and try to compile it without using the fully qualified path.

...kepp in mind the default directory actually isn't /home, it's /home/*username*.

(and there is no such directory as "/home/Documents, unless you have a user account called "Documents")

/home is not your home directory, it's where all the user home directories are contained. (On the other hand $HOME, or ~, would actually point to your home directory instead of /home itself.)

---

### Post by QIII on 2012-01-26
Agreed.  Hasty bit that.

But your point is exactly why I asked him to use cat as I did.  I'll do some self-flagellation for getting it right there and then being a complete bumble in the post referenced.

I'm going to edit my post appropriately in case someone else stumbles on this.

---

### Post by mcduck on 2012-01-26
To be honest, I often make that kind of mistakes when typing instructions in a hurry so no need for any self-flagellation... ;)


...and I agree that the problem is most likely because of wrong path, or not being in correct directory when running the commands. That's pretty much _always_ the reason for "No such file or directory" errors.

(actually if it's not a question of the path, then it would be a error in the filename itself. Which is usually pretty easy to spot. But if everything else seems to fail it's also a good idea to check that there isn't a space at the end of the filename or something like that. And of course use autocompletion to fill in the paths & filenames...)

---

### Post by ngubk on 2012-01-26
In my case, i often have a makefile before hand. For whichever coding project, just modify the file a little and use

---

### Post by QIII on 2012-01-26
I use IDEs that do all that stuff for me, which is probably why it took a bit for me to see what I believe to be the problem.

I'm a bit rusty at doing it for myself.

---

### Post by Adam Jensen on 2012-01-26
> **QIII said:**
> Geez!  Hold on!  Dur!  I'm sorry.  I think I see it now.

When you are at the command line under your account, the "default"  directory you are working in is /home/adamjensen.  Is your file saved in /home/adamjensen/Documents?  If so, you are trying to compile  something in /home/adamjensen/Documents and the file does not exist where "you are" in /home/adamjensen.

The reason it wasn't compiling with the full path is that you were missing the leading "/", I believe.

Move the thing to the /home/adamjensen directory (that is, move it out of /Documents) or 

```
cd Documents
```

and try to compile it without using the fully qualified path.

Hey guys. Thanks for all of the responses. I really appreciate it.

Good news!!! IT WORKED!!!!

I moved the source file from Documents to home and it compiled! :guitar:

Thank you so much. Now I can continue the tutorial and start building apps!!! Now I have another question; how do I archive this conversation? It seems that this is a common issue for new gtk users and I think reading this conversation will be beneficial for them.

---

### Post by anewguy on 2012-01-26
It will be here in the forum so you don't need to archive it anywhere.

BTW - I'd have to go looking to see if I kept any of it before I lost my hard drive and had to start over (I didn't do a backup), but *if* I can find it I'll send you some sample GTK programs in C.  Perhaps they can help you learn.

Dave ;)

---

### Post by Adam Jensen on 2012-01-28
> **anewguy said:**
> It will be here in the forum so you don't need to archive it anywhere.

BTW - I'd have to go looking to see if I kept any of it before I lost my hard drive and had to start over (I didn't do a backup), but *if* I can find it I'll send you some sample GTK programs in C.  Perhaps they can help you learn.

Dave ;)

Thanks! I'd really appreciate that!

---

### Post by anewguy on 2012-01-28
It may take me a day or 2, but I'll try to find it and send it to you!

Dave ;)

---

### Post by anewguy on 2012-02-16
Couln't find my old code, but I've been working on a new project anyway.  here's a link to the source code for it.  There are a couple of things that just don't work yet, but it compiles and runs ok for what it does have.


[http://ubuntuone.com/79IMEVagHCIrI0m8myr620]("http://ubuntuone.com/79IMEVagHCIrI0m8myr620")

---

### Post by Adam Jensen on 2012-02-26
> **anewguy said:**
> Couln't find my old code, but I've been working on a new project anyway.  here's a link to the source code for it.  There are a couple of things that just don't work yet, but it compiles and runs ok for what it does have.


[http://ubuntuone.com/79IMEVagHCIrI0m8myr620]("http://ubuntuone.com/79IMEVagHCIrI0m8myr620")

Thanks for the link, but I could not open it. I get a page saying that Ubuntu One could not find the page. Bummer...

---


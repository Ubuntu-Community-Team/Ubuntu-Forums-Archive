---
title: "New/future programmer. what IDE/text editor, and what can they do?"
date: 2011-03-28
forum: Programming Talk
---

### Post by btf18 on 2011-03-28
Hey there,

Ive been dabbling in different tutorials and am halfway through programming for dummies book. Ive learnt to use vim text editor, but i havent created any programs in anything, as i always struggle with technical difficulties such as getting a working compiler.

To make quick programs that have a GUI, such as windows and menus, and give me instant programming gratification, can you use a console text editor? If not, are console text editors still widely used, as they can write the source code for the GUI to work?

I'd like to maybe start in BASIC. Can you recommend a free BASIC IDE? I have windows 7 and ubuntu 10.10. I've only found expensive ones. When i want to extensively learn a language, would i view it's library, or is it more just doing tutorials that makes you learn the whole language?

I havent managed to successfully work a compiler, so an IDE that is easier to use compiling functionality is essential.

Thanks

---

### Post by GregBrannon on 2011-03-28
Check out Gambas.  I'm not recommending, just suggesting.

---

### Post by lykwydchykyn on 2011-03-28
Asking this question is going to get you a lot of people sounding off about their favorite editor, so you may want to be specific about what you prefer and what you want.  

Vim and Emacs are widely used; (I don't know about other console editors, but I've heard people say they use them)  they both have strengths that make them powerful development tools.  Nothing prevents you from writing GUI code with them if you want to.  I've written several GUI programs in Emacs.

I would advise you not to find a "BASIC" editor/IDE.  If you are going to be serious about programming, you'll be writing in many languages eventually.  Having a different editor for each language gets tedious and confusing.  Find a good, generic editor with support for many languages and learn to use it well, because no matter what you end up learning you'll surely be editing a lot of text files with it.

---

### Post by btf18 on 2011-03-29
Thanks guys. I like vim. Im not seeing how i could create a GUI with the console version of vim, but then again i know hardly anything about programming. So how is a GUI created from a console text editor like vim? And i could  go to Gvim too :-) Is vim something that could be used for massive commercial programming like developing an OS?
 
I also have Dev-C++ for windows which is an IDE, tbh, its easier than vim, and i get closer to creating a program that runs, as it contains a compiler, though i still have troubles compiling source code i copy and paste from a tutorial. I know it's only for C++ but i will be learning this language eventually. Please offer opinions or advice :-)

---

### Post by Some Penguin on 2011-03-29
Might want to read the sticky threads first.

---

### Post by numinous on 2011-03-29
> **btf18 said:**
> Thanks guys. I like vim. Im not seeing how i could create a GUI with the console version of vim, but then again i know hardly anything about programming. So how is a GUI created from a console text editor like vim? And i could  go to Gvim too :-) Is vim something that could be used for massive commercial programming like developing an OS?
 
I also have Dev-C++ for windows which is an IDE, tbh, its easier than vim, and i get closer to creating a program that runs, as it contains a compiler, though i still have troubles compiling source code i copy and paste from a tutorial. I know it's only for C++ but i will be learning this language eventually. Please offer opinions or advice :-)




Here's the example code, just a GTK window with a very simple menu. 



```


#include <gtk/gtk.h>


int main( int argc, char *argv[])
{

  GtkWidget *window;
  GtkWidget *vbox;

  GtkWidget *menubar;
  GtkWidget *filemenu;
  GtkWidget *file;
  GtkWidget *quit;

  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_default_size(GTK_WINDOW(window), 250, 200);
  gtk_window_set_title(GTK_WINDOW(window), "menu");

  vbox = gtk_vbox_new(FALSE, 0);
  gtk_container_add(GTK_CONTAINER(window), vbox);

  menubar = gtk_menu_bar_new();
  filemenu = gtk_menu_new();

  file = gtk_menu_item_new_with_label("File");
  quit = gtk_menu_item_new_with_label("Quit");

  gtk_menu_item_set_submenu(GTK_MENU_ITEM(file), filemenu);
  gtk_menu_shell_append(GTK_MENU_SHELL(filemenu), quit);
  gtk_menu_shell_append(GTK_MENU_SHELL(menubar), file);
  gtk_box_pack_start(GTK_BOX(vbox), menubar, FALSE, FALSE, 3);

  g_signal_connect_swapped(G_OBJECT(window), "destroy",
        G_CALLBACK(gtk_main_quit), NULL);

  g_signal_connect(G_OBJECT(quit), "activate",
        G_CALLBACK(gtk_main_quit), NULL);

  gtk_widget_show_all(window);

  gtk_main();

  return 0;
}



```






Copy it and paste it into a simple text editor and save it as;


 **gtkmenu01.c**



Now open up a terminal in the same directory where you just saved that program and issue the following command (you can just copy it and paste it) at the command line;


**gcc gtkmenu01.c  -o mymenu01 `pkg-config gtk+-2.0 --cflags --libs` **


After that an executable file will be created in that directory called

 **mymenu01**

Now issue the following command at your command line;



.**/mymenu01**


you should see the simple GTK window and menu


So you see to create a GUI in a text editor you just learn the functions related to the GUI toolkit and get busy writing code!

---

### Post by btf18 on 2011-03-29
Thanks! i cant compile. If i use an IDE it comes up with a bunch of things down the bottom like no such file or directory. Compiling is my biggest problem, i cant compile anything

---

### Post by btf18 on 2011-03-29
and when i make it in vim, save it, this is my attempt to compile:

ben@ubuntu:~$ gcc gtkmenu01.c -o mymenu 'pkg-config gtk+2.0 --cflags --llbs'
gcc: pkg-config gtk+2.0 --cflags --llbs: No such file or directory
gtkmenu01.c:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;<&#8217; token
ben@ubuntu:~$ ls
aa                 download.html?product=firefox-4.0rc1  index.html  Templates
'bitchin program'  Downloads                             Music       Ubuntu One
desktop            examples.desktop                      Pictures    Videos
Desktop            gg                                    Public      we
Documents          gtkmenu01.c                           say         weeze
ben@ubuntu:~$ gcc gtkmenu01.c
gtkmenu01.c:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;<&#8217; token
ben@ubuntu:~$ g++ gtkmenu01.c
gtkmenu01.c:1: error: expected constructor, destructor, or type conversion before &#8216;<&#8217; token
ben@ubuntu:~$ ls
aa                 download.html?product=firefox-4.0rc1  index.html  Templates
'bitchin program'  Downloads                             Music       Ubuntu One
desktop            examples.desktop                      Pictures    Videos
Desktop            gg                                    Public      we
Documents          gtkmenu01.c                           say         weeze
ben@ubuntu:~$ 


Thanks

---

### Post by ve4cib on 2011-03-29
I think you've used the wrong apostrophe-like character in your command-line:

> gcc gtkmenu01.c -o mymenu 'pkg-config gtk+2.0 --cflags --llbs'
is what you have.  You're using the apostrophe (') character.  You should be using `, the back-tick (or whatever it's really called).  It's on the same keyboard button as the tilde (~) on standard English keyboards.

> gcc gtkmenu01.c -o mymenu `pkg-config gtk+2.0 --cflags --llbs`

or

> gcc gtkmenu01.c -o mymenu $(pkg-config gtk+2.0 --cflags --llbs)

should do the trick.

---

### Post by numinous on 2011-03-29
You simply need to install the GTK+ development libraries, also make sure you have gcc installed, otherwise you won't be able to compile it.


If you need help go thru the following tutorial;


[http://knol.google.com/k/hesham-elsaghir/developing-gui-programs-with-c-c-in/3noo92ojj7hi0/30#]("http://knol.google.com/k/hesham-elsaghir/developing-gui-programs-with-c-c-in/3noo92ojj7hi0/30#")


But I was just showing an example, for starting out stay with BASIC or maybe Python or some other interpreted language there are many others also.

Keep it simple and have fun before you attempt more complicated programs.

---

### Post by btf18 on 2011-03-29
im installing about 15 GTK packages from the repositories as idk what one it is and there is heaps, also, the codes ve4cb suggested didnt work. Thanks. Why cant i just paste the code into another IDE i have on windows and make it run?

---

### Post by btf18 on 2011-03-29
also i have g++ but i think thats the c++ version of gcc

---

### Post by numinous on 2011-03-29
First install the development libraries for GTK+

```

sudo apt-get install gnome-core-devel build-essential install libgtk2.0-dev libgtk2.0-doc devhelp



```

next install gcc

```

sudo apt-get install gcc

```

Now you should be able to compile the example.

---

### Post by btf18 on 2011-03-29
thanks. did that, got this message:ben@ubuntu:~$ sudo apt-get install gnome-core-devel build-essential install libgtk2.0-dev libgtk2.0-doc devhelp
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package install
ben@ubuntu:~$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ben@ubuntu:~$ 

as u can see it said unable to locate package install

The command still doesnt work it displays this:

ben@ubuntu:~$ gcc gtkmenu01.c -o mymenu `pkg-config gtk+2.0 --cflags --llbs`
--llbs: unknown option
gtkmenu01.c:1: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;<&#8217; token

But thanks anyway, i dont think there is much we can do about it is there?

---

### Post by numinous on 2011-03-29
Anyhow the example code I put up will compile as either C or C++ so you can compile it with gcc or g++ it doesn't matter.

Someone else will have to help install the GTK+ development library, I don't understand why you can't install it.

good luck with that.

But I really would recommend you stay with an interpreted language for awhile like Python or one of the others, there are many.

---

### Post by btf18 on 2011-03-29
Thanks, so is GTK something that allows those commands to make windows and a GUI? yeah i'd like to not compile haha. Not for now i mean. I have figured out one way that does it most times. I write a c++ program in codeblocks IDE and name it something.cpp and it works, but if i name it something, not.cpp, it doesnt work. its magical to me

---

### Post by safarin on 2011-03-29
> **btf18 said:**
> Thanks, so is GTK something that allows those commands to make windows and a GUI? yeah i'd like to not compile haha. Not for now i mean. I have figured out one way that does it most times. I write a c++ program in codeblocks IDE and name it something.cpp and it works, but if i name it something, not.cpp, it doesnt work. its magical to me

Hi all, I also still new in programming, C++ is my second language. About installing the package I also get "E: Unable to locate package install", but I has solved it by install manually from "Synaptic Package Manager" and I just install "gnome-core-devel" which are include a lots of library :P

About your compiling problem. I think you should replace ` to ' manually.
` happens because you copy directly from this forum. :D
`pkg-config gtk+2.0 --cflags --llbs`(copied) to 'pkg-config gtk+2.0 --cflags --llbs' (type from keyboard)

Sorry for my english.

---

### Post by btf18 on 2011-03-29
Thanks all. Im doing a bit of programming in windows as thats working for me well with code::blocks. I downloaded a GTK+ bundle and followed the readme file instructions to get it going, and put it in my %PATH% and from the DOS command prompt it does run :-) I'll try get it on linux sometime, but i love using code::blocks IDE for C++ programming in windows for now as its compiling the easiest and i like the user interface, plus it recommended that in a great C++ tutorial.
 
Thanks heaps!

---

### Post by btf18 on 2011-03-29
However i just tried your code and i dont know what to type instead of your #include gtk or whatever, as my gtk is in a different place than yours and its in about 10 folders as its a bundle, o well i'll leave this for later. Thanks

---

### Post by lykwydchykyn on 2011-03-29
If you're talking about using a visual form designer (a la visual basic), you can do that regardless of what editor you use.  You'd just design the GUI and import the resulting file into your code.  Exactly how you do this depends on the toolkit and the method you choose to work with, but that's the basic idea.

On Linux you've got glade (gtk) or qt-designer (Qt), among many other choices.

---


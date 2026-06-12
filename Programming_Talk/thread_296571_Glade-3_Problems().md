---
title: "Glade-3 Problems(?)"
date: 2006-11-09
forum: Programming Talk
---

### Post by JamesWP on 2006-11-09
Hi there, I recently decided to get into the whole c++ thing, and I came across Glade-2. I was immediately impressed and for a moment i kinda had the hang of callbacks and signals etc.
```

sudo aptitude remove glade-2
sudo aptitude install glade-3
```

After reading a tutorial i heard that glade-3 was in the edgy repositories, so i decided to remove glade-2 and install glade-3, this feels a lot nicer to use, however, I'm not sure if its a problem with the way I've set it up or not, but I lack the Build/Compile button in glade-3, when i save, it only saved 'blah.glade', and if i run from the terminal i get these warnings (not sure if these are related, or even matter).

```
** (glade-3:11425): WARNING **: Instantiatable class 'GtkMenuShell' built without a 'generic-name'

** (glade-3:11425): WARNING **: Unable to load icon for GtkMenuShell (Failed to open file '/usr/share/glade3/pixmaps/22x22/widget.png': No such file or directory)

** (glade-3:11425): WARNING **: Unable to load icon for GtkMenuShell (Failed to open file '/usr/share/glade3/pixmaps/16x16/widget.png': No such file or directory)
```

Anyway, any help would be appreciated, it doesn't seem logical that they would remove the build feature from the application.

Thanks! :)

---

### Post by slavik on 2006-11-09
the 1st error I do not understand, the 2nd and 3rd errors are simply missing icons (make placeholder icons?)

it doesn't seem like the 1st error is critical though (since it is only a warning and not an error)

---

### Post by llonesmiz on 2006-11-10
> **JamesWP said:**
> Hi there, I recently decided to get into the whole c++ thing, and I came across Glade-2. I was immediately impressed and for a moment i kinda had the hang of callbacks and signals etc.
```

sudo aptitude remove glade-2
sudo aptitude install glade-3
```After reading a tutorial i heard that glade-3 was in the edgy repositories, so i decided to remove glade-2 and install glade-3, this feels a lot nicer to use, however, I'm not sure if its a problem with the way I've set it up or not, but I lack the Build/Compile button in glade-3, when i save, it only saved 'blah.glade', and if i run from the terminal i get these warnings (not sure if these are related, or even matter).

```
** (glade-3:11425): WARNING **: Instantiatable class 'GtkMenuShell' built without a 'generic-name'

** (glade-3:11425): WARNING **: Unable to load icon for GtkMenuShell (Failed to open file '/usr/share/glade3/pixmaps/22x22/widget.png': No such file or directory)

** (glade-3:11425): WARNING **: Unable to load icon for GtkMenuShell (Failed to open file '/usr/share/glade3/pixmaps/16x16/widget.png': No such file or directory)
```Anyway, any help would be appreciated, it doesn't seem logical that they would remove the build feature from the application.

Thanks! :)

Hi, I'm afraid that code generation has always been discouraged because of maintenance problems(if you change slightly the UI you have to generate again the code and there may be some inconsistencies with the code you wrote manually) so that feature has been removed. The best way to use glade in your programs is using libglade. Libglade allows changing the UI without recompiling. Some links with information regarding glade and libglade:

[http://glade.gnome.org/](http://glade.gnome.org/)
[http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)

So if you really need code generation you have to stick with glade-2. I think that learning to use libglade (or libglademm if you are using c++) it's a very good thing, once you are familiar you'll be able to create applications rather easily. If you install the package "libglademm-2.4-dev" (needed to use libglademm) you can find some examples in the directory:

/usr/share/doc/libglademm-2.4-dev/examples

Good luck.

---

### Post by JamesWP on 2006-11-10
Mmmm thanks for the reply llonesmiz, I'm gonna check libgrademm out and see how it works, if it's going to be better in the long run, I'd prefer to use libglademm instead of Glade-2's code generator :).

---

### Post by JamesWP on 2006-11-10
Finally got home and decided to give the example files a whirl, i started with ```
/usr/share/doc/libglademm-2.4-dev/examples/basic
```

Not sure if i'm using the wrong syntax, i'm meant to be using an entirely different command or not, but when i do 

```
gcc basic.cc
or
g++ basic.cc
```

I get a long block of errors;

```
james@edgyjames:/usr/share/doc/libglademm-2.4-dev/examples/basic$ gcc basic.cc
basic.cc:1:28: error: libglademm/xml.h: No such file or directory
basic.cc:2:19: error: gtkmm.h: No such file or directory
basic.cc:5: error: ‘Gtk’ has not been declared
basic.cc:5: error: expected constructor, destructor, or type conversion before ‘*’ token
basic.cc: In function ‘void on_button_clicked()’:
basic.cc:9: error: ‘pDialog’ was not declared in this scope
basic.cc: In function ‘int main(int, char**)’:
basic.cc:15: error: ‘Gtk’ has not been declared
basic.cc:15: error: expected `;' before ‘kit’
basic.cc:18: error: ‘Glib’ has not been declared
basic.cc:18: error: ‘Gnome’ has not been declared
basic.cc:18: error: ‘refXml’ was not declared in this scope
basic.cc:21: error: ‘Gnome’ has not been declared
basic.cc:23: error: ISO C++ forbids declaration of ‘Gnome’ with no type
basic.cc:23: error: expected `)' before ‘::’ token
basic.cc:23: error: expected `{' before ‘::’ token
basic.cc:23: error: ‘::Glade’ has not been declared
basic.cc:23: error: ‘ex’ was not declared in this scope
basic.cc:23: error: expected `;' before ‘)’ token
basic.cc:31: error: ‘pDialog’ was not declared in this scope
basic.cc:35: error: ‘Gtk’ has not been declared
basic.cc:35: error: ‘pButton’ was not declared in this scope
basic.cc:39: error: ‘sigc’ has not been declared
basic.cc:42: error: ‘kit’ was not declared in this scope

```

Probably just me not having set up a library or something, but can't find a solution for the life of me :P.

---

### Post by llonesmiz on 2006-11-10
I'm sorry I didn't try it before telling you.  It's not as simple as:

gcc basic.c

you need to tell the compiler where to look for the include files and the libraries. There are lots of them, it's not possible to write them all by yourself. There is a program called pkg-config that helps with it but the easiest way to compile a program is using Makefiles. I don't know exactly how to set them up but luckily anjuta does. I was able to compile and execute the program basic.cc using the makefiles from anjuta. You need to install anjuta:

sudo apt-get install anjuta autogen

If you don't have libgtkmm-2.4-dev installed you will need to install it too.

Then you run anjuta, select new->project, forward, select C++ then gtkmm, forward, change the name, forward, select a destination, forward, and apply.

Now to compile the example programs just copy the *.glade file to the src directory under the destination you chose for the project, and copy the contents of the basic.cc to the file main.cc in that directory. Then you press F11 and, after it's compiled, F3 from anjuta (F11 is build, F3 is execute). Or if you are using the command line, go to the src directory enter "make" and then "./gtk-foobar" (or the name you chose in anjuta). I know this solution is pretty lame, but at least it works.

If you want to use the program that anjuta writes by default you need to copy gtk-foobar.glade to the root directory (the directory which contains "src") or else the program will tell you "can't find the file gkt-foobar.glade".

I recommend you install devhelp. Then you can run it by selecting Applications->Programming->Devhelp. It lists documentation you have installed. You can find there a section about libglademm with all the functions you can use.

PS: Reading this you'll be able to tell that English is not my first language. I apologize in advance for any mistakes you'll see.

---


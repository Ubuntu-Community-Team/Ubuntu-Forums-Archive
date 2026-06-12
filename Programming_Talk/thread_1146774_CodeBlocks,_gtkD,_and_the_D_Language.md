---
title: "Code::Blocks, gtkD, and the D Language"
date: 2009-05-02
forum: Programming Talk
---

### Post by nazarel on 2009-05-02
I've tried searching the Ubuntu Forums and have read the FAQs. I've already tried asking this in the Code::Blocks forum, but the topic got locked (because they said it was unrelated to C::B IDE - it is a compiler/linker issue). 
 
I'm running Ubuntu 8.10 with the Code::Blocks IDE. I installed the gtkD library using make and sudo make install. I linked the resulting gtkD library (libgtkd.a) to the C::B Linker Settings under Project > Build Options > Linker Settings, and I added the gtkD folder to the C::B Search Directories tab. I also have the libdl.a and the libc.a linked in. 
 
The program compiles with the warning: 
 
```
Using 'dlopen' in statically linked applications requires at runtime the shared libraries from the glibc version used for linking.
```The program executes, but instead of showing a window, it displays in the terminal: 
 
```
Segmentation Fault
```Here's the code I'm trying to run in C::B (it's from the examples on the gtkD Dsource website):

```
import gtk.MainWindow;
import gtk.Label;
import gtk.Main;

void main(char[][] args)
{
    Main.init(args);
    MainWindow win = new MainWindow("Hello World");
    win.setDefaultSize(200, 100);
    win.add(new Label("Hello World"));
    win.showAll();

    Main.run();
}
```I'm guessing that I need to install another version of the glibc - would anyone know of another version of glibc used for linking? I have the glibc-core version 2.8 installed already through synaptic. I tried searching in the Ubuntu lib packages: [http://packages.ubuntu.com/intrepid/libs/](http://packages.ubuntu.com/intrepid/libs/) - but I can't seem to find it.

Thanks in advance!

---

### Post by Jiraiya_sama on 2009-05-02
This is just a guess, but it seems the libraries for glibc aren't installed. Do you have build-essential installed?

---

### Post by nazarel on 2009-05-02
I installed the build essentials awhile back, and I have the core glibc library installed on my system. The compiler warning seems to suggest that I need another version of glibc installed - one used for linking. I can't seem to locate it.

---

### Post by nazarel on 2009-05-03
Mystery Solved! I simply linked in libdl.so instead of the static libdl.a and the program runs like a dream.

---

### Post by NawaMan on 2009-09-03
Would you mind giving us detail step of setting that up? I am very interested of writing program in D but really but I am not very familiar with tool chain of C (I am from Java and Delphi). So it will really help.

---


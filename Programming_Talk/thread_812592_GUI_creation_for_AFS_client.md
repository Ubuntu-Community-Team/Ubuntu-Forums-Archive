---
title: "GUI creation for AFS client"
date: 2008-05-30
forum: Programming Talk
---

### Post by vishnumrao on 2008-05-30
I am trying to switch to Ubuntu at work. I installed OpenAFS on my machine. But I have to go to the command line to do a "klog username" to login to afs. 

I wish to create a GUI that will prompt me to put in a username and password, just like my windows OpenAFS client does(I tried looking around for a GUI, but was unable to find one, hence decided to make one myself). 

I have never done any linux programming, but have lots of experience with C++. 

Can someone guide me on how to build a GUI to do the above in linux. 

Thanks in advance.
Vishnu Rao.

---

### Post by ad_267 on 2008-05-30
You may find it would be a lot easier to do this using a bash script with zenity. Zenity is used to create gtk dialog boxes with prompts. You can then put this script in ~/bin and create a launcher to run it. Zenity has an option to hide input text which would be useful when entering a password.

This shows some of what zenity can do: 
[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by dtmilano on 2008-05-30
If zenity doesn't fit your bill, give  [autoglade]("http://autoglade.sf.net") a try.
See the rdc (rdp client) example in the tutorial.

---

### Post by vishnumrao on 2008-05-30
Thanks for your replies. I decided to give zenity a try. 

I tried looking into the documentation at: [http://library.gnome.org/users/zenity/unstable/zenity-usage.html.en](http://library.gnome.org/users/zenity/unstable/zenity-usage.html.en) and also some other links that you had provided. But I am unable to find a way to create a GUI with more than one text entry option.

The kind of GUI that I am trying to build is similar to the one one in the file attached to this post. Could you guide me on how to create a GUI with more than one text entry box.

Secondly question: I created a text_script.txt. But how do I execute it? 

Thanks again.
VMR.

---

### Post by ad_267 on 2008-05-30
I'm not sure if zenity supports having multiple text entries in one dialog so maybe using C++, C or python is a better idea unless you use three consecutive dialog boxes for each entry. You can use glade-3 to make very complex guis. This tutorial is pretty good although the last part isn't finished yet: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

To make it executable remove the .txt extension (you don't really need to do this), right click on the file, go to permissions and tick "allow executing file as a program." The first line of the file should be
```
#!/bin/bash
```

If you put this file in a directory bin in your home folder you can run it from anywhere using it's file name

---

### Post by vishnumrao on 2008-05-30
I do need to have a GUI that displays 3 text entry boxes. I am comfortable with C++. How an I create a GUI using C++? 

Is glade3 same as autoglade? 


> **ad_267 said:**
> You may find it would be a lot easier to do this using a bash script with zenity. Zenity is used to create gtk dialog boxes with prompts. You can then put this script in ~/bin and create a launcher to run it. Zenity has an option to hide input text which would be useful when entering a password.

I converted the script to a executable. and can execute from the file browser. How can I execute it from the command line? 

Thanks for your patience.
VMR

---

### Post by ad_267 on 2008-05-30
Autoglade looks like it takes your glade file you have created with glade and can create an application without doing much programming. I haven't used it before so can't be much help with that sorry, but it looks like that might be a good way to go. This looks like a good tutorial: [http://autoglade.wiki.sourceforge.net/autoglade+tutorial+-+first+steps](http://autoglade.wiki.sourceforge.net/autoglade+tutorial+-+first+steps)

Glade is a tool for creating a gui using GTK ([http://www.gtk.org/](http://www.gtk.org/)). There is a GTK binding for C++ ([http://www.gtkmm.org/](http://www.gtkmm.org/), [http://www.gtkmm.org/docs/gtkmm-2.4/docs/FAQ/html/index.html#id2569725](http://www.gtkmm.org/docs/gtkmm-2.4/docs/FAQ/html/index.html#id2569725)) or you can use the C functions with C++.

What glade does is it creates an xml file that describes your gui and can be loaded by your C++ application using GTK.

If you install glade make sure you get glade-3 not glade-2.

To execute it from the command line without having to be in that directory or to execute it from a launcher it needs to be in your PATH. This includes /usr/bin, /usr/local/bin, ~/bin etc. So if it's in a directory bin in your home folder then you can just type the name of the file and it should run.

---


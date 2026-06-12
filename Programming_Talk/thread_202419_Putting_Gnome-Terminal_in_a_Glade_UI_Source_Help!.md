---
title: "Putting Gnome-Terminal in a Glade UI? Source? Help!"
date: 2006-06-23
forum: Programming Talk
---

### Post by OPTIMO on 2006-06-23
I've created a rather nice GUI using Glade and can compile and run it.  However, in the GUI I want one of the boxes to be filled with the terminal, Gnome-terminal, I suppose.

I can't figure out how to add the widget to my UI.  Ideally I'd like to be able to send commands to it without user intervention.  I've written scripts to some good stuff but now I want my GUI to call these scripts via a terminal.

I've been racking my brain for 3 days on this.  The GUI is done, my shell scripts are done, but I can't figure out how to add a terminal widget to my user interface.  Please help.

The empty box to the left of the EXECUTE button is where the terminal will go (I'll make it bigger so it's more useful I suppose).
[IMG]http://www.ubertechnik.com/Utils/project1/esxrc2.JPG[/IMG]

I'm thinking the source code for Gnome-Terminal using vte would help me, but there has to be a much easier way, methinks.

Thanks in advance!

---

### Post by OPTIMO on 2006-06-23
I tried to throw in my callbacks.c so that when the button is pushed it would launch Gnome-Terminal.  I threw this in there:

```
exec("gnome-terminal");
```

but that didn't work.

---

### Post by wmcbrine on 2006-06-23
```

system("gnome-terminal");

```
would work better. However, I'm fairly certain it's not what you want.

Gnome-terminal is no widget. But let's put that aside for the moment... What exactly is it that you *really* want to do? Display the output of commands launched from your GUI? If so, popen() might be the way to go, in combination with something like a textview widget. If there needs to be input, it's a  little more complicated.

---

### Post by skymt on 2006-06-24
Actually, Gnome-Terminal is a widget. Specifically, it uses the VTE widget, so install libvte-dev and read the documentation.

---

### Post by ngine13 on 2008-08-30
Hello guys. :)

I want to make a ui that will display some output of the "smartctl -a /dev/sda" command.

I opened glade and made this :

[IMG]http://users.auth.gr/~pmousoul/images/Screenshot.png[/IMG]

I putted two labels ( Temp, Cycle count) and next to them two textviews..

Under them i putted a button that will close the window.


I did a little search and i found this [site]("http://xrob.wordpress.com/2007/04/20/creating-a-gui-application-using-glade-and-ruby/") that helped me understant how to make the underlying script with "ruby-glade-create-template" command.

I don't know how to connect this ui with the terminal's command output... :( 

Does anyone know where can i find a piece of good documentation, so i can complete similar tasks without wasting much time?

---


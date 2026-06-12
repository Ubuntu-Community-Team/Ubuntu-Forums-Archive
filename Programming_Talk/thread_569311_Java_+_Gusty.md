---
title: "Java + Gusty?"
date: 2007-10-06
forum: Programming Talk
---

### Post by Lemons on 2007-10-06
I have no idea if this belongs here, but its about java programming. But any java programmer tried to use a default look and feel in gusty, and got some GTK crtical errors? These are what I get:

```
(<unknown>:16796): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:16796): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed
```

The combo box works, but it isnt very visually pleasing. I have not found this with any other feature (JCheckBox, JTable, JLabel, JTextPane, JButton, and a few others), so is it just this? atm im just using a list as a work around, but if anyone knows a fix, it would be helpful.

---

### Post by jespdj on 2007-10-07
Which version of Java are you using? Are you using Sun Java or GNU Java?

---

### Post by Lemons on 2007-10-07
Im using Sun's Java 1.0.6_03b05

---

### Post by bonsiware on 2007-10-21
I've posted a bug in launchpad...

[https://bugs.launchpad.net/ubuntu/+bug/150917](https://bugs.launchpad.net/ubuntu/+bug/150917)

It happens to me launching Netbeans 6Beta1 or Sun Java Web Start...

bye

---

### Post by tenmillionmilesaway on 2007-10-21
This is just a hunch but are you using a theme different from the default theme that comes with ubuntu?

Richard

---

### Post by bonsiware on 2007-10-21
I'm using the default Human theme (see attachment)... 
It's not a theme related issue...

---

### Post by tenmillionmilesaway on 2007-10-21
It was just a hunch. Before i have seen similar errors and I assumed that I was because I was using a non-default theme.

---

### Post by geirha on 2007-10-21
Does it work with other versions of java? you can switch between the different java versions installed with update-java-alternatives, unless it's different in Gutsy (this applies for Edgy and Feisty at least)

```
$ sudo update-java-alternatives --list
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj
$ sudo update-java-alternatives --set java-gcj 
...
```

---

### Post by antodasana on 2007-10-21
I'm having the same problem.

java version "1.6.0_02"
Java(TM) SE Runtime Environment (build 1.6.0_02-b05)
Java HotSpot(TM) Client VM (build 1.6.0_02-b05, mixed mode, sharing)

It happens only with JComboBox in any Java Swing aplication, and in my case this is happening since I updated to 7.10, there was no problem with 7.04.

Is it a GTK+ or an Ubuntu 7.10 distribution error?

---

### Post by santiagozky on 2007-10-22
I have the same problem.

Is there any way of disabling the java integration with gnome and use the default swing theme?

---

### Post by bonsiware on 2007-10-22
You can launch netbeans with the following argument:

--laf javax.swing.plaf.metal.MetalLookAndFeel

For the rest I don't know...  :(

---

### Post by santiagozky on 2007-10-22
great. I think that will do for a while. 

thanks for the tip

---

### Post by jede on 2007-10-25
I have the same problem. I think this is a Java bug in the GTK L&F implementation of Swing. The comboboxes in all other Swing application are looking fine. 
BTW: the error "works" on all GTK+ themes, not just for the Human theme.

Bye,
Stefan

---

### Post by tpischke on 2007-10-30
I am seeing this problem too and can say that it has appeared recently.  It started happening either with the upgrade to Java 6 update 3, or the upgrade to gutsy.  GTK is looking great on Java now, with this problem with combo boxes being one of the few remaining blemishes.

---

### Post by jede on 2007-10-30
I've create a bug report in the Java bug database at Sun. Hopefully it will get accepted and fixed...

---

### Post by hugoheden on 2007-10-30
> **jede said:**
> I've create a bug report in the Java bug database at Sun. Hopefully it will get accepted and fixed...

Excellent, thanks. Do you have a link for it? The bug you posted I mean. I'd like to follow what happens to it.

---

### Post by jede on 2007-11-03
It's not accepted yet :-( So there's no link ...
I hope they will not ignore it!!!

---

### Post by jede on 2007-11-05
The bug has been accepted by Sun. Please go there and vote for it!

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6624717](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6624717)

---


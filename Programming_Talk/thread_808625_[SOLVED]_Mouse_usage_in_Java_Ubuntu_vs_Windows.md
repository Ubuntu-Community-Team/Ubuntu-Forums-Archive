---
title: "[SOLVED] Mouse usage in Java: Ubuntu vs Windows"
date: 2008-05-26
forum: Programming Talk
---

### Post by NormR2 on 2008-05-26
I'm porting my Java programs from Windows(XP and 98 ) to Ubuntu and am having a problem in my java program recognizing mouse events on Ubuntu. This program has worked for a long time on Windows up to Java 1.5
I have java 1.6 on Ubuntu.

The mouse event listeners are not being called. The event flag isPopupTrigger() is now being set on mousePressed where before on windows was set on mouseReleased.

Are there mouse settings I need to make?
Is the environment so different that I have to rewrite/design the programs to work on Ubuntu?

Thanks,
Norm

---

### Post by xlinuks on 2008-05-27
I only know that by default on Linux the double click is shorter (somewhat like 200ms, while 400 would be normal, perhaps this has already been fixed). Never heard of what you're talking about.
Can you post your project so we can test it?

---

### Post by dwhitney67 on 2008-05-27
> **xlinuks said:**
> I only know that by default on Linux the double click is shorter (somewhat like 200ms, while 400 would be normal, perhaps this has already been fixed).

There's nothing to fix.  It is configurable!

Goto:  **System->Preferences->Mouse**

Maybe it is Windows that needs to be fixed.

---

### Post by xlinuks on 2008-05-27
It's perhaps my fault, when saying "by default on Linux the double click is shorter" I mean "by default the JAVA configuration on Linux the double click is shorter", and by the way, this issue cannot be solved programmatically, there are workarounds like counting the time between two clicks but that's lame and can't be used in certain situations.

---

### Post by NormR2 on 2008-05-27
The problem is NOT with double click timing. It's with mouse events like right click, pressed and drag. 
I'm attaching a zip with the jar file and the program source.
The program was an attempt at a WYSIWUG GUI builder. 
This is an old program where I wrote my own controls instead of using Swing which was so SLOOOOW then. I've not bothered to rewrite it as it works.

---

### Post by xlinuks on 2008-05-27
Yes that was offtopic.
Since you created that app using awt classes instead of Swing you're supposed to have troubles sooner or later since nobody cares anymore about awt GUI, thus Sun updates it only if there's some security flaw (which is unlikely).
NetBeans has nowadays a nice wysiwyg interface and no offence, it's much better than yours (and much better than mine if I tried writing one), but it's not yet as advanced as the Borland builders and alike.
You might not need/care/have time to switch to Swing, but you have too, the sooner the better I guess.
It's also beneficial cause you can create much more rich GUIs with Swing, not to mention such things like the upcoming Swing Nimbus L&F which I find pretty cool.

---

### Post by NormR2 on 2008-05-30
I've converted the program to use Swing for the GUI building portion of the program and am still not able to get it to work on Ubuntu. Only button, label and textfield are added as Swing components.  Works fine on XP.

I can add a Swing component but then::confused:
 a RC on the component does not put up a popup menu
 a mouse press on a component and drag does not move the component
 a mouse press on a component with ALT moves the whole window vs resizing the component with a mouse drag.

Any suggestions?

---

### Post by xlinuks on 2008-05-30
What IDE are you using?
What's that:
```


import NormsTools.ShowMsgBox;
import NormsTools.ChoiceOfYesOrNo;
import NormsTools.GetInput;
import NormsTools.ShowListBox;
import NormsTools.EditableList;
import NormsTools.EditableListAdder;
import NormsTools.ErrDialog;

```
How can we test it since you didn't post those classes?
I would suggest not developing apps using an anonymous package and also slit the program into several class files, looks like you've learned Java by an old book, ironically so did I as well when I started learning Java and it was pretty disappointing realizing how much time I spent in vain learning deprecated stuff.

---

### Post by NormR2 on 2008-05-30
Thanks for the response. Sorry I didn't include the other classes this time. They are in the zip file I sent earlier in the thread (#5).
I wrote this program years ago. Swing was so SLOOOOOOOW on my system (200Mhz) that I wrote my own JOptionPane type classes for simple user input. I haven't bothered rewriting them as they work OK on windows.

You could comment them all out to see the problems with the mouse. The classes would only be called if the popup menu worked.

Now in trying to learn Linux I thought I port some of my utilities to Linux and see what it took to get them to work. Hence my current problems.

I'm using geany as IDE. I haven't tried the app outside of it yet. I'll give that a try the next time I have Linux up.

---

### Post by xlinuks on 2008-05-30
In the attachments you posted I couldn't find their source code.

---

### Post by NormR2 on 2008-05-30
Sorry, I didn't think you'd need them. I'd be embarassed to show them to anyone as they are very Quick and Dirty.
You should be able to compile the main program by putting the zip file with the class files in the classpath. (haven't tried it myself)
Or just comment out all references to NormsTools programs.

---

### Post by NormR2 on 2008-05-30
Here's a version with all the NormsTools stuff removed. Which means there won't be code there for the popups to call if you get that far.
What this code does (on windows) is add components from the .Add menu, allow you to move them around, resize them (ALT + mouse drag in blue) and get a popup menu when you RC on the panel and a different popup menu when you RC on a component.

---

### Post by achelis on 2008-05-30
Hi

Just trying to see if I understand you right first.

You want to be able to right click the components the user inserts using the add-method?

You are setting the components to enabled=false; after creating them (or rather to some boolean determining whether a test is being run..)

As soon as the components are enabled the components respond to mouse events, which is the expected behavior. 

Let me know if I'm completely missing the mark here :)

EDIT: Just saw you're using 1.5+ and in that case I'd advice you to use generics.

---

### Post by NormR2 on 2008-05-30
Thanks for the response.
The problem (see above) is that I'm not able to move, resize or get popup  menus on any of the added components.
I'll try again with the components enabled (ie Test on)

This program was originally written with JDK 1.3 and has been working for years on windows (98 and XP)

---

### Post by xlinuks on 2008-05-31
You need to re-write your app. You prolly noticed it's getting harder and harder to spot and remove random bugs.
In your case, for instance, not being able to move components is due, in part, that in some parts of the code you (still) add AWT components to a Swing component (which is Swing components are incompatible with AWT), look at the screenshot, there was " add new Button", I changed it to "add new JButton" and after that I could actually move the button, but moving is still kinda awkward - I didn't dig dipper into the reason. Same noticed about CheckBox, renamed to JCheckBox but decided not to test, I hope you understood the idea.
If I were you, I would choose something else to do because what you're doing is not an easy task, or at least redesigning the app with the logic and implementation split apart.

---

### Post by achelis on 2008-05-31
Hmm.. just played around a bit myself. Turns out that MouseEvents are captured even if the component is disabled.

And what xlinuks says makes sense. Heed his words :)

---

### Post by NormR2 on 2008-05-31
Thanks for the advice.
I've converted more of the code to Swing and a few more bits work.
There are differences on the X,Y for the mouse position between Swing and AWT. The positioning code needs to be reworked.
Also on Linux, a RC is recognized on mousePressed vs mouseReleased on Windows.

One problem: how to resize the component. On Ubuntu/GNOME the ALT key with a mouse drag moves the whole window. Can it be turned off so that my program can use it?  I use ALT + mouse drag to resize components.

I use CTL for another function. I'd like to keep the key usages simple, so I chose ALT for resizing, but it's being used on Ubuntu/GNOME.


As I said before, this project is an excuse to learn Linux and Swing. Not that I need the program to work as I do all my development on Windows.
So far Linux has been disappointing. I use a floppy to copy files from XP to Ubuntu and usually have to mount/unmount the floppy a couple times before I can copy the files onto the Linux machine.
Or I have to delete all the files and recopy them on the XP before Ubuntu will see them???:confused:

---

### Post by xlinuks on 2008-05-31
The "shortcut" issue is pretty messy, there are several desktops which handle them differently, in Gnome there's "system-preferences-keyboard shortcuts", there's also "system-preferences-keyboard-layouts-layout options" and you never know which settings supersedes others. I would choose not to use that shortcut at all or to change the key binding in your program, or, which is more difficult, do like jEdit - it has a powerful GUI of choosing every single shortcut for every single action, including for those from the macros and plugins (but again, it's pretty lots to code).

There's an important issue to keep in mind (and stop dreaming): Java, Mono, Python, Perl, Ruby, whatever, all of them who use bindings or alike are second-class citizens on the desktop, no matter how much their fanatics might tell you otherwise, you'll soon understand it as you start developing serious apps on any of these "powerful technologies" (not to confuse "whether can be done" with "how could be done"). It's as usually a matter of trade-off.
The US, despite it's actual state, is one of the most rich countries in the world, I'm sorta amazed that you're using a floppy, why not an USB Flash drive? Much easier, faster, safer and costs a few bucks.

---

### Post by NormR2 on 2008-05-31
Thanks for taking the time to look at my junk.
I have a prototype working and could convert the whole progam some day when the mood hits me.
To get the resizing to work, I changed the ALT/Win behavior in the Keyboard Prefs to Add the standard behavior to Menu key
Then to actually do the resizing, I press on both the ALT key and the win key (between ALT and CTL) and it works.

Not sure what you mean by shortcut. Does that refer to pressing a key while moving the mouse?

I've been retired for years and doubt I'll ever be writing any serious apps. All my code is to solve my personal problems.
For example the Guibuilder was to make building a simple GUI quick and easy. I can write the working code to read files and generate reports or manipulate files etc fairly quickly, but then to write the Gui with input fields, choices, buttons etc doubles the time to write a simple app. So I wrote a Q&D program to generate a tailored gui for any app I write.

The USB plugin for my Linux computer is at the back, behind the desk. Its hard to get to. The floppy reader is on the front, very easy to get to. My programs are 70K, no problem. I use my stick when the files are in the Ms.

Thanks for all your help.
I don't know how all helpers on the forum get time to answer questions for all of us.
Norm

---

### Post by jamesstansell on 2008-05-31
> **NormR2 said:**
> 
The USB plugin for my Linux computer is at the back, behind the desk. Its hard to get to.

If you feel like it sometime you should be able to find an "extension" cable that you can arrange to plugin your usb devices without having to get behind your computer.

---

### Post by NormR2 on 2008-05-31
I find the floppy easier to insert than plugging in a usb, the polarity is easier to see. And I don't have to ask XP if its safe to remove.

---

### Post by xlinuks on 2008-06-01
Basically by "shortcut" I mean any type of accelerator/mnemonic, be it a combination of keyboard keys with or without mouse.

The following link shows how NetBeans can do visual editing, perhaps you'll like it (it's up to day and easy/intuitive):
[http://java.sun.com/docs/books/tutorial/uiswing/learn/index.html](http://java.sun.com/docs/books/tutorial/uiswing/learn/index.html)

If so, since you use JDK 1.3 and netbeans requires at least 1.5, here's a link you can use to download both of them bundled, choose "JDK 6 Update 6 with NetBeans 6.1":
[http://java.sun.com/javase/downloads/?intcmp=1281](http://java.sun.com/javase/downloads/?intcmp=1281)

---

### Post by LaRoza on 2008-06-01
> **NormR2 said:**
> I find the floppy easier to insert than plugging in a usb, the polarity is easier to see. And I don't have to ask XP if its safe to remove.

You have to wait until the data is written, just like you do with a USB drive.

---

### Post by Zugzwang on 2008-06-01
> **NormR2 said:**
> I find the floppy easier to insert than plugging in a usb, the polarity is easier to see. And I don't have to ask XP if its safe to remove.

The following is way off-topic, but: You can easily configure XP to write everything onto the pen drive immediately. This way it won't complain if you unplug it after everything has been written.

Even more OP: Does anyone know how to do this with Hardy?

---

### Post by NormR2 on 2008-06-01
Thanks again.
Xlinuks:
I'm not currently using 1.3. I used it when I wrote the GuiBuilder program. I now have 1.6  I've tried Netbeans but find it slow. I use WinEdit as my IDE on XP.

LaRoza - my floppy problem on Linux is getting Linux to read the floppy that was written on XP. I insert the floppy on Linux, mount it and about half the time Linux is NOT able to find any valid data. Sometimes I umount it and mount it again and it works. Sometimes I take the floppy back to XP, delete all files on it, copy the files I want, take it back to Linux and mount finds the files OK. Never can tell when it will work.
Haven't had any problem on XP reading a file written to the floppy by Linux.

---


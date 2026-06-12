---
title: "WYSIWYG designer for GUI toolkits"
date: 2009-05-29
forum: Programming Talk
---

### Post by Volt9000 on 2009-05-29
I'm writing an application in Python with a GUI. I haven't decided on a GUI toolkit yet, but perhaps the answer to this question will help my decision: 

Are there any GUI toolkits for which WYSIWYG visual editors exist? I mean kind of like how Visual Studio has its nice drag-and-drop form designer. I would much prefer to use one so I can quickly design a GUI without having to worry about hand-coding coordinates.

---

### Post by crdlb on 2009-05-29
All the major contenders have a GUI designer: for gtk+ you can use glade, for Qt I believe it's called QtDesigner, and wx has something called wxGlade. (I've heard wxGlade is the weakest of the three)

Note that you shouldn't be positioning widgets by coordinates anyway, instead you should use boxes, tables, etc. so that the layout can scale.

---

### Post by EXCiD3 on 2009-05-29
wxGlade is terrible but if you are planning anything cross-platform wx is the best choice as it will use the native toolkits it has available on the current OS. I have used it a lot for developing [Keryx]("http://keryxproject.org").

Glade-3 is excellent and so is QtDesigner. If you are not going cross-platform, then one of these is good choice. I prefer Glade because I'm a gnomer but QtDesigner felt to be more complete.

Just my opinions on the subject. Take it with a grain of salt. :P

---

### Post by Volt9000 on 2009-05-29
Thanks for your suggestions.

I like the idea of wxGlade using the platform's native widgets, but what makes it so bad?

---

### Post by Simian Man on 2009-05-29
I agree with crdlb - you should *never* use absolute positioning for your GUIs.  Use of gui design tools can sometimes lead to this bad practice.  I think you should go with wxWidgets.  Very cross-platform and has great Python bindings.

---

### Post by lykwydchykyn on 2009-05-29
Check out Eric with qtdesigner 4.  They seem to make a good combination.  

Though honestly, I just usually end up going back to hand-coding the GUI.  Just meshes with my brain better.

---

### Post by EXCiD3 on 2009-05-29
wxGlade just is poor at generating the python code after you drag/drop the widgets. You can design it just fine but it sets some wacky default settings which I never intended and made the interface look funky. It also does not give you access to quite a few of the extra widgets that are available. Its really best to work by coding the interface by hand IMO. You get to know the toolkit a lot better that way.

The native widget part is excellent, nothing against that, just wxGlade.

Also, to just state the idea one more time so you realize how important it is. Absolute positioning (which is what Visual Studio does) is the dumbest thing ever invented. I may take you a little while to grasp the idea of using sizers and other containers to hold your widgets and keep track of their sizing for you but it makes much more sense to do it that way instead of th way you are used to with Visual Studio. I was in the same boat as you a while back and it took me a while to understand sizing widgets in these other toolkits, but VS is the odd man out when it comes to widget sizing because it's the only one that uses absolute positioning.

---

### Post by Volt9000 on 2009-05-30
> **EXCiD3 said:**
> wxGlade just is poor at generating the python code after you drag/drop the widgets. You can design it just fine but it sets some wacky default settings which I never intended and made the interface look funky. It also does not give you access to quite a few of the extra widgets that are available. Its really best to work by coding the interface by hand IMO. You get to know the toolkit a lot better that way.

The native widget part is excellent, nothing against that, just wxGlade.

Also, to just state the idea one more time so you realize how important it is. Absolute positioning (which is what Visual Studio does) is the dumbest thing ever invented. I may take you a little while to grasp the idea of using sizers and other containers to hold your widgets and keep track of their sizing for you but it makes much more sense to do it that way instead of th way you are used to with Visual Studio. I was in the same boat as you a while back and it took me a while to understand sizing widgets in these other toolkits, but VS is the odd man out when it comes to widget sizing because it's the only one that uses absolute positioning.

Ah I see, thanks for the explanation.
I'm just used to the absolute positioning/sizing thing because of my background in Windows GUIs.

However, in this particular case, this application will (most likely) run in a fixed, unsizable window, so in this case sizers would be pointless.

---

### Post by Majorix on 2009-05-30
I once coded the GUI of a small application using wxGlade, editing/adding code on the output in the Python language.

There is no Visual-Studio-alike IDE for Python.

However, if you want an alternative, and have time to learn Java, I would really suggest Netbeans. In my thoughts, it is a really good environment that may well be compared to Visual Studio on Windows.

---

### Post by lykwydchykyn on 2009-05-30
Qt designer will do absolute positioning if you don't use any layout objects.

---

### Post by happysmileman on 2009-05-30
> **EXCiD3 said:**
> 
Glade-3 is excellent and so is QtDesigner. If you are not going cross-platform, then one of these is good choice. I prefer Glade because I'm a gnomer but QtDesigner felt to be more complete.

Both GTK and Qt are cross-platform.
Gimp and Pidgin among others are written using GTK and are available for many platforms.
And Opera, Skype, VLC and Adobe Photoshop Album (Though not Photoshop itself) all use Qt.

---

### Post by EXCiD3 on 2009-05-31
They are both cross-platform of course, but they require the toolkit to be installed instead of using the native widget system, which I much prefer.

---


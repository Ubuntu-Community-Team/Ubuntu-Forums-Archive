---
title: "Alice ran twice, and now wont start"
date: 2007-08-16
forum: Programming Talk
---

### Post by Tyke91 on 2007-08-16
I need to use the program "Alice" for my computer science class at school. I don't have the option of running it in windows as there are no longer any windows computers in my home (that genuine advantage thing finally sent my family over the edge and now we use ubuntu :D ).

Basically, i downloaded and unpacked the program. The only instructions in the readme were to run the file "Alice-run" which worked twice.

on a third try however, it didn't start. when i ran it in a terminal, i got this response 

```
 attempting to register mp3 capability... 
Registered succesfully
java.lang.IndexOutOfBoundsException: Invalid index
        at javax.swing.DefaultRowSorter.convertRowIndexToModel(DefaultRowSorter.java:497)
        at sun.swing.FilePane$SortableListModel.getElementAt(FilePane.java:525)
        at javax.swing.plaf.basic.BasicListUI.updateLayoutState(BasicListUI.java:1337)
        at javax.swing.plaf.basic.BasicListUI.maybeUpdateLayoutState(BasicListUI.java:1288)
        at javax.swing.plaf.basic.BasicListUI.getCellBounds(BasicListUI.java:929)
        at javax.swing.JList.getCellBounds(JList.java:1600)
        at javax.swing.JList.ensureIndexIsVisible(JList.java:1116)
        at sun.swing.FilePane.ensureIndexIsVisible(FilePane.java:1514)
        at sun.swing.FilePane.doDirectoryChanged(FilePane.java:1440)
        at sun.swing.FilePane.propertyChange(FilePane.java:1487)
        at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:339)
        at java.beans.PropertyChangeSupport.firePropertyChange(PropertyChangeSupport.java:276)
        at java.awt.Component.firePropertyChange(Component.java:7865)
        at javax.swing.JFileChooser.setCurrentDirectory(JFileChooser.java:568)
        at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.worldsDirectoryChanged(AuthoringTool.java:478)
        at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.dialogInit(AuthoringTool.java:631)
        at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.<init>(AuthoringTool.java:413)
        at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:131)


```

the ```
attempting to register mp3 capability... 
Registered succesfully
``` is normal, the rest is not.

what's going on? :confused::confused:

---

### Post by pmasiar on 2007-08-16
you could link to "alice" you downloaded, so we know what are you using. Alice is rather popular with Google :-)

---

### Post by Tyke91 on 2007-08-16
sorry, i thought alice was more popular than it is :)

[http://www.alice.org/downloads/authoringtool/](http://www.alice.org/downloads/authoringtool/)

---

### Post by pmasiar on 2007-08-16
I can see PC and Mac versions only. Which one did you used? Do you use some emulators? Or from sources? Which version? 

Maybe for others it is obvious, but my ESP is cloudy tonight. :-)

---

### Post by Tyke91 on 2007-08-16
lol... there's a link that says "info for linux"

i clicked it and it took me to a download page

i need this program for class and only have linux... wondering if i should now buy a mac for school :P

---

### Post by pmasiar on 2007-08-16
Oh! it was so tiny I missed it.

That page says: 
"This release of Alice for Linux is more a proof-of-concept than an official release. There are lots of bugs which we are working to fix...."

"We have tested this out on Fedora Core 5 and a custom version of Fedora Core 2. "

So my best bet would be to get Fedora Core 2, and try it there. Report a bug!

---

### Post by Tyke91 on 2007-08-16
heh... ill try

gunna be hard not to work on ubuntu tho... still love this os :lolflag:

---

### Post by Rorke on 2008-06-07
I'd be interested in your progress. My kids love 'Alice' and I recently binned Windows for Ubuntu. Took me 2 weeks to iron out things, and I still run a VirtualBox - but if you do get it running on Ubuntu, please post here :-)
Thanks

---


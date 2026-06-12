---
title: "Java GUI Tabbed Pane Problem"
date: 2009-08-05
forum: Programming Talk
---

### Post by Igniteflow on 2009-08-05
Hi, I'm trying to build a GUI for a working program I have using NetBeans.  I know how to assign EventListeners to buttons, but I want to have a tabbed pane so the user can click on a tab for ease of use.  However, when the user clicks on the the tab the panels and buttons etc associated with that tab do not appear, this is the same for all the tabs.  Any ideas?

---

### Post by pacofvf on 2009-08-05
Is quite hard to help you without some code...if you are using frames, maybe you forgot to set visible the frame where the pane is packed.
```

        frame.pack();
        frame.setVisible(true);

```
other common mistake is to forget to add items to the pane:
```

        JPanel panel = new JPanel(false);
//you make some stuff like buttons
        panel.add(button1);
        panel.add(button2);
        .
        .

```

---

### Post by CatsRninja on 2009-08-05
Not quite, if you are using netbeans grafic interface to build the GUI,you dont actualy need to mess with the code.

I dont remember what hotkey it was, but in the view menu(or equivalent) you can watch the relations between componets, just check if it is as you wanted, and if the buttons you created are present, in its options check also if its marked as visible.

You gave poor information about your case, im kinda guessing here.

---

### Post by Igniteflow on 2009-08-10
Thank you for the help, sorry if my problem description was too vague.  I've just realised that all I need to do was drag the bottom border of the tabbed pane container down to the bottom of the GUI and now the panels show up fine :oops:

---


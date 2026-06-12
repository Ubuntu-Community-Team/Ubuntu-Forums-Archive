---
title: "Java help with LayoutManager"
date: 2009-12-28
forum: Programming Talk
---

### Post by SpinningAround on 2009-12-28
I'm working on a little program in Java that will monitor my traffic amount there is a few things left but at the moment I'm trying to find a way to setup the Layout so it get the Layout as seen in picture two in attachment. The first attachment show how it looks now with flowlayout.

---

### Post by doas777 on 2009-12-28
try a border layout. may be more what you need.

---

### Post by SpinningAround on 2009-12-28
> **doas777 said:**
> try a border layout. may be more what you need.
Might be possible but there are eight elements
JLabel
JTextField
JPanel
JLabel
JTextField
JLabel
JTextField
JPanel

---

### Post by kahumba on 2009-12-28
I'd use a javax.swing.BoxLayout for the content pane and then add all the widgets, thus:
(1) The BoxLayout must do vertical layou (PAGE_LAYOUT)
(2) (Since we're dealing with BoxLayout) we need to have each widget's preferredSize etc. set up properly.
(3) Each object must be in the center: setAlignmentX(Component.CENTER_ALIGNMENT).

Attached example source code as a NetBeans ( 6.8 ) project and a screenshot.

---

### Post by kahumba on 2009-12-28
Trying again to attach the screenshot.
Edit: oh nevermind, it's already there, looks like a glitch in the ubuntuforums.

---

### Post by SpinningAround on 2009-12-28
Thanks solved it got it in a straight line now.

---


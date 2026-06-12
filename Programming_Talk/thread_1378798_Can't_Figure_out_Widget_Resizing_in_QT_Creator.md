---
title: "Can't Figure out Widget Resizing in QT Creator"
date: 2010-01-11
forum: Programming Talk
---

### Post by not_a_phd on 2010-01-11
Using qtCreator 1.2 (also 1.3) on Karmic. I have not had a lot of luck getting my widgets on the form to resize. I am trying to set up a tabbed UI. I am able to get the tabWidget to resize by calling:
[CODE] setCentralWidget(ui->tabWidget); [\CODE]


But, I can't figure out how to get a plainTextEdit widget to resize that is placed inside one of the tabs. I am afraid that this code in the constructor is probably hosing up the internal widget layouts.



This seems pretty basic. I have tried dropping a layout widget in the tab first, but to no avail.


I have searched long and far for some decent layout tutorials, and they are out their, just no one showing me my specific problem.


I was laboring under the assumption that the various layouts auto-resized with the parent components. I also though that the parent child relationship between widgets in the designer was established in the tree-view of the widgets. Am I wrong?



The QT Forum is completely overrun with spam right now, or I would go there first.


Suggestions?

---


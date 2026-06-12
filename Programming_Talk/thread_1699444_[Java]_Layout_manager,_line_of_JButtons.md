---
title: "[Java] Layout manager, line of JButtons"
date: 2011-03-03
forum: Programming Talk
---

### Post by SpinningAround on 2011-03-03
I got a JPanel that is inside a JScrollPane and to the JPanel are JButtons added, starting from 1. What I would like to do is to have JButtons accepted there preferred size and if more are added to the JPanel then what it can show then should the scrollpane allow it to grow.

What I would like is something like GridLayout but without the expanding, if I only add one JButton the it take up the entire JPanel. I tried with GridBagLayout but if I add more JButtons than fit inside the JPanel then will the JButtons collapse.

EDIT: SOLUTION
setting minimumSize solved it
[php]JComponent.setMinimumSize(new Dimension(width, height));[/php]

---

### Post by myrtle1908 on 2011-03-03
Horizontally or vertically?  Either way, an unknown number of buttons are not really suited for presenting options in this manner.

If horizontal use a MenuBar or a ToolBar.

If vertical consider a Tree or a List.

As an aside, to ease the pain when creating Java/Swing GUIs you would be better served using NetBeans.

---


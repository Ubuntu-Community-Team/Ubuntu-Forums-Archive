---
title: "How Resize JOptionPane?"
date: 2010-04-23
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-04-23
Does anyone know how to resize a JOptionPane?  The message is a JPanel and the JPanel changes size based on what is selected in the JPanel.  Is there any way to resize the enclosing JOptionPane?  The question that led to this question is posted here -- for more background:

[http://ubuntuforums.org/showthread.php?p=9160348&posted=1#post9160348](http://ubuntuforums.org/showthread.php?p=9160348&posted=1#post9160348)

---

### Post by SNYP40A1 on 2010-04-24
> **SNYP40A1 said:**
> Does anyone know how to resize a JOptionPane?  The message is a JPanel and the JPanel changes size based on what is selected in the JPanel.  Is there any way to resize the enclosing JOptionPane?  The question that led to this question is posted here -- for more background:

[http://ubuntuforums.org/showthread.php?p=9160348&posted=1#post9160348](http://ubuntuforums.org/showthread.php?p=9160348&posted=1#post9160348)

Did you try 			SwingUtilities.getWindowAncestor(this).pack();?

Lazy bastard.

---


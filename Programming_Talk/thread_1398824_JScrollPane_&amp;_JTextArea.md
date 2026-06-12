---
title: "JScrollPane &amp; JTextArea"
date: 2010-02-05
forum: Programming Talk
---

### Post by Finalfantasykid on 2010-02-05
```
this.bioPanel = new JScrollPane();
        this.bioPanel.setBorder(new TitledBorder("Biography"));
        
        this.text = new JTextArea();
        this.text.setLineWrap(true);
        this.text.setWrapStyleWord(true);
        this.text.setEditable(false);
        this.text.setOpaque(false);
        this.bioPanel.getViewport().add(this.text);

```

This will add a JTextArea to a JScrollPane.  My only problem that the scrollpane starts at the very bottom of the text.  I would like it to start at the beggining instead, but I have been unable to find an appropriate method to do this.

---

### Post by Zugzwang on 2010-02-05
Probably this one?: [http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/JViewport.html#setViewPosition(java.awt.Point](http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/JViewport.html#setViewPosition(java.awt.Point))

---


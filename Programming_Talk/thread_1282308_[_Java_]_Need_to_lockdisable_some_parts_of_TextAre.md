---
title: "[ Java ] Need to lock/disable some parts of TextArea content."
date: 2009-10-04
forum: Programming Talk
---

### Post by credobyte on 2009-10-04
All I need is a way to lock the highlighted string. I mean, I need it to be there, no matter what user does ( Backspace ). Any ideas ?

```
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Shell extends JFrame {
    
    public Shell() {
        setSize(500, 250);
        setTitle("Winux Shell");
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        
        JPanel panel = new JPanel();
        getContentPane().add(panel);
        panel.setLayout(null);
        
        JTextArea shellInput = new JTextArea([COLOR=Red]"user@winux: "[/COLOR], 5, 20);
        getContentPane().add(shellInput);
        
        JScrollPane scrollPane = new JScrollPane(shellInput);
        getContentPane().add(scrollPane);
    }
    
    public static void main(String args[]) {
        Shell shell = new Shell();
        shell.setVisible(true);
    }
    
}

```

---

### Post by Zugzwang on 2009-10-04
You can write a custom document class which only performs changes to this text if the part of the text is not changed and plug it into the JTextArea.

See here for details: [http://java.sun.com/javase/7/docs/api/javax/swing/text/Document.html](http://java.sun.com/javase/7/docs/api/javax/swing/text/Document.html)

---

### Post by Reiger on 2009-10-04
Or alternatively use 2 components one being editable and another component not being editable at all; but make it look like it is only one area. You would update the latter area on <enter> so that the number of lines in the non-editable area is always 1 more than the number of lines in the editable area. It also simplifies some more complicated matching scenario's when continuations (>) and variable paths possibly with wildcards (~) come into play, as well as the issue that it makes no sense to edit history in a running shell session.

---

### Post by PaulM1985 on 2009-10-04
If you want the text to remain there and not be edited by the user, you can use the setEditable() method on the JTextField object if the user has done a mouse drag event on the object.  When the user clicks, you could set it as editable again.

Paul

---

### Post by credobyte on 2009-10-04
> **PaulM1985 said:**
> If you want the text to remain there and not be edited by the user, you can use the setEditable() method on the JTextField object if the user has done a mouse drag event on the object.  When the user clicks, you could set it as editable again.

Paul

JTextField doesn't exist and I don't think that using labels or text fields along with my text area would be a good idea - how would I select multiple lines, including [COLOR=Gray]user@winux[/COLOR] ( which obviously would be a separate element ) ?

---

### Post by PaulM1985 on 2009-10-05
Sorry, I meant setEditable on the JTextArea.

Paul

---


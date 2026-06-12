---
title: "Handle events in Java"
date: 2023-04-11
forum: Programming Talk
---

### Post by ronakmehta on 2023-04-11
First [COLOR=#232629][FONT=-apple-system]Here's the code:
[/FONT][/COLOR]```
[COLOR=var(--highlight-keyword)][FONT=inherit]package[/FONT][/COLOR][COLOR=var(--highlight-color)][FONT=inherit] javaapplication1;[/FONT][/COLOR]

[COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR] javax.swing.*;
[COLOR=var(--highlight-keyword)][FONT=inherit]import[/FONT][/COLOR] java.awt.event.*;

 [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Elem[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]implements[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]ActionListener[/FONT][/COLOR]{

    [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]perform[/FONT][/COLOR][FONT=inherit]()[/FONT]{
        [COLOR=var(--highlight-namespace)][FONT=inherit]JFrame[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]frame[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JFrame[/FONT][/COLOR]();
        JButton button;
        button = [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JButton[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]"Button"[/FONT][/COLOR]);
        frame.getContentPane().add(button) ;
        frame.setSize(400,400);
        frame.setVisible([COLOR=var(--highlight-literal)][FONT=inherit]true[/FONT][/COLOR]);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        button.addActionListener([COLOR=var(--highlight-literal)][FONT=inherit]this[/FONT][/COLOR]);
     }

    [COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]actionPerformed[/FONT][/COLOR][FONT=inherit](ActionEvent ev)[/FONT]{
        button.setText([COLOR=var(--highlight-variable)][FONT=inherit]"Clicked"[/FONT][/COLOR]);
    }
}

 [COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]class[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]JavaApplication1[/FONT][/COLOR] {

  [COLOR=var(--highlight-keyword)][FONT=inherit]public[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]static[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]void[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]main[/FONT][/COLOR][FONT=inherit](String[] args)[/FONT] {
   [COLOR=var(--highlight-namespace)][FONT=inherit]Elem[/FONT][/COLOR] [COLOR=var(--highlight-variable)][FONT=inherit]obj[/FONT][/COLOR] [FONT=inherit]=[/FONT] [COLOR=var(--highlight-keyword)][FONT=inherit]new[/FONT][/COLOR] [COLOR=var(--highlight-literal)][FONT=inherit]Elem[/FONT][/COLOR]();
   obj.perform();
  }   [COLOR=var(--highlight-color)][FONT=inherit]}[/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system]

[/FONT][/COLOR]I just finished my first event-based GUI in Java, but I'm not sure where I went wrong. When no event handling was used, the code functioned perfectly.

---

### Post by TheFu on 2023-04-12
Too hard to read the code with all the attempted, but failed, extra formatting.  Post plain text, without any highlighting.  Syntax highlighting is often incorrect and should never be trusted.

---


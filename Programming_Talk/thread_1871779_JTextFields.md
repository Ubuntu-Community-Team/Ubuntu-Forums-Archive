---
title: "JTextFields"
date: 2011-10-29
forum: Programming Talk
---

### Post by raac on 2011-10-29
Is there a way to execute an event when someone types on a text field. I googled it, and I found something like 
```

theTextField.addActionListener(new TextFieldListener());

    private class TextFieldListener implements ActionListener {

        public void actionPerformed(ActionEvent event) {
            System.out.println("EVENT");
        }
    }
```


But the event only executes when I hit ENTER on the text box.

I want it to execute whenever I TYPE on the text box, any ideas?

---

### Post by ofnuts on 2011-10-29
> **raac said:**
> Is there a way to execute an event when someone types on a text field. I googled it, and I found something like 
```

theTextField.addActionListener(new TextFieldListener());

    private class TextFieldListener implements ActionListener {

        public void actionPerformed(ActionEvent event) {
            System.out.println("EVENT");
        }
    }
```
But the event only executes when I hit ENTER on the text box.

I want it to execute whenever I TYPE on the text box, any ideas?
What you want is a TextListener that receives TextEvent. But if you really want to act on the text contents (convert oto uppercase on the fly, etc), you should extend the JTextField class to provide a different model, see the introduction in [http://download.oracle.com/javase/6/docs/api/javax/swing/JTextField.html](http://download.oracle.com/javase/6/docs/api/javax/swing/JTextField.html)

---


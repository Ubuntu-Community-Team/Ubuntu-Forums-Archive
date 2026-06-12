---
title: "A few java questions"
date: 2006-06-28
forum: Programming Talk
---

### Post by Horsman on 2006-06-28
I'm currently finishing up a suduko solving app, mainly an experiment to figure out swing development.

[img]http://img236.imageshack.us/img236/7005/screenshot2dy.png[/img]

It works, but I have a few questions.

How do you make a textfield have only a certain amount of characters?
How to you make a text field automatically select it's text when you tab to it?

Thanks in advance for the help.

---

### Post by xeero on 2006-06-29
[QUOTE=Horsman]
How do you make a textfield have only a certain amount of characters?
How to you make a text field automatically select it's text when you tab to it?
[/QUOTE]

It does seem strange, but seems like there's no built in mechanism to limit input size.  Tried this and it doesn't work:

    JTextField txtTitle = null;
    txtTitle = new JTextField(15);
    txtTitle.setMaximumSize(new java.awt.Dimension(12,1));

It doesn't do what I wanted it to do.  I don't have time to try these right now, but found some possible solutions.. but not sure if there's a difference between TextField and JTextField in this situation.

[Limit TextField input to a maximum length]("http://www.rgagnon.com/javadetails/java-0227.html")

[Limit JTextField input to a maximum length]("http://www.codeguru.com/java/articles/444.shtml")

This one looks like the simplest solution.  
[JTextField max length]("http://www.experts-exchange.com/Programming/Programming_Languages/Java/Q_21754218.html")
Scroll down to:
```

textfield.addKeyListener(new KeyAdapter() {
            public void keyTyped(KeyEvent e) {
                String text = textfield.getText();
                int length = text.length();
                if (length == maxChars) {
                    e.consume();
                } else if (length > maxChars) {
                    // show your error message
                }
            }
```

To select the text when someone tabs into the text field, my guess is that you'd also use an action listener.  look for the right event (sorry but can't research this right now for the right event) and then call the text field's selectAll() method (which is inherited from TextComponent).

hope this helps!

---

### Post by Horsman on 2006-06-29
Thanks for the bits of help so far! I'll post the program up soonish!

---

### Post by mlind on 2006-06-29
You could also use DocumentFilter, and attach it to your textfield.
Or extend PlainDocument and customize the behaviour that you want to
happen when text is

```

private static class MyDocumentFilter extends DocumentFilter {
	private int size;
		
	public MyDocumentFilter(int size) {
		this.size = size;
	}
		
	@Override
	public void replace(FilterBypass fb, int offset, int length, String text, AttributeSet attrs) throws BadLocationException {
		if (fb.getDocument().getLength() + text.length() > size) {
		     return;
		}
			
		super.replace(fb, offset, length, text, attrs);
	}
}

//
JTextField field = new JTextField(10);
PlainDocument model = (PlainDocument) field.getDocument();
model.setDocumentFilter(new MyDocumentFilter(5));

```


For text selection, this could work
```

field.addFocusListener(new FocusListener() {
	public void focusGained(FocusEvent e) {
		((JTextComponent)e.getSource()).selectAll();
	}

	public void focusLost(FocusEvent e) {
		((JTextComponent)e.getSource()).setSelectionEnd(0);
	}	
});

```

---


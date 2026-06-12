---
title: "Adding listeners to a JTextField"
date: 2005-10-26
forum: Programming Talk
---

### Post by NeoChaosX on 2005-10-26
Okay, I need some help here. I need to add a listener to a JTextField that gets the data that's in the JTF. However, everytime I run the program, I keep getting NullPointerExceptions when the Listener runs. Here's my code for adding the listener - 

```
JTextField tf = new JTextField("" + d.getValueAt(i), 20);
final JTextField f = tf;
tf.addActionListener(new ActionListener()
{
    public void actionPerformed(ActionEvent e)
    {
       int value = Integer.getInteger(f.getText());
       // remaining code here
       . . .
    }
});
```

From the readouts on the code, it's messing up where it's doing the getText() method. So, am I doing this right? Or is there another way to add a Listener that will check for changes in the TextField without blowing up with NullPointerExceptions?

---

### Post by LordHunter317 on 2005-10-27
Post more code (pref whole .java file).  I think your issue is f isn't declared in a scope where you can actually access it, but because of the brokeness of Java's inner class system, code is being emitted that tries anyway.

---

### Post by NeoChaosX on 2005-10-27
Actually, I figured it out. f is being accessed just fine, it's that I was using the wrong method to get the integer out of the string. What I should've done was Integer.parseInt(), not getInteger() - the latter returns null when trying to read the text in the TextField. Thanks for helping, though.

---


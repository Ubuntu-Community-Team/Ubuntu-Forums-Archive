---
title: "resize java button"
date: 2010-02-01
forum: Programming Talk
---

### Post by ubudog on 2010-02-01
Hello, in my program, I have a java button and a textview.  If I try to run them at the same time, the button comes on top, and I cant see the textview.  Is there a piece of code I can use to resize the button to make it smaller?

---

### Post by TennTux on 2010-02-01
I'm assuming your programming in Java if you have a Java Button, though, the answer may be different if your using JavaScript.

The answer has more to do with how you create / insert the button and text view into the window, frame, dialog, etc. Unfortunetly you havn't provided quite enough info to answer your question. How about a small code sample.

---

### Post by ubudog on 2010-02-01
```
TextView tv = new EditText(this);
        tv.setText("I am text");
        setContentView(tv);
        tv = new Button(this);
        tv.setText("I am a button");
        setContentView(tv);
```

Hope that helps.

---

### Post by kahumba on 2010-02-01
1) imo that's not enough, ideally one should be able to reproduce your problem.
2) Just in case: "new Button()" - are you using java.awt.Button? That stuff has been deprecated before Jesus Christ was born.

---

### Post by myrtle1908 on 2010-02-01
What is setContentView?  Is this some non-AWT/Swing UI incarnation?  With Java, typically one employs a Layout Manager (e.g BorderLayout, FlowLayout) to handle the placement of widgets.

---

### Post by ubudog on 2010-02-02
Nevermind, sorry about this.  Figured it out. [http://lmgtfy.org/?q=resize+java+button]("http://lmgtfy.org/?q=resize+java+button")

---


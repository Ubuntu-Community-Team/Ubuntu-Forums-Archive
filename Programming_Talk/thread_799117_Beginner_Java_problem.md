---
title: "Beginner Java problem"
date: 2008-05-18
forum: Programming Talk
---

### Post by ConMan318 on 2008-05-18
I have just begun learning Java and I typed this code:
```

import javax.swing.*;

public class TestJava {
   public static void main(String[] args) {
      JFrame frame = new JFrame("Hello, Java!");
      JLabel label = new JLabel("Hello, Java!", JLabel.CENTER);
      frame.getContentPane().add(label);
      frame.setSize(300, 300);
      frame.setVisible(true);
   }
}

```
Upon compiling, this error is generated:
```

connor@connor-laptop:~/Documents/programs/java$ javac TestJava.java
TestJava.java:6: warning: The static field SwingConstants.CENTER should be accessed directly
        JLabel label = new JLabel("Hello, Java!", JLabel.CENTER);
                                                         ^^^^^^
1 problem (1 warning)

```
It still runs the program, except when the window opens it doesn't close, then it grays out and I have to force a quit.  I'm not sure if this problem is related to the error or not.

But how can I access the static field SwingConstants directly?

---

### Post by drubin on 2008-05-18
```
SwingConstants.CENTER
```

also there is an option something like
```
JFrame.setDefaultCloseOption(JFrame.EXIT_ON_CLOSE)
```

I could be wrong about the exact parameters but think the function is right.

---

### Post by mike_g on 2008-05-18
Yeah, its more like:
```

frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

```
By in my experience that has always already been set somewhere. Dunno, maybe Netbeans did it automatically for me.

I'm not sure if youre going about centering the text in the JLabel correctly; or at least I have never done it that way. This should work:
```
JLabel label = new JLabel("Hello, Java!");
label.setHorizontalAlignment(SwingConstants.CENTER);
```

---

### Post by drubin on 2008-05-18
> **mike_g said:**
> Yeah, its more like:
```

frame.setDefaultCloseOperation(WindowConstants.EXIT_ON_CLOSE);

```
By in my experience that has always already been set somewhere. Dunno, maybe Netbeans did it automatically for me. 


The fact I wrote JFrame.EXIT_ON_CLOSE is still valid as Source code for JFrame is 
```
JFrame ..... implements WindowConstants (Some where up the component tree.)
```

Also im my experience if your idea is doing some thing to your code with out your knowledge you might want to check it out? :) as this is not the default behavior of a base JFrame. 

The default behavior is.
JFrame.DO_NOTHING_ON_CLOSE;

---

### Post by mike_g on 2008-05-18
Well, I did say that I use netbeans, and like I said it seems to set the default close operation to exit by default. Also, the code you originally posted wouldent work for me, probably cos you wrote its as setDefaultCloseOption.

---

### Post by drubin on 2008-05-19
> probably cos you wrote its as setDefaultCloseOption.

:) sorry was a late, night.

---


---
title: "how to run java swing programs from terminal?"
date: 2013-10-08
forum: Programming Talk
---

### Post by vamshikrishna072 on 2013-10-08
hi i am newbie,

I am having a problem in  running swing programs from terminal
I installed open JDK 7
My current version : javac 1.7.0_25

THIS IS MY SAMPLE PROGRAM 

import javax.swing.JFrame;
import javax.swing.SwingUtilities;
public class Sampleswing extends JFrame
{
public Sampleswing()
{

setTitle("sample example");
setSize(300,200);
setLocationRelativeTo(null);
setDefaultCloseOperation(EXIT_ON_CLOSE);
}
public  static void main(String[] args)
{


SwingUtilities.invokeLater(new Runnable(){
public void run()
{
Sampleswing ss=new Sampleswing();
}
});
}
}

when i compile :
javac Sampleswing.java
java Sampleswing

no window is opening and no output

please tell me how to run swing and applet programs from terminal?

---

### Post by Erik1984 on 2013-10-08
I could be wrong but I see no code to actually display the JFrame you could try to add these two lines to the constructor of Sampleswing

```

pack()
setVisible(true)

```

---

### Post by vamshikrishna072 on 2013-10-08
ya that was a mistake .
but this program ran well in NETBEANS.

---


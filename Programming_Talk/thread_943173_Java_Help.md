---
title: "Java Help"
date: 2008-10-09
forum: Programming Talk
---

### Post by Master_Odin on 2008-10-09
Sorry if this is the wrong forum. Noticed a FAQ for setting up JAVA (compiling/running), so thought this was the place for this kind of thing. Anyway...

Not sure why the hell this is happening to me, but basically, the only way I can sum up my problem is whenever I use a JOptionPane.* object (or is it method, I'm a newb to this stuff), it'll show the nice little pop-up and than basically crash. I can manually stop the code using eclipse, but if I run it through Terminal, the pop-up never disappears, I can't hit the "Ok" button or the "X" button to get rid of it. Annoying as hell. Basically, the following code:
```

import javax.swing.*;
public class popTest {
	public static void main(String[] args) {
		JOptionPane.showMessageDialog(null, "Hello, World!");
		System.exit(0);
	}
}

```
does what I want it to (create a message pop-up), I just can't get rid of it.

Any suggestions?

---

### Post by doas777 on 2008-10-09
I usually pass this into the optionpane

```

JOptionPane.showMessageDialog(this, "Hello, World!");

```

no idea id it will help. googleing 'JOptionPane.showMessageDialog crashes' did turn up a number of hits. do you have a stacktrace of the error?
what does the exception look like if you trap your call in a try/catch?

---

### Post by Master_Odin on 2008-10-09
Thanks for the search tip. Was searching something completely idiotic ("eclpise pop-up crashes"). Found what I was looking for here:
[http://ubuntuforums.org/archive/index.php/t-684511.html](http://ubuntuforums.org/archive/index.php/t-684511.html)

Apparently, all I had to do was change the compiler and all is now right with the world. Damn eclipse for using a crappy compiler :P

Thanks for the comment though doas777, though I have no idea what you meant by "do you have a stacktrace of the error?" I'm a complete newb to Java programming. :P

---

### Post by doas777 on 2008-10-10
> **Master_Odin said:**
> Thanks for the search tip. Was searching something completely idiotic ("eclpise pop-up crashes"). Found what I was looking for here:
[http://ubuntuforums.org/archive/index.php/t-684511.html](http://ubuntuforums.org/archive/index.php/t-684511.html)

Apparently, all I had to do was change the compiler and all is now right with the world. Damn eclipse for using a crappy compiler :P

Thanks for the comment though doas777, though I have no idea what you meant by "do you have a stacktrace of the error?" I'm a complete newb to Java programming. :P

I'm glad you got it going! 

a stacktrace is the standard output as a java program crashes. if you are using the terminal to run the class, then it jsut prints there. in eclipse, it prints in the output pane when the app crashes.

a stacktrace basically just tells you where the program crashes. it looks like gibberish at first, but you'll pick it up. 

an exception is an object that expresses information about an error. exception handling is a bigger concept but if your taking a class you'll prolly cover it. if not check out [this]("http://java.sun.com/docs/books/tutorial/essential/exceptions/").

good luck and have fun,
Franklin

---


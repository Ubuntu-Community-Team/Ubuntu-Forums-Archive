---
title: "[java] javax.Swing."
date: 2008-06-24
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-24
Hello,

I am attempting to learn how to create a GUI using the swing methods. I am using eclipse to do the programming and am using Ubuntu 8.04. Using the code below i am trying to create a simple window which should create a 100x100 pixel window with a single label inside with the text "Testing". This is carried out successfully but after about 5 seconds of running the background of the window turns greay (meaning it froze) and a few seconds after that the window indicating that it has indeed frozen appears and gives me the option to force quit it. I have tried using the eclipse compiler and the java command in the terminal. I am confused as to why this is happening and have no real answers for my self and was hoping someone could point me in a direction that could solve this problem.

Thank you very much
~Cody Woolaver

```

import javax.swing.*;

public class Test extends JFrame{
	
	private static final long serialVersionUID = -8015882300734993465L;
	
	public static void main(String args[]) {
		new Test();
	}
	
	Test()
	{
		JLabel jlbHelloWorld = new JLabel("Testing");
		add(jlbHelloWorld);
		this.setSize(100, 100);
		
		setVisible(true);
	}
}

```

---

### Post by myrtle1908 on 2008-06-24
Could this be the problem?

[http://ubuntuforums.org/showthread.php?p=5167618#post5167618](http://ubuntuforums.org/showthread.php?p=5167618#post5167618)

---

### Post by Zugzwang on 2008-06-24
Works well here. By the way, you forget to call "setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);" to make sure that the application terminates when closing the window.

---

### Post by fyplinux on 2008-06-24
I runned the code on my machine, there is no problem. 

It might be as myrtle1908 suggested, there is the problem with the java runtime.

---


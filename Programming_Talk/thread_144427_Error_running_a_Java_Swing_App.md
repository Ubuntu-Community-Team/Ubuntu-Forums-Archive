---
title: "Error running a Java Swing App"
date: 2006-03-14
forum: Programming Talk
---

### Post by icyisamu on 2006-03-14
Tried to compile the following code using javac.

Compiled using Javac. Obtained Interface.class and Interface$1.class
How can I use Jar on the generated classes? Do I need to use a Manifest file to get it done? If so, how?
I tried to set it on Interface class but it isn't working.

(there are some empty codes in there, I plan to add them on later, after this problem is solved.)
```

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Interface extends JFrame implements ActionListener{

private static int height,width;
private JButton btnClick;

public Interface(){
btnClick = new JButton("Hello World");

getContentPane().add(btnClick);

}

public void actionPerformed( ActionEvent e) {



} // End actionPerformed

public static void main(String args[]){

Interface i = new Interface();
i.setSize(300,300);
i.setVisible(true);

i.addWindowListener(new WindowAdapter() {
			public void windowClosing(WindowEvent e) {
				System.exit(0);
			}
		});

} // End Main

} // End Class


```

---

### Post by simon.schmidt on 2006-03-14
You don't really need a manifest file, this should work:
jar cf Interface.jar Interface.class
or possibly *.class instead of Interface.class if you have more files

---

### Post by icyisamu on 2006-03-14
[QUOTE=simon.schmidt]You don't really need a manifest file, this should work:
jar cf Interface.jar Interface.class
or possibly *.class instead of Interface.class if you have more files[/QUOTE]

Hi, I tried as you said, but I got this error:

```

@desktop:~/Desktop/Java/App# jar cf Interface.jar *.class
@desktop:~/Desktop/Java/App# java -jar Interface.jar
Failed to load Main-Class manifest attribute from Interface.jar

```

---

### Post by simon.schmidt on 2006-03-14
[QUOTE=icyisamu]Hi, I tried as you said, but I got this error:

```

@desktop:~/Desktop/Java/App# jar cf Interface.jar *.class
@desktop:~/Desktop/Java/App# java -jar Interface.jar
Failed to load Main-Class manifest attribute from Interface.jar

```[/QUOTE]

ok, make a file called manifest that contains only :
```
Main-Class: Interface
```
and then:
jar cmf manifest myjar.jar *.class

---

### Post by icyisamu on 2006-03-14
It worked!

Thanks alot ;)

---

### Post by hod139 on 2006-03-14
For all the goodies on working with Jar files, see [http://java.sun.com/docs/books/tutorial/deployment/jar/](http://java.sun.com/docs/books/tutorial/deployment/jar/)

---


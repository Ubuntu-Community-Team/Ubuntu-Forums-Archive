---
title: "javax.swing elements don't show up"
date: 2007-06-20
forum: Programming Talk
---

### Post by Ru$$i@N on 2007-06-20
Hi there,

I'm using Ubuntu 7.04 x64.
It seems to me that I've installed java6 jdk, but when i compile a program under Geany with JLabel, JButton, and stuff, I can't see any of it. I do see the frame though. I copied the code from a book word-to-word...

What am I not getting here?

---

### Post by Brendan Hart on 2007-06-20
add this to your code maybe 
```
import javax.swing.*;
```

---

### Post by Ru$$i@N on 2007-06-20
............................ :roll:
geee, thanks. I already have that. I wrote that I have copied the text exactly from a book.
The program works fine under x32 Windoz, so it's not the program that's troubling me.

---

### Post by Modred on 2007-06-20
Given that I don't have the book you mention, or if I do I don't know so since you didn't give a name, it might help to post some of the code.  I intially thought you had forgot to set the visibility, but if you see the frame, that doesn't seem to be the problem.  If it works on Windows, it could be problem with the java install.  I don't know enough about Java on 64 bit to give an answer to that, though.

[http://dmartin.org/weblog/how-to-get-java-swing-apps-working-under-beryl-or-compiz-including-java-web-start](http://dmartin.org/weblog/how-to-get-java-swing-apps-working-under-beryl-or-compiz-including-java-web-start)
Are you running Beryl or Compiz?  This appears to be a common problem and that link may be able to help.

---

### Post by Ru$$i@N on 2007-06-20
Here's the code
```

//Application001.java

import javax.swing.*;

public class Application001 extends JFrame {

	JTextField username = new JTextField(15);
	JPasswordField password = new JPasswordField(15);
	JTextArea comments = new JTextArea(4,15);

	public Application001() {
		super("Feedback Form");
		setSize(260,160);
		setDefaultCloseOperation(EXIT_ON_CLOSE);

		JPanel pane = new JPanel();

		JLabel usernameLbl = new JLabel("Username: ");
		JLabel passwordLbl = new JLabel("Password: ");
		JLabel commentsLbl = new JLabel("Comments: ");

		comments.setLineWrap(true);
		comments.setWrapStyleWord(true);

		pane.add(usernameLbl);
		pane.add(username);
		pane.add(passwordLbl);
		pane.add(password);
		pane.add(commentsLbl);
		pane.add(comments);

		setContentPane(pane);

		show();
	}

	public static void main(String[] args) {
		Application001 app = new Application001();
	}
}

```

I tried to avoid Swing, and found examples with just AWT. Works fine.

Yeah, i'm running Beryl.
Thanks for the link. I think this might just be my problem.

---

### Post by ScottLij on 2007-06-20
> **Ru$$i@N said:**
> Yeah, i'm running Beryl.
Thanks for the link. I think this might just be my problem.

I'm sure this is the problem.  I'm running compiz and Java elements don't show up on my frame when I run Java programs with compiz running.

---

### Post by Ru$$i@N on 2007-06-20
Yup, it's Beryl.
When I set the window manager to Metacity, everything works perfectly.
And now the frostwire works fine too, and i think azureus should work also.
Thanks everybody. ;)

---


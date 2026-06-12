---
title: "JOptionPane works with double but how do I make it work with int?"
date: 2009-09-07
forum: Programming Talk
---

### Post by s3a on 2009-09-07
The following is a sample piece of code I have:

```
import javax.swing.JOptionPane;

public class If

{
	public static void main (String [] args)
	
	{
		double number;
		String input;
		
		input = JOptionPane.showInputDialog("Enter a number");
		number = Double.parseDouble(input);
		
		if (number >= 5.0)
		JOptionPane.showMessageDialog(null, "Big");
		
		if (number < 5.0)
		JOptionPane.showMessageDialog(null, "Small");
		
System.exit(0);
		
	}
}
```

Why doesn't this work and how can I make it work?:

```
import javax.swing.JOptionPane;

public class If

{
	public static void main (String [] args)
	
	{
		int number;
		String input;
		
		input = JOptionPane.showInputDialog("Enter a number");
		number = Int.parseInt(input);
		
		if (number >= 5.0)
		JOptionPane.showMessageDialog(null, "Big");
		
		if (number < 5.0)
		JOptionPane.showMessageDialog(null, "Small");
		
System.exit(0);
		
	}
}
```

---

### Post by baizon on 2009-09-08
Read this:
[http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Integer.html#parseInt%28java.lang.String,%20int%29]("http://java.sun.com/j2se/1.5.0/docs/api/java/lang/Integer.html#parseInt%28java.lang.String,%20int%29")

---


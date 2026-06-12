---
title: "JOptionPane question (Java)"
date: 2009-09-07
forum: Programming Talk
---

### Post by s3a on 2009-09-07
What is wrong with this? (I get one compilation error):

```
import.javax.swing.JOptionPane;

public class AverageScore

{

	public static void main (String [] args)
		
		{
			
			double score1;
			double score2;
			double average;
			
			String input;
			
			
[b]			input = JOptionPane.showInputDialog("Enter score #1:");
			score1 = Double.parseDouble(input);
			
			input = JOptionPane.showInputDialog("Enter score #2:");
			score2 = Double.parseDouble(input);[/b]
			
			average = (score1 + score2)/2.0;
			
			J.OptionPane.showMessageDialog(null, "The average is " + average);
			
			System.exit(0);
			
		}
		
}
```

Also would it work if it was like this?:

```
import.javax.swing.JOptionPane;

public class AverageScore

{

	public static void main (String [] args)
		
		{
			
			double score1;
			double score2;
			double average;
			
			String input;
			
			
			[b]score1 = JOptionPane.showInputDialog("Enter score #1:");
			
			score2 = JOptionPane.showInputDialog("Enter score #2:");[/b]
			
			average = (score1 + score2)/2.0;
			
			J.OptionPane.showMessageDialog(null, "The average is " + average);
			
			System.exit(0);
			
		}
		
}
```

---

### Post by baizon on 2009-09-07
You got 2 syntax errors in line 1 and 24. Change it to:

```
import javax.swing.JOptionPane;
...
JOptionPane.showMessageDialog(null, "The average is " + average);
```

Edit:
> **s3a said:**
> 
Also would it work if it was like this?:


No, this wont work because:
[http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/JOptionPane.html]("http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/JOptionPane.html")

I think you mean something like that:
```
import javax.swing.JOptionPane;

public class AverageScore {

	public static void main (String [] args)
			{
				double score1;
				double score2;
				double average;
				
				score1 = Double.parseDouble(JOptionPane.showInputDialog("Enter score #1:"));
				
				score2 = Double.parseDouble(JOptionPane.showInputDialog("Enter score #2:"));
				
				average = (score1 + score2)/2.0;
				
				JOptionPane.showMessageDialog(null, "The average is " + average);
				
				System.exit(0);
			}
			
}
```

---

### Post by SunSpyda on 2009-09-07
Don't post the exact same question on both Debian User Forums AND Ubuntu Forums.

I've left a response to the one you left on Debian User Forums, so look at that.

---


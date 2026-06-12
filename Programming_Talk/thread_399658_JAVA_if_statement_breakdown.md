---
title: "JAVA if statement breakdown"
date: 2007-04-02
forum: Programming Talk
---

### Post by ClinicalMistake on 2007-04-02
Hey yall.  I can't seem to get my if statements to execute.  I believe the code to be correct, but somewhere the logic is failing.  Any ideas?

```
import javax.swing.*;
public class Conversions {
	public static void main(String args[]) {
		String choice, input;
		double result;
		
		choice = JOptionPane.showInputDialog(null, "If you would like to convert from feet ot meters or vice versa" +
											"\nInput either \"meter\" or \"feet\"");
		if(choice=="feet") {
			input = JOptionPane.showInputDialog(null, "How many feet would you like to convert to meters?");
			result = Double.parseDouble(input) * 3.305;
			JOptionPane.showMessageDialog(null, "When converting " +input + "feet, you have " +result + " meters");
		}
		else if(choice=="meter") {
			input = JOptionPane.showInputDialog(null, "How many meters would you like to convert to feet?");
			result = Double.parseDouble(input) / 3.305;
			JOptionPane.showMessageDialog(null, "When converting " +input + " meters, you have " +result + " feet");
		}
		System.exit(0);
	}
}
```

---

### Post by proalan on 2007-04-02
you can't use the conventional <=, ==, >= operators for string comparison, they are used to check that 2 objects are the same

use

equals()
compareTo()

instead

e.g. choice.equals("feet")

---

### Post by ClinicalMistake on 2007-04-02
Awesome!  Thank you very much!
I can't understand what my teacher is saying in class, so I think I miss out on a lot of information, this is very helpful!

---


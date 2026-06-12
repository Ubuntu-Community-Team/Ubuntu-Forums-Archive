---
title: "Java I/O Dialogs help"
date: 2008-09-20
forum: Programming Talk
---

### Post by carl_pr on 2008-09-20
The user will enter 10 numbers and I need the program to give of the 10 entered number which one is the biggest (more value) and how many times it repeat itself in those 10 entered number. Lets say the user entered 3 times 100 and thats the biggest the program will give

biggest value : 100
repeat: 3 times
 
i have this so far, i have to do it using I/O dialogs. how can i do that? maybe if else, i try but nothing. 

```

import javax.swing.*;

public class Valores 
{
	public static void main (String args[])
	{
		String str1Number, str2Number, str3Number, 
		str4Number, str5Number, str6Number, str7Number,
		str8Number, str9Number, str10Number;
		
		double firstNumber, secondNumber, thirdNumber,
		fourthNumber, fifthNumber, sixthNumber, seventhNumber,
		eighthNumber, ninthNumber, tenthNumber;
		
		str1Number = JOptionPane.showInputDialog("Enter the first number");
		str2Number = JOptionPane.showInputDialog("Enter the second number");
		str3Number = JOptionPane.showInputDialog("Enter the third number");
		str4Number = JOptionPane.showInputDialog("Enter the fourth number");
		str5Number = JOptionPane.showInputDialog("Enter the fifth number");
		str6Number = JOptionPane.showInputDialog("Enter the sixth number");
		str7Number = JOptionPane.showInputDialog("Enter the seventh number");
		str8Number = JOptionPane.showInputDialog("Enter the eighth number");
		str9Number = JOptionPane.showInputDialog("Enter the ninth number");
		str10Number = JOptionPane.showInputDialog("Enter the tenth number");
		
		firstNumber = Double.parseDouble(str1Number);
		secondNumber = Double.parseDouble(str2Number);
		thirdNumber = Double.parseDouble(str3Number);
		fourthNumber = Double.parseDouble(str4Number);
		fifthNumber = Double.parseDouble(str5Number);
		sixthNumber = Double.parseDouble(str6Number);
		seventhNumber = Double.parseDouble(str7Number);
		eighthNumber = Double.parseDouble(str8Number);
		ninthNumber = Double.parseDouble(str9Number);
		tenthNumber = Double.parseDouble(str10Number);
		
		
		


		
		JOptionPane.showMessageDialog
		(null, "It repeats "  , "Operation Results", JOptionPane.PLAIN_MESSAGE);
		
		
	}

}

```

---

### Post by screech on 2008-09-20
You could use a Map for counting and Collections.max() to get the maximum.

Here is an example:

```

import java.util.Collections;
import java.util.HashMap;
import java.util.Map;
import javax.swing.JOptionPane;

public class Input {

    public static void main(String[] args) {
        String[] strNumber = new String[10];
        Map<Double, Integer> count = new HashMap<Double, Integer>();
        
        for (int i = 0; i < 10; i++) {
            strNumber[i] = JOptionPane.showInputDialog("Enter number #" + (i + 1));
            Double num = Double.parseDouble(strNumber[i]);
            if (count.containsKey(num)) {
                count.put(num, count.get(num) + 1);
            } else {
                count.put(num, 1);
            }
        }
        
        double maximum = Collections.max(count.keySet());
        
        JOptionPane.showMessageDialog(null, "biggest value: " + maximum + "\n" +
                "repeat: " + count.get(maximum));
        
    }
}

```

---

### Post by LaRoza on 2008-09-20
Here is the answer: [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---


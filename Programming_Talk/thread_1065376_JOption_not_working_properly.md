---
title: "JOption not working properly"
date: 2009-02-09
forum: Programming Talk
---

### Post by green_lantern on 2009-02-09
couldn't find a fitting directory for this thread, mods please help

Hello,

I wrote a java program with a JOption input box, using the text editor. It compiles and doesnt give runtime errors with the terminal but when the first dialog box appears the programs seems to stop. However using an IDE the dialog boxes work as expected. Something im not doing?

---

### Post by dmizer on 2009-02-09
Moved to programming talk.

---

### Post by HotCupOfJava on 2009-02-09
Please post your code. Then we can probably spot the problem quickly.

---

### Post by green_lantern on 2009-02-10
> **HotCupOfJava said:**
> Please post your code. Then we can probably spot the problem quickly.

the code is fine, as I implied it works with an IDE but here it is:

```
import javax.swing.*;
public class multidimArrays
{
	public static void main(String args[])
	{
		int table[][] = new int[13][13];
		String strFirstFactor,
		           strSecondFactor;
		int    firstFactor,
        		secondFactor,
        		i,
        		j;
		for(i=0; i<=12; i++)
		{
			for (j=0; j<=12; j++)
			{
				table[i][j] = i * j;
			}
		}
		strFirstFactor = JOptionPane.showInputDialog("First Factor");
		strSecondFactor = JOptionPane.showInputDialog("Second Factor");
		firstFactor = Integer.parseInt(strFirstFactor);
		secondFactor = Integer.parseInt(strSecondFactor);
		JOptionPane.showMessageDialog(null, "The product is " + table[firstFactor][secondFactor],"Multiplication Table" ,JOptionPane.PLAIN_MESSAGE);
	}
}

```

This program works fine in linux with an IDE and on windows with command line and IDE. The problem is that the terminal doesent seem to manage the dialogs well.

---

### Post by HotCupOfJava on 2009-02-10
> **green_lantern said:**
> 
This program works fine in linux with an IDE and on windows with command line and IDE. The problem is that the terminal doesent seem to manage the dialogs well.

Ah, I wasn't aware of this part. I originally thought perhaps the IDE had done some automatic packaging or something else that might be throwing you. That's why I wanted to see. I just tested your code from the terminal on my Linux box and it executes fine. I'm curious: which Java Virtual Machine are you using? Did you get your Java through the repositories? I have noticed little bugs with some of the GNU project java packages (no offense Richard). I prefer to use Sun's stuff.

---

### Post by green_lantern on 2009-02-10
> **HotCupOfJava said:**
> Ah, I wasn't aware of this part. I originally thought perhaps the IDE had done some automatic packaging or something else that might be throwing you. That's why I wanted to see. I just tested your code from the terminal on my Linux box and it executes fine. I'm curious: which Java Virtual Machine are you using? Did you get your Java through the repositories? I have noticed little bugs with some of the GNU project java packages (no offense Richard). I prefer to use Sun's stuff.

I think that is it my friend. I will uninstall the JVM form the repos use sun's instead.

---


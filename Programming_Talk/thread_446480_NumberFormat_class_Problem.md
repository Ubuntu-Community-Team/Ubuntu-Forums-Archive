---
title: "NumberFormat class Problem"
date: 2007-05-17
forum: Programming Talk
---

### Post by Ameliorate on 2007-05-17
I have a problem with this class:

package chapter5;
import java.text.NumberFormat;
import java.util.Locale;
import javax.swing.JOptionPane;
import javax.swing.JTextArea;

public class Interest {
	public static void main(String args[])
	{
		double amount, principal = 1000.0, rate = 0.05;
		NumberFormat moneyFormat = NumberFormat.getCurrencyInstance(Locale.US);
		JTextArea outputArea = new JTextArea();
		outputArea.setText("Year\tAmount on deposit\n");
		
		for(int year = 1; year<=10;year++)
		{
			amount = principal*Math.pow(1.0+rate, year);
			outputArea.append(year+"\t"+moneyFormat.format(amount)+"\n");
		}
		JOptionPane.showMessageDialog(null, outputArea, "Interest over 10 Years", JOptionPane.PLAIN_MESSAGE);
		System.exit(0);
	}
}



there are no errors at compile time. However, at runtime I get this error and i dont know why:

Exception in thread "main" java.lang.IllegalArgumentException: The currency code, $, is not supported.
   at java.util.Currency.getInstance(libgcj.so.70)
   at java.text.DecimalFormatSymbols.getCurrency(libgcj.so.70)
   at java.text.DecimalFormat.getCurrency(libgcj.so.70)
   at java.text.NumberFormat.getCurrencyInstance(libgcj.so.70)
   at chapter5.Interest.main(Interest.java:11)

and the eclipse console displays this in the headbar:
<terminated> Interest [Java Application] /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/java

Is there a problem with the gcj?                                                  ^^^

---

### Post by Ramses de Norre on 2007-05-17
It works perfect here on sun jre 6.0, so I guess it's gcj or your locale settings.

---

### Post by Ameliorate on 2007-05-18
How would i fix this problem?

---

### Post by Ramses de Norre on 2007-05-18
Have you got any serious reason to choose gcj over sun's jre? If gcj isn't compatible with some java classes you can file a bug report or search for another class that does the same and does work with gcj... I don't know a better solution (but I don'"t know much about gcj neither).

---

### Post by slavik on 2007-05-20
might be that gcj is outdated (since it is only java 1.4, the code might be 1.5 or 1.6)

---

### Post by Ameliorate on 2007-05-20
What is the best way to uninstall gcj?

(Please include a set of steps :) )

---

### Post by samjh on 2007-05-20
Firstly, at line18, the variable **amo unt** should be **amount** :)
```
outputArea.append(year+"\t"+moneyFormat.format(**amo unt**)+"\n");
```

Second, use the "code" tags to preserve code formatting when posting source code on these forums.

Third, you don't have to remove GCJ.  Just install Java5 or Java6 from Synaptic (open up Synaptic and search for "java", and find packages starting with sun-java*.  And then use this command:
```
sudo update-alternatives --configure java
```to set what kind of Java you want to use.

---

### Post by Ramses de Norre on 2007-05-21
Use **sudo update-java-alternatives -s *version*** to set all java alternatives once, find the version with **sudo update-java-alternatives -l**.

---


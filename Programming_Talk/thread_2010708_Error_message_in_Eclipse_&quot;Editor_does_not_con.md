---
title: "Error message in Eclipse: &quot;Editor does not contain a main type&quot;"
date: 2012-06-25
forum: Programming Talk
---

### Post by jhargis1012 on 2012-06-25
Hello.

I'm still new at Linux and programming so please forgive the newbie question.

I am learning Java programming and I would like to move my projects to Ubuntu. I downloaded Eclipse as my IDE, and it was working fine for me for a while (I was able to edit, run, and save programs). I dual boot with Windows 7 and I've done most of my programming work in Windows. I store and access all my Java files on the Windows partition at /media/Windows7_OS/Users/Jeremy/Documents/Study - Java 1/linux/TestEclipse/src.

When I boot up, I first open Ubuntu's file browser and open the Windows partition so it is mounted. Then I open Eclipse. I am able to view the code for my *.java files, but suddenly for some reaosn when I try to run them I get this error: "Editor does not contain a main type". That is strange to me because I've tried it on several Java programs that I know work just fine in Windows (although I don't use Eclipse in Windows).

I skimmed Google and either the situation in which others had similar errors didn't apply to me or I didn't understand the solutions.

Thank you in advance for your help!

Here is an example of the code I'm working on:

```

import javax.swing.*;
public class StudentIDArray
{
   public static void main(String[] args)
	{
	   int[] studentIDs = {1234, 2435, 3456, 4567, 5678, 6789, 7890, 8901, 9012, 0123};
		String[] firstNames = {"John", "Ben", "Mary", "Sally", "Fred", "Biff", "Diane", "Justin", "Pete", "Laura"};
	   double[] gradeAverage = {2.3, 3.1, 4.0, 2.5, 3.6, 3.3, 3.1, 2.9, 3.8, 3.7};
		final int NUMBER_OF_STUDENTS = 10;
		String inputString;
		int inputNumber;
		String selectedName = "";
		double selectedGPA = 0;
		boolean validID = false;
		do
		{
		   inputString = JOptionPane.showInputDialog(null, "Enter the student ID of the student >>");
		   inputNumber = Integer.parseInt(inputString);
			for(int x = 0; x < NUMBER_OF_STUDENTS; ++x)
		   {
		      if(inputNumber == studentIDs[x])
			   {
			      validID = true;
				   selectedName = firstNames[x];
				   selectedGPA = gradeAverage[x];
			   }
		   }
		}
		while(validID == false);
		   JOptionPane.showMessageDialog(null, "Information for student " + inputNumber + ":\n Name: " + selectedName +
			   "\n GPA: " + selectedGPA);
	}
}

```

---


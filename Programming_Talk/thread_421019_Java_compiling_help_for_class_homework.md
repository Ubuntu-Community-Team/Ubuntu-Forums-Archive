---
title: "Java compiling help for class homework"
date: 2007-04-24
forum: Programming Talk
---

### Post by ClinicalMistake on 2007-04-24
Hey, this may seem strange, but can anyone compile this and run it? I just finished typing it for school and currently my java complier wont work (broke when I upgraded to feisty.) and I really don't have the time to fix it or wait until our IT building opens in the morning (I need sleep!).  The code is pretty much all good, but I want to make sure all of the logic works.  Thanks in advance!

Please - let me know if you have any errors!

```
import javax.swing.*;
public class StudentRecord {
	Student[] CardStack= new Student[6];
	public void main(String args[]) {
		boolean notdone;
		String Input;
		int number;
		int[] sort= new int[6];
		
		for( int i=0; i<6; i++)
			sort[i]=i;
		
		for (int i=0; i<6; i++)
			CardStack[i].scoreList();
		
		notdone=true;
		while(notdone) {
			
			Input= menuChoice();
			
			if (Input=="A") {
				
				Input= JOptionPane.showInputDialog(null, "Which test would you like to sort?\n" +
						"Choose a test 1-4");
				number= Integer.parseInt(Input);
				SortScores(sort, number);
			
				System.out.println("--------------------------------------" +
						"\nThis is a sorted list for test " +number);
				for (int i=0; i<6; i++)
					System.out.println("\n" +CardStack[sort[i]].getName()+ ": " + CardStack[sort[i]].getScore(number));
				System.out.println("\n--------------------------------------");
			} 
			
			else if (Input=="B") {
				SortNames(sort);
			
				for (int i=0; i<6; i++)
					System.out.println(CardStack[sort[i]].getName() + "\n");
			}
			
			else if (Input=="P") {
				for (int i=0; i<6; i++)
					CardStack[i].scoreList();
			}
			
			else if (Input=="E") {
				notdone=false;
			}
		}
		for (int i=0; i<6; i++)
			CardStack[i].scoreList();
		
		System.exit(0);
	}
	
	public void SortScores(int[] cardNumList, int scoreNum) {
		for(int j=cardNumList.length; j>=2; j--)
			for(int k=0; k<j-1; k++)
				if(CardStack[cardNumList[k]].getScore(scoreNum) > CardStack[cardNumList[k+1]].getScore(scoreNum))
					swap(cardNumList, k, k+1);
	}
	
	public void SortNames(int[] cardNumList) {
		for(int j=cardNumList.length; j>=2; j--)
			for(int k=0; k<j-1; k++)
				if(CardStack[cardNumList[k]].getName().compareTo(CardStack[cardNumList[k+1]].getName()) > 0)
					swap(cardNumList, k, k+1);
	}
	
	public static void swap(int[] a, int pos1, int pos2) {
		int temp= a[pos1];
		a[pos1]= a[pos2];
		a[pos2]= temp;
	}	
	
	
	private static String menuChoice () {
		return JOptionPane.showInputDialog(null, "Enter A to choose a test and then sort it in ascending order by lowest to highest student grade\n" +
				"Enter B to sort the student's alphabetically and then display their grades\n" +
				"Enter P to print a list of all of the student's grades\n" +
				"Enter E to exit the program");
	}
}

class Student {
	int[] Scores= new int[4];	
	String Name;
	
	Student() {
		this.Name= JOptionPane.showInputDialog(null, "Input the student's name");
		for (int i= 0; i< 4; i++) 
			this.Scores[i]= (int) (Math.random()*100);
	}
	
	public void scoreList() {
			System.out.println("--------------------------------------------------------------------------------------------\n" +
					"Information for Student:" +Name+"\n");
			for(int i= 0; i<4; i++) {
				System.out.println("Test " +i+1+ "Score:" +Scores[i]+ "\n");
			}
			System.out.println("---------------------------------------------------------------------------------------------\n\n");
	}
	
	public int getScore(int number) {
		return Scores[number-1];
	}
	
	public String getName() {
		return Name;
	}
}
```

---

### Post by Ramses de Norre on 2007-04-24
You've got a non static main method? Java doesn't want to run that here... And changing it to static gives more problems with references to the instance variable.

---


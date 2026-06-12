---
title: "Free program that convert pound to kilos and inchs to cms and feet to metres code"
date: 2008-01-27
forum: Programming Talk
---

### Post by zivxx on 2008-01-27
hey, for those who talk to people around the world, and ask their weight and height i made a program just for you!
when you runing this program after compiling it will ask you for inchs,pounds or feets value...after you enter it it will calcute and give you the results, inchs to Cms feets to Metres and Pound to Kilos...have fun guys...btw its in C#

[PHP]// main program
using System;
public class Sup
{
	public static void Main()
	{
		string Exit="";
		while (Exit !="exit")
		{
			if (Exit!="1"&&Exit!="2"&&Exit!="3")
			{
				Console.WriteLine("choose a menu");
				Console.WriteLine("1 Inch To Centimeter Converter");
				Console.WriteLine("2 Pound To KiloGrams Converter");
				Console.WriteLine("3 Feet To Meter Converter");
				Exit=Console.ReadLine();
			}
			//program 1
			if (Exit=="1")
			{
				double inch,centimeter;
				Console.WriteLine("enter inch value");
				inch=double.Parse(Console.ReadLine());
				centimeter=inch*2.54;
				Console.WriteLine(centimeter);
				Console.WriteLine("what menu would you like to go back to?(for the main menu choose something which is not 1 2 or 3)");
				Exit=Console.ReadLine();
			}
			//program 2
			if (Exit=="2")
			{
				double pound,kg;
				Console.WriteLine("enter pounds value");
				pound=double.Parse(Console.ReadLine());
				kg=pound*0.4535924;
				Console.WriteLine(kg);
				Console.WriteLine("what menu would you like to go back to?(for the main menu choose something which is not 1 2 or 3)");
				Exit=Console.ReadLine();
			}
			//program 3
			if (Exit=="3")
			{
				double meter,feet;
				Console.WriteLine("enter feet value");
				feet=double.Parse(Console.ReadLine());
				meter=0.3048*feet;
				Console.WriteLine(meter);
				Console.WriteLine("what menu would you like to go back to?(for the main menu choosing something which is not 1 2 or 3)");
				Exit=Console.ReadLine();
			}
		}
	}
}
	[/PHP]

---

### Post by LaRoza on 2008-01-27
(You should give the method to compile and run it)

I wrote these:

[http://laroza.freehostia.com/home/index.php?p=opera](http://laroza.freehostia.com/home/index.php?p=opera)

---

### Post by seventhc on 2008-01-27
I thought C# was windows specific....does C# run on ubuntu??? If so, what would I do to run this code?

---

### Post by amo-ej1 on 2008-01-27
C# is only a language nothing more .... 


Concering the application, google is just a bit more userfriendly. Surf to google.com and type in the inputfield  "1kg in pounds"

---

### Post by zivxx on 2008-01-27
here is a guide to install mono and compile and run my program too

[http://www.builderau.com.au/program/linux/print.htm?TYPE=story&AT=339279567-339028299t-320002022c](http://www.builderau.com.au/program/linux/print.htm?TYPE=story&AT=339279567-339028299t-320002022c)

---

### Post by bruce89 on 2008-01-27
As a wee exercise in C, here's a C clone of this.

[PHP]
#include <stdio.h>

enum
{
	INCH_TO_CM = 1,
	POUND_TO_KG = 2,
	FOOT_TO_M = 3
} mode;

int
main (void)
{
	int mode;
	double imperial;
	double metric;

	printf ("Choose from the menu\n");
	printf ("1 -- Inches to centimetres converter\n");
	printf ("2 -- Pounds to kilograms converter\n");
	printf ("3 -- Feet to metres converter\n");
	scanf ("%d", &mode);

	switch (mode)
	{
		case INCH_TO_CM:
			/* Program 1 */
			printf ("Enter inch value ");
			scanf ("%lf", &imperial);
			metric = imperial * 2.54;
			printf ("%lf\n", metric);
			break;
		case POUND_TO_KG:
			/* Program 2 */
			printf ("Enter pounds value ");
			scanf ("%lf", &imperial);
			metric = imperial * 0.4535924;
			printf ("%lf\n", metric);
			break;
		case FOOT_TO_M:
			/* Program 2 */
			printf ("Enter feet value ");
			scanf ("%lf", &imperial);
			metric = imperial * 0.3048;
			printf ("%lf\n", metric);
			break;
		default:
			fprintf (stderr, "Mode not recognised\n");
	}
	return 0;
}
[/PHP]

```
gcc -g -Wall -o conv conv.c
```

---

### Post by zivxx on 2008-01-28
C looks a bit more complicated to be honest :|

---

### Post by Martin Witte on 2008-01-28
> **zivxx said:**
> C looks a bit more complicated to be honest :|

maybe c++ suits you more?

[PHP]
#include <iostream>
#include <string>
#include <sstream>

using namespace std;

void convert(const string& what, const double& factor)
{
	double result(0.0), input(0.0);
	string giveninput;
	stringstream tester;

	cout << "enter " << what << " value" << endl;
	cin >>  giveninput;
	tester << giveninput;
	if (!(tester >> input))
	{
		cerr << giveninput << " not valid" << endl;
	}
	else
	{
		result = factor * input;
		cout << result << endl;
	}
}

int main()
{
	string exit;
	bool leave(false);
	while (! leave)
	{
		cout << "what menu would you like to go for?(for the main menu choose something which is not 1 2 or 3)" << endl;
		cin >> exit;
		if (exit == "1")
		{
			convert("inch", 2.54);
		}
		else if (exit == "2")
		{
			convert("pounds", 0.4535924);
		}
		else if (exit == "3")
		{
			convert("feet", 0.3048);
		}
		else if (exit == "exit")
		{
			leave = true;
		}
		else
		{
			cout << "choose a menu" << endl;
			cout << "1 Inch To Centimeter Converter" << endl;
			cout << "2 Pound To KiloGrams Converter" << endl;
			cout << "3 Feet To Meter Converter" << endl;
		}
		
	}
	return 0;
}
[/PHP]

---

### Post by Acglaphotis on 2008-01-28
In c++:

[php]
/**************************************************************
//Made By Acglaphotis on Sun Jan 27 22:08:32 VET 2008
 * Imperial to Metric Converter
 * ***********************************************************/  
#include <cstdio>
#include <cstdlib>
#include <iostream>
#include <string>
using namespace std;
int main(void)
{
    double standard, imperial; //assigning variables
    short int choice;
    char menu[2];
    int loop = 30000;
       while(loop != 0, loop--)	
       {
	    cout<<"Choose from the menu"<<endl;
	    cout<<"1 -- Inches to centimetres"<<endl;
	    cout<<"2 -- Pounds to kilograms"<<endl;
	    cout<<"3 -- Feet to metres"<<endl;
            cout<<"0 -- exit"<<endl;
            cin>>choice;
	    switch(choice) 
    	{
		case 1:
		    cout<<"Enter inch: ";
	            cin>>imperial;
	   	    standard = imperial * 2.54;
	            cout<<endl;
	            cout<<"The result is: "<<standard<<endl;
	            cout<<"Return to menu? y/n: ";
		    cin>>menu; //returning to the mneu
		    if (strcmp(menu,"y") == 0 || strcmp(menu,"Y") == 0  )
			break;
		    else if (strcmp(menu,"n") == 0 || strcmp(menu,"N") == 0)
			exit(0);
		    else if (strcmp(menu,"n") != 0  || strcmp(menu,"N") != 0 || strcmp(menu,"y") != 0 || strcmp(menu,"Y") != 0)
			cout<<"Input not recognized. Exiting."<<endl;
		        exit(0);
    		case 2:
	            cout<<"Enter pounds: ";
	            cin>>imperial;
	            standard = imperial * 0.4535924;
	            cout<<endl;
	            cout<<"The result is: "<<standard<<endl;
	            cout<<"Return to menu? y/n: ";
	            cin>>menu;
		    if (strcmp(menu,"y") == 0 || strcmp(menu,"Y") == 0  )
			break;
		    else if (strcmp(menu,"n") == 0 || strcmp(menu,"N") == 0)
			exit(0);
		    else if (strcmp(menu,"n") != 0  || strcmp(menu,"N") != 0 || strcmp(menu,"y") != 0 || strcmp(menu,"Y") != 0)
			cout<<"Input not recognized. Exiting."<<endl;
		        exit(0);
		case 3:
	            cout<<"Enter feets: ";
	            cin>>imperial;
	            standard = imperial * 0.3048;
	            cout<<endl;
	            cout<<"The result is: "<<standard<<endl;
		    cout<<"Return to menu? y/n: ";
		    cin>>menu;
		    if (strcmp(menu,"y") == 0 || strcmp(menu,"Y") == 0  )
			break;
		    else if (strcmp(menu,"n") == 0 || strcmp(menu,"N") == 0)
			exit(0);
		    else if (strcmp(menu,"n") != 0  || strcmp(menu,"N") != 0 || strcmp(menu,"y") != 0 || strcmp(menu,"Y") != 0)
			cout<<"Input not recognized. Exiting."<<endl;
		        exit(0);
	        case 0:
	            exit(0);
		default:
	            cout<<"The number you entered is incorrect. Exiting"<<endl;
	    	    exit(0);
	}
    }
    return 0;
}
[/php]

Uh, sorry, when i first entered the post, Martin had not posted his version.

---

### Post by bruce89 on 2008-01-29
> **Martin Witte said:**
> maybe c++ suits you more?


Looks even more complex IMHO.

---

### Post by LaRoza on 2008-01-29
> **bruce89 said:**
> Looks even more complex IMHO.

For tasks like this, interpreted and dynamic languages make life easier and more productive.

---


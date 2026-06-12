---
title: "Gasoline method java"
date: 2012-03-04
forum: Programming Talk
---

### Post by Tzio on 2012-03-04
Please help!
I cant get the result to popup, but i think it´s close now or am 
I? 

swedish! i translated this not perfect but i hope u understand it





import java.util. *;
import java.awt.Component. *;
import javax.swing. *;
import static javax.swing.JOptionPane. *;
public class ill
{
     public static void main (String [] args)
{
Scanner scan = new Scanner (System.in);
JFrame f = new JFrame ();
String input;
double km;
double l;
int repeat;
do
{
Show message dialog (null, "This program calculates the consumption of" +
"a car either," + "\ n" + "According to the European standard (E) in litres/100:" + "\ n" +
"Or, according to U.S. standards (U) in gallons / miles:");
String [] choices = {"E", "U", "Cancel"};
int answer = show option dialog (f,
"Do you want to count on the EU standard (E) '+
"or with the U.S. standard (U)",
"Choose the default"
YES_NO_CANCEL_OPTION,
QUESTION_MESSAGE,
null, choice, choices [2]);
if (answer == 0) eu ();
else if (answer == 1) us ();
else {
Show message dialog (null, "Avrbutet");
}
Show message dialog (null, "response");
repeat = showConfirmDialog (null, 'Do you want to make a new determination: ");
} while (repeat == 0);
System.exit (0);
}
static double eu () {
String input;
double km;
double l;
input = Show input dialog ("How many miles did you run?");
km = Integer.parseInt (input);
input = Show input dialog ("How many liters of petrol has gone to?");
l = Integer.parseInt (input);
double euförbruk = l / (km/100);
return euförbruk;
}
static double us () {
String input;
double km;
double l;
input = Show input dialog ("How many miles did you run?");
km = Integer.parseInt (input);
input = Show input dialog ("How many liters of petrol has gone to?");
l = Integer.parseInt (input);
double usförbruk = (l * 3785) / (km * 1609);
return usförbruk;
}
}

---

### Post by PaulM1985 on 2012-03-05
Could you post something that builds and please enclose it in CODE tags?  This will help people look at it if they can build it for themselves and the code tags will maintain the correct spacing that you have in your original code.

Paul

---


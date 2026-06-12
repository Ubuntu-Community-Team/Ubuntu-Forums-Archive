---
title: "Need help in java code"
date: 2008-11-07
forum: Programming Talk
---

### Post by redasu on 2008-11-07
Hi I new to the forum so nice to discuss with you everybody
I am trying to use recursive functions for this assignment it compiles pretty well but it gives me this kind of output:
The minimum number is -5.000
The sum of the numbers at even indexes is -13.43
The sum of the negative numbers is -15.867
The total number of positive numbers is 3
Exception in thread "main" java.util.NoSuchElementException
at java.util.Scanner.throwFor(Scanner.java:838)
at java.util.Scanner.next(Scanner.java:1461)
at java.util.Scanner.nextDouble(Scanner.java:2387)
at Assignment6.main(Assignment6.java:21)
what's this exception thing??? plz help
here is my code:




import java.text.DecimalFormat;

import java.util.Scanner;

public class Assignment6
{
public static void main (String[] args)
{

DecimalFormat form1 = new DecimalFormat("0.000");
DecimalFormat form2 = new DecimalFormat("0.##");
DecimalFormat form3 = new DecimalFormat("0.0##");

int index;

Scanner scan = new Scanner( System.in );
double [] number = new double[101];
for(index=0;index < number.length;index++)
{

number[index] = scan.nextDouble( );
if(number[index]==0)
{
System.out.println("The minimum number is "+form1.format(findMin(number,index)));
System.out.println("The sum of the numbers at even indexes is "+form2.format(computeSumAtEven(number,index)) );
System.out.println("The sum of the negative numbers is "+form3.format(computeNegativeSum(number,index )));
System.out.println("The total number of positive numbers is "+countPositive(number,index));
}
}





}
public static double findMin(double[] numbers, int i)
{
double min;
if (i==0){
return numbers[0];}
else {
min = findMin (numbers , i-1);
if (numbers[i]< min )
{ return numbers[i];}
else {
return min;}
}}
public static double computeSumAtEven(double[] numbers, int i)
{

if (i==0){
return numbers[0];}
else {
double sum = computeSumAtEven(numbers, i-1);
if (i%2==0){
return sum + numbers[i];}
else
{return sum; }}

}
public static double computeNegativeSum(double[] numbers, int i)
{
double sum;
if (i==0){
if (numbers[i]<0)
{sum = numbers[0];
return sum;}
else {
sum=0;
return sum;}
}
else
{ sum = computeNegativeSum(numbers, i-1);
if (numbers[i]< 0)
{return sum + numbers[i];}
else {
return sum;}
}
}

public static int countPositive(double[] numbers , int i)
{if(i==0)
{ if(numbers[0]>0)
return 1 ;
else
return 0;}
else
{
int sum = countPositive(numbers,i-1);

if (numbers[i]>0)
{ sum++;
return sum;}

else{
return sum ;}}
}
}

---

### Post by dribeas on 2008-11-08
You should go back to basics and read about exceptions in your course books or any java tutorial (short answer: error reporting mechanism). Once you get to know what exceptions are and how to work with them, read the API of the classes you are using and note where exceptions may be thrown and for what reasons.

The message will even help you deduce where the problem is arising:

at Assignment6.main(Assignment6.java:21)

If you still have doubts, do ask again.

---

### Post by achelis on 2008-11-08
You might also want to look at the Scanner class to see why a NoSuchElementException is thrown. 

```

http://java.sun.com/j2se/1.5.0/docs/api/

```

You may not have reached exceptions in your course yet (you should eventually though, as it's an important concept in Java), but briefly put it tells you there is a runtime error - these can be directly related to the code (trying to call a method on a null-object et.c.), or could be due a bad disk read et.c.

```

Exception in thread "main" java.util.NoSuchElementException
at java.util.Scanner.throwFor(Scanner.java:838)
at java.util.Scanner.next(Scanner.java:1461)
at java.util.Scanner.nextDouble(Scanner.java:2387)
at Assignment6.main(Assignment6.java:21)

```

Is a stacktrace of the exception. Looking at the stacktrace you can see:
1) The error you got was a NoSuchElementException.
2) It occured in line 21 of the Assignment6 class of your program - and further that it happened when the scanner tried to get the next element.

Hope this makes sense :)

PS. I'm curious to hear how you produce the error, as I'm unable to reproduce it - I can only get the InputMismatchException.

---

### Post by redasu on 2008-11-08
We never went through exceptions yet I tried to read the Api but I still don't know what kind of exception should I put , and how I should put it

---

### Post by slavik on 2008-11-08
thread closed until further notice ...

---


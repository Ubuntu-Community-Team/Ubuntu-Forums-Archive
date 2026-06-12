---
title: "having a problem with my java code plz help"
date: 2008-11-07
forum: Programming Talk
---

### Post by redasu on 2008-11-07
Hi
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
what's this exception thing
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

### Post by bapoumba on 2008-11-08
Moved to PT. Please use code tags to paste errors output.
I'm also closing the thread, UF is not a resource for homework help.

---


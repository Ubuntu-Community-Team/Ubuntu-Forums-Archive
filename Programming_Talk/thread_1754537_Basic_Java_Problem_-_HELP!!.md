---
title: "Basic Java Problem - HELP!!"
date: 2011-05-10
forum: Programming Talk
---

### Post by hadenkl on 2011-05-10
Hi guys,

I'm learning java, and I've got a program for calculating the area of an annulus with loops and arrays. I'm just having a real struggle getting my if statement to compile properly: I've got an 'illegal start of expression' error and I can't figure out why! Can someone help? Code is below:

import java.util.Scanner;

public class AreaAnnulus
{
    public static void main (String args[])

    {
       
// set grid size
int gridSize = 20;


//create Scanner object
Scanner keyboard = new Scanner (System.in);

//ask user for outer radius
System.out.println ("Please enter the outer radius of the annulus");

double r1 = keyboard.nextDouble();

//Ask user for the inner radius
System.out.println ("Please enter the inner radius of the annulus");

double r2 = keyboard.nextDouble();

//set column = x

//set minx = 1r1
double minx = -r1;       
//set maxx = r1
double maxx = r1;        
//set miny -= -r1
double miny = -r1;        
//set maxy = r1
double maxy = r1;
        
//set counter = 0

int counter = 0; 
// set x and y

for (int column = 0; column< gridSize-1;column++) {

double x = minx +(column +0.5)*((maxx-minx)/gridSize);
//set row

for (int row = 0; row< gridSize-1; row++){
//set test
double y = miny +(row + 0.5)*((maxy-miny)/gridSize);

//set test

double test = x*x + y*y;

if(test <r1*r1 && > r2*r2)
{

counter = counter +1;
}
//set area
}
}
double area = (maxx-minx)*(maxy-miny)*counter/(gridSize*gridSize);

System.out.println ("Area: " + area);

}
}

---

### Post by fballem on 2011-05-10
if(test <r1*r1 && > r2*r2)

should probably read if(test < r1*r1 && test > r2*r2)

Just a guess

---

### Post by hadenkl on 2011-05-10
I knew it would be something simple in front of me: thank you so much!! That's saved a headache!!

---


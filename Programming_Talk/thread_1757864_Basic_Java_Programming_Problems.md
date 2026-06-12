---
title: "Basic Java Programming Problems"
date: 2011-05-13
forum: Programming Talk
---

### Post by hadenkl on 2011-05-13
Hi everyone,

I'm stuck on arrays in a program I'm trying to create to measure the area of an annulus. Can someone help me? I can't figure out how to loop my first array to repeat 100 times, and I think my 2D array is also looking dodgy.

Here is my pseudocode to show what I'm supposed to be doing, and my actual program is beneath it. Sorry it's so long!!!! :

[COLOR="Navy"]BEGIN Area of Annulus
Set gridSize = 20 (we could use 20 by 20 grid cells)
Create a 2D array, hits, to count how many points are on the shape
Set samples = 100 (let’s use 100 random points inside each cell)
Get r1 from user (outer radius)
Get r2 from user (inner radius)
Set minx = -r1
Set maxx = r1
Set miny = -r1
Set maxy = r1
Set counter = 0 (will count how many grid cells are on the annulus)
For column = 0 to gridSize-1
For row = 0 to gridSize-1
Set hits[column][row] to 0
Repeat samples times
Set x = minx + (column + random)*((maxx–minx)/gridSize)
Set y = miny + (row + random)*((maxy–miny)/gridSize)
Set test = x*x + y*y
if test < r1*r1 and test > r2*r2
Set hits[column][row] = hits[column][row] + 1
Set hits[column][row] = hits[column][row]/samples
Set counter = counter + hits[column][row]
Set area = (maxx-minx)*(maxy-miny)*counter/(gridSize * gridSize)
Output “Area : ” area
END Area of Annulus[/COLOR]



import java.util.Scanner;


public class AreaOfAnnulus
{
    public static void main (String args[])

    {
       
// set grid size
int gridSize = 20;

//declare a new array
final int samples = 100;
int []numbers= new int [samples];
    
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

double counter = 0; 

//set column and row for loops
for (int column = 0; column <samples.length(); column++) {  [COLOR="Red"]I'm getting an 'int can not be dereferenced eroor on these lines!![/COLOR]
    for (int row = 0; row <samples.length(); row++){
        
//set 2D array

int [][] hits = new int [column][row];

hits [column][row] = hits [0][0];


//set inner nested loop

double y = miny +(row + Math.random())*((maxy-miny)/gridSize);

double x = minx +(column +Math.random())*((maxx-minx)/gridSize);  
    
//set x and y

//set test

double test = x*x + y*y;

if(test < r1*r1 && test > r2*r2)
{

hits [0][0] = hits [0][0]+1;

hits [0][0] = hits [0][0]/samples;

counter = counter + hits [0][0];
}
//set area
}
}
double area = (maxx-minx)*(maxy-miny)*counter/(gridSize*gridSize);

System.out.println ("Area: " + area);

{
System.out.println ("What is the outer radius of the annulus?");

double radius1 = keyboard.nextDouble();

System.out.println ("What is the inner radius of the annulus?");

double radius2 = keyboard.nextDouble();

//calculate the area based on the measurements provided

area = Math.PI * (radius1 * radius1 - radius2 * radius2);

System.out.println ("The area of the annulus is" + area);
}
}
}

---

### Post by Some Penguin on 2011-05-14
1.  Please use CODE tags.

2.  If you pay attention the actual error message, it should be clear what's wrong.

An 'int' cannot be dereferenced, because it's not a reference; it's a primitive.  'samples' is an int.  It's not even clear WHY you're trying to dereference it, instead of simply treating it like an int; e.g. "column < samples".  What is the length of an int?

---

### Post by hadenkl on 2011-05-14
1. I DON'T KNOW WHAT CODE TAGS ARE.

2. Yeah I had actually figured that bit out, but it's not solving the issue of how to get the pseudocode to translate into programmable code.

Not even remotely helpful: I'm not a programmer, I don't like programming, and I'm forced to teach myself because I'm learning externally and it's a compulsory subject. 

I'll ask somewhere else.

---

### Post by hadenkl on 2011-05-14
sorry; my tutor just came back to me with something that sounded like Yoda talking; it's due tomorrow and I got stressed.

Almost done. Thanks for your help :-)

---

### Post by r-senior on 2011-05-14
> **hadenkl said:**
> 1. I DON'T KNOW WHAT CODE TAGS ARE.
Code tags allow you to put code into a post and retain the formatting. It makes your code snippets much easier to read and you are more likely to get help.

You can:

1. Enclose your code with tags like these (no spaces inside the tags): ```
 and  [ /code]

or

2. When you reply or post, select your code with the mouse and press the shortcut button '#' in the toolbar that appears above it.

For example:

[code]
int main(int argc, char **argv)
{
        printf("hello, world");
}

```

as opposed to:

int main(int argc, char **argv)
{
        printf("hello, world");
}

---

### Post by dr_saaron on 2011-05-14
samples is neither an array nor an object

---


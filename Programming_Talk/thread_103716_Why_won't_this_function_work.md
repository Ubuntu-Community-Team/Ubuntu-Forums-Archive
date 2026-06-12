---
title: "Why won't this function work?"
date: 2005-12-14
forum: Programming Talk
---

### Post by matthew on 2005-12-14
I am teaching myself C. This is not for a class, but just for my own enjoyment...you won't be helping me cheat or anything. :)

The short program is one of the exercises from the book _Practical C Programming_ by O'Reilly (Exercise 6-1, page 93).

The original exercise was to "Write a program to find the square of the distance between two points." This was easy enough.

For more advanced study I wanted to find the actual distance. The book has not yet covered the sqrt function, but I figured it can't be too difficult. I'm attaching my code since it is so short. Please take a look and see where I am making a mistake.

When I try to compile this I get: 
```
In function `main':
undefined reference to `sqrt'
collect2: ld returned 1 exit status

``` I have looked in every book I have as well as online in these and other locations and I can't figure out what I am doing wrong.
[http://www-ccs.ucsd.edu/c/]("http://www-ccs.ucsd.edu/c/")
[http://www-ccs.ucsd.edu/c/math.html]("http://www-ccs.ucsd.edu/c/math.html")

FYI, I am using the gcc compiler and I have build-essential installed.

```
/[FONT=Courier New]******************************************************
  * 6-1    - program from Practical C Programming chapter 6   
  *          exercise number 6-1 on page 93            
  *                                
  * Author:    matthew                    
  *                                
  * Purpose:    to find the square of the distance between    
  *             two points                    
  *                                        
  * Usage:    Enter coordinates for two points on a chart    
  *           and square the difference            
  *           
  * For extra practice I want to learn the sqrt function 
  * and find the actual distance                        
  ***********************************************************/

 #include <stdio.h>
 #include <math.h>

 char line[20];
 float point1_x;        /* x coordinate for point 1 */
 float point1_y;        /* y coordinate for point 1 */
 float point2_x;        /* x coordinate for point 2 */
 float point2_y;        /* y coordinate for point 2 */

 float a_squared;    /* these three are used in calculating */
 float b_squared;    /* the distance in the function below  */
 double c_squared;

 double distance;        /* final answer */

 int main()
 {
     printf("Please input x coordinate for point 1: ");
     
     fgets(line, sizeof(line), stdin);
     sscanf(line, "%f", &point1_x);

     printf("Please input y coordinate for point 1: ");
     
     fgets(line, sizeof(line), stdin);
     sscanf(line, "%f", &point1_y);

     printf("Please input x coordinate for point 2: ");
     
     fgets(line, sizeof(line), stdin);
     sscanf(line, "%f", &point2_x);

     printf("Please input y coordinate for point 2: ");
     
     fgets(line, sizeof(line), stdin);
     sscanf(line, "%f", &point2_y);

     /********************************************************
      * the function is based on the pythagorean theorem    
      * a^2 + b^2 = c^2                    
      * a is the height, b is the length, c is the straight    
      *     line distance between them            
      ********************************************************/
     
     a_squared = (point1_x - point2_x) * (point1_x - point2_x);
     b_squared = (point1_y - point2_y) * (point1_y - point2_y);
     c_squared = a_squared + b_squared;
             
     printf("The square of the distance is %f.\n",
           c_squared);

[/FONT][FONT=Courier New] /*    I tried to modify the program to print 
  *    the actual distance instead of just the square and 
  *    added the distance calculation below. The part
  *    above works perfectly.
  */[/FONT]
[FONT=Courier New]    
 /* I don't know why this next part isn't working */

      distance = sqrt( c_squared );         

     printf("The distance between the two points is %f.\n",
         distance);
     
     return (0);
 }[/FONT]           
```It seems like this should be really easy. What am I missing??

---

### Post by darth_vector on 2005-12-14
did you link the math library when compiling?

gcc -o progname progname.c -lm

---

### Post by matthew on 2005-12-14
[quote=darth_vector]did you link the math library when compiling?

gcc -o progname progname.c -lm[/quote]Yep, that confirms it. I'm a n00b.

Linking the math library took care of the problem. Thanks, darth_vector!!

<goes off to read documentation on using gcc>

---

### Post by darth_vector on 2005-12-14
lol, dont worry - everyone forgets that. i've done it a million times :)

---

### Post by Jessehk on 2005-12-14
I thought distance was sqrt((x1 - x2)^2 + (y1 - y2)^2)...

---

### Post by darth_vector on 2005-12-14
thats what he did:

     a_squared = (point1_x - point2_x) * (point1_x - point2_x);
     b_squared = (point1_y - point2_y) * (point1_y - point2_y);
     c_squared = a_squared + b_squared;
...
      distance = sqrt( c_squared );

---

### Post by matthew on 2005-12-14
Yeah, I did it the way I did intentionally. My formula says the same thing. I was more interested in playing with the commands and syntax than keeping the code concise.

---


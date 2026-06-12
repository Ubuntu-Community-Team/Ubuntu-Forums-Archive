---
title: "ArrayIsOutOfBoundExceptions Error - Java"
date: 2011-05-16
forum: Programming Talk
---

### Post by hadenkl on 2011-05-16
I keep getting an ArrayIsOutOfBoundsException error on this code below. I can't figure out how to fix it. Could someone tell me what needs to be done to sort it out? It's driving me crazy! I'm not very good at arrays........



```


import java.util.Scanner;

public class Shape
{
    public static void main (String args[])

    {
       
        // set grid size
        int gridSize = 20;

        //create a 2D array called hits
        final int COLS = 20;
        final int ROWS = 20;
        
        double hits [][] = new double[COLS][ROWS];

        //set samples
        final int samples = 100;
    
        //create Scanner object
        Scanner keyboard = new Scanner (System.in);

        //ask user for outer radius
        System.out.println ("Please enter the outer radius of the annulus");

        double r1 = keyboard.nextDouble();

        //Ask user for the inner radius
        System.out.println ("Please enter the inner radius of the annulus");

        double r2 = keyboard.nextDouble();

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

        for (int column = 0; column < gridSize-1; column++) {
        double x = minx + (column + Math.random()) * ((maxx-minx)/gridSize);
            
            for (int row = 0; row < gridSize-1; row++){
                double y = miny + (row + Math.random()) * ((maxy-miny)/gridSize);
            
        
                //set hits to 0
               
                for (int i= 0; i<COLS; i++){
                    for (int j= 0; j<ROWS; j++){
                     
                         //set test
                        double test = x*x + y*y;

                        if (test < r1*r1 && test > r2*r2)
                        {
                            //set hits = hits +1
                            hits [COLS][ROWS] = hits [i][j] +1;
                        }
                        
              //set hits = hits/samples
              hits [COLS][ROWS] = hits [COLS][ROWS] /samples;  [COLOR="Red"]error message shows here[/COLOR]
              //set counter = counter +hits
              counter = counter + hits [COLS][ROWS]; [COLOR="red"]or here[/COLOR]
            
            }
            
        }
                    
    }
}
           
//set area
double area = (maxx-minx)*(maxy-miny)*counter/(gridSize*gridSize);
//output area
System.out.println ("Area: " + area);
}
}

```

---

### Post by Zugzwang on 2011-05-16
You define your "hits" array as an array with 20x20 elements:
```

double hits [][] = new double[COLS][ROWS];

```
Note that array indices start from 0 in Java, thus you have the columns 0...19 in your array. But then, you access the 20th column in your code:
```

hits [COLS][ROWS] = hits [COLS][ROWS] /samples;

```
This is the cause of the error. You probably forgot to fill in "column" and "row" instead of "COLS" And "ROWS" in this line.

---

### Post by hadenkl on 2011-05-16
You my friend have just shaved about ten years off my aging process: thank you so much for that!!! Something so simple is really hard to see after fretting over it for days!!!

---

### Post by Zugzwang on 2011-05-16
> **hadenkl said:**
> Ohhhhh yeah!!! I forgot about that!! Okay, so when you say I probably forgot to write rows and columns, what exactly do you mean? How would I do that? (I'm really, really confused after staring at this for about three days - not kidding).

I meant the following. You have two nested for loops:
```

for (int column = 0; column < gridSize-1; column++) {
        double x = minx + (column + Math.random()) * ((maxx-minx)/gridSize);
            
            for (int row = 0; row < gridSize-1; row++){

```
These use the variables "column" and "row" to mark their proceeding. Now in the following line:
```

hits [COLS][ROWS] = hits [COLS][ROWS] /samples;

```
it looks as if you meant:
```

hits [column][row] = hits [column][row] /samples;

```
As "row" and "column" were the name of variables, I put them into quotation marks in the post above to avoid confusing them with the ordinary plain English words row and column.

---

### Post by hadenkl on 2011-05-16
I figured out what you meant and frantically tried to edit my response before you replied!!

thank you

thank you

thank you

thank you


you have saved the day!!

---


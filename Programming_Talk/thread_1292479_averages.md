---
title: "averages"
date: 2009-10-15
forum: Programming Talk
---

### Post by nathang1392 on 2009-10-15
i am making a program that long story short is taking information from a file, putting it into an array, and then using those to calculate. it is about hurricanes and i am calculating the category, pressure, and speed averages. mostly everything works, but the averages are outputting all wrong numbers, im not sure what is wrong, but i think you guys may be a big help. thank you in advance for any contributions.
```
import java.io.PrintWriter;
import java.io.IOException;
import java.util.*;
import java.io.File;
public class Hurricanes2
{
    public static void main(String [] args) throws IOException
    {
     
   int Index = 0; 
   int Index2 = 0;
  
    int year[] = new int[60];
    String month[] = new String[60];
    int pressure[] = new int[60];
    int speed[] = new int[60];
    String name[] = new String[60];
    
    int category[] = new int[60];

    int speedAverage = 0;
    int speedSum = 0;
    
    int categorySum = 0;
    int categoryAverage = 0;
    int categorySpeed = 0;
    
    int pressureSum = 0;
    int pressureAverage = 0;
    
    Scanner inFile = new Scanner(new File("hurcdata2.txt"));
   
            while (inFile.hasNext())
            {
                
            year[Index] = inFile.nextInt();
            month[Index] = inFile.next();
            pressure[Index] = inFile.nextInt();
            speed[Index] = inFile.nextInt();
            name[Index] = inFile.next();
            Index++;
            }   
         
            
            inFile.close();
            
            //category
            
            
            for (int counter = 0; counter <= 60;counter++)
            {
            if(speed[Index] > 155)
            {
                category[Index2] = 5;
            }
            
            else if(speed[Index] > 130)
            {
                category[Index2] = 4;
            }
            
            else if(speed[Index] > 111)
            {
                category[Index2] = 3;
            }
            
            else if(speed[Index] > 96)
            {
                category[Index2] = 2;
            }
            else
            {
                category[Index2] = 1;
            }

            categorySum += category[Index2];
            categoryAverage = categorySum/ 60;
            
            }
        
            //speed
            for(int counter = 0; counter <= 60; counter++)
            {
                
                speedSum += speed[Index];
                speedAverage = speedSum/60;
                
                
            }
            
            //pressure
               
            for (int counter = 0; counter <= 60; counter++)
           {    
                pressureSum += pressure[Index];
                pressureAverage = pressureAverage/60;
   
          }
          
          System.out.println(categoryAverage);
          System.out.println(speedAverage);
          System.out.println(pressureAverage);
        
}
    
}
``` and if it is relevant, here is my file that i am reading from.
> 1980 Aug	945	100	Allen

1983 Aug	962	100	Alicia

1984 Sep	949	100	Diana

1985 Jul	1002	65	Bob

1985 Aug	987	80	Danny

1985 Sep	959	100	Elena

1985 Sep	942	90	Gloria

1985 Oct	971	75	Juan

1985 Nov	967	85	Kate

1986 Jun	990	75	Bonnie

1986 Aug	990	65	Charley

1987 Oct	993	65	Floyd

1988 Sep	984	70	Florence

1989 Aug	986	70	Chantal

1989 Sep	934	120	Hugo

1989 Oct	983	75	Jerry

1991 Aug	962	90	Bob

1992 Aug	922	145	Andrew

1993 Aug	960	100	Emily

1995 Aug	973	85	Erin

1995 Oct	942	100	Opal

1996 Jul	974	90	Bertha

1996 Sep	954	100	Fran

1997 Jul	984	70	Danny

1998 Aug	964	95	Bonnie

1998 Sep	987	70	Earl

1998  Sep	964	90	Georges

1999 Aug	951	100	Bret

1999 Sep	956	90	Floyd

1999 Oct	987	70	Irene

2002 Oct	963	80	Lili

2003 Jul	979	80	Claudette

2003 Sep	957	90	Isabel

2004 Aug	972	70	Alex

2004 Aug	941	130	Charley

2004 Aug	985	65	Gaston

2004 Sep	960	90	Frances

2004 Sep	946	105	Ivan

2004 Sep	950	105	Jeanne

2005 Jul	992	65	Cindy

2005 Jul	930	130	Dennis

2005 Jul	929	135	Emily

2005 Aug	975	85	Irene

2005 Aug	902	150	Katrina

2005 Sep	960	100	Maria

2005 Sep	979	80	Nate

2005 Sep	976	80	Ophelia

2005 Sep	985	70	Phillipe

2005 Sep	897	150	Rita

2005 Sep	979	70	Stan

2005 Sep	987	65	Vince

2005 Sep	882	150	Wilma

2005 Sep	960	100	Beta

2005 Sep	979	75	Epsilon

2006 Aug	995	65	Ernesto

2006 Sep	972	80	Florence

2006 Sep	955	105	Gordon

2006 Sep	954	110	Helene

2006 Sep	985	75	Isaac




---

### Post by Can+~ on 2009-10-15
```
1980,Aug,945,100,Allen
1983,Aug,962,100,Alicia
1984,Sep,949,100,Diana
1985,Jul,1002,65,Bob
1985,Aug,987,80,Danny
1985,Sep,959,100,Elena
1985,Sep,942,90,Gloria
1985,Oct,971,75,Juan
1985,Nov,967,85,Kate
1986,Jun,990,75,Bonnie
1986,Aug,990,65,Charley
1987,Oct,993,65,Floyd
1988,Sep,984,70,Florence
1989,Aug,986,70,Chantal
1989,Sep,934,120,Hugo
1989,Oct,983,75,Jerry
1991,Aug,962,90,Bob
1992,Aug,922,145,Andrew
1993,Aug,960,100,Emily
1995,Aug,973,85,Erin
1995,Oct,942,100,Opal
1996,Jul,974,90,Bertha
1996,Sep,954,100,Fran
1997,Jul,984,70,Danny
1998,Aug,964,95,Bonnie
1998,Sep,987,70,Earl
1998,Sep,964,90,Georges
1999,Aug,951,100,Bret
1999,Sep,956,90,Floyd
1999,Oct,987,70,Irene
2002,Oct,963,80,Lili
2003,Jul,979,80,Claudette
2003,Sep,957,90,Isabel
2004,Aug,972,70,Alex
2004,Aug,941,130,Charley
2004,Aug,985,65,Gaston
2004,Sep,960,90,Frances
2004,Sep,946,105,Ivan
2004,Sep,950,105,Jeanne
2005,Jul,992,65,Cindy
2005,Jul,930,130,Dennis
2005,Jul,929,135,Emily
2005,Aug,975,85,Irene
2005,Aug,902,150,Katrina
2005,Sep,960,100,Maria
2005,Sep,979,80,Nate
2005,Sep,976,80,Ophelia
2005,Sep,985,70,Phillipe
2005,Sep,897,150,Rita
2005,Sep,979,70,Stan
2005,Sep,987,65,Vince
2005,Sep,882,150,Wilma
2005,Sep,960,100,Beta
2005,Sep,979,75,Epsilon
2006,Aug,995,65,Ernesto
2006,Sep,972,80,Florence
2006,Sep,955,105,Gordon
2006,Sep,954,110,Helene
2006,Sep,985,75,Isaac
```

I made a .csv from your data, and now in R:

[PHP]> x = read.csv("asd.csv", col.names=c("Year", "Month", "Pressure", "Speed", "Nickname"))
> x$Speed
 [1] 100 100  65  80 100  90  75  85  75  65  65  70  70 120  75  90 145 100  85
[20] 100  90 100  70  95  70  90 100  90  70  80  80  90  70 130  65  90 105 105
[39]  65 130 135  85 150 100  80  80  70 150  70  65 150 100  75  65  80 105 110
[58]  75
> mean(x$Speed)
[1] 91.12069
> mean(x$Pressure)
[1] 963.8793[/PHP]

About your Java code:

[PHP]            for (int counter = 0; counter <= 60; counter++)
           {    
                pressureSum += pressure[Index];
                pressureAverage = pressureAverage/60;
   
          }[/PHP]

Notice that you're doing "Average = Average/60". And you don't even need to do it each cycle, getting the average could be done in the end of the code, not inside the for loop.

---

### Post by fct on 2009-10-16
First, I don't see "Index" or "Index2" changing in that code past the loading of the values. Instead, you're changing "counter" but it's not used to access arrays for calculations (!?).

Second, when you declare an array like this:

```
int year[] = new int[60];
```

You have 60 elements numbered from 0 to 59.

So this:

```
for (int counter = 0; counter <= 60;counter++)
```

is actually looping 61 times, and if you used "counter" to access an array it would be out of bounds in the last step.

---

### Post by nathang1392 on 2009-10-16
i got most of the issues that you guys pointed out fixed. now one of my averages sort of works, i think, but its not making any sense. its like this
> 1
91
0


my code seems to be right though,
```

/**
 * Write a description of class Hurricanes2 here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
import java.io.PrintWriter;
import java.io.IOException;
import java.util.*;
import java.io.File;
public class Hurricanes2
{
    public static void main(String [] args) throws IOException
    {
     
   int Index = 0; 
   
  
    int year[] = new int[60];
    String month[] = new String[60];
    int pressure[] = new int[60];
    int speed[] = new int[60];
    String name[] = new String[60];
    
    int category[] = new int[60];

    int speedAverage = 0;
    int speedSum = 0;
    
    int categorySum = 0;
    int categoryAverage = 0;
    int categorySpeed = 0;
    
    int pressureSum = 0;
    int pressureAverage = 0;
    
    Scanner inFile = new Scanner(new File("hurcdata2.txt"));
   
            while (inFile.hasNext())
            {
                
            year[Index] = inFile.nextInt();
            month[Index] = inFile.next();
            pressure[Index] = inFile.nextInt();
            speed[Index] = inFile.nextInt();
            name[Index] = inFile.next();
            Index++;
            }   
         
            
            inFile.close();
            
            //category
            
            
            for (int counter = 0; counter <= 59;counter++)
            {
            if(speed[counter] > 155)
            {
                category[counter] = 5;
            }
            
            else if(speed[counter] > 130)
            {
                category[counter] = 4;
            }
            
            else if(speed[counter] > 111)
            {
                category[counter] = 3;
            }
            
            else if(speed[counter] > 96)
            {
                category[counter] = 2;
            }
            else
            {
                category[counter] = 1;
            }
            
            categorySum += category[counter];
            
            
            }
        
            //speed
            for(int counter = 0; counter <= 59; counter++)
            {
                
                speedSum += speed[counter];
                
                
                
            }
            
            //pressure
               
            for (int counter = 0; counter <= 59; counter++)
           {    
                pressureSum += pressure[counter];
                
   
          }
          categoryAverage = categorySum/ 59;
          speedAverage = speedSum/59;
          pressureAverage = pressureAverage/59;
          
          System.out.println(categoryAverage);
          System.out.println(speedAverage);
          System.out.println(pressureAverage);
        
}
    
}

```

---

### Post by Arndt on 2009-10-16
> **nathang1392 said:**
> i got most of the issues that you guys pointed out fixed. now one of my averages sort of works, i think, but its not making any sense. its like this




Why doesn't it make sense? Maybe you want the average to be a real number, not an integer.

Besides, if you have 60 elements, you divide by 60 to get the average, not 59.

---

### Post by benj1 on 2009-10-16
i would change it so you work out the avg speed first then apply the avg category to the avg speed

edit: or atleast be aware that its possible that you will get two different answers

---


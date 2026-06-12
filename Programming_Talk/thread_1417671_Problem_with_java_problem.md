---
title: "Problem with java problem"
date: 2010-02-27
forum: Programming Talk
---

### Post by vik_2010 on 2010-02-27
I'm having this problem with a Java program. It's the simple number guessing game that's featured in beginning programmer challenges ( i.e. guess a num between 1 and 100). This program just keeps asking for more input. If I enter 50, it goes the next line and continues waiting for more input. how do I get it to get to the next stage where it states whether the number was too high or low?
[PHP]import java.util.*;
import java.io.*;
public class NumberGame {
    public static void main(String[] args) {
        int again_opt = 1;    
        Scanner scan = new Scanner(System.in);
        PrintWriter out = new PrintWriter(System.out);
        String input;
        int inputint=0, answer;
        while (again_opt==1) {
                System.out.println("Pick a random num between 1 and 100.");
                answer=(int)(Math.random()*100)+1;                
                try
                    while (inputint != answer){
                        inputint = Integer.parseInt(scan.nextLine());                    
                        if (inputint < answer)
                            out.println("Higher");
                        else
                            out.println("Lower");
                    }
                    out.println("Congragulations! The random num was "+answer+".\nPlay again? [y/n]");
                    
                    do {                
                            input=scan.nextLine();    
                        if (input=="n" || input=="N" || input=="No")
                            again_opt=0;
                        else if (input != "y" || input != "Y" || input != "Yes" || input != "yes")            
                            again_opt=1;
                        else {
                            out.println("Enter answer again [y/n]");
                            again_opt=2;
                        }
                    } while (again_opt==2);    
                                
                } catch(Exception e){
                    out.println("Pleae put an integer value");
                }
        }        
        out.println("Thank's for playing");    
    }
}[/PHP]

Also, it seems way too complicated (too many loops, etc). I remember doing this a few weeks ago and it seemed much simpler at the time. Is my program too convoluted for the prompt?

---

### Post by Conzar on 2010-02-27
Looks like your program works except that the PrintWriter isn't actually printing to the screen.  I would suggest using System.out.println instead of out.println.

Also the code below is incorrect.
```
    if (input=="n" ...)

```

In java, if you want to compare Strings you must use the "equals" method.  By using the == operator, you are actually comparing the reference of the two Strings.

In this case, input will never have the same reference as "n"

So the proper statement would be (input.equals("n") ...)

Hope this helps

---

### Post by Queue29 on 2010-02-27
Also just a protip, instead of:
```
if(input.equals("n") || input.equals("N"))
```

you could instead do:
```
if(input.equalsIgnoreCase("n"))
```

String manipulation is fun.

---


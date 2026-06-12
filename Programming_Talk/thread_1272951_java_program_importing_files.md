---
title: "java program importing files"
date: 2009-09-22
forum: Programming Talk
---

### Post by nathang1392 on 2009-09-22
```
import java.util.Scanner;
import java.io.File;
import java.io.IOException;
public class Family
{
    public static void main(String [] args) throws IOException
    {
        int sampleSize = 0;
        int probabilityOfBoy = 0;
        int probabilityOfGirl = 0;
        int probabilityOfBoyAndGirl = 0;
        
        
        
        System.out.println("Sample Size: " + sampleSize);
        System.out.println("Two Boys: " + probabilityOfBoy);
        System.out.println("One Boy One Girl: " + probabilityOfBoyAndGirl);
        System.out.println("Two Girls: " + probabilityOfGirl);
        
        String token = "";
        Scanner inFile = new Scanner(new File("test1.txt"));
        while (inFile.hasNext())
        {
            token = inFile.next( );
            
            
                
              
        }
        inFile.close();
        }
    
}
```

"Write a program to calculate the probability that a family with two children
will consist of two boys, a boy and a girl, or two girls."

these are my instructions. i am supposed to write a program to calculate the probability of a family having two children. i am okay importing the file, but the file that i am supposed to import is like this: bb gg bg, representing boy and girl outcomes, but i dont know how to implement that into a program that is supposed to predict the probability of a couple's child combination.  thank you for any help.

---

### Post by PaulM1985 on 2009-09-23
What is the specific problem that you require solving?
"I don't know how to do my homework?" is not specific enough.

What are you trying to do?  Read information from a file?  If so what information are you trying to read in?  What format is it in?  Numbers, text, a mixture? (maybe give an example of the first couple of lines from the file)

What are your aims after that?

People won't do your coursework for you, but most would consider giving you general pointers to solving a particular problem.

---

### Post by nathang1392 on 2009-09-23
the bottom of the post says that the file is a txt that has bb,gg,bg representing boys and girls or a boy and a girl. im supposed to import it and use it to calculate the probability of a birth of two children. im sorry if it seemed i was just trying to get someone to do my work for me because that wasnt my intent. although this is very hard work for a high schooler, who is taking the course online, with no direct help from a teacher. i have updated the code to this: ```
import java.util.Scanner;
import java.io.File;
import java.io.IOException;
public class Family

{
    public static void main(String [] args) throws IOException
    {
        int sampleSize = 0;
        int twoBoys = 0;
        int twoGirls = 0;
        int boyAndGirl = 0;
        int probabilityOfBoy = 0;
        int probabilityOfBoyAndGirl = 0;
        int probabilityOfGirl = 0;
        int counter = 0;
        String token = "";
        
        Scanner inFile = new Scanner(new File("test1.txt"));
        token = inFile.next( );
        
        while (inFile.hasNext())
        {
            
            
            
                if (token.equals("BB"))
                {
                    twoBoys++;
                    counter++;
            
                }
                else if (token.equals("GG"))
                {
                    twoGirls++;
                    counter++;
            
                }
                else if (token.equals("BG"))
                {
                    boyAndGirl ++;
                    counter++;
                }   
                else if (token.equals("GB"))
                {    boyAndGirl++;
                    counter++;
                }
                    
                
            
            
        probabilityOfBoy = twoBoys / counter++ * 100;
        probabilityOfGirl = twoGirls / counter++ * 100;
        probabilityOfBoyAndGirl = boyAndGirl / counter++ * 100;
        
       
        System.out.println("Sample Size: " + counter++);
        System.out.println("Two Boys: " +"%" + probabilityOfBoy);
        System.out.println("One Boy One Girl: " +"%"+ probabilityOfBoyAndGirl);
        System.out.println("Two Girls: " +"%"+ probabilityOfGirl);
        inFile.close();
        }    
        
        
        
    }
        
        
        
    

}
```
i know it isnt the most efficient, but im just trying to make it work. i think i have most of it right, except i am getting an error: java.lang.IllegalStateException: Scanner closed
	at java.util.Scanner.ensureOpen(Scanner.java:1025)
	at java.util.Scanner.hasNext(Scanner.java:1280)
	at Family.main(Family.java:29)

---

### Post by myrtle1908 on 2009-09-23
There are a number of problems.  I'll point out the glaringly obvious to point you in the right direction.

1. You are closing inFile inside your while loop.  You probably don't want to do this.

2. The part where you are calculating probability and printing to the console is also inside the while loop and is probably not your intention.

The other problems you should be able to identify yourself.

---

### Post by nathang1392 on 2009-09-23
thanks for the help. i took all that stuff out of the loop, its really strange, but now when i compile i get no syntax errors, but when i run, it just doesnt do anything. im using blue j and the bar at the bottom left starts going and wont stop until i right click it and hit reset machine. what does this mean?

---

### Post by PaulM1985 on 2009-09-23
You have said that you have moved stuff outside of the while loop to do with calculations.

I'm not sure if you moved this out:

probabilityOfBoyAndGirl = boyAndGirl / counter++ * 100;

But I think you want to use "counter" rather than "counter++".  counter++ increases the counter variable and I am not sure you would want to do this in the while loop.

About the program not appearing to print anything and not stop.  When I am reading from a file I usually put a print statement in the while loop that tells me what line I am on.  So you could use something like:

System.out.println("currently on line " + counter);

Try creating a copy of your test file but only keep the first four lines so you should expect to see the counter message above four times and then the program finish to try and highlight the problems better.

Also, it may depend on where you have moved the other print statements.  Posting another copy of the current code would help.

Paul

---

### Post by PaulM1985 on 2009-09-23
I think the reason why you are not having the program end is that you are using a:

while (inFile.hasNext())

loop, you are never using the next() method on it to get the next line.  It will always loop because it will always have a next line if you don't get it.

Try using the next method (token = inFile.next(); ) to get the next line at the bottom of the while loop.  This should read all the lines from the file and hopefully this will solve your problem.

Paul
EDIT:

Rather than having the line 
token = inFile.next();
as the last line of the while loop, I would make it the first line inside the while loop and remove the token = inFile.next(); line before the start of the while loop

---


---
title: "I need an explanation!"
date: 2010-03-22
forum: Programming Talk
---

### Post by Michaeljs1990 on 2010-03-22
ok so I worked on this code forever and i finally figured it out. However i have no idea why it acts this way if someone could explain this to me it would be much appreciated 

the first code runs fine but gives the wrong answer. the second works. the spot in the program where i am confused i put in bold. Thank you very much in advanced.
```

package javahelp;
/***********************************************
*a guy
*what!?!
*3-21-10
*This program does random analysis of a sentence
************************************************/
import java.util.Scanner;
public class Main
{
        public static void main(String[] args)
        {
        int vowelsInSent = 0;
        String sentence; // users input sentence.
        int length;      // variable that is initialized find sentence length.
        Scanner stdIn = new Scanner(System.in);
        System.out.print("Please enter a sentence: ");
        sentence = stdIn.nextLine();
        length = sentence.length();
        length = length - 1;
        if (sentence.charAt(length) == '.')
                {
                char sH;
                int nextLetter;
                nextLetter = 0;
                sH = sentence.charAt(nextLetter); /***WHY DOES THIS NOT WORK?** **why does this have to go in the while loop***/
                while (length > nextLetter)
                        {
                        
                        if (sH == 'a' || sH == 'e' || sH == 'i' || sH == 'o' || sH == 'u')
                        {
                        vowelsInSent ++;
                        nextLetter ++;
                        }
                        else
                        {
                        nextLetter ++;
                        }
                        }
                }
        else
                {
                System.out.print("\"" + sentence + "\"" + ", is not a sentence." + '\n');
                }
        System.out.println("Your sentence contains " + vowelsInSent + " vowels.");
        }
}

``````

package javahelp;
/***********************************************
*person
*what!?!
*3-21-10
*This program does random analysis of a sentence
************************************************/
import java.util.Scanner;
public class Main
{
        public static void main(String[] args)
        {
        int vowelsInSent = 0;
        String sentence; // users input sentence.
        int length;      // variable that is initialized find sentence length.
        Scanner stdIn = new Scanner(System.in);
        System.out.print("Please enter a sentence: ");
        sentence = stdIn.nextLine();
        length = sentence.length();
        length = length - 1;
        if (sentence.charAt(length) == '.')
                {
                char sH;
                int nextLetter;
                nextLetter = 0;
**                // WHY DO I HAVE TO PUT sH= sentence.charAt(nextLetter); in the while loop **
                while (length > nextLetter)
                        {
                        
                        if (sH == 'a' || sH == 'e' || sH == 'i' || sH == 'o' || sH == 'u')
                        {
                        sH = sentence.charAt(nextLetter);
                        vowelsInSent ++;
                        nextLetter ++;
                        }
                        else
                        {
                        nextLetter ++;
                        }
                        }
                }
        else
                {
                System.out.print("\"" + sentence + "\"" + ", is not a sentence." + '\n');
                }
        System.out.println("Your sentence contains " + vowelsInSent + " vowels.");
        }
}



```

---

### Post by ndefontenay on 2010-03-22
Hi.

What you do is:

get a sentence
put letter Number n in sH variable.
Check if is a vowel.

You'll have to modify the value of sH inside the loop in order for sH to get the next letter as a value.

If you do that before the loop, sH will get the very first letter as a value and never change.

That is why it doesn't work with  sH = sentence.charAt(nextLetter) outside of the loop

---

### Post by Michaeljs1990 on 2010-03-22
thank you very much! have a good day!

---


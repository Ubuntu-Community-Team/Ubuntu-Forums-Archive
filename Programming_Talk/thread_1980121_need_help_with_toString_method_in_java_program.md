---
title: "need help with toString method in java program"
date: 2012-05-14
forum: Programming Talk
---

### Post by Mia_tech on 2012-05-14
guys, I'm working on a program that converts numbers to words, but I'm having problems with the toString() method. All the methods were given to me so I could implement them, so I can't remove any of them... 

number: 4564 --> four thousand and five hundred and sixty four

here's the code
Numbers class

```
package numberstowords;


public class Test {
    
    //array to store the word equivalent of numbers
    public static String[] s = new String[8];

    public static void main(String[] args) {
        
        int count = 0;    
        Scanner input = new Scanner(System.in);
        do
        {
            System.out.println("Enter an integer (4 digits max)--> ");
            int value = input.nextInt();
            if(value > 0)
            {
                Numbers n = new Numbers(value);
                //s[count] = n.toString();
                System.out.println(n.toString());
                count++;
            }
            else break;
        }while(true);


```

---

### Post by PaulM1985 on 2012-05-14
Sounds very much like a homework question.

Do you want to explain what is happening specifically?  What you are struggling with?  Since this is a homework question, people are not going to tell you the answer, they are more likely to point you in the right direction if you give some more.

Paul

---

### Post by dwhitney67 on 2012-05-14
> **Mia_tech said:**
> guys, I'm working on a program that converts numbers to words, but I'm having problems with the toString() method...

I ran your code, and it seems to work fine for numbers that fit your requirements.  For negative numbers, the application merely exits without issuing a warning message.  For 5-digit numbers the app crashes.  Both of these issues should be addressed.

As for nit-picking, I would take out the "and" when printing thousands followed by hundreds; in other words, remove the "and" (and replace with a white-space) at this line:
```

strOut = strOut + " and " + hundredsToString(hundred);

```
Also, 30 is spelled as "thirty", not "therty".

---

### Post by Mia_tech on 2012-05-14
> **dwhitney67 said:**
> I ran your code, and it seems to work fine for numbers that fit your requirements.  For negative numbers, the application merely exits without issuing a warning message.  For 5-digit numbers the app crashes.  Both of these issues should be addressed.

As for nit-picking, I would take out the "and" when printing thousands followed by hundreds; in other words, remove the "and" (and replace with a white-space) at this line:
```

strOut = strOut + " and " + hundredsToString(hundred);

```
Also, 30 is spelled as "thirty", not "therty".

no number 2345 = two thousand and three hundred and forty five

that "and" needs to go after the thousand numbers.

it does not work for teen numbers 11...19 it prints out 
"eleven one"
how could I get around that?

I appreciate the help

---

### Post by PaulM1985 on 2012-05-14
I would deal with numbers between 0 and 99 together.

You would have:
```

if (tens == 1 && ones != 0)
{
   // Do something for teens
}
else
{
   // Do tens

   // Do ones
}

```

Paul

---

### Post by dwhitney67 on 2012-05-14
> **Mia_tech said:**
> 
it does not work for teen numbers 11...19 it prints out 
"eleven one"
how could I get around that?


You should have shared that little nugget within your opening post!

---


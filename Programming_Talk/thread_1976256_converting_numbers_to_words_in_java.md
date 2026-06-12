---
title: "converting numbers to words in java"
date: 2012-05-08
forum: Programming Talk
---

### Post by Mia_tech on 2012-05-08
guys, I'm working on a program in which I need to convert numbers to words eg: 101 = one hundred one. I have found a couple of code samples on the net like this [one ]("http://www.rgagnon.com/javadetails/java-0426.html"); however, I'm trying to use a different methodology. But still not working correctly... if anyone could help or have a better way of doing this I appreciate

```
/* 
 * Program to convert numbers to words
 * Date:7/05/2012
 * 
 */

package numberstowords;

import java.util.Scanner;

public class NumbersToWords {
    //array containing single digits
    public static final String[] digits = 
    {
        "",
        " one",
        " two",
        " three",
        " four",
        " five",
        " six",
        " seven",
        " eight",
        " nine",
        
    };
    
    //array containing teens
    public static final String[] teens = 
    {
        " eleven",
        " twelve",
        " thirteen",
        " fourteen",
        " fifteen",
        " sixteen",
        " seventeen",
        " eighteen",
        " nineteen"
    };
    
    //array containing tens numbers
    public static final String[] tens = 
    {
        "ten",
        "twenty",
        "therty",
        "fourty",
        "fifty",
        "sixty",
        "eighty",
        "ninety",
    };
    
    //string for hundreds numbers
    public static final String hundred = "hundred";
    
    
    
    public static int tmpNum,  //temp number for calculations
                      newNum,  //number reslut from division
                      number,  //number to be converted to words
                      result;  //result number
                                                

    public static void main(String[] args) {
        
        
        Scanner in = new Scanner(System.in);
        
        //getting user input
        System.out.print("Please enter a number: ");
        number = in.nextInt(); //number to be converted
        //input validation
        while(number <= 0)
        {
            System.out.println("Number should be biger than cero!");
            System.out.print("Please enter a number:");
            number = in.nextInt();
        }
        
       while(number != 0)
       {
           //converting num to word for num smaller than 10
           if(number > 0 && number < 10)
           {
               newNum = number / 10;
               tmpNum = newNum * 10;
               result = number - tmpNum;
               System.out.println("digits " + digits[result+1]);
               number = newNum;
           }
           //converting num to word for num < 10 && > 19
           if(number > 10 && number < 19)
           {
               newNum = number / 10;
               tmpNum = newNum * 10;
               result = number - tmpNum;
               System.out.println("teens " + teens[result]);
               number = newNum;
           }
           //converting for num tens digits
           if(number == 10 || (number > 19 && number < 100))
           {
               newNum = number / 10;
               tmpNum = newNum * 10;
               result = number - tmpNum;
               System.out.println("tens " + tens[result]);
               number = newNum;
               
           }
           //converting for hundreds
           if(number > 100 && number < 999)
           {
               newNum = number / 10;
               tmpNum = newNum * 10;
               result = number - tmpNum;
               System.out.println("hundreds " + hundred);
               number = newNum;
           }
       }
              
    }
}

```

---

### Post by cajual on 2012-05-08
This seems incredibly convoluted for no reason...

```

    if(number > 0 && number < 10)
    {
       newNum = number / 10;
       tmpNum = newNum * 10;
       result = number - tmpNum;
       System.out.println("digits " + digits[result+1]);
       number = newNum;
    }

```Can't you just do:

```

    if(number >= 0 && number < 10)
    {
       System.out.println("digits " + digits[Math.floor(number)]
       // Given digits index begins at 0 => "Zero" and whole integers
    }

    >> 9 >> digits[9] >> "Nine"
    >> 9.1234 >> digits[9] >> "Nine"

```

---

### Post by Mia_tech on 2012-05-10
I came up with this solution, the only caveat is that it will only convert up to 999... could any one implement pass 999?
```
/* 
 * Program to convert numbers to words
 * Date:7/05/2012
 * 
 */

package numberstowords;

import java.util.Scanner;

public class NumbersToWords {
    //array containing single digits
    public static final String[] digits = 
    {
        "",
        " one",
        " two",
        " three",
        " four",
        " five",
        " six",
        " seven",
        " eight",
        " nine",
        
    };
    
    //array containing teens
    public static final String[] teens = 
    {
        " eleven",
        " twelve",
        " thirteen",
        " fourteen",
        " fifteen",
        " sixteen",
        " seventeen",
        " eighteen",
        " nineteen"
    };
    
    //array containing tens numbers
    public static final String[] tens = 
    {
        "ten",
        "twenty",
        "therty",
        "fourty",
        "fifty",
        "sixty",
        "seventy",
        "eighty",
        "ninety",
    };
    
    //string for hundreds numbers
    public static final String hundred = "hundred";  
    
    
    public static int tmpDigit,  //temp number to store digits
                      tmpTeen,  //temp to store teens numbers
                      tmpTen,  //temp number to store tens
                      number,  //number to be converted to words
                      result;  //result number
    //deciding whether a num is teen or not
    public static boolean teen = false; 
                                                

    public static void main(String[] args) {
        
        
        Scanner in = new Scanner(System.in);
        
        //getting user input
        System.out.print("Please enter a number: ");
        number = in.nextInt(); //number to be converted
        //input validation
        while(number <= 0)
        {
            System.out.println("Number should be bigger than cero!");
            System.out.print("Please enter a number:");
            number = in.nextInt();
        }
        //converting single digits number
        if(number > 0 && number < 10)
        {
            result = number % 10;
            System.out.println(digits[result]);
        }
        //converting teen numbers
        if(number > 10 && number < 20)
        {
            result = number % 10;
            System.out.println(teens[result-1]);
        }
        //converting from 20 to 100 numbers
        if(number > 19 && number < 100)
        {
            result = number / 10; //finding tens
            System.out.print(tens[result-1]);
            
            number %= 10; //finding single digits
            System.out.println(digits[number]);
        }
        //converting from 101 to 999
        if(number > 100 && number < 1000)
        {
            result = number / 100; //getting hundreds
            //getting tens, and finding tens, and teens numbers
            tmpTen = number % 100;
            if(tmpTen > 1 && tmpTen < 20)//if teen go get it
            {
                tmpTeen = tmpTen % 10;
                teen = true; 
            }
            else //if not a teen split number
                tmpTen /= 10;
            //finding digits
            tmpDigit = number % 10;
            
            if(!teen)//if final result doesn't include teen numbers print the following
                System.out.println(digits[result]+" "+hundred+" "+tens[tmpTen-1]+" "+digits[tmpDigit]);
            else
                System.out.println(digits[result]+" "+hundred+" "+teens[tmpTeen-1]);           
        }
           
              
    }
}

```

---


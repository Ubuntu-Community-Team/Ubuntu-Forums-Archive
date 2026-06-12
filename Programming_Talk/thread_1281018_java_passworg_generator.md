---
title: "java passworg generator"
date: 2009-10-02
forum: Programming Talk
---

### Post by nathang1392 on 2009-10-02
im supposed to make a password generator that allows you to pick what type of password you want and how many characters. i think what i have is right, but i cant get it to work. if you think this is the wrong direction to go in, or if you can help me make this one work, please feel free.

---

### Post by nathang1392 on 2009-10-02
i havent gotten super far, i want to make sure that im going in the right direction before i go much further.

```
import java.util.Scanner;
import java.util.Random;
import java.io.IOException;
import java.io.PrintWriter;
import java.io.File;

public class Password
{
    public static void main(String [] args)
    {
        Scanner in;  
        in = new Scanner(System.in);
    
    
        System.out.println("                Password Generation Menu                ");
        System.out.println("********************************************************");
        System.out.println("*  [1] Lowercase Letters                               *");
        System.out.println("*  [2] Lowercase & Uppercase Letters                   *");  
        System.out.println("*  [3] Lowercase, Uppercase, and Numbers               *");
        System.out.println("*  [4] Lowercase, Uppercase, Numbers, and Punctuation  *");
        System.out.println("*  [5] Quit                                            *");
        System.out.println("********************************************************");
        System.out.println("Enter Selection (1-5): ");
        int choice = in.nextInt();
        System.out.println("Password Length (1-14): ");
        int passwordLength = in.nextInt();
        int randNum = ((int)(0+ Math.random()* 122));
        
        boolean lowerCase = (randNum>=97) && (randNum<=122);
        boolean upperCase = (randNum>=65) && (randNum<=90);
        boolean numbers = (randNum>=48) && (randNum<=57);
        boolean punctuation = (randNum>=58) && (randNum<=64);
        
        System.out.println("\n");
        
        
       for (int counter = 0; counter == passwordLength; counter++) 
       {
            if (choice == 1)
            {
                while(lowerCase)
                {
                    randNum = ((int)(0+ Math.random()* 122));
                    char letters = (char) randNum;
            
                }

            }
        
            if (choice == 2)
            {
                while(upperCase)
                {
                    randNum = ((int)(0+ Math.random()* 122));
                }
            
            }
                
                
            if (choice == 3)
            {
            
                while(numbers)
                {
                    randNum = ((int)(0+ Math.random()* 122));
                }
        
            }
        
            if (choice == 4)
            {
            
                while(punctuation)
                {
                    randNum = ((int)(0+ Math.random()* 122));
                }
            }
        
        }
        
        
        
    }

}
```

---

### Post by mcsimon on 2009-10-02
```

for (int counter = 0; counter == passwordLength; counter++)

```

should be:

```

for (int counter = 0; counter < passwordLength; counter++)

```

---

### Post by nathang1392 on 2009-10-02
i made the correction, its still not working though. do you think my loops and if statements are correct?

---

### Post by NovaAesa on 2009-10-02
I would highly suggest writing an algorithm before you even attempt writing any code. There isn't really much you can do in code before you have a good algorithm. Might I suggest an algorithm such as this:

```

main() {
    choice = input()
    if choice == 5 then quit
    pwLength = input()
    for counter = 1 up to pwLength {
        if choice == 1 {
            output((char)random number between 97 and 122)
        } else if choice == 2 {
            output((char)random number between 97 and 122 or 65 and 90)  
        } else if choice == 3 {
            output((char)random number between 97 and 122 or 65 and 90 or 48 and 57)
        } else if choice == 4 {
            output((char)random number between 97 and 122 or 65 and 90 or 48 and 57 or 58 and 65)
        }
    }   
}

```

Of course, I don't know *exactly* what you are trying to do, so my algorithm will obviously need to be adjusted by you to suit what the exact task is. Once you are happy with the algorithm, you can then go onto implement it in Java.

---

### Post by nathang1392 on 2009-10-03
alright. im going to wirk on developing an algorithm, an trying to get it into code. yours looked good. thanks for the advice. just so there is no confusion, here is a set of instructions that makes some sense: > Display a menu giving the user a choice of character sets to use 
        to construct the password. (Note: Do not use the first range of 
        punctuation symbols with ASCII values from 33--47). 
      Allow the user to select the number of characters in the password (at least 1--14). 
      Create a randomly generated password from the selected character sets.

---

### Post by nathang1392 on 2009-10-03
> **NovaAesa said:**
> I would highly suggest writing an algorithm before you even attempt writing any code. There isn't really much you can do in code before you have a good algorithm. Might I suggest an algorithm such as this:

```

main() {
    choice = input()
    if choice == 5 then quit
    pwLength = input()
    for counter = 1 up to pwLength {
        if choice == 1 {
            output((char)random number between 97 and 122)
        } else if choice == 2 {
            output((char)random number between 97 and 122 or 65 and 90)  
        } else if choice == 3 {
            output((char)random number between 97 and 122 or 65 and 90 or 48 and 57)
        } else if choice == 4 {
            output((char)random number between 97 and 122 or 65 and 90 or 48 and 57 or 58 and 65)
        }
    }   
}

```

Of course, I don't know *exactly* what you are trying to do, so my algorithm will obviously need to be adjusted by you to suit what the exact task is. Once you are happy with the algorithm, you can then go onto implement it in Java.


> output((char)random number between 97 and 122 or 65 and 90) 

alright, im trying to code and i just dont know any code to do this. could i get an example?

---

### Post by dwhitney67 on 2009-10-03
If the user asks for the password to contain numbers, upper and lowercase letters, and symbols, then the password should contain these.

The code the OP presented will allow for a random password to be created, however it does not *guarantee* that the password will contain these values.  IMO, randomness alone is not a viable solution; the app also needs to verify that the password meets the user's criteria.

I wrote some C++ code recently that generates "random" passwords.  It met the criteria of having at least one symbol, one uppercase letter, one lowercase letter, and one number, because this is what is required for the passwords at my job site.

Here's that code (which should be easy to translate to Java):
```

#include <string>
#include <iostream>
#include <cstdlib>
#include <ctime>

class PasswordGenerator
{
public:
   PasswordGenerator(const size_t size);

   std::string getPassword();

private:
   bool validPassword() const;

   size_t m_size;
   bool   m_hasUpper;
   bool   m_hasLower;
   bool   m_hasNum;
   bool   m_hasSpecial;
};

PasswordGenerator::PasswordGenerator(const size_t size)
   : m_size(size)
{
   srand(time(0));
}

std::string
PasswordGenerator::getPassword()
{
   const int minChar = 0x21;
   const int maxChar = 0x7E;

   std::string password;

   while (!validPassword())
   {
      std::string tmpPassword;

      while (tmpPassword.size() < m_size)
      {
         const int ch = (rand() % (maxChar - minChar)) + minChar;

         if ((ch >= 0x21 && ch <= 0x2F) ||
             (ch >= 0x3A && ch <= 0x40) ||
             (ch >= 0x5B && ch <= 0x60) ||
             (ch >= 0x7B && ch <= 0x7E))
         {
            m_hasSpecial = true;
            tmpPassword += ch;
         }
         else if ((ch >= 0x30 && ch <= 0x39))
         {
            m_hasNum = true;
            tmpPassword += ch;
         }
         else if ((ch >= 0x41 && ch <= 0x5A))
         {
            m_hasUpper = true;
            tmpPassword += ch;
         }
         else if ((ch >= 0x61 && ch <= 0x7A))
         {
            m_hasLower = true;
            tmpPassword += ch;
         }
      }

      password = tmpPassword;
   }

   return password;
}

bool
PasswordGenerator::validPassword() const
{
   return m_hasUpper && m_hasLower && m_hasNum && m_hasSpecial;
}


int main(int argc, char** argv)
{
   if (argc != 2)
   {
      std::cerr << "Usage: " << argv[0] << " <password size>" << std::endl;
      return -1;
   }

   PasswordGenerator passgen(atoi(argv[1]));

   std::cout << passgen.getPassword() << std::endl;
}

```

---

### Post by nathang1392 on 2009-10-03
> **dwhitney67 said:**
> If the user asks for the password to contain numbers, upper and lowercase letters, and symbols, then the password should contain these.

The code the OP presented will allow for a random password to be created, however it does not *guarantee* that the password will contain these values.  IMO, randomness alone is not a viable solution; the app also needs to verify that the password meets the user's criteria.

I wrote some C++ code recently that generated "random" passwords.  It met the criteria of having at least one symbol, one uppercase letter, one lowercase letter, and one number, because this is what is required for the passwords at my job site.

Here's that code (which should be easy to translate to Java):
```

#include <string>
#include <iostream>
#include <cstdlib>
#include <ctime>

class PasswordGenerator
{
public:
   PasswordGenerator(const size_t size);

   std::string getPassword();

private:
   bool validPassword() const;

   size_t m_size;
   bool   m_hasUpper;
   bool   m_hasLower;
   bool   m_hasNum;
   bool   m_hasSpecial;
};

PasswordGenerator::PasswordGenerator(const size_t size)
   : m_size(size)
{
   srand(time(0));
}

std::string
PasswordGenerator::getPassword()
{
   const int minChar = 0x21;
   const int maxChar = 0x7E;

   std::string password;

   while (!validPassword())
   {
      std::string tmpPassword;

      while (tmpPassword.size() < m_size)
      {
         const int ch = (rand() % (maxChar - minChar)) + minChar;

         if ((ch >= 0x21 && ch <= 0x2F) ||
             (ch >= 0x3A && ch <= 0x40) ||
             (ch >= 0x5B && ch <= 0x60) ||
             (ch >= 0x7B && ch <= 0x7E))
         {
            m_hasSpecial = true;
            tmpPassword += ch;
         }
         else if ((ch >= 0x30 && ch <= 0x39))
         {
            m_hasNum = true;
            tmpPassword += ch;
         }
         else if ((ch >= 0x41 && ch <= 0x5A))
         {
            m_hasUpper = true;
            tmpPassword += ch;
         }
         else if ((ch >= 0x61 && ch <= 0x7A))
         {
            m_hasLower = true;
            tmpPassword += ch;
         }
      }

      password = tmpPassword;
   }

   return password;
}

bool
PasswordGenerator::validPassword() const
{
   return m_hasUpper && m_hasLower && m_hasNum && m_hasSpecial;
}


int main(int argc, char** argv)
{
   if (argc != 2)
   {
      std::cerr << "Usage: " << argv[0] << " <password size>" << std::endl;
      return -1;
   }

   PasswordGenerator passgen(atoi(argv[1]));

   std::cout << passgen.getPassword() << std::endl;
}

```

> if ((ch >= 0x21 && ch <= 0x2F) ||
             (ch >= 0x3A && ch <= 0x40) ||
             (ch >= 0x5B && ch <= 0x60) ||
             (ch >= 0x7B && ch <= 0x7E))

alright, i dont know c++, but is this throwing out all of the randoms that you wont use?

---

### Post by nathang1392 on 2009-10-03
so would this be a way of going about doing it? 
```
       for (int counter = 0; counter <  passwordLength; counter++) 
       {
           randNum = ((int)(0+ Math.random()* 122));
           
           if((randNum>= 48 && randNum <=57) ||  (randNum >=58 && randNum <= 64) || (randNum >=65 && randNum <=90) || (randNum >= 97 && randNum <= 122))
           {
               
           
                    else if (choice == 1)
                    char letter = randNum;
                
          }
```

---

### Post by nathang1392 on 2009-10-03
lol im am going through alot of different thoughts all at once, sorry for posting so much. is this a possible way to do it?
```
       for (int counter = 0; counter <  passwordLength; counter++) 
       {
           randNum= ((int)(0+ Math.random()* 122));
           
           while(randNum >=58 && randNum <= 64)
           {
               
               char myChar = (char) randNum;
               System.out.println(myChar);
        }
        
```

---

### Post by dwhitney67 on 2009-10-03
> **nathang1392 said:**
> alright, i dont know c++, but is this throwing out all of the randoms that you wont use?

No, what I am doing is filtering the random value to ensure that it is an ASCII value.  There are certain ASCII values which are not printable (ie. not viewable) and thus these cannot be used in the password.

For a complete listing of the ASCII table, run this command (or google):
```

man ascii

```

---

### Post by nathang1392 on 2009-10-03
my last post of code will output the menu, let me select my type and amount of characters, but then after that it just wont output my char. anyone have any advice?

---

### Post by dwhitney67 on 2009-10-03
> **nathang1392 said:**
> my last post of code will output the menu, let me select my type and amount of characters, but then after that it just wont output my char. anyone have any advice?

Why are using a while loop to validate the randNum value?  It is not necessary, and furthermore you never change the value of randNum once (and if) you enter the while-loop.

You need to focus on either outputting a single _printable_ character at a time to the standard out (System.out.print()), or better yet, build up a string with the password.  For example
```

String password = "";

for (int len = 0; len < passwordLength; ++len)
{
   char randCh = 0;

   do
   {
      randCh = (char)(Math.random() * 122);

   } while (!isPrintable(randCh));

   password += randCh;
}

```

P.S.  isPrintable() can be defined as:
```

import java.lang.Character;
...
public static boolean isPrintable(char ch)
{
   int type = Character.getType(ch);

   return type != Character.CONTROL && type != Character.SPACE_SEPARATOR;
}
...

```

---

### Post by nathang1392 on 2009-10-03
i get what your saying, but how else could i validate that my random number is in that range? i am just trying to get it to work now, but i have to make menu options 2 - 4 give multiple types of characters. i tried to use what you suggested about building my string. now this is my code:```
import java.util.Scanner;
import java.util.Random;
import java.io.IOException;
import java.io.PrintWriter;
import java.io.File;

public class Password
{
    public static void main(String [] args)
    {
        Scanner in;  
        in = new Scanner(System.in);
    
    
        System.out.println("                Password Generation Menu                ");
        System.out.println("********************************************************");
        System.out.println("*  [1] Lowercase Letters                               *");
        System.out.println("*  [2] Lowercase & Uppercase Letters                   *");  
        System.out.println("*  [3] Lowercase, Uppercase, and Numbers               *");
        System.out.println("*  [4] Lowercase, Uppercase, Numbers, and Punctuation  *");
        System.out.println("*  [5] Quit                                            *");
        System.out.println("********************************************************");
        System.out.println("Enter Selection (1-5): ");
        int choice = in.nextInt();
        System.out.println("Password Length (1-14): ");
        int passwordLength = in.nextInt();
        int randNum = ((int)(0+ Math.random()* 122));
        String password = "";
        

        
        System.out.println("\n");
        
        
       for (int counter = 0; counter <  passwordLength; counter++) 
       {
           
           randNum= ((int)(0+ Math.random()* 122));
           
           if (choice ==1)
           {
           while(randNum >=97 && randNum <= 122)
           {
               password += (char)randNum;
               

            }
        }
            
            if (choice == 2)
            {
            while(randNum >=65 && randNum <= 90)
            {
                password += (char)randNum;
                
            }
        }
         if (choice ==3)
        {
            while(randNum >=48 && randNum <= 57)
            {
                password += (char)randNum;
            }
        }
        if (choice ==4)
        {
            
            while(randNum >=58 && randNum <= 64)
            {
                password += (char)randNum;
            }
        }
        
    }
    
    }
}
        
```
if you will help me understand how to do it without the while loops i will try to fix my code.

---

### Post by nathang1392 on 2009-10-03
here is my output if it helps:
>                 Password Generation Menu                
********************************************************
*  [1] Lowercase Letters                               *
*  [2] Lowercase & Uppercase Letters                   *
*  [3] Lowercase, Uppercase, and Numbers               *
*  [4] Lowercase, Uppercase, Numbers, and Punctuation  *
*  [5] Quit                                            *
********************************************************
Enter Selection (1-5): 
1
Password Length (1-14): 
3







---

### Post by dwhitney67 on 2009-10-03
As I stated earlier, you do not need the while-loops.  You will however require if-statement(s).

You should consider employing the use of the Character class (it is documented here [http://java.sun.com/javase/6/docs/api/java/lang/Character.html](http://java.sun.com/javase/6/docs/api/java/lang/Character.html)).

Depending on the user's choice for the type of password, create a filter that can be used to validate each of the characters you obtain from the Math.random() function.

Here's working code, however as I stated in my opening post, this code has one feature missing... a validator to ensure that the password meets the user's complete requirements.  I will leave this as an exercise for you to complete.  (For hints, look at the C++ code I provided earlier.)
```

import java.util.Scanner;
import java.util.Random;
import java.util.ArrayList;
import java.lang.Character;


public class PasswordGenerator
{
   public PasswordGenerator()
   {
   }

   public String getPassword(int length, ArrayList<Integer> filter)
   {
      String password = "";

      for (int len = 0; len < length; ++len)
      {
         char ch = 0;

         do
         {
            ch = (char)(Math.random() * 122);

         } while (!isValid(ch, filter));

         password += ch;
      }

      return password;
   }

   private boolean isValid(char ch, ArrayList<Integer> filter)
   {
      int type = Character.getType(ch);

      boolean valid = false;

      for (int i = 0; i < filter.size(); ++i)
      {
         int ftype = filter.get(i);

         if (type == ftype)
         {
            valid = true;
            break;
         }
      }

      return valid;
   }

   public static void main(String [] args)
   {
      Scanner in = new Scanner(System.in);
    
      System.out.println("                Password Generation Menu                ");
      System.out.println("********************************************************");
      System.out.println("*  [1] Lowercase Letters                               *");
      System.out.println("*  [2] Lowercase & Uppercase Letters                   *");  
      System.out.println("*  [3] Lowercase, Uppercase, and Numbers               *");
      System.out.println("*  [4] Lowercase, Uppercase, Numbers, and Punctuation  *");
      System.out.println("*  [5] Quit                                            *");
      System.out.println("********************************************************");
      System.out.print("Enter Selection (1-5): ");

      int choice = in.nextInt();

      if (choice == 5) return;   // we're done!

      System.out.print("Password Length: ");

      int passwordLength = in.nextInt();

      ArrayList<Integer> filter = new ArrayList<Integer>();

      // add filters per the user's request
      switch (choice)
      {
         case 1:
             filter.add(new Integer(Character.LOWERCASE_LETTER));
             break;

         case 2:
             filter.add(new Integer(Character.LOWERCASE_LETTER));
             filter.add(new Integer(Character.UPPERCASE_LETTER));
             break;

         case 3:
             filter.add(new Integer(Character.LOWERCASE_LETTER));
             filter.add(new Integer(Character.UPPERCASE_LETTER));
             filter.add(new Integer(Character.DECIMAL_DIGIT_NUMBER));
             break;

         case 4:
             filter.add(new Integer(Character.LOWERCASE_LETTER));
             filter.add(new Integer(Character.UPPERCASE_LETTER));
             filter.add(new Integer(Character.DECIMAL_DIGIT_NUMBER));
             filter.add(new Integer(Character.CONNECTOR_PUNCTUATION));
             filter.add(new Integer(Character.DASH_PUNCTUATION));
             filter.add(new Integer(Character.END_PUNCTUATION));
             filter.add(new Integer(Character.FINAL_QUOTE_PUNCTUATION));
             filter.add(new Integer(Character.INITIAL_QUOTE_PUNCTUATION));
             filter.add(new Integer(Character.OTHER_PUNCTUATION));
             filter.add(new Integer(Character.START_PUNCTUATION));
             break;
      }

      PasswordGenerator pg = new PasswordGenerator();
      String password = pg.getPassword(passwordLength, filter);

      System.out.println("Password: " + password);
   }
}

```

P.S.  The example above uses the 122-value that you employed.  Technically though, you should use 125, since this will allow the characters '{', '|', '}', and '~' to be considered when generating a password string.

---

### Post by nathang1392 on 2009-10-03
wow. thats some pretty advanced stuff. im only in high school computer science lol.

---

### Post by dwhitney67 on 2009-10-03
> **nathang1392 said:**
> wow. thats some pretty advanced stuff. im only in high school computer science lol.

You do not need to make your app with an OO-design.  All you have to remember to do is to ensure that you have all of the information from the user and any other information you can extrapolate from the user's input that will assist you in putting together the password.

The "Character" class is convenient, but not necessary to use.  You can compare the character obtained from the use of Math.random() in a similar way I did in my C++ program.  Just look at the ASCII table to see the values that correspond to each character.  Numbers for instance, range from 48 to 57 (or 0x30 - 0x39).

Good luck with your project!

---

### Post by nathang1392 on 2009-10-03
i know this is pretty basic but the thing  i am having the most problems with is getting my random numbers to be in the correct range.

---

### Post by dwhitney67 on 2009-10-03
> **nathang1392 said:**
> i know this is pretty basic but the thing  i am having the most problems with is getting my random numbers to be in the correct range.

Bookmark this page: [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

Wrt the Math.random() function, the documentation is here: [http://java.sun.com/javase/6/docs/api/java/lang/Math.html#random(](http://java.sun.com/javase/6/docs/api/java/lang/Math.html#random())

Now, if you read the documentation, random() returns a value ranging from 0.0 to less than 1.0.  In cases where you want to yield a value that is in your data set (say the ASCII values), you convert the "[normalized]("https://www.opends.org/wiki/page/DefinitionNormalizedValue")" value returned by random() to a unique point in your data set.  In some circles, this unique point is referred to as an "engineering" value.

If that is not quite clear, then think of a scale on a map.  For every inch, that distance may represent say 500 miles.

Another analogy, but more technical, is taking the normalized (raw) value reported by an A/D (analog to digital) converter.  The application can read the converter to obtain a value between 0 and 1.0, and this may map to an engineering value between, say, -5V to +5V.  One can then deduce a formula to represent how the normalized value relates to a voltage value.

```

Voltage = NormValue * (MaxVoltage - MinVoltage) + MinVoltage

```

For the ASCII table, you are doing the same; but instead of voltage, you are converting to a unique value from 0 to 127.  Thus:
```

AsciiValue = NormValue * (127 - 0) + 0;

```
Obviously the "+ 0" is not required, but it is there to complete the formula, which is:
```

EngValue = NormValue * (Max - Min) + Min;

```

Anyhow, I hope this helps in understanding the point of converting the Math.random() value.

---

### Post by nathang1392 on 2009-10-03
i dont know if the last quote on your post was a formula, but if it was, what represents normValue? if it wasnt, is there a formula to help me calculate the scale of these numbers?

---

### Post by nathang1392 on 2009-10-03
```
 for (int counter = 0; counter <  passwordLength;) 
       {
           
          counter++;
          
                 if (choice ==1)
                 {
           
              randNum =   (int) (Math.random() * (122 - 97 + 1) ) + 97;
              char letter = (char) randNum;
              password += letter;
               
               
            }
            
           else if (choice == 2)
            {
               randNum =   (int) (Math.random() * (122 - 97 + 1) ) + 97 ||  (int) (Math.random() * (122 - 97 + 1) ) + 97;<==================================
              char letter = (char) randNum;
              password += letter;
                
                
            }
```
alright, i have gotten this figured out up until here(the place with an arrow.) i know this is incorrect, but i have it there to show you what i am trying to do. how can i make this pick between two ranges?

---

### Post by pbrockway2 on 2009-10-03
Just a thought, but why not increment the counter **after** you have selected the random number.  This would allow you to "throw away" random numbers that do not meet the criteria.

So the plan of attack would be something like:

```

Get choice and passwordLength from the user
initialise password to ""
initialise counter to 0
while(counter < passwordLength)
    select randNum from the total permitted range
    if choice is 1
        if randNum satisfies  the right conditions
            append the character to the string
            increment counter
        endif
    endif
    if choice is 2
        // etc with a different condition being checked
    endif
    // etc for all the choices
endwhile

```

There might be something better than a whole lot of if statements like this, and it might be possible to remove the counter variable altogether (isn't it just the current length of the password?).  But something like this seems easier than trying to pick a random number subject to various constraints.  It seems to the user that you are doing this, but what you really do is pick lots of random numbers until you get enough that "fit".

---

### Post by dwhitney67 on 2009-10-03
> **nathang1392 said:**
> ```
 ...
alright, i have gotten this figured out up until here(the place with an arrow.) i know this is incorrect, but i have it there to show you what i am trying to do. how can i make this pick between two ranges?

I will try to answer the question above, and the one posted previous to this one.

Wrt to the earlier question, 'NormValue' is the normalized value, which for example, is the value returned by Math.random().

Now for your second question (ie the one above), what you need to do is obtain a normalized value from the range of 0 to 127.  If you want to be more selective, you can actually trim that range a wee bit, based on the plausible ASCII values that will meet your app's requirements.

Once again, referring to the ASCII table ('man ascii'), the first character you probably care about is the exclamation point ('!'), and the last is the tilde ('~').  Thus, you can limit the characters to those in the range of 0x21 (33) through 0x7E (126).  So those are your min and max values.

So, a random ASCII value can be yielded with:
[code]
char ascii = (char)(Math.random() * 0x7E) + 0x21;

```
If you prefer to place the decimal equivalents of the hex numbers in the formula above, then go for it.

Anyhow, now that you have an ASCII value, see if it meets your password's criteria.  Is the value that of an ASCII numeral?  Is it an ASCII uppercase or lowercase letter?  Perhaps a symbol (ie ~!@#$%^&*()-_+=<>?/\[]{})??

---

### Post by nathang1392 on 2009-10-03
what im saying though is that lowercase is 97 - 122, uppercase is 65 - 90. and i am not supposed to use 0 - 47 or 91 - 36.so if i wanted to say random number needs to be between 65 and 90 or between 97 and 122, how would i say that in code?

---

### Post by nathang1392 on 2009-10-03
i dont see any possible way that i can grab both ranges, since upper and lower are separated by 6 characters on the table.

---

### Post by nathang1392 on 2009-10-03
i have googled every thing i can think of, does anyone know if it is even possible to do this. i mean i think it is the only way i can do what i am trying to do without tripping my code apart, and i have worked too hard on it to do all that. if anyone knows a way i can make that happen please shed some light.

---

### Post by dwhitney67 on 2009-10-03
> **nathang1392 said:**
> what im saying though is that lowercase is 97 - 122, uppercase is 65 - 90. and i am not supposed to use 0 - 47 or 91 - 36.so if i wanted to say random number needs to be between 65 and 90 or between 97 and 122, how would i say that in code?

](*,)

Just grab one random character value.... then do the filtering.

```

String password = "";

while (password.size() < passwordLength)
{
   char ch = (char)(Math.random() * 0x7E) + 0x21;

   if ((ch >= 0x21 && ch <= 0x2F) ||
       (ch >= 0x3A && ch <= 0x40) ||
       (ch >= 0x5B && ch <= 0x60) ||
       (ch >= 0x7B && ch <= 0x7E))
   {
      // special character
   }
   else if (ch >= 0x30 && ch <= 0x39)
   {
      // number
   }
   else if (ch >= 0x41 && ch <= 0x5A)
   {
      // uppercase letter
   }
   else if (ch >= 0x61 && ch <= 0x7A)
   {
      // lowercase letter
   }
   else
   {
      // don't care... ignore character
   }
}

```
Of course, this is not exactly what you need, but hopefully this time it makes sense.  You get **one** character, then check its value type.

The use of the Character class makes the task much easier.

---

### Post by nathang1392 on 2009-10-03
> **dwhitney67 said:**
> ](*,)

Just grab one random character value.... then do the filtering.

```

String password = "";

while (password.size() < passwordLength)
{
   char ch = (char)(Math.random() * 0x7E) + 0x21;

   if ((ch >= 0x21 && ch <= 0x2F) ||
       (ch >= 0x3A && ch <= 0x40) ||
       (ch >= 0x5B && ch <= 0x60) ||
       (ch >= 0x7B && ch <= 0x7E))
   {
      // special character
   }
   else if (ch >= 0x30 && ch <= 0x39)
   {
      // number
   }
   else if (ch >= 0x41 && ch <= 0x5A)
   {
      // uppercase letter
   }
   else if (ch >= 0x61 && ch <= 0x7A)
   {
      // lowercase letter
   }
   else
   {
      // don't care... ignore character
   }
}

```
Of course, this is not exactly what you need, but hopefully this time it makes sense.  You get **one** character, then check the what value it is.

The use of the Character class makes the task much easier.

my problem is that i have hardly went over the very basic stuff in my class, so translating that into my code and it working is like a .000000000000002% chance. but as far as the concept of what you are saying, do you mean like to say 65 - 122, but not 91 92 93 94 95 96?

---

### Post by dwhitney67 on 2009-10-03
A password is built from individual characters, each of which can be considered a discrete value.  In other words, a value cannot be two different things at the same time.

If you are fishing through a grocery sack that has various fruits in it, and all you care about are eating the apples & oranges, obviously if you pull out a Durian, you will toss it away.

It is the same with the characters of the ASCII table; you want to consider some of them for your password, and the others you will toss out (ignore).

So if the user wants a 8-character password consisting of lowercase letters only, and your random generator produces a numeral character, you toss it, and then try again by getting another random character.  You repeat this over and over again until you succeed in forming the 8 character password.

I do not know how else to explain this.  It is so trivial; perhaps you should take a break, and then look at this exercise tomorrow.

---

### Post by nathang1392 on 2009-10-03
lol i understand what you are saying precisely, its simply i dont think i have ample skills to implement it into code.

---

### Post by NovaAesa on 2009-10-03
> **nathang1392 said:**
> lol i understand what you are saying precisely, its simply i dont think i have ample skills to implement it into code.

Here's a bit more of a direct hint. You want to keep generating random numbers until you find one that is in the appropriate range. For this, a *do* loop is what you are looking for. 
```

do {
    ...
} while (condition)

```The condition should be true if the random number is in the correct range, and the inside of the loop should be what is generating the random number.

---

### Post by nathang1392 on 2009-10-04
alright, so is this what you are saying? im sorry, im just very very confused on this assignment, it turned out to be alot harder than it looked.
```
 else if (choice == 2)
            {
               do
               {
              randNum = (int) Math.random();   
              char letter = (char) randNum;
              password += letter;
            }
            while (randNum ! = lowerCase) || (randNum !=upperCase);
                
            }
```

---

### Post by dwhitney67 on 2009-10-04
> **nathang1392 said:**
> alright, so is this what you are saying? im sorry, im just very very confused on this assignment, it turned out to be alot harder than it looked.
```
 else if (choice == 2)
            {
               do
               {
              randNum = (int) Math.random();   
              char letter = (char) randNum;
              password += letter;
            }
            while (randNum ! = lowerCase) || (randNum !=upperCase);
                
            }
```

Do not assign the letter to the password until you find it to be the desirable type.

Remember, Math.random() returns a value ranging from 0.0 to less than 1.0.  Thus you need to convert this normalized value to the range of numbers used to identify ASCII characters.  For the sake of this project, your range is from 33 to 126 (or 122 if your instructor said so).

Lastly, the variables 'lowerCase' and 'upperCase' cannot be used to compare against the random ASCII number acquired.  You need to compare against the actual numbers that identify the ASCII characters!

```

String password = "";

...

else if (choice == 2)
{
   while (password.length() < passwordLength)
   {
      int ch = 0;

      do
      {
         ch = (int) (Math.random() * (126 - 33 + 1)) + 33;

      } while ( !( (ch >= 65 && ch <= 90) || (ch >= 97 && ch <= 122) ));
//                    lowercase range           uppercase range

      passwd += (char) ch;
   }
}

...

System.out.println("Password: " + password);

```
A little explanation concerning the usage of Math.random() above.  The range of ASCII characters I am interested in are identified with numbers ranging from 33 to 126.  Thus I need to normalized the random number to 94 possible values (126 - 33 + 1).  In essence, I want my random number to range from [0, 93], which are 94 possible values.

So if random() returns a 0.0, and I multiply by (126 - 33 + 1), the result is 0; then I add it to 33 to yield a 33... which represents the lowest ordered ASCII character I care about.

If random() returns a 0.99999, and I multiply by (126 - 33 + 1), the result is 93.99906, which after casting to an int, becomes 93.  Adding 33 to 93 yields 126... which represents the highest ordered ASCII character I care about.

P.S.  When acting on your other 'choice' values, you need to augment (or simplify, as in the case of choice == 1) the do-while loop conditional statement to the range of data that is acceptable for the password.

---

### Post by nathang1392 on 2009-10-04
alright, but >  while ( !( (ch >= 65 && ch <= 90) || (ch >= 97 && ch <= 122) ));
 will only work for two ranges right?
or does this work also?
>  while ( !( (ch >= 65 && ch <= 90) || (ch >= 97 && ch <= 122) || (ch >= 48 && ch <= 58) )); 

---

### Post by nathang1392 on 2009-10-04
alright, i have gotten everything working. thank you for all of your help. its is very appreciated.

---


---
title: "Java phonebook help"
date: 2010-08-25
forum: Programming Talk
---

### Post by liquidfunk on 2010-08-25
So I'm in the process of making a phonebook application and I'm looking for some guidance. 

So far this application takes the input .txt file and prints out the first 3 lines. 

It then asks the user to input some information, and then allows the user to search for a term inside that entertered information. 

What I want the code to do is to read in the .txt file, and ask the user what they want to search for, then reply with the line that the information is on, as well as the rest of the information. 

E.g. "Enter the search term" - 'Ubuntu'

'Ubuntu' was found on line 22 and the phone number is 0123456789

Any suggestions?

(Code is below)


```
import java.util.Scanner;
import java.io.File;
import java.io.IOException; 
import java.io.BufferedWriter;
import java.io.BufferedReader;
import java.io.FileReader;  
import java.io.InputStreamReader;
import java.util.regex.Matcher;
import java.util.regex.Pattern;



     class blondie    
    {        
        public static void main(String args[])
    
       throws IOException           
    { 
           Scanner FileInput = new Scanner(new File("/Users/Josh/Dropbox/Jubilee Healthcare/Java app/Code/phone.txt"));      
         
                System.out.println("");
                System.out.print("Name:               ");           
                System.out.println(FileInput.nextLine());           

                System.out.print("Telephone Number:   ");
                System.out.println(FileInput.nextLine());
                System.out.print("Address:             ");
                System.out.print(FileInput.nextLine());
                System.out.println("");
                System.out.println("");   
        
              BufferedReader FileOutput = new BufferedReader(new InputStreamReader(System.in));
              System.out.println("Enter information: ");
                
            try
    {             
                String text = FileOutput.readLine();
                System.out.println("Enter the word to search for: ");
                String word = FileOutput.readLine();
                String[] TextSplit = text.split(" ");
                
                
 
            for(String str:TextSplit)
    {
                 if(str.equalsIgnoreCase(word))
                System.out.println(word + " can be found here - " + text);
                 
                 else
                 
                 System.out.println("Sorry I can't find that, mind trying again?");
                 
 
    }
 
    }
            catch(IOException e)
    {
            e.printStackTrace();
   
    }
    
  }
         
}   
    
    
  
```

---

### Post by PaulM1985 on 2010-08-25
How about considering classes for this?

Maybe you could have a phone book class called PhoneBook, which contained an ArrayList of Contact classes.

You could create your PhoneBook when you start the application by passing the name of the txt file into the constructor:

myPhoneBook = new PhoneBook("mytxtfile.txt");

The constructor could then read this text file and create a number of Contact classes which are then added to an arraylist.  (Try to use something like an arraylist rather than just using an array).

Your PhoneBook class could have a method called lookup(String value) which when called looked up the Contact class in the list which had appropriate values.

Paul

---


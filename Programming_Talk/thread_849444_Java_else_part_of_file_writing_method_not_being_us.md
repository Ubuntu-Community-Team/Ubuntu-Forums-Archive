---
title: "Java: else part of file writing method not being used, so old data is overwritten."
date: 2008-07-04
forum: Programming Talk
---

### Post by Joe88 on 2008-07-04
I'm not a complete Java beginner since I've been learning it in the first year of my university computer science course which I've now finished (though the emphasis of my course this year was on learning about general computer science rather than programming). 

For practice, I've been building a multiple choice testing program which is now 80% works. As the name would suggest, this program makes tests and questions, which it can then run - returning the users results afterwards.

The thing I'm stuck on is writing information about questions to save files, so they can be reused - the writing and loading of individual questions I can do, the problem is I cannot save more than one question because the print writer is overwriting the previously written information.

This is despite the use of a method check to see if the file is empty or not - if its not empty, the previous contents should be read and saved to an array list, so that they can be rewritten to the file along with the new information.

You can see from the code below that the problematic code is for general reading and writing of file data.

```

import java.util.*;
import java.io.*;

/**
 * This class deals with the accessing and modification of save files
 * @version 3/7/08 - 12.48am
 */

public class FileManager
{  
    /**
    * This method creates files, if they are not already made
    */
    public static void make(File input)
    {
        try
        {
            input.createNewFile();
        }

        catch(IOException e)
        {
            
        }
    }

    /**
    * This method writes the contents of an arraylist to an inputted    file- if the file is not empty the previous contents
    * is loaded and re-written then the new data is written afterwards. If deletion will take place the boolean parameter 
    * has to be true.
    */
    public static void save(File writeTo,ArrayList<String> input,boolean deletion)
    {       
        // NOTE : printing of file empty / not added for tester.  
        try
        {
            FileWriter fw = new FileWriter(writeTo);
            BufferedWriter bw = new BufferedWriter(fw);
            PrintWriter out = new PrintWriter(bw);
            
            File theFile = writeTo; 
            
            ArrayList<String> previous = load(theFile);
            
            if(fileIsEmpty(theFile) == true)
            {        
                out.println("file is Empty" );
                out.println("[start]");
                out.flush();
                            
                for(String line : input)
                {
                    out.println(line);
                    out.flush();
                }
                                           
                out.println("[finish]");
                out.flush();
            }

            else
            {
                //Write previous data  then right new inputted data
                for(String line : previous)
                {
                    out.println("file is not Empty" );
                    out.println(line);
                    out.flush();
                }

                for(String line : input)
                {
                    out.println(line);
                    out.flush();
                }
            }            
            
            out.close();
        }

        catch(IOException e)
        {
            
        }   
    }
   
    /**
     * This checks if a file is emptyor not
     */
    public static Boolean fileIsEmpty(File toCheck)
    {      
        try
        {
            Scanner reader = new Scanner(toCheck);
            
            if(reader.hasNext() == true )
            {
                return false;
            }
            
            else
            {
                return true;    
            }
        }
        
        catch(IOException e)
        {
            return true;    
        }
    }
    
    /**
    * This method reads the contents of the inputted file and puts each line in a string 
    * arraylist - then returns the arraylist
    */
    public static ArrayList<String> load(File readFrom)
    {
        try
        {
            Scanner reader = new Scanner(readFrom); 
            ArrayList<String> readLines = new ArrayList<String>();

            while(reader.hasNextLine() )
            {
                readLines.add(reader.nextLine() );
            }
            
            return readLines;
        }

        catch(IOException e)
        {
            return null;
        }   
    }
    
    public static void delete(File input)
    {
            input.delete();    
    }
}
```

I've also written a tester class to help work out the problem:

```

import java.io.File;
import java.util.*;
/**
 * Write a description of class Tester here.
 * 
 * @version 3/7/08 12.00am
 */
public class Tester
{
    private static File testSaves = new File("testSaves.txt");

    public Tester()
    {
        FileManager.make(testSaves);    
    }    
    
    public static void test()
    {
        System.out.println('\f');
        System.out.println("**************** File Manager test ****************");  
        System.out.println("");
        System.out.println("This tests the save method.");
        System.out.println("");
        System.out.println("2 arrayLists containing a list of names will be added to test");
        System.out.println("saves.txt, each should have 5 names in seperated by [start] and");
        System.out.println("finish.");
        
        ArrayList<String> names1 = new ArrayList<String>();
        names1.add("Joe");
        names1.add("Alan");
        names1.add("Mike");
        names1.add("Richard");
        names1.add("John");
        
        ArrayList<String> names2 = new ArrayList<String>();
        names2.add("Jimmy");
        names2.add("Alison");
        names2.add("Sarah");
        names2.add("Jeremy");
        names2.add("Stephen");
        System.out.println("");
        System.out.println("");
        
        System.out.println(" ");
        System.out.println("File is empty before array1 added ?: " + FileManager.fileIsEmpty(testSaves) );
        
        FileManager.save(testSaves,names1,false);
   
        System.out.println(" ");
        System.out.println("File is empty afterwards?: " + FileManager.fileIsEmpty(testSaves) );
        
        System.out.println("Loaded contents after array 1 saved:");
        ArrayList<String> contents1 = FileManager.load(testSaves);
        
        for(String current : contents1)
        {
            System.out.println(current);    
        }
        
        System.out.println("");
        FileManager.save(testSaves,names2,false);
        System.out.println("Loaded contents after array 2 saved:");
        ArrayList<String> contents2 = FileManager.load(testSaves);
        
        for(String current : contents2)
        {
            System.out.println(current);    
        }
        
        System.out.println("");
        System.out.println("The array lists have now been added using the .save method.");
        System.out.println("Enter a letter and then press return to delete the file:");
        
        Scanner respond = new Scanner(System.in);
        System.out.print("< ");
        String response = respond.next();
        
        if(response.equals("") || !response.equals("") )
        {
            FileManager.delete(testSaves);
            System.exit(0);
        }
    }
}

```

From the results of the tester, I think the source of problem must be the ELSE part of the IF statement code not being used but I don't know why this is happening - the tester shows that the fileIsEmpty method returns the correct results. 

For tester results see the attached tester.gif.

Please help if you can.

---

### Post by geirha on 2008-07-04
```
            FileWriter fw = new FileWriter(writeTo);
```
My java is a bit rusty, but I believe that is the line that truncates your file. 
Try with this constructor instead: [http://java.sun.com/j2se/1.5.0/docs/api/java/io/FileWriter.html#FileWriter(java.io.File, boolean)](http://java.sun.com/j2se/1.5.0/docs/api/java/io/FileWriter.html#FileWriter(java.io.File, boolean))
Setting the boolean argument to true should leave the content alone, and start writing at the end of the file.

---

### Post by Joe88 on 2008-07-04
:oops: Guess I should have read the constructor information a little more closely.

**Thanks for the help.**

---


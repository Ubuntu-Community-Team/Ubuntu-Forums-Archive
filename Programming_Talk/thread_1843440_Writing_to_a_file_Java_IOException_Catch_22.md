---
title: "Writing to a file Java IOException Catch 22"
date: 2011-09-13
forum: Programming Talk
---

### Post by joep353 on 2011-09-13
I am trying to get my Java program to write to a file. I have declared a variable  
"PrintWriter fileWriter = new PrintWriter (new BufferedWriter (new FileWriter ("adOutput.txt")));"

Then later on I use the print method "fileWriter.print(name);"

When I compile this I get the warning "unreported exception java.io.IOException; must be caught or declared to be thrown."  So I then wrapped my "fileWriter.print" command in a try/catch block. However, when I compiled it again, I got the error "exception java.io.IOException is never thrown in body of corresponding try statement." So, I find myself in a catch 22. Here is my code without the try/catch block:

```
public class AD 
{
         
    public String setAd (String filename, String month, String week, String folder)   
    {
        
            PrintWriter fileWriter = new PrintWriter (new BufferedWriter (new FileWriter ("adOutput.txt")));
            Scanner in = ResourceUtil.openFileScanner(filename);
       
       try
        {
            
                           if (in == null) {
                               System.out.println("File not found: " + filename);
                               return null;
                           }
                           else{
                               System.out.println("File Read Successfully.");
                            }//en if else to test for good file name.
                       
                         while (in.hasNext()){
                           String name=in.nextLine();
                           String link;                           
                           folder=folder.replaceAll(" ","%20");                                                    
                           link="=HYPERLINK(\"Competitor%20Ads/"+folder+"/"+name+"\",\""+name+"\")";
                           name+="_" + month + "_" + week+"_";
                           name=name.replaceAll("_",";");
                           name+=link;
                           System.out.println(name);    
                           fileWriter.print(name);
                           } // end While reading in names & write to file.
                                                
                        System.out.println ("DONE");
                    } // try
                    
            
       finally
       {
       // fileWriter.close();
       System.out.print("Finally");
       } // finally      
            
            
       return "Thank you for using JoPo Software";
    }
```

Any help would be greatly appreciated.

---

### Post by PaulM1985 on 2011-09-13
You are declaring a new FileWriter.  This is what throws an IOException.  You want a try catch round this.  Make sure you check the line number when the error messages are output by the compiler, it would help you track the error down to this line.

Paul

---

### Post by joep353 on 2011-09-13
Paul,

Thank you so much for your response. I thought I had tried that before, but for some reason it didn't work then. It works now.  Thanks a bunch!

---


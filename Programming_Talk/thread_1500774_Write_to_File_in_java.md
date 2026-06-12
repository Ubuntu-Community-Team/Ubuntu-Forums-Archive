---
title: "Write to File in java"
date: 2010-06-03
forum: Programming Talk
---

### Post by Gondee on 2010-06-03
I'm just starting out programing, and i have come across a problem with writing to a file. I lack the back ground knowledge to know why it inst working, as far as I'm concerned it all compiled fine. =(
```

public void MakeClientPage() //creating the initial page for the client
{   //Begin the write
    try{

        System.out.println("Write to file....");
        BufferedWriter Write = new BufferedWriter(new FileWriter(Name + ".html",true));
        
       Write.write("<HTML><title> " + Name + "</title><BODY>"); //writes header
       Write.write("<BR><BR><CENTER><LARGE>Client: " + Name + "<CENTER><LARGE>");
       Write.write("<BR><BR> ");
       Write.write("<B></I>Client Personal Info</B></I><BR>");
       Write.write("<table>");
       Write.write("    <TR>   ");
       Write.write("    <TD>Entry Date</TD><TD> Work in Progress</TD>   ");
       Write.write("    </TR>");
       Write.write("    <TR>   ");
       Write.write("    <TD><b>Client Name  </b></TD><TD> " + Name + "</TD>   ");
       Write.write("    </TR>");
       
       
       
       
       Write.write("</BODY></HTML>");
        
        
        
        
        
        
        
        
    }catch(IOException e)
            {
                System.out.println("There was an Error Writing the file");
        
            }//End of catch


}//End of MakeClientPage

```

Name is declared else where. The program creates the file with the right name, but doesn't write a single thing to it. Any help would be appreciated.

---

### Post by piousp on 2010-06-03
Flush it?
Call **Write.flush();** after you are done writing.

Then close the resource you opened
Write.close();

---

### Post by Gondee on 2010-06-03
I tried Flushing it right before i wrote it, and it didnt seem to have an effect. 
I got the example code from 
[http://www.exampledepot.com/egs/java.io/WriteToFile.html](http://www.exampledepot.com/egs/java.io/WriteToFile.html)

Is that even current java syntax?

---

### Post by Gondee on 2010-06-03
I guess i had to Write.Close(); inorder for it to actully write to the file. 

Thats really odd, but i guess thats how its done =)

---

### Post by piousp on 2010-06-03
Well yeah, you have to call close() for various reasons.
Just, you have to call flush AFTER you write, not before.

I just read the .close() javadoc, and it call flush() just before closing the stream.

Glad it worked out

---

### Post by Gondee on 2010-06-03
Thanks for the quick responce and help. =)

---

### Post by piousp on 2010-06-03
No problem, your welcome :)

---

### Post by true_friend on 2010-06-06
C# has some static methods for quick writing to a file like File.WriteAllText(), File.AppendallText(). But when write thorugh a StreamWriter same as in Jave, it should be closed afterwards otherwise no writing. I prefer static methods for my quick text processing tasks.

---


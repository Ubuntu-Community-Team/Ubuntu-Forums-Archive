---
title: "Java problem"
date: 2010-02-11
forum: Programming Talk
---

### Post by vik_2010 on 2010-02-11
Sorry for bringing up an old thread. But if anyone could help me with this, I'd appreciate it.

I'm trying to write a simple java program that uses I/O streams, taking input from one file and outputting it into another. I'm taking input from the windowspager.ini file (courtesy Jochen Baier, creator of the program) and outputting it to a file on my desktop.

[PHP]
import java.io.*;
public class firstClass {
    public static void main(String[] args) throws IOException {
        System.out.println("Hello world");
        System.out.println("We are going to create a txt file");
        BufferedReader bi = new BufferedReader(new FileReader("C:\\Users\\Vikram\\Desktop\\windowspager-0.90\\windowspager-0.90\\windowspager64bit\\Windowspager.ini"));
        BufferedWriter out = new BufferedWriter(new FileWriter("C:\\Users\\Vikram\\Desktop\\out.txt"));
        
        while (bi.readLine() != null) {
            String line = bi.readLine();      
            out.write(line);
            out.write("\r\n");
            System.out.println("Writing...");
    
        }
        System.out.println("Done");
        bi.close();
        out.close();
    }
}
[/PHP]The problem is that the file created only has every OTHER line in the original. I'm not sure if it has something to do with the carriage return+line feed combo, since I'm not used to it as I usually work on Ubu.

If anyone could just point out what's going on,  I would appreciate it.

---

### Post by cariboo on 2010-02-12
A new thread is better than tacking your post on to an old thread.

---

### Post by LKjell on 2010-02-12
For input check Scanner class. Output you can check out PrintWriter.

```
PrintWriter file = null;
String lines[] = ...
try {
	file = new PrintWriter(new FileWriter(filename));
	for(String line : lines) {
		file.println(line);
	}

} catch (Exception e) {
	System.out.println("Got some error when trying to write to file");
} finally {
	if (file != null) {
		file.close();
		System.out.println("Finish writing to file");
	}
}


```

---

### Post by stumbleUpon on 2010-02-12
The problem is here
[PHP]
        while (bi.readLine() != null) {
            String line = bi.readLine();      
            out.write(line);
            out.write("\r\n");
            System.out.println("Writing...");
    
        }
[/PHP]

You have already read in the first line when you do bi.readLine() to check if u have reached the end of the file. You then again read in another line and write it out. Obviously you will only read every other line. The code segment below works.

[PHP]
      String line = bi.readLine();
      while (line != null) {
            out.write(line);
            out.write("\r\n");
            System.out.println("Writing...");
            line = bi.readLine(); 
      }
[/PHP]

---

### Post by vik_2010 on 2010-02-12
Thanks for the help, stumble. 

LKJell brought up a point that has been at the back of my mind for a while:

what's the difference between the functionalities offered by the Scanner and FileWriter classes?

The only difference seems to me to be that the scanner class offers the ability to parse input based upon a specific character.

-V

---


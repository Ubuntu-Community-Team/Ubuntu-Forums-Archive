---
title: "Java Text Reader Problem"
date: 2008-11-09
forum: Programming Talk
---

### Post by Sugz on 2008-11-09
Alright, so im in the middle of creating a text editor, using a buffered reader and a File input stream. 
The code itself has been tried and tested in command line, but i have made the transition to a GUI testing
both AWT and Swing TextArea components. 

While using the same method's and code as before, the code runs perfectly fine.
When debugging, the variables and Objects show the right values, however, 

Nothing is displayed in the TextArea's nothing, .. Zip.. 
Despite the code and debugger telling me that its working correctly. I Am totally and utterlly clueless. :confused:

Anyway, without any further delay. please Find attached the Coding of the Output class and the GUI class.

This has honestly got me stumped so please any help i will be very grateful for

---

### Post by cl333r on 2008-11-09
Please post the whole NetBeans project. I can't find a class "FileStore" to test your app.
Right-click the name of the project (to the left, in the "projects" area), choose "copy.." and choose say the desktop. Then archive the folder (say into a .zip file) and attach it.

---

### Post by Sugz on 2008-11-09
inCorrect post

---

### Post by drubin on 2008-11-09
> **Sugz said:**
> Ok mate, check your PM

Firstly you should know by now the cons of posting support issues as PM's.

---

### Post by drubin on 2008-11-09
> **Sugz said:**
> Alright, so im in the middle of creating a text editor, using a buffered reader and a File input stream. 
The code itself has been tried and tested in command line, but i have made the transition to a GUI testing
both AWT and Swing TextArea components. 


Mixing AWT and SWING should be avoided.  See these articles for reasons
[http://java.sun.com/products/jfc/tsc/articles/mixing/](http://java.sun.com/products/jfc/tsc/articles/mixing/)
[http://www.devx.com/tips/Tip/14718](http://www.devx.com/tips/Tip/14718)

---

### Post by cl333r on 2008-11-09
I don't have any messages. But you can also append it to your reply: below the reply text area is a button "Go advanced" which takes you to another screen where you'll find "Manage attachments". But if that's something that needn't be shared in public I understand so private is also ok. Drubin is right, it _could_ be a matter of mixing swing and awt (but could also be not).

---

### Post by Sugz on 2008-11-09
no, no i only did that as a method of testing other TextArea
The problem described above is present for Both Text areas... Oh and the I decided to keep it open on here without PM'ing.
For various reasons, i am reluctant on posting the complete project. 

Here is a list of what does what.

FileObj - Creates a File object (with File object, dir and name)
File Store - creates an array of FileObj's
Log - Just a Log

im sorry i cant be more specific at the moment in time

In response to Drubin's recent forum thread. I have completed the entire program, and gone to great lengths to try and debug it. however this is really something that i am unable to solve, i dont ask for copy/pasting code, but i dont think this is a matter of simply adding more code.

---

### Post by drubin on 2008-11-09
> **Sugz said:**
> 
In response to Drubin's recent forum thread. I have completed the entire program, and gone to great lengths to try and debug it. however this is really something that i am unable to solve, i dont ask for copy/pasting code, but i dont think this is a matter of simply adding more code.
Hehe Yes I can see you aren't after that. But that thread was aimed at people answering the questions not people asking them :)

Did converting them to all swing components not work? If not post that code (use code tags and not attachments this way searches will show them up for people having similar issues) and I will relook at at further for you.

---

### Post by Sugz on 2008-11-09
Will do fella. 
No problem, i just thought i should make that explicit. 
Anyway.. 
All the components i use are Swing, i use 1 AWT component (i just put that in quickly for testing purposes) but neither display text, THey dont even display anything when i parse simple "BLAH BLAH BLAH" strings to them (As shown in the Output class above) i would normally parse LineIn to each TextArea (LineIn is just A String Line in the TxtFile, Think of it as a pointer to a line of text inside a txt file)

---

### Post by drubin on 2008-11-09
> **Sugz said:**
> 
All the components i use are Swing, i use 1 AWT component 
By definition ALL -1 does not equal ALL :)
try remove the AWT component. Also just so you know swing is not thread safe you might want to take a look at [SwingUtilities.invokeLater]("http://java.sun.com/j2se/1.4.2/docs/api/javax/swing/SwingUtilities.html#invokeLater(java.lang.Runnable)")

---

### Post by cl333r on 2008-11-09
I checked the code, this time it wasn't because of using AWT, the author has received a PM with the solution.

---

### Post by drubin on 2008-11-10
> **cl333r said:**
> I checked the code, this time it wasn't because of using AWT, the author has received a PM with the solution.

Great so now the search engines will show this thread when searching for [Java Text Reader]("http://www.google.co.za/search?q=Java+Text+Reader+problem&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")first hit!

These forums general do not support, "Support Queries" as PM's. I my self would also like to know the solution. If the answer is personal and appropriate for public viewing please do not post the issue publicly. 
Thanks

---

### Post by Sugz on 2008-11-10
In the spirit of Linux and open sourcyness :) 
i will post up what was changed. 
But all kudos should go to cl33r and drubin as they were the ones who helped me. But i really appreciate everyone's help on this. As promised, i will examine the new code (After breakfast :) ) and post up how it was fixed. 

Again to all, Many thanks

---

### Post by Sugz on 2008-11-10
Ok as promised, here is what helped me.

Basically before, I had a component on my GUI form lets call it containerX
Which is of type TextArea. 
This will contain the Text from the file that i have read. 

To read the File itself, i used a component JFileChooser which brings up a GUI interface to select the file. 
From the JFileChooser, i then store the selected File in a File Object of my own lets call it. FileX of type File. 
From the stores FileX i wanted to output this into the JFileChooser. THis requires two methods. 
THe first is the BufferedReader and FileReader. 
The File FileX is parsed to the FileReader --> which is parsed to the BufferedReader (lets call this BuFF. 
The Buffered reader would then output each line of text (type String) to ContainerX via a while Loop

(While inpString != null)
  {
    ContainerX.append(inpString);
    inpString = BuFF.readline();
  }

The problem occured here. 

My method included Keeping the Output of the file in a separate class to that of the GUI.

Lets call the Output Class FileOut

This class was created by Extending the GUI class.

This therefore Allowed me to use ContainerX and its associated methods in the FileOut  Class.

This was identified as insufficient. 

The FileOut method Inside the FileOut class needed to be parsed the actual ContainerX Object.

This is done by doing the following

Before: public void FileOut(File fileIn)
: This is the method declaration of FileOut which accepts FileIn as a parameter.

After: public void Output(File FileIn, javax.swing.JTextArea ta)
: This is the modified version, which accepts the GUI component JTextArea (ContainerX) as a parameter

The method therefore looks like this

```


         public void Output(File FileIn, javax.swing.JTextArea ContainerX)
         
         String FileDir = FileIn.getDir;     
         FileInputStream read = new FileInputStream(FileDir);
         BufferedReader buFF = new BufferedReader(new InputStreamReader(read));
         String InpString = buFF.readLine();

         while (InpString !=null)
            {
             ContainerX.append(InpString + "\n" );
             InpString = buFF.readLine();
            }


```

Tada.. And thanks once again to all those who helped. Mods,please feel free to adjust this post if anything is deemed unsuitable for this forum. 
Cheers!

-Sugz

---

### Post by drubin on 2008-11-10
> **Sugz said:**
> 
Tada.. And thanks once again to all those who helped. Mods,please feel free to adjust this post if anything is deemed unsuitable for this forum. 
Cheers!
I am sure there is nothing wrong with this post.

Sounds great. glad you got it sorted. :)

---


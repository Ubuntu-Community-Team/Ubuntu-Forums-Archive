---
title: "Extremenly Weird and Frustraing problem - Java"
date: 2008-11-05
forum: Programming Talk
---

### Post by Sugz on 2008-11-05
Context:

Im desiging a program as a very primitive Text reader.
Im using the command line to compile and run it because its quicker and more effeciant
The Program Uses FileChooser classes, as well as File objects and Buffered readers.

Now when i use the command line on the .java File everything works without a hitch

IF i then run it in Netbeans IDE, it compiles ok and runs to point where i get the constant error.

"File not found" (A self made exception handler) 

But the exact same Code outside of Netbeans and the Netbeans File Dir runs perfectly. 

I have compared both examples of the .java file and both are identical, just that Netbeans seems to find it difficult to read the stored Files (Or something like that)

Is there any help on how to import the .java file into netbeans without completely breaking it?

i can supply code snippets, but im afraid i cannot offer the entire file

Thanks for your help

---

### Post by Zugzwang on 2008-11-05
Note that by default, if you run a program in Netbeans, then it will be executed in some sub-folder of your Netbeans profile. If you need to read files from the directory where the source is located, change the "Run Directory" in the project accordingly!

---

### Post by Sugz on 2008-11-06
thanks for the input, 
No the files that i read are defnined by the user using a file chooser. so the files that are to be read could be from any directory.

---

### Post by Zugzwang on 2008-11-06
In that case it's hard to tell where the problem is without knowing details.

A general advice: Modify your custom exception class to also store the name/URL of the file that was accessed. This way you can see if the file name was somehow messed up.

Oh, and try starting netbeans from the console! You might be using a different JRE if you start it from the GNOME/KDE menu.

---

### Post by Sugz on 2008-11-06
thanks again.. i have tried the suggested and here are my results.

In the fully working example, the file name is identical to the file name of the Non-working example
Also i cannot run Netbeans through the terminal without running the startup script for netbeans as i am running 6.1

im now trying a few more solutions.

Ahha its working.. 

How i did it..

Basically, the FileBuffer was reading only the file name of the stored file object. This is not a problem, if the file you are trying to read is in the same dir as the java class file. But because mine isnt, i needed to use a different file method.

Instead of using the file.getName() method which only returns the name of the file eg. File1.txt
Use file.getPath() methof. This returns the entire path of the file in questions eg. /home/me/Desktop/File1.txt

Thank you very much for your help.. i believe a thanks is in order  ;)

---


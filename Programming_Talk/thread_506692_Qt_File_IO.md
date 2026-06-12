---
title: "Qt File I/O"
date: 2007-07-22
forum: Programming Talk
---

### Post by mgoblue on 2007-07-22
I need some help doing file I/O in Qt.  What I'm trying to do right now is read in a list of names and store it in a vector.  The copied piece of code is supposed to get the "length" of the data file, but it doesn't work (it just gives me a value of 1).  If you can I'd appreciate any help or pointers :)

```

int getFileSize(void)
{
   

  /***********************/    
   int cntr=0;
   QString line;
   QFile inputFile("test.txt");
   QTextStream in(&inputFile);
   /************************/


   /****************************/
   if (!inputFile.open(QIODevice::ReadOnly | QIODevice::Text))
   {
       //Open Error Box Here //
    
       return(56);  //just used to test 
   }


   /*****Determine Size*****/
   while(!inputFile.atEnd())
   {
       QByteArray line = inputFile.readLine();
       cntr ++;
   }
   return cntr;
}




```

---

### Post by the_unforgiven on 2007-07-22
> **mgoblue said:**
> I need some help doing file I/O in Qt.  What I'm trying to do right now is read in a list of names and store it in a vector.  The copied piece of code is supposed to get the "length" of the data file, but it doesn't work (it just gives me a value of 1).  If you can I'd appreciate any help or pointers :)

```

int getFileSize(void)
{
   

  /***********************/    
   int cntr=0;
   QString line;
   QFile inputFile("test.txt");
   QTextStream in(&inputFile);
   /************************/


   /****************************/
   if (!inputFile.open(QIODevice::ReadOnly | QIODevice::Text))
   {
       //Open Error Box Here //
    
       return(56);  //just used to test 
   }


   /*****Determine Size*****/
   while(!inputFile.atEnd())
   {
       QByteArray line = inputFile.readLine();
       cntr ++;
   }
   return cntr;
}




```
You could simply use [URL="http://doc.trolltech.com/4.3/qfile.html#size"]QFile::size()
[/URL] or [QFileInfo::size()]("http://doc.trolltech.com/4.3/qfileinfo.html#size") to get the file size.

---

### Post by mgoblue on 2007-07-22
> **the_unforgiven said:**
> You could simply use [URL="http://doc.trolltech.com/4.3/qfile.html#size"]QFile::size()
[/URL] or [QFileInfo::size()]("http://doc.trolltech.com/4.3/qfileinfo.html#size") to get the file size.


Okay thanks :). I'll try that but I still don't understand why what I posted doesn't work :confused:

Also I know in c++ (that's what I'm used to) you need to close the file after reading, do I need to do that here as well?

---

### Post by the_unforgiven on 2007-07-22
> **mgoblue said:**
> Okay thanks :). I'll try that but I still don't understand why what I posted doesn't work :confused:
readLine() is going to read the entire line in one go and the loop will increment the counter - essentially, that's like counting the no. of lines instead of chars/bytes. The fact that cntr returns 1 means you've got only one line in the file?

> **mgoblue said:**
> Also I know in c++ (that's what I'm used to) you need to close the file after reading, do I need to do that here as well?
Not really...
If you have more work (reading from the file, here) to do with the file, there is no need to close it.

---


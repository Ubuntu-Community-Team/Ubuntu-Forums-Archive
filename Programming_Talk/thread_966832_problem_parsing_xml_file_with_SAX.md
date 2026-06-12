---
title: "problem parsing xml file with SAX"
date: 2008-11-01
forum: Programming Talk
---

### Post by badperson on 2008-11-01
Hi,

I'm running a parsing test in my code and getting the following error: 

```
Problem with File I/O, file: /home/jason/Documents/java/work/BenderXMLUtil/BenderXMLUtil/lib/test/parseTest/validate-test.xml, unknown protocol: c
java.net.MalformedURLException: unknown protocol: c
```

here is how I'm creating the file object:

```
File test = new File("lib/test/parseTest/validate-test.xml");
```

I did some googling and saw a few things saying that it may be expecting a url such as
```
File://c:/myfile.xml
```

but when I tried putting that prefix in front of the /home/jason/etc, etc path, it didn't work. 

Is there a proper syntax for the "file://" prefix in ubutntu? 
bp

---

### Post by reality1011 on 2008-11-01
Here are a couple of pointers...

**First,** debug the program by entering system.out.println statements and print out some of the variables like the files name.  I personally use so many debug statements that I actually create a debug method to pass the printed statement in...

for example:
```

 public void debug(String s){
                if(DEBUG)System.out.println(s);
    }

```

```

debug("******************\n" + "ABOUT TO BROADCAST"+ "\n******************");

```


Second, you are not setting your file system separator correctly, you should use something like this:

```
 System.getProperty("file.separator")
```


When you try this I am sure you will see that you are not creating the file object correctly.

---

### Post by pp. on 2008-11-02
This line is a dead giveaway that you specified an URL which is not properly formed:
```
java.net.MalformedURLException: unknown protocol: c
```
It does not only tell you that you gave a poorly formed URL, it also appears to say that your URL begins with "c:", yet the code samples you give later do not confirm this.

```
File://c:/myfile.xml
``` is an URL which is properly made up. It refers to a file which is located in the root directory of a disk partition in Windows.

URLs are not specific to any one operating systems. My suggestion is to look for a document which explains the syntax and use of URLs.

---

### Post by reality1011 on 2008-11-02
PP actually made me realize something  I did not catch at first.  You using URI, why not use this constructor:

```
File(String pathname)
          Creates a new File instance by converting the given pathname string into an abstract pathname.
```

---

### Post by badperson on 2008-11-02
Hi,

thanks for the replies, I think I figured it out, and it doesn't have to do with the url/local filename issue. 

first, File://c:/myfile.xml is not the real filename that I was trying to parse, that is a made up filename showing what a file might be named if it were in windows using the url syntax that was reccomended by some posts I came across on a google search. 


The problem had to do with the doctype tag. I'm using a file from work, so the location of the dtd isn't available on my local machine. I was able to parse the file when I removed the doctype tag and declared all the namespaces in the root element. 
thanks,
bp

---


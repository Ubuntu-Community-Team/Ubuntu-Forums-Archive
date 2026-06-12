---
title: "Good Books to help learn Eclipse SWT with Java"
date: 2009-06-08
forum: Programming Talk
---

### Post by Halcyon31415 on 2009-06-08
I'm just starting at square 1. I would like to learn how to program in Java. I downloaded Eclipse and it is a wonderful IDE (as far as I know it's my first and only) I did the two tutorial projects with the program. I was wondering what is a good step from here? Is there a book that anyone would recommend that I can get from Boarders or something that has little projects and tutorials to get used to what is going on.

Like I said regreatably I'm very new to this and would be concerned that I would get a book that is for Java but doesn't explain how to work with Eclipse or a book on Eclipse that doesn't talk about Java. Maybe I need two books? Or maybe I don't need a book at all but a good website.

Any suggestions would be welcome and thank you for your time. 

Cheers

---

### Post by froggyswamp on 2009-06-08
I don't answer your question but since you're new I thought you might not know that:
Java has 2 built-in GUI libraries: AWT and Swing. Awt was the first one and has been deprecated for good reasons long ago. People were left with Swing but at the time it was painfully slow, because of that, IBM, after doing some in-house testing decided Swing is too slow and started backing up the SWT/Eclipse combo instead.
Fast-forward, nowadays Swing is much faster (especially on windows) and the whole point of using SWT has become moot. Besides SWT is rather buggy and it doesn't extend very well. Also, each time you create a SWT Java app you also have to add those libraries to your program, manage the classpath etc.
Also, by now NetBeans has emerged as the preferred Java IDE (especially for beginners) because it's (much) more user friendly than Eclipse, it also provides a lot of tutorials for Java+NetBeans: [www.netbeans.org]("http://www.netbeans.org")

---

### Post by JordyD on 2009-06-08
How about:

[http://eclipsetutorial.sourceforge.net/totalbeginner.html]("http://eclipsetutorial.sourceforge.net/totalbeginner.html")

I've never used it before, but it looks like what you're asking for.

---

### Post by Halcyon31415 on 2009-06-11
thank you very much I'm trying to get net beans going but for some reason it seems like i need to install some program called JDK which is proving impossible at this time. I have downloaded the file jdk-6u14-linux-i586.bin onto my desktop but when it comes to running the script in the terminal (which unfortunately I have no idea what it means) the terminal tells me it can't find the file. this is the installation instructions i have been trying to follow.

[http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html)

could you please go over these instructions and try them your self to see if they make sense. I changed <version> to be "u14" but other then that I can't understand what is going on.

also no one likes a complainer but why wouldn't the program just come with this file if it is required? I guess I'm just a little frustrated because i can't install it 

thank you for any help!

---

### Post by Ruhe on 2009-06-11
1. Install jdk:
open terminal (Accessories->Terminal). type
```
sudo apt-get install sun-java6-jdk
```
This install Sun java development kit.
After it is installed don't close terminal. Type
```
sudo update-java-alternatives -s java-6-sun
```
This makes sun's java default in your ubuntu. Check this by command
```
java -version
```

2. I think that Netbeans is much better for newbies. So download it and install.
For the first time you'll need Java SE bundle.
[Download it]("http://www.netbeans.org/downloads/index.html"), and put into your home directory. Open terminal and run
```
sudo sh ./*netbeans-6.5-ml-java-linux.sh*
```
*netbeans-6.5-ml-java-linux.sh* - is the name of downloaded file.

Go through the [tutorials on netbeans site]("http://www.netbeans.org/kb/trails/java-se.html").

Good luck.

---

### Post by Halcyon31415 on 2009-06-11
wow thank you very much that was exactly what needed to happen thanks so much now i can try some tutorials I don't understand how typing things into the terminal knows how to download stuff online but that is a mystery for another day. ok i'm off to try some tutorials and examples thx again to everyone!

---

### Post by gorilla on 2009-06-12
So it sounds you're completely new to programming? In this case I would recommend the free eBook [How To Think Like A Computer Scientist, Java Edition]("http://greenteapress.com/thinkapjava/")
Oh, and better ditch Eclipse/ Netbeans for the beginnig, until you got a feel and understanding for the whole process ;)

---

### Post by Halcyon31415 on 2009-06-12
thats a great book! i appreciate you pointing that out to me. Yes it is very true i'm starting right at the beginning. Fortunately I will have a friend who knows how to program help me out but he wont be around for a few months so i want to get started with out him if possible :) I have always really liked computers but never got into programing and figured it was time to stop being scared of it and give it a shot. Thank you for your assistance!

---


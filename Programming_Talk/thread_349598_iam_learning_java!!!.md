---
title: "iam learning java!!!"
date: 2007-01-30
forum: Programming Talk
---

### Post by stealth75711 on 2007-01-30
Hello, I finally figured out through googling how to get a java program to run!!!

I do have a question i figured out how to use the IDE,

How do i run a Java application from the regular linux terminal,

outside of the IDE?

---

### Post by Ramses de Norre on 2007-01-30
Nice :) But have you got auto indentation turned off? And why that strange package statement at the top?

To run it from the terminal: cd to the folder containing the class file and run ```
java Countdown
```
(When not using the IDE at all you'll need to compile it first: javac Countdown.java)

---

### Post by stealth75711 on 2007-01-30
ok thanks how do i turn auto-indention on?

---

### Post by phossal on 2007-01-30
I think he's asking about auto-indentation because your main function is at the same spot as the class declaration. Normally, main() would be tabbed right, and the things inside it would be tabbed right again.

Your package statement is okay, too. Most beginners probably would leave their single class in the default package (which eclipse warns about), but you're doing fine.

---

### Post by stealth75711 on 2007-01-30
keith@Zamis-laptop:~/Desktop$ ls
Countdown.class  Countdown.java  mkdev.sh~  Screenshot.png
keith@Zamis-laptop:~/Desktop$ javac Countdown.java
bash: javac: command not found
keith@Zamis-laptop:~/Desktop$ java Countdown.java
Exception in thread "main" java.lang.NoClassDefFoundError: Countdown/java
keith@Zamis-laptop:~/Desktop$ 


//I got the following errors when i tried to compile from the command line
//How i fix?:confused:

---

### Post by phossal on 2007-01-30
By default, my eclipse tabs things like this:


```
package com.developer.sandbox;

//Compiler set to 6.0

public class Countdown {
	
	/*************************
	 * variables
	 *************************/
	String[] text = {
			"Three...",
			"Two...",
			"One...",
			"Liftoff...",
			"Houston, all systems stable. ",
			"What a view!"
			};
	
	/*************************
	 * constructor(s)
	 *************************/
	public Countdown() {
		for (String line : text) {
			System.out.println(line);
		}
	}
	
	
	/*************************
	 * main
	 *************************/
	public static void main(String args[]) {
		new Countdown();
	}
}
```

---

### Post by phossal on 2007-01-30
You're using an IDE, but you're compiling from the command line? If that's so, there shouldn't be a package declaration. Ramses was correct. Your source would look like this:
```

[COLOR="SeaGreen"]//NO PACKAGE DECLARATION NEEDED FOR A SINGLE CLASS[/COLOR]

[COLOR="SeaGreen"]//Compiler set to 6.0[/COLOR]

[COLOR="DarkRed"]public[/COLOR] class Countdown {
	
[COLOR="Blue"]	/*************************
	 * Variables
	 *************************/[/COLOR]
	String[] text = {
[COLOR="Blue"]			"Three...",
			"Two...",
			"One...",
			"Liftoff...",
			"Houston, all systems stable. ",
			"What a view!"[/COLOR]
			};
	
[COLOR="Blue"]	/*************************
	 * constructor(s)
	 *************************/[/COLOR]
	[COLOR="DarkRed"]public[/COLOR] Countdown() {
		[COLOR="DarkRed"]for[/COLOR] (String [COLOR="Blue"]line[/COLOR] : [COLOR="Blue"]text[/COLOR]) {
			System.[COLOR="Blue"]out[/COLOR].println(line);
		}
	}
	
[COLOR="Blue"]	
	/*************************
	 * main
	 *************************/[/COLOR]
	[COLOR="DarkRed"]public static void[/COLOR] main(String args[]) {
		[COLOR="DarkRed"]new[/COLOR] Countdown();
	}
}
```

You'll save, by example, as:
```
Countdown.java
```
You'll compile it with:
```
javac Countdown.java
```
You'll run it with:
```
java Countdown
```

---

### Post by stealth75711 on 2007-01-30
javac Countdown.java

When i type in this command it says:

keith@Zamis-laptop:~/Desktop$ javac Countdown.java
bash: javac: command not found

---

### Post by phossal on 2007-01-30
You apparently haven't set a JAVA_HOME variable. Anyway... try this:
```
locate javac
```
That will tell you where it is. 
Then you type the full path to it:
/path/javac Countdown.java

---

### Post by stealth75711 on 2007-01-30
keith@Zamis-laptop:~$ locate javac
keith@Zamis-laptop:~$ 


still it does nothing do i have to install javac?

---

### Post by Tomosaur on 2007-01-30
Javac should have come with your Java distribution. Try these commands:
```

sudo slocate -u

```

and then
```

slocate javac
```

You should get a path to the javac variable, something like this:
```

/home/keith/jdk/bin/javac

```
You want to remove the /bin/javac bits of the path, so you've just got the /home/keith/jdk bit, then type this command:
```

export JAVA_HOME=/home/keith/jdk

```

You can add that command to your .bashrc file so that it remains next time you load up the terminal.

---

### Post by phossal on 2007-01-30
What is the output to this:
```
sudo update-alternatives --display java
```

It's obvious you've got a JDK lurking about, as you're working in eclipse.

---

### Post by stealth75711 on 2007-01-30
keith@Zamis-laptop:~$ sudo slocate -u
keith@Zamis-laptop:~$ slocate javac
keith@Zamis-laptop:~$ 


//Nothing happened:confused:

keith@Zamis-laptop:~$ sudo update-alternatives --display java
java - status is auto.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/man/man1/java.1.gz
Current `best' version is /usr/lib/jvm/java-1.5.0-sun/jre/bin/java.
keith@Zamis-laptop:~$

---

### Post by phossal on 2007-01-30
Are you running eclipse from the command line? You *are* running eclipse, right?

Try this: 
```
sudo gedit /etc/eclipse/java_home
```

What's in that file?

Does this work:
```
/usr/lib/jvm/java-1.5.0-sun/bin/javac -version
```

---

### Post by stealth75711 on 2007-01-30
# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

yes i am using eclipse

---

### Post by phossal on 2007-01-30
Please answer the question:*** Are you using eclipse?***

Do either of these work:```

/usr/lib/j2sdk1.5-ibm/bin/javac -version
/usr/lib/jvm/java-1.5.0-sun/bin/javac -version
```

---

### Post by stealth75711 on 2007-01-30
bash: /usr/lib/j2sdk1.5-ibm/bin/javac: No such file or directory
keith@Zamis-laptop:~$ /usr/lib/jvm/java-1.5.0-sun/bin/javac -version
bash: /usr/lib/jvm/java-1.5.0-sun/bin/javac: No such file or directory
keith@Zamis-laptop:~$

---

### Post by phossal on 2007-01-30
[COLOR="Red"]**[SIZE="3"]ARE YOU USING ECLIPSE?[/SIZE]**[/COLOR]

---

### Post by phossal on 2007-01-30
Just to avoid the trouble:
```
sudo apt-get install sun-java6-sdk
```

---

### Post by Note360 on 2007-01-30
lol odd. Hmm go into synaptic and reinstall all the Java packages. Does it work now?

Also, I am not sure how your running anything without javac. Also you probably shouldnt be using gjc because it doesnt run alot of code atm. In the future gjc should become better as the Sun source is gpled now.

---

### Post by stealth75711 on 2007-01-30
keith@Zamis-laptop:~$ sudo apt-get install sun-java6-sdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-sdk
keith@Zamis-laptop:~$ 

// Yes i am using eclipse.

---

### Post by phossal on 2007-01-30
lol Some people don't *want* to be helped, really. The question is whether or not the photo of eclipse in the first post is of *his* desktop. I assume it *isn't*, and that he doesn't have a JDK installed.

---

### Post by phossal on 2007-01-30
Open eclipse. 
In the toolbar...
Window -> Preferences -> Java -> Installed JRE 

With that screen open, take a picture of it, and post it.

---

### Post by stealth75711 on 2007-01-30
Yes the first post is my desktop

---

### Post by stealth75711 on 2007-01-30
ok ill stop the madness!!

I just gotta learn the eclipse IDE more thoughraly

and java in general sorry if i irritated anyone.

Can anyone post any links on learning

eclipse with Java?

thankyou.

---

### Post by phossal on 2007-01-30
That path, that's indicated in the JRE field, does *that* work?

It's something like...
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08...

So try...
```
/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/javac -version
```

---

### Post by phossal on 2007-01-30
By the way, eclipse is usually set to auto-build the class files by default. That means, somewhere in your workspace, is an already compiled version of Countdown. 

You can just run that, and copy it to wherever you want.

---

### Post by Tomosaur on 2007-01-30
There's not much to eclipse that you won't be able to figure out on your own really. There are plenty of Java tutorials out there, but I find the official javadocs to be the best resource really.

---

### Post by lloyd mcclendon on 2007-01-30
good call on staying within eclipse.  the best thing you can do at this point is learn as many keyboard shortcuts as you can.  eclipse is a wonderful platform and the more time you invest at becoming proficient in it, the less time it will take you to develop quality software.  pissing around with vi and the command line FOR JAVA DEVELOPMENT is always counterproductive when eclipse can bust out so much stuff for you.

ctrl + space is your new best friend (code completion, press it all the time)

if you have an error, put the cursor on it & press ctrl + 1 for some useful suggestions.  

don't worry about imports at all.  if you use ctrl + space the import is taken care of. when i'm done with a file, it's always shift + ctrl + o, ctrl + s, ctrl + w.  (organize imports, save, close)


f3 will jump to the declaration of anything, VERY useful if you're dealing with a lot of artifacts.

ctrl + shift + g will show you everything that references something you're about to change.  also get familiar with the refactor menu.  

i could go on and on but i have to run, here read this [http://www.javaworld.com/javaworld/jw-08-2005/jw-0829-eclipse.html](http://www.javaworld.com/javaworld/jw-08-2005/jw-0829-eclipse.html)

---

### Post by Ramses de Norre on 2007-01-30
If eclipse is able to build and run your applications you must have a java compiler.. But I assume you're not using sun's then.
So you'll want to install it: ```
sudo aptitude install sun-java6-bin sun-java6-jdk sun-java6-jre
update-java-alternatives -l
sudo update-java-alternatives -s ...
```
The first java-alternatives line will show all the available jdk's, enter the version number for java6 instead of the "..." in the last line.
Now you'll have javac installed and everything should compile fine. I suggest you don't use that package statement and point eclipse to your new jre in window>properties>java>installed JRE or something like that. It's somewhere in /usr/lib/jvm.

---

### Post by stealth75711 on 2007-02-21
stealth@stealth-desktop:~$ javac Countdown.java
stealth@stealth-desktop:~$ java Countdown
Three...
Two...
One...
Liftoff...
Houston, all systems stable. 
What a view!



Thanks for the help all!!!!!!!

Ill keep learning this crazy java!

---

### Post by Tomosaur on 2007-02-21
Congratulations :)

---


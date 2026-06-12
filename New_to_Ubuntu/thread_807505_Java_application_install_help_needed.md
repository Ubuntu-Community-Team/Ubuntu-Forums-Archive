---
title: "Java application install help needed"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by thomas175 on 2008-05-25
I have installed Ubuntu 8.04 within VirtualBox and then installed Java with "sudo apt-get install sun-java6-jre". Everything went well as far as I can tell.

Then I wanted to install an application that I need which I use in XP. The Unix install instructions for this application are "java -cp jts.jar:pluginsupport.jar:jcommon-1.0.0.jar:jfreechart-1.0.0.jar:jhall.jar:other.jar:riskfeed.jar:rss.jar -Xmx256M jclient.LoginFrame ." I get an error message "Exception in main thread ..." Attached is a screen shot of the error.

Can anyone suggest what my next step should be?

tia
Thomas

---

### Post by NormR2 on 2008-05-25
Where is the class file: LoginFrame.class?
It should be in the subdirectory: jclient/ from where you issued the java -cp .... jclient.LoginFrame   command or in one of the jar files.

---

### Post by thomas175 on 2008-05-25
I don't know where the class file is, so I took a screen shot of the contents of the installation file. See attached. Is there some way to search through these jar files to find where the class file is located? And if I do find it then what do I do?

---

### Post by jamesstansell on 2008-05-31
> **thomas175 said:**
> I don't know where the class file is, so I took a screen shot of the contents of the installation file. See attached. Is there some way to search through these jar files to find where the class file is located? And if I do find it then what do I do?

Yes, there are a variety of tools that might do it - but simplest would be to just inspect the jar files.  There are several ways to do that (jar is a variation of the zip file format,) but what I just did was right-click on the jar file and say 'open with "Archive Manager".'  One of the jars should have a directory called jclient, and the LoginFrame.class inside it.

When you do find that class you need to make sure its jar is in the list of jar files.  If there's a jar that's not in the list you might look in that one first. :)

What application is this?  Offhand it sounds like whoever created it could use a little packaging help.

Regards,

-james.

---

### Post by thomas175 on 2008-06-01
Thanks james.

I found the LoginFrame.class inside a directory called jclient, which is inside the jts.jar. I added jclient.jar to my installation list but still I am getting the same error.

Attached is a screen shot of this error message.

My guess is that the way I added the jclient is not the correct way?

This is the source url of this application:
[http://www.interactivebrokers.com/en/control/systemstandalone.php?os=unix&ib_entity=llc](http://www.interactivebrokers.com/en/control/systemstandalone.php?os=unix&ib_entity=llc)

And yes they could use some help but would likely not be open to it.

---

### Post by NormR2 on 2008-06-01
Can the java command see all the .jar files? ie are the jar files in the directory where you are issuing the java command?
I don't think the java commmand complains if it can't find a .jar file that is listed in the -cp option.  Make sure the paths to the jar files are correct.

Here's a sample from XP: The jar files do not exist.

C:\Documents and Settings\Owner>java -cp asdf.jar;ddd.jar something
Exception in thread "main" java.lang.NoClassDefFoundError: something

---

### Post by thomas175 on 2008-06-01
Norm, I am not sure what you are asking so I took three screen shots each down further in the IBJts directory where I am trying to install the application.

Does this show that the paths to the jar files are correct?

---

### Post by NormR2 on 2008-06-01
Check to see that all the jar files that are listed on the commandline following the -cp option are in the IBJts folder and that they are spelled correctly. The java command ignores jar files that it can't find, so double check the spellings. 

The java command looks on the classpath to find the classes it needs.
 If you have class files that are not in jar files but are in the directory where you are entering the java commmand, add :. to the -cp option:  
java -cp <fn>.jar:<fn1>.jar:. <package>.<classnm>



I'm attaching a jar file (rename it by removing the .zip extension) that will look for a class file on the classpath. Here is a Windows batch file that can be used to execute the program:

java -jar FindClass.jar  -CP %CLASSPATH%;BuildDoit.jar;.

The item in % is an Environment variables.

Remove what follows the -CP option above and replace it with the list of jar files in your java command following the -cp. 
 When you execute the program it will show you if it can't find any of the jar files. If it finds them OK, enter the package.class name in the Class/package input window and press Search. It will show you the path(s) to the class you entered. I've never tried it on Linux, so it might not work. Good Luck.

---

### Post by jamesstansell on 2008-06-02
Thomas,

I just looked again at the screenshots you posted.

The first shows that your current directory is something like ~/IBJts (which apparently means /home/thomas/IBJts)

The second shows a directory of /IBJts

When you run the "java -cp jts.jar:..." command your current directory should be the one that has the jar files.

---


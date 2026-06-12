---
title: "Eclipse Text Search problem"
date: 2007-05-01
forum: Programming Talk
---

### Post by jnjintc on 2007-05-01
Does anyone else have a problem using the mulit-file 'search' function within Eclipse. If I press the menubar search function and choose File Search, Eclipse will usually scan my workspace for the desired text. When I run Eclipse with my OpenSuse installation it works fine, but on Ubuntu 7.04 the search function does not seem to work. It does work if I scan within one file, but when I try to scan my workspace, Eclipse reports there were no matches found.

Can anybody using ubuntu 7.04 and the Eclipse IDE verify this works for them. I have been pulling my hair trying to figure this out

thanks,
Adam

---

### Post by jcapp on 2007-05-03
Adam, I had the same problem.  I resolved it by installing sun-java5-bin and setting JAVA_HOME
to it before starting eclipse.

```

$ export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
$ eclipse
```

This solves the problem.  Perhaps someone out there can suggest a more permanent/elegant
solution.

Cheers.

---

### Post by bigbadken on 2007-06-13
There's a config file that determines which JAVA_HOME Eclipse should use and there's also a way to set it on a per user basis.  Either way, this will stop you from having to run the "export" command each session before you run Eclipse.

**Setting Eclipse JAVA_HOME Globally**
First, make sure you've got sun-java5-bin installed
```
sudo apt-get install sun-java5-bin
```

Once that's all done, edit this file...
```
sudo gedit /etc/eclipse/java_home
```

...by inserting the following line at the top, below the comments:
```
/usr/lib/jvm/java-1.5.0-sun
```

**Setting Eclipse JAVA_HOME Per User**
Alternatively, you can set the JAVA_HOME on a per user basis via the  ~/.eclipse/eclipserc file.

Create/edit the file with your favorite text editor...
```
gedit ~/.eclipse/eclipserc
```

... and then paste the following command into it:
```
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
```

FYI:  Creating the eclipserc script will override the settings in the /etc/eclipse/java_home file.

---

### Post by BatteryKing on 2007-07-30
Java 6 also works.

Java 6 specific instructions:
1. (From ubuntuguide wiki) sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
2. Available JVMs: update-java-alternatives -l
3. Switch to Java 6: update-java-alternatives -s java-6-sun (if installed properly and listed)
4. Set environment variable in appropriate place(s): export JAVA_HOME=/usr/lib/jvm/java-6-sun (probably want to set at a global level seeing it co-insides with a global default jvm.)

---

### Post by buddie on 2007-08-08
> **bigbadken said:**
> 
Once that's all done, edit this file...
```
sudo gedit /etc/eclipse/java_home
```

...by inserting the following line at the top, below the comments:
```
/usr/lib/jvm/java-1.5.0-sun
```


Thanks for this. I'm on 7.04 with eclipse 3.2 and java 6.

my jvm line would be:
```
/usr/lib/jvm/java-6-sun
```

thanks to thread-starter for bringing this up...
happy coding...

---

### Post by oskarl on 2008-11-26
I had this same issue with eclipse just returning immediately with 0 hits for whatever search I tried to make. This started after I had checked out a new project from CVS, eclipse for some unknown reason regarded every file in this new project as a derived resource, regardless of if it really was or not. I got constant pop-ups whenever I was editing files saying something like "This is a derived file, are you sure you want to edit this?"

Anyways, when doing a File Search in eclipse there is a checkbox 'Consider derived resources', if I tick this eclipse seems to perform it's search as it's supposed to, I leave it unticked I immediately get 0 hits in project for any search...

I'm on Windows tho, hehe, but I can't see how this could be OS dependant.

/O

---

### Post by donwinchell on 2010-01-13
This could be an answer to a very old post regarding eclipse search problems. I have discovered something which I could still use help with but may solve some people's problems.
It seems that eclipse simply does not "see" files in the workspace unless they have been saved by eclipse.  if I bring files into the project or in some other way get them in the editor, then save them, eclipse will see them and search them.  If files are just copied into the workspace the search function will not work.

So this may solve the problem for some or point others in the right direction.

I would still like to know how to start using eclipse on an existing directory.
all the best for 2010

---

### Post by donwinchell on 2010-01-13
to Answer my own question about getting eclipse to see other directories besides the workspace directory.
this seems to work, but I don't know if I am using the architecture correctly

file>> New> >Folder  >> Advanced (near bottom of dialog box)
click the box "link to folder in system'
then find the folder(s) you want to have seen by eclipse

hope this helps

---


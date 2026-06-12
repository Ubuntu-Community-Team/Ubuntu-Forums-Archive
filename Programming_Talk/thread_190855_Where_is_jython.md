---
title: "Where is jython?"
date: 2006-06-06
forum: Programming Talk
---

### Post by Hoffmann on 2006-06-06
Hello Guys:

I have looked for jython on Dapper repositories, but I didn't find it.  Where is it?

---

### Post by Bukunut on 2006-06-06
Heya

Doing a (apt-files:jython) file search through Konqueror for 'jython' brings the following results:-


> Package search result for "jython"
  eclipse-pydev  Python development plug-in for Eclipse
  eclipse-pydev-gcj  Python development plug-in for Eclipse (GCJ version)
  libbsf-java  Bean Scripting Framework to support scripting languages in Java
  python-all  Package depending on all supported Python runtime versions
  python-all-dev  Package depending on all supported Python development packages

Hope that helps somewhat.
Bukunut

---

### Post by Hoffmann on 2006-06-06
[QUOTE=Bukunut]Heya

Doing a (apt-files:jython) file search through Konqueror for 'jython' brings the following results:-




Hope that helps somewhat.
Bukunut[/QUOTE]
Ok...
And if I enter: 
> $ sudo apt-get install jython
Reading package lists... Done
Building dependency tree... Done
Package jython is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package jython has no installation candidate

But, where is it?
That output does not help at all. :)

---

### Post by simplyw00x on 2006-06-07
He just provided a list of packages containing files named 'jython'. There is no jython packe. Try python-all or something.

---

### Post by Hoffmann on 2006-06-07
[QUOTE=simplyw00x]He just provided a list of packages containing files named 'jython'. There is no jython packe. Try python-all or something.[/QUOTE]
All right.
I can make the download from Jython website any way. After that, all I need to do is to compile it. No problem, so.

---

### Post by vermoos on 2006-09-27
I tried installing jython from jar, but something is missing: 

cd ~/jython
sudo chmod a+x jython_Release_2_2alpha1.jar
java -jar jython_Release_2_2alpha1.jar

ignored this warning: (.:10174): Gdk-CRITICAL **: gdk_window_get_origin: assertion `GDK_IS_WINDOW (window)' failed

cd ~/jythonRelease_2_2alpha1
sudo chmod a+x jython
sh jython

-->  *sys-package-mgr*: processing new jar, '/home/meso/jythonRelease_2_2alpha1/jython.jar'
     *sys-package-mgr*: processing new jar, '/usr/share/sablevm-classpath/libclasspath.jar'
     *sys-package-mgr*: processing new jar, '/usr/share/sablevm-classpath/resources.jar'
     Jython 2.2a1 on java1.4.2 (JIT: )

The python command prompt (>>>) and copyright stuff is missing !

p2 of O'Reilly Jython Essentials says the command prompt should look like this:

Jython 2.1a3 on java1.3.0 (JIT: null)
Type "copyright", "credits" or "license" for more information. 
>>>

Anyone know whats up here? 

Also: 

System monitor is showing:
	'sh' is 'sleeping'  
	'sabelvm' is using memory and used 

/usr/bin/sablevm -Y --classpath=~/jythonRelease_2_2alpha/jython.jar --property=python.home=~/jythonRelease_2_2alpha1 org.python.util.jython

thanks for any help

---

### Post by vermoos on 2006-10-06
PROBLEM: Jython does not install with the native gij 'java' command. 

SOLUTION: To correct this i did the following: 

	0)	Download jre-1_5_0_06-linux-i586.bin from sun.com 
	1)	I removed the gij shortcut from /etc/alternatives
	3)	mkdir /usr/java 
	4)	sudo cp jre-1_5_0_06-linux-i586.bin /usr/java
	5)	cd /usr/java
	6)	make sure its executable: 
                sudo chmod a+x jre-1_5_0_06-linux-i586.bin
	7)	sudo ./jre-1_5_0_06-linux-i586.bin
		(accept licence etc)
	8)	cd /etc/alternatives 
	9)	Point your command line to the new java: 
                sudo ln -s /usr/java/jre1.5.0_09/bin/java

The java command should now correctly install jython. Cheerio!

---


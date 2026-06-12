---
title: "How to run .sh file  without changing directory?"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by beew on 2011-09-23
Hi,

I have a program that is started by running a .sh file (say programxx.sh). I have the program in the folder /home/usetname/programxx (say) I can start it by going to the terminal and type 

```
cd programxx

sh programxx.sh
```

Now I want to create a launcher for it, I think the command should be 

```
sh /home/usetname/programxx/programxx.sh
```

But it doesn't work when I try it on the terminal.

What should I do?

Thanks.

---

### Post by searchfgold6789 on 2011-09-23
It should work. Verify that you have typed the code in correctly, although it probably makes your ears bleed hearing me say that. Is there a specific error code you recieved?

---

### Post by beew on 2011-09-23
I think it doesn't work because the sh file invokes some libraries in the programxx folder (thus resulting in a bunch of "not found" errors)

I tried ```
cd programxx && sh programxx.sh 
``` and still doesn't work, I think I might have made some syntax error here though

---

### Post by dave01945 on 2011-09-23
the first code you tried should work. did you write the script yourself and does the top of the scrip start with

```
#!/bin/sh
or
#!/bin/bash
```

because if it starts with **#!/bin/bash** you will need to start it with 

```
bash /home/usetname/programxx/programxx.sh
```

this is because bash can do thing's that sh cannot so you may have parts of the script that sh cannot understand 

also /bin/sh in ubuntu actually points to **dash** which is a light weight shell and may no have all the functionality you need but if the top of the script starts with **#!/bin/sh** then it should work if it runs with

```
./programxx.sh
```

--edit--

also if there is no **#!/bin/bash or #!/bin/sh** at the top when you run it from terminal it will run from bash as this is the default shell for users so i suggest try with bash

---

### Post by beew on 2011-09-23
The top of the script started with #!/bin/bash

I tried ```
bash /home/username/programxx/programxx.sh
``` but it still doesn't work.

However, cd into the folder progamxx first and than run sh programxx.sh and it works so I am not sure if it is a shell issue. I think it is because the script invokes libraries with hard coded paths (without prefixes like /home/username/programxx)

I didn't write the script myself. It is a program called Open modelsphere for DB modeling. [http://www.modelsphere.com/](http://www.modelsphere.com/)

 It is written in java  and it is therefore cross platform but it is started by running a batch file that works only in Windows. You can start it in Linux if you change the batch file to a .sh file following the instructions I found  here. [http://geowind.javaforge.com/wiki/66477](http://geowind.javaforge.com/wiki/66477)

Edit: I think it will work if I change the paths in the .sh files by prefixing them with programxx/, but I would like to have a more elegant way of doing it.

---

### Post by grayraven on 2011-09-23
Hey beew,

I just took a look at the script conversion guide you linked. Since the script works when you are in directory, I believe the problem is with the classpath settings. My recommendation is to change the -cp variables to have the absolute path instead of the current directory.

For example: instead of .:./modelsphere.jar I would change it to be /home/user/programxx:/home/user/programxx/modelsphere.jar where /home/user/programxx is the path to the program.

Its been a while since I used java so you may only have to change the first part, but I would start by changing all the paths to be absolute. You can then roll back. Hope this helps.

Cheers,

James

---

### Post by beew on 2011-09-23
Hi, James,

I change the paths like this

```
java -ms64m -mx512m -ss16m -cp .:./modelsphere.jar
:./resources.zip
:./resources
:./targets
:./lib/jakarta-regexp-1.5/jakarta-regexp-1.5.jar

```to 

```
java -ms64m -mx512m -ss16m -cp /home/username/Open_ModelSphere_3.1-912:Open_ModelSphere_3.1-912/modelsphere.jar 
home/username/Open_ModelSphere_3.1-912:Open_ModelSphere_3.1-912/resources.zip 
home/username/Open_ModelSphere_3.1-912:Open_ModelSphere_3.1-912/resources 
home/username/Open_ModelSphere_3.1-912:Open_ModelSphere_3.1-912/targets 
home/username/Open_ModelSphere_3.1-912:Open_ModelSphere_3.1-912/lib/jakarta-regexp-1.5/jakarta-regexp-1.5.jar

```Still doesn't work. Maybe I have made some syntax errors? (I might have gotten the position of the colon wrong)

Thanks for the help.

---

### Post by grayraven on 2011-09-23
Hey beew,

I made some modifications to what you posted. Let me know if they help. If not, can you attach the script, and I will take a look through it.

```
-cp /home/username/Open_ModelSphere_3.1-912:/home/username/Open_ModelSphere_3.1-912/modelsphere.jar:/home/username/Open_ModelSphere_3.1-912/resources.zip:/home/username/Open_ModelSphere_3.1-912/resources:/home/username/Open_ModelSphere_3.1-912/targets:/home/username/Open_ModelSphere_3.1-912/lib/jakarta-regexp-1.5/jakarta-regexp-1.5.jar
```

Cheers,

James

---

### Post by beew on 2011-09-23
Hi James,

The script now looks like this

```
#!/bin/bash 
java -ms64m -mx512m -ss16m -cp /home/bee/Open_ModelSphere_3.1-912/modelsphere.jar:home/bee/Open_ModelSphere_3.1-912/resources.zip:home/bee/Open_ModelSphere_3.1-912/resources:home/bee/Open_ModelSphere_3.1-912/targets:home/bee/Open_ModelSphere_3.1-912/lib/jakarta-regexp-1.5/jakarta-regexp-1.5.jar:home/bee/Open_ModelSphere_3.1-912/velocity-1.6.1.jar:home/bee/Open_ModelSphere_3.1-912/lib/jazzy-core/jazzy-core.jar:home/bee/Open_ModelSphere_3.1-912/lib/jython-2.2.1/jython.jar:home/bee/Open_ModelSphere_3.1-912/lib/velocity-1.6.1/lib/commons-collections-3.2.1.jar:home/bee/Open_ModelSphere_3.1-912/lib/velocity-1.6.1/lib/commons-lang-2.4.jar:home/bee/Open_ModelSphere_3.1-912/lib/lablib-checkboxtree-3.0.2.jar org.modelsphere.sms.Application 
```

When I run 

```
sh Open_ModelSphere_3.1-912/openmodelsphere.sh
```

I got these errors
> : not foundphere_3.1-912/openmodelsphere.sh: 1: 
Exception in thread "main" java.lang.ExceptionInInitializerError
Caused by: java.util.MissingResourceException: Can't find bundle for base name org.modelsphere.sms.international.MiscResources, locale en
    at java.util.ResourceBundle.throwMissingResourceException(ResourceBundle.java:1427)
    at java.util.ResourceBundle.getBundleImpl(ResourceBundle.java:1250)
    at java.util.ResourceBundle.getBundle(ResourceBundle.java:952)
    at org.modelsphere.jack.international.LocaleMgr.findResourceBundle(Unknown Source)
    at org.modelsphere.jack.international.LocaleMgr.getRes(Unknown Source)
    at org.modelsphere.jack.international.LocaleMgr.getString(Unknown Source)
    at org.modelsphere.sms.Application.<clinit>(Unknown Source)
Could not find the main class: org.modelsphere.sms.Application.  Program will exit.





Also cd into the directory first no longer works.

---

### Post by grayraven on 2011-09-23
Hey beew,

Thanks for including the script. I believe the issue is that after the first entry into the class path the other entries are missing the leading / before home. I have included an updated script below:

```
#!/bin/bash 
java -ms64m -mx512m -ss16m -cp /home/bee/Open_ModelSphere_3.1-912/modelsphere.jar:/home/bee/Open_ModelSphere_3.1-912/resources.zip:/home/bee/Open_ModelSphere_3.1-912/resources:/home/bee/Open_ModelSphere_3.1-912/targets:/home/bee/Open_ModelSphere_3.1-912/lib/jakarta-regexp-1.5/jakarta-regexp-1.5.jar:/home/bee/Open_ModelSphere_3.1-912/velocity-1.6.1.jar:/home/bee/Open_ModelSphere_3.1-912/lib/jazzy-core/jazzy-core.jar:/home/bee/Open_ModelSphere_3.1-912/lib/jython-2.2.1/jython.jar:/home/bee/Open_ModelSphere_3.1-912/lib/velocity-1.6.1/lib/commons-collections-3.2.1.jar:/home/bee/Open_ModelSphere_3.1-912/lib/velocity-1.6.1/lib/commons-lang-2.4.jar:/home/bee/Open_ModelSphere_3.1-912/lib/lablib-checkboxtree-3.0.2.jar org.modelsphere.sms.Application
```

Let me know if that helps.

Cheers,

James

---

### Post by grayraven on 2011-09-23
I can't remember if cp needs absolute paths to work correctly, but if the suggestion above fixes the problem you may want to try the changes below. This should allow the script to work for any user who has the Open_ModelSphere_3.1-912 directory installed in their home directory.

```
#!/bin/bash 
java -ms64m -mx512m -ss16m -cp ~/Open_ModelSphere_3.1-912/modelsphere.jar:~/Open_ModelSphere_3.1-912/resources.zip:~/Open_ModelSphere_3.1-912/resources:~/Open_ModelSphere_3.1-912/targets:~/Open_ModelSphere_3.1-912/lib/jakarta-regexp-1.5/jakarta-regexp-1.5.jar:~/Open_ModelSphere_3.1-912/velocity-1.6.1.jar:~/Open_ModelSphere_3.1-912/lib/jazzy-core/jazzy-core.jar:~/Open_ModelSphere_3.1-912/lib/jython-2.2.1/jython.jar:~/Open_ModelSphere_3.1-912/lib/velocity-1.6.1/lib/commons-collections-3.2.1.jar:~/Open_ModelSphere_3.1-912/lib/velocity-1.6.1/lib/commons-lang-2.4.jar:~/Open_ModelSphere_3.1-912/lib/lablib-checkboxtree-3.0.2.jar org.modelsphere.sms.Application
```

Cheers,

James

---

### Post by beew on 2011-09-23
Hi James,

Adding the missing "/" works. 

Thanks a million!

But there is still this error even though it doesn't prevent the script from running
> : not foundphere_3.1-912/modelsphere.sh: 1: 

It was there with the original script too(the first one from the website) , wonder what that might means.

---

### Post by grayraven on 2011-09-23
That one is weird. I don't see anything in the script that should be causing that. My first thought is that it is an internal java reference, but I am not sure why the java code would be looking for a script. I am glad it is working minus that last issue.

Cheers,

James

---

### Post by beew on 2011-09-23
Thanks a lot!

---

### Post by gandaran on 2011-09-23
hi
sorry to high-jack the thread but I'm having the same problem running Mobile Atlas Creator from start.sh script, the start.sh works okay from terminal but I want to create a launcher, I have tried various options and most of the times it just shows file not found.
the java application path is /home/mfp/.Mobile Atlas Creator/start.sh
```
#!/bin/sh

# This file will start the Mobile Atlas Creator with custom memory settings for
# the JVM. With the below settings the heap size (Available memory for the application)
# will range from 64 megabyte up to 512 megabyte.

java -Xms64m -Xmx512M -jar Mobile_Atlas_Creator.jar
```
what should I do?

---

### Post by beew on 2011-09-23
Hi,

Try to replace "Mobile_Atlas_Creator.jar" in
```
java -Xms64m -Xmx512M -jar Mobile_Atlas_Creator.jar
```
 with the actual path to the .jar file to see if it works.

---

### Post by Paddy Landau on 2011-09-23
@beew

A script does not need bash or sh in front of it to run. Your script contains #!/bin/bash, so the script itself is runnable. Check that the file has the executable bit set, and instead of:
[FONT=Fixedsys]bash [scriptname][/FONT]
just do
[FONT=Fixedsys][scriptname][/FONT]

So, in your case, typing (or putting in the launcher) the following will do the trick.```
/home/usetname/programxx/programxx.sh
```

---

### Post by beew on 2011-09-23
Thanks Paddy.

grayraven's solution works perfectly. I think the problem arises because the the libraries invoked in the script were named in such a way that it assumes you are running the script in the directory where these libraries reside. Changing them to the absolute path names resolves the problem.

I had tried your suggestion before (without sh), it didn't work.

---

### Post by gandaran on 2011-09-23
> **beew said:**
> Hi,

Try to replace "Mobile_Atlas_Creator.jar" in
```
java -Xms64m -Xmx512M -jar Mobile_Atlas_Creator.jar
```
 with the actual path to the .jar file to see if it works.
yes it does launch the java application and works but without the custom memory settings for the JVM, that's why I need to start it from start.sh script.

---

### Post by grayraven on 2011-09-23
Hey gandaran,

I think if you modify your launcher script to have a classpath set to the location of your jar file it should work. I am not sure if you have to escape the spaces in the directory name or not. This is assuming that the jar file is in the same directory as the startup.sh.

Below is the addition I am suggesting with the spaces escaped:

```
java -Xms64m -Xmx512M -cp /home/mfp/.Mobile\ Atlas\ Creator -jar Mobile_Atlas_Creator.jar
```

If this doesn't work you will probably need to add the full path to the jar call. I believe this is what beew was suggesting. For example (with cp still included):

```
java -Xms64m -Xmx512M -cp /home/mfp/.Mobile\ Atlas\ Creator -jar /home/mfp/.Mobile\ Atlas\ Creator/Mobile_Atlas_Creator.jar
```

Hope this helps.

Cheers,

James

---

### Post by gandaran on 2011-09-23
> **grayraven said:**
> Hey gandaran,

I think if you modify your launcher script to have a classpath set to the location of your jar file it should work. I am not sure if you have to escape the spaces in the directory name or not. This is assuming that the jar file is in the same directory as the startup.sh.

Below is the addition I am suggesting with the spaces escaped:

```
java -Xms64m -Xmx512M -cp /home/mfp/.Mobile\ Atlas\ Creator -jar Mobile_Atlas_Creator.jar
```

If this doesn't work you will probably need to add the full path to the jar call. I believe this is what beew was suggesting. For example (with cp still included):

```
java -Xms64m -Xmx512M -cp /home/mfp/.Mobile\ Atlas\ Creator -jar /home/mfp/.Mobile\ Atlas\ Creator/Mobile_Atlas_Creator.jar
```

Hope this helps.

Cheers,

James
the second option did start the application but again without the custom memory settings, well I think I will have to live with that as the application still works, the only annoying thing is the settings xml file on home user directory while if the start.sh script is run from terminal the settings file is neatly placed inside the Mobile Atlas Creator folder.

---

### Post by grayraven on 2011-09-23
Hey gandaran,

Not sure why the memory options are not taking, but the following options might help with the settings.xml file location.

```
cd /home/mfp/.Mobile\ Atlas\ Creator
java -Xms64m -Xmx512M -cp /home/mfp/.Mobile\ Atlas\ Creator -jar /home/mfp/.Mobile\ Atlas\ Creator/Mobile_Atlas_Creator.jar
cd -
```

I haven't tested it, but it might be worth a try to see if it fixes the issue.

Cheers,

James

---


---
title: "Eclipse advice"
date: 2009-07-16
forum: Programming Talk
---

### Post by Mirge on 2009-07-16
I've got PDT 2.1.0 installed on both Vista & Kubuntu 9.04... Kubuntu comp has 8GB RAM, Vista comp has 4GB (3.5 read). Eclipse seems to run leaps & bounds faster in Vista than in Linux for some reason.

Is it the Java version installed? I've got sun's java6 installed in Linux... any thoughts on how to perk it up a bit? Hardware-wise, both comps are pretty similar other than RAM (Linux having double the amount).

---

### Post by doas777 on 2009-07-16
personally, i've always found eclipse to run slowly, but I haven't really seen a differance in speed with differant oses, unless im using pydev. you may want to double check your jdk bindings in the eclipse configuration to make sure you have the right libs sources and tools.

good luck

---

### Post by Mirge on 2009-07-16
> **doas777 said:**
> what type of java do you have installed?
```
javac -version
``` may help determine that. 

if you don't have the sun java package you can install it with 
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk

```

mike@mike-kubuntu:/etc/eclipse$ javac -version
javac 1.6.0_0
mike@mike-kubuntu:/etc/eclipse$

```Running: sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk

javac -version reports the same...
java -version reports:
```

mike@mike-kubuntu:/etc/eclipse$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
mike@mike-kubuntu:/etc/eclipse$

```

---

### Post by doas777 on 2009-07-16
sorry, i edited my post after rereading yours. lol. see above.

---

### Post by Mirge on 2009-07-16
Well running that apt-get.. it installed 1 new package & upgraded 2.

I don't think I'm imagining things... since content assist was actually hanging/crashing prior to it... now it's quite snappy. Not sure what to make of it, I just hope it sticks!

---

### Post by jespdj on 2009-07-17
You are running OpenJDK Java 6, not Sun Java 6. After installing Sun Java 6 (you already did that), do the following to select the default version of Java to use:
```
sudo update-java-alternatives -s java-6-sun
```
See this for more info: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Defrector on 2009-07-17
If a lot of editor tabs are open in Eclipse things tend to slow down for me. Similar to if working on larger projects versus smaller projects. Closing some of those tabs tends to speed things up again.

---

### Post by Mirge on 2009-07-17
```

mike@mike-kubuntu:~$ sudo update-java-alternatives -s java-6-sun
[sudo] password for mike:                                       
No alternatives for firefox-javaplugin.so.                      
No alternatives for iceape-javaplugin.so.                       
No alternatives for iceweasel-javaplugin.so.                    
No alternatives for midbrowser-javaplugin.so.                   
No alternatives for mozilla-javaplugin.so.                      
No alternatives for xulrunner-javaplugin.so.                    
Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide 'appletviewer'.
Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.                  
Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.        
Using '/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide 'HtmlConverter'.
Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.                  
Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.        
Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.                    
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.                
Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.            
Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.                
Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.                
Using '/usr/lib/jvm/java-6-sun/bin/jconsole' to provide 'jconsole'.          
Using '/usr/lib/jvm/java-6-sun/bin/jdb' to provide 'jdb'.                    
Using '/usr/lib/jvm/java-6-sun/bin/jhat' to provide 'jhat'.                  
Using '/usr/lib/jvm/java-6-sun/bin/jinfo' to provide 'jinfo'.                
Using '/usr/lib/jvm/java-6-sun/bin/jmap' to provide 'jmap'.                  
Using '/usr/lib/jvm/java-6-sun/bin/jps' to provide 'jps'.                    
Using '/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide 'jrunscript'.      
Using '/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide 'jsadebugd'.        
Using '/usr/lib/jvm/java-6-sun/bin/jstack' to provide 'jstack'.              
Using '/usr/lib/jvm/java-6-sun/bin/jstatd' to provide 'jstatd'.              
Using '/usr/lib/jvm/java-6-sun/bin/jstat' to provide 'jstat'.                
Using '/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide 'native2ascii'.  
Using '/usr/lib/jvm/java-6-sun/bin/rmic' to provide 'rmic'.
Using '/usr/lib/jvm/java-6-sun/bin/schemagen' to provide 'schemagen'.
Using '/usr/lib/jvm/java-6-sun/bin/serialver' to provide 'serialver'.
Using '/usr/lib/jvm/java-6-sun/bin/wsgen' to provide 'wsgen'.
Using '/usr/lib/jvm/java-6-sun/bin/wsimport' to provide 'wsimport'.
Using '/usr/lib/jvm/java-6-sun/bin/xjc' to provide 'xjc'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for midbrowser-javaplugin.so.
No alternatives for mozilla-javaplugin.so.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so'.

No alternatives for xulrunner-javaplugin.so.
mike@mike-kubuntu:~$

```

java -version reports:

```

mike@mike-kubuntu:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
mike@mike-kubuntu:~$

```

---

### Post by jespdj on 2009-07-17
So, it looks like you've correctly set Sun Java 6 as the default Java to be used.

The error message at the end is because you don't have the Sun Java 6 browser plug-in installed (to run Java applets in Firefox). If you want that too, do:
```
sudo apt-get install sun-java6-plugin
```
and run the update-java-alternatives command again.

---

### Post by Mirge on 2009-07-17
Thanks!

I've ran into a couple times where Eclipse's content assist in PHP would hang for 30-60 seconds then throw an error... now _sometimes_ it'll hesitate for 1-2 seconds, but usually it's darn quick!

---


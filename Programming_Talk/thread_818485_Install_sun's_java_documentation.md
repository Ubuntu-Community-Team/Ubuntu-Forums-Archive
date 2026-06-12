---
title: "Install sun's java documentation"
date: 2008-06-04
forum: Programming Talk
---

### Post by ultimate_aektzis on 2008-06-04
Hi everybody.I think my question is very simple for you.I have downloaded java documentation from sun and I cant find a way to install it so that I can use it while programming at Eclipse IDE.To be more specific I want to write
```
System.
``` 
and when I press . to see a drop down menu with the class methods.I would be very grateful if you can help me with this simple thing

---

### Post by mike_g on 2008-06-04
This thread:
[http://ubuntuforums.org/showthread.php?t=641736](http://ubuntuforums.org/showthread.php?t=641736)
Post #4 did the trick for me.

---

### Post by ultimate_aektzis on 2008-06-05
I opened the terminal window wrote sudo apt-get sun-java6-doc but it produced some strange warnings and installation not completed 
I followed those instuctions but anything happened:(:(

[http://www.cis.upenn.edu/~matuszek/General/Pages/eclipse-faq.html#api_javadoc](http://www.cis.upenn.edu/~matuszek/General/Pages/eclipse-faq.html#api_javadoc)

---

### Post by geirha on 2008-06-05
You forgot the install keyword, so it should be ```
sudo apt-get install sun-java6-doc
``` If it asks for the jdk-6-doc.zip, go to [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/) and download the documentation to your Desktop. Then move it to /tmp and change ownership as the information suggests. Like this:
```
DESKTOP=`xdg-user-dir DESKTOP`
sudo mv "$DESKTOP/jdk-6-doc.zip" /tmp/
sudo chown root:root /tmp/jdk-6-doc.zip

```
If it fails, paste the output here and we might be able to identify the problem.

---

### Post by ultimate_aektzis on 2008-06-05
ok I ve done it and this is the output.What's next??
Note that some of the output is in greek but dont mind.Its just the process of the command execution

```
periklis@p:~$ sudo apt-get install sun-java6-doc
[sudo] password for periklis: 
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;                  
Reading state information... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;             
&#964;&#959; sun-java6-doc &#949;&#943;&#957;&#945;&#953; &#942;&#948;&#951; &#951; &#964;&#949;&#955;&#949;&#965;&#964;&#945;&#943;&#945; &#941;&#954;&#948;&#959;&#963;&#951;.
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#960;&#959;&#965; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; &#945;&#965;&#964;&#972;&#956;&#945;&#964;&#945; &#954;&#945;&#953; &#948;&#949;&#957; &#967;&#961;&#949;&#953;&#940;&#950;&#959;&#957;&#964;&#945;&#953; &#960;&#953;&#945;:
  libseda-java libcommons-cli-java circuslinux-data etw-data
  libcommons-lang-java
&#935;&#961;&#951;&#963;&#956;&#959;&#960;&#959;&#953;&#942;&#963;&#964;&#949; &#964;&#959; 'apt-get autoremove' &#947;&#953;&#945; &#957;&#945; &#964;&#945; &#945;&#960;&#959;&#956;&#945;&#954;&#961;&#973;&#957;&#949;&#964;&#949;
0 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.
1 &#956;&#951; &#960;&#955;&#942;&#961;&#969;&#962; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945; &#942; &#945;&#966;&#945;&#953;&#961;&#941;&#952;&#951;&#954;&#945;&#957;.
After this operation, 0B of additional disk space will be used.
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] DESKTOP=`xdg-user-dir DESKTOP`
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: &#963;&#966;&#940;&#955;&#956;&#945; &#963;&#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965; sun-java6-doc (--configure):
 &#951; &#965;&#960;&#959;&#948;&#953;&#949;&#961;&#947;&#945;&#963;&#943;&#945; post-installation script &#949;&#960;&#941;&#963;&#964;&#961;&#949;&#968;&#949; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; &#955;&#940;&#952;&#959;&#965;&#962; 1
&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
periklis@p:~$ DESKTOP=`xdg-user-dir DESKTOP`
periklis@p:~$ udo mv "$DESKTOP/jdk-6-doc.zip" /tmp/
&#932;&#959; &#960;&#961;&#972;&#947;&#961;&#945;&#956;&#956;&#945; 'udo' &#948;&#949;&#957; &#949;&#943;&#957;&#945;&#953; &#945;&#965;&#964;&#942; &#964;&#951; &#963;&#964;&#953;&#947;&#956;&#942; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#959;.  &#924;&#960;&#959;&#961;&#949;&#943;&#964;&#949; &#957;&#945; &#964;&#959; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#942;&#963;&#949;&#964;&#949; &#960;&#955;&#951;&#954;&#964;&#961;&#959;&#955;&#959;&#947;&#974;&#957;&#964;&#945;&#962;:
sudo apt-get install udo
bash: udo: command not found
periklis@p:~$ sudo mv "$DESKTOP/jdk-6-doc.zip" /tmp/
periklis@p:~$ sudo chown root:root /tmp/jdk-6-doc.zip
periklis@p:~$ 


```

---

### Post by geirha on 2008-06-05
Ok, I was unclear on that point. The code to copy the jdk-6-doc.zip file to /tmp as apt-get instructed, 
```
DESKTOP=`xdg-user-dir DESKTOP`
sudo mv "$DESKTOP/jdk-6-doc.zip" /tmp/
sudo chown root:root /tmp/jdk-6-doc.zip
```
should've been run in a different terminal when the message 
```
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

``` was showing on the apt-get command. If you still have the zip-file in /tmp now, it should work if you run ```
sudo apt-get install sun-java6-doc
``` again. If you've rebooted meanwhile, all files in /tmp has been deleted, so download the file and move it to /tmp again, before running apt-get then.

---

### Post by ultimate_aektzis on 2008-06-05
Hmm.No results.It claims that is unable to unlock.:(

> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by bobhonea on 2009-03-24
I used the Package Manager to do this job, and left it open while working to download and chown, etc. I got the "lock" message.

The message about the lock on the Admin Directory happened to me because the Synaptic Package Manager was open. Funny thing is, you need it open to finish the job....

0. exit the Package Manager.
1. Get the Java Document Package you need (1.5, or 1.6) from sun.
2. Open a terminal and move them into /tmp.
3. use chown to make root their owner (chown root:root <zipfile name>
4. if installing Java6 docs, rename the zipfile (jdk-6u10-doc.zip, in my case) to jdk-6-doc.zip.

5. Open the Package Manager.
    a) if the Package manager 'thinks' our java-docs are installed, or partially installed, go through the process to remove them.
    b) select the checkbox for the java docs you want to install.
    c) the install should go forward when you "apply", ending with an advisory that you can delete the zipfile from /tmp...(do with them what you will....for they are just a hollow shell...)

---

### Post by Albert Net on 2009-11-24
Very detailed instruction. I managed to install java documentation. At least, it doesn't give me error.
How can I use it in eclipse?

---

### Post by Pooven on 2009-11-27
Try reading this post: [http://ubuntuforums.org/showthread.php?t=476280](http://ubuntuforums.org/showthread.php?t=476280) and the 2nd post will tell you how to configure eclipse to use the Java docs.

Though, for me, I just added '/usr/lib/jvm/java-6-sun' to the docs path in Netbeans.

---


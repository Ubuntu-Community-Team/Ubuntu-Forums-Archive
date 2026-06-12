---
title: "how to unzip/untar war files"
date: 2007-08-17
forum: Programming Talk
---

### Post by adhg on 2007-08-17
Hi all,
I'm trying to write a shell that unzip a war file. I wonder what is the command line to unzip?
So far I've been doing that with the GUI "archive manager". I tried unzip /home/xian/Desktop prj.war
but the return result was:

unzip:  cannot find or open /home/xian/Desktop/Runway.war, /home/adhg/Desktop/Runway.war.zip or /home/adhg/Desktop/Runway.war.ZIP.

any idea?

---

### Post by slavik on 2007-08-17
```
jar xf prj.war
```

this might work (not tested)

```
tar zxf prj.war
```

---

### Post by kalikiana on 2007-08-18
I suggest you try these commands as well. ;)

```
man unzip
```

```
man tar
```

---

### Post by adhg on 2007-08-18
thank you all for your help.
As I am a complete newbie to Linux, As suggested by kalikiana I tried the command line:

adriana@ubuntu:~$jar /home/adhg/Desktop/Runway.war

and the result came in as:

The program 'jar' can be found in the following packages:
 * sun-java5-jdk
 * kaffe
 * java-gcj-compat
 * j2sdk1.4
 * fastjar
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
Make sure you have the 'multiverse' component enabled
bash: jar: command not found


I Googled for that and I'm not sure how to set the path to the jar command. (how can I tell where is the jar file lives?)

thanks for any pointers
adhg

---

### Post by Max Luebbe on 2007-08-18
you dont have java installed.

```
sudo apt-get install sun-java6-jdk
```

then try again - if you're confused on how to use jar, consult its man page.

---

### Post by adhg on 2007-08-19
GREAT! thanks Max, I downloaded the Java and the jar works.

I tried: jar xf /home/adhg/Desktop/Runway

and it worked. 

I learned that the extracted folder is under home/adhg and not under my desktop (all files are scattered into this folder)

I tried variation of unzip...as in: unzip file.zip -d /home/adhg/Desktop/tmp

(on my side it was:
jar xf /home/adhg/Desktop/Runway -d /home/adhg/Desktop/tmp)

Although the prompt return with no errors....nothing happens! can you advise how to unzip (unjar) the folder into the desktop.

thank you so much!

---

### Post by slavik on 2007-08-19
cd Desktop/somedir (somedir has to already exist)
jar xf ../file.war

---

### Post by adhg on 2007-08-19
got ya! 
thanks

---


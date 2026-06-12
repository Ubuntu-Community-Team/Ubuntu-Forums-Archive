---
title: "Repositories/JDK9/Ubuntu Software"
date: 2018-01-09
forum: New to Ubuntu
---

### Post by zezzreth on 2018-01-09
Greetings Everyone, I have just spent a large quantity of time attempting to install JDK9 onto Ubuntu 16.04.

The instuctions from the Oracle website say -> 

[LIST=1]
[*]Download the file, jdk-9.minor.security.patch_linux-x64_bin.tar.gz.  Before you download a file, you must accept the license agreement.  The archive binary can be installed by anyone (not only by root users)  in any location that you can write to.
 The .tar.gz archive file (also called a tarball) is a file that can be simultaneously uncompressed and extracted in one step.
 

[*]Change the directory to the location where you want to install the JDK, then move the .tar.gz archive binary to the current directory.
[*]Unpack the tarball and install the JDK:  % tar zxvf jdk-9.minor.security.patch_linux-x64_bin.tar.gz
 
  The Java Development Kit files are installed in a directory called jdk-9.minor.security.patch in the current directory.
 

[*]Delete the .tar.gz file if you want to save disk space.
[/LIST]

I got the tar.gz, moved it from the downloads folder to /usr/local/java, and unpacked it. I don't understand how you install the file once it's unpacked. Javac is still showing 1.8.0_051. 

1) How do I install the file once unpacked into /usr/local/java? 
2) Why isn't the JDK in the Ubuntu Software library? This is one of those "big applications". It isn't something obscure. Ubuntu is the most popular Linux distribution and according to Linuxcounter there are over 95million Linux users. Out of those 95million, surely some % of those are Android developers. The resounding question echoing in my mind is "Why?"

I have never had such difficulty getting anything to work properly. The Oracle instructions are vague. YouTube has a few videos but a lot of them are using bash files and have led to errors. What magic spell, what hocus pocus is required to make this install happen?

---

### Post by QIII on 2018-01-10
Hello!

Oracle does not allow anyone to have the Oracle Java binaries in their repositories.  They must be downloaded from Oracle.  Period.  End of story.

webupd8.org has an installer that consists of several scripts to download and install Java, but Andrei doesn't have the actual binaries in his PPA.

You can find the instructions for using his installer [here]("http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html").  This is by far the easiest way to install Oracle Java.  Java is automatically updated as you do your normal updates when Andrei has had time to update the scripts to use Oracle's new releases.  If you are looking for something that accounts for Meltdown and Spectre, he may not have gotten that put together yet.  

Cheers!

---

### Post by zezzreth on 2018-01-10
> **QIII said:**
> Hello!

Oracle does not allow anyone to have the Oracle Java binaries in their repositories.  They must be downloaded from Oracle.  Period.  End of story.

webupd8.org has an installer that consists of several scripts to download and install Java, but Andrei doesn't have the actual binaries in his PPA.

You can find the instructions for using his installer [here]("http://www.webupd8.org/2015/02/install-oracle-java-9-in-ubuntu-linux.html").  This is by far the easiest way to install Oracle Java.  Java is automatically updated as you do your normal updates when Andrei has had time to update the scripts to use Oracle's new releases.  If you are looking for something that accounts for Meltdown and Spectre, he may not have gotten that put together yet.  

Cheers!

Qlll - Hello. Thanks. I saw that webupd8 repository/installation guide on a lot of videos on Youtube but I wasn't sure if it could be trusted. I've got JDK9 installed now but it feels a bit like cheating after of that effort from before. I really wanted to figure out how to install it in case I had to install something else in a similar fashion. A bit like a puzzle, really. 

Along my journey I learned how to change directories, go back to previous directory location, check current working directory, make directory, list files in directories, search for specific names in files, move files, unpack tarballs(weird name), delete files, check java version. I'm pretty happy about that. 

The tar file is unpacked and in it's install location. How do you "connect" the install location to operating system to let it know where the files are? It's as though your car is in the parking at a mega mall with multi floor parking and you don't know which floor you parked on. How can I tell the os where the car is? ](*,)](*,)

---

### Post by deadflowr on 2018-01-10
> The tar file is unpacked and in it's install location. How do you "connect" the install location to operating system to let it know where the files are? It's as though your car is in the parking at a mega mall with multi floor parking and you don't know which floor you parked on. How can I tell the os where the car is? &#65532;&#65532;
The systems uses shortcuts called Paths.
There are set Paths that the system is told to look in and if what you want is found in any of those paths it runs that command
It comes with a default selection but you can add new paths to it if you need as well.
```
$PATH
```
will show a list of all current paths.
Almost all methods of package installation will adhere to install the files in one of those locations.

---


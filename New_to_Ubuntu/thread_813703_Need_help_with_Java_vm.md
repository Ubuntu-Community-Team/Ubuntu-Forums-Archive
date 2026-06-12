---
title: "Need help with Java vm"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by LaXBubbaMan on 2008-05-31
I am having trouble installing java vm. I cant seem to be able to get it to install into usr/java and run properly. I need it so that I can install

sh ./thinkorswim_installer.sh

When I try to install this it tells me that I do not have java loaded.

---

### Post by helino on 2008-05-31
How did you install the java vm, through Synaptic?

Which packages did you install?

---

### Post by LaXBubbaMan on 2008-05-31
Fisrt I downloaded the java bin file from java.com then I tried to follow the step that they gave me on the website. But since the bin file was on my desktop I think that is where is got installed to.

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u<version>-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l



Make sure the installation file has executable permission

   6. Start the installation process.Type:
      ./jre-6u<version>-linux-i586.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.



type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_<version> directory. When the installation has completed, you will see the word Done.



The installation completes

   8. The JRE is installed in jre1.6.0_<version> sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.6.0_<version> directory. Verify that the jre1.6.0_<version> sub-directory is listed under the current directory. Type:
      ls



Verify the installation filename

The installation is now complete. Skip to the Enable and Configure section. 

These are the steps I followed but in order to get the bin file to run I had to be on my desktop. the usr/java file already exists it just has nothing in it.

---

### Post by LaXBubbaMan on 2008-05-31
This is the stuff from the terminal


karl@karl-desktop:~$ su
Password: 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@karl-desktop:/home/karl# sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
root@karl-desktop:/home/karl# cd /usr/java
root@karl-desktop:/usr/java# chmod a+x jre-6u6-linux-i586.bin
chmod: cannot access `jre-6u6-linux-i586.bin': No such file or directory
root@karl-desktop:/usr/java# ls -l
total 0
root@karl-desktop:/usr/java# ./jre-6u6-linux-i586.bin
bash: ./jre-6u6-linux-i586.bin: No such file or directory
root@karl-desktop:/usr/java#

---

### Post by jamesstansell on 2008-05-31
> **LaXBubbaMan said:**
> Fisrt I downloaded the java bin file from java.com then I tried to follow the step that they gave me on the website.

I recommend that you use one of the Java runtimes that Ubuntu packages.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

"you should enable the Universe repository in Add/Remove programs, and install either the openjdk-6-jre package or the sun-java6-bin package"

The link above also has some additional information.  If you have any problems or questions feel free to ask.

---

### Post by LaXBubbaMan on 2008-06-01
How do I enable the universe repository?

How do I get the GPG key?

---

### Post by dracayr on 2008-06-01
are there any alteratives listed when issueing

```
sudo update-alternatives --config java
```

edit: to add the universe repository: System &#8594; Administration &#8594; Software Sources

Then check the option where it says universe in the brackets
dracayr

---

### Post by LaXBubbaMan on 2008-06-02
It is already like that. And add and remove programs still will not find sun java.

---

### Post by jamesstansell on 2008-06-02
> **LaXBubbaMan said:**
> It is already like that. And add and remove programs still will not find sun java.

In Add/Removed Applications, in order to show sun java you need to switch the Show option to "All available applications".  On the left, click the "All" category.  Then type sun-java in the search box and you should see the Sun Java 6 Runtime.

---

### Post by Xiong Chiamiov on 2008-06-02
[How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/") and [Installing Java on Ubuntu]("http://www.psychocats.net/ubuntu/java").

Also, because of the way Ubuntu uses root, instead of typing "su" to get to a root shell, you have to type either
```

sudo -s

```
or
```

sudo -i

```

---

### Post by LaXBubbaMan on 2008-06-02
Ok I was able to find and install the sun java 6 console. then when I went to install the program that I need it did this.

karl@karl-desktop:~$ cd Desktop
karl@karl-desktop:~/Desktop$ ls -a
.   Screenshot-1.png  Screenshot-3.png  Steven
..  Screenshot-2.png  Screenshot.png    thinkorswim_installer.sh
karl@karl-desktop:~/Desktop$ sudo sh thinkorswim_installer.sh
[sudo] password for karl:
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/karl/.install4j
karl@karl-desktop:~/Desktop$

---

### Post by jamesstansell on 2008-06-03
what is the output of this command? ```
java -version
```

does this one help the thinkorswim installer run? ```
rm /home/karl/.install4j
```

---

### Post by LaXBubbaMan on 2008-06-03
OK I was able to find and install the sun java 5 console. But when I try to run the shell file that I really need to install I get this following message. Attached is a screen shot.


For whatever reason it is not seeing the newest version of java that is installed.

---

### Post by jamesstansell on 2008-06-03
> **LaXBubbaMan said:**
> 
For whatever reason it is not seeing the newest version of java that is installed.

Did you run either of the commands listed above?  What were the results?

---

### Post by sabbnet on 2008-12-14
I have a somewhat different issue with thinkorswim_installer.sh and java. I have an ASUS eeepc 1000 which, I think, has Xandros (pre-installed).

Here's what I get:

/home/user/My Documents/DownloadsTemp> su
Password:
asus-409075138:/home/user/My Documents/DownloadsTemp> sh ./thinkorswim_installer.sh
testing JVM in /usr ...
Starting Installer ...
Exception in thread "main" java.lang.NoClassDefFoundError: Documents/DownloadsTemp/thinkorswim_installer/sh

& here's the version of Java:
asus-409075138:/home/user/My Documents/DownloadsTemp> java -version
java version "1.5.0_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_10-b03)
Java HotSpot(TM) Client VM (build 1.5.0_10-b03, mixed mode)

Can someone please HELP!!! I've searched everywhere (well maybe not everywhere, but tons of places), and I haven't found anyone with the same problem or a good solution for this error.

Thanks.

---

### Post by jamesstansell on 2008-12-14
The thinkorswim installer appears to not be finding one of it's classes.  My first thought is that the space in "My Documents" may be confusing it.

Can you try moving it to a different location that doesn't have a space in the path?

---


---
title: "Absolut Nubie - Help"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by mikepelton on 2008-08-17
[SIZE="3"]I attempted to load Java Runtime Environment and instructed to type su in the terminal which I have done and was then asked for the Root password. Can someone please advise what is the root password and where do you locate it to enable insertion. Thanks

---

### Post by tangibleorange on 2008-08-17
Unlike other linux systems, Ubuntu does not use a root password. Instead, it uses something called sudo. So when you want to run a command as root, simply prefix it with 'sudo'
```
sudo *command*
```
you will then be asked for YOUR password. enter it any you're away!

as a side note, you can install java from the ubuntu repositories with this command:
```
sudo apt-get install sun-java6-jre
```

---

### Post by scragar on 2008-08-17
there is no root password, it's random, instead of su use:
```
sudo -i
```
or ```
sudo su
```
and enter your own password.

---

### Post by Crafty Kisses on 2008-08-17
Sounds like your using openSUSE or Sabayon, but I'm pretty sure the root password usually is something like "admin" or "root" by default, but there is no root password with Ubuntu.

---

### Post by mikepelton on 2008-08-17
> **tangibleorange said:**
> Unlike other linux systems, Ubuntu does not use a root password. Instead, it uses something called sudo. So when you want to run a command as root, simply prefix it with 'sudo'
```
sudo *command*
```
you will then be asked for YOUR password. enter it any you're away!

as a side note, you can install java from the ubuntu repositories with this command:
```
sudo apt-get install sun-java6-jre
```

Thank you tangibleorange for your advice and typed at the terminal 
sudo apt-get install sun java6-jre and got the following response
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-jre
michael@michael-desktop:~$

In regard to your first option when you type 
sudo command - what do you replace command with?

I have downloaded the java installation at 
/home/michael/desktop/jre-6u7-linux-i586.bin

I would appreciate any further assistance you could provide for me to get this right.

Cheers

---

### Post by mikepelton on 2008-08-17
> **scragar said:**
> there is no root password, it's random, instead of su use:
```
sudo -i
```
or ```
sudo su
```
and enter your own password.

Thank you scrager for your advice I typed at the terminal
michael@michael-desktop:~$ sudo -i
Password:
root@michael-desktop:~#

What commands should I then write, as I had no luck in trying to follow these instructions from Java Installation site.

 To install the Linux (self-extracting) file

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
I have downloaded the java installation at
/home/michael/desktop/jre-6u7-linux-i586.bin

I would appreciate any further assistance you could provide for me to get this right.

Cheers

---

### Post by tangibleorange on 2008-08-17
you do not need to install the package from the java website - it is available in the ubuntu repositories:

first, make sure you have all the software sources available:

System > Administration > Software Sources

and make sure the first four boxes are ticked (main, universe, restricted, multiverse).

then go back to a terminal and type:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
```

that should do it!

---

### Post by scragar on 2008-08-17
if you don't know what your doing then I'm assuming you don't absolutly need to install java in this way, install it from repo's

```
sudo apt-get install sun-java6-jre
```

---

### Post by mikepelton on 2008-08-17
> **tangibleorange said:**
> you do not need to install the package from the java website - it is available in the ubuntu repositories:

first, make sure you have all the software sources available:

System > Administration > Software Sources

and make sure the first four boxes are ticked (main, universe, restricted, multiverse).

then go back to a terminal and type:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
```

that should do it!


I am sorry to continue being a nuisance but there is no Software Sources in System > Administration only Software Properties.

I am using Ubuntu Version 6.06 LTS so I don't know if this is a problem.

Cheers

---

### Post by hyper_ch on 2008-08-17
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by tangibleorange on 2008-08-17
Sorry didn't know that! This URL explains how to add extra repositories for 6.06. It is indeed System > Administration > Software Properties. You need to have main, restricted, universe and multiverse enabled:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
then run:
```
sudo apt-get update
sudo apt-get install sun-java5-jre sun-java5-plugin
```
that should now work!

---


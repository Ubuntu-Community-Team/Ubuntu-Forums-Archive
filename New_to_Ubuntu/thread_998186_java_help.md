---
title: "java help"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by blondielegs on 2008-11-30
okay i want to install the latest version of java. version 6 update 10 and it says go into the terminal and enter su then the root password. i finally figured out how to do that. so now what is the next command cause i cant seem to figure it out.

---

### Post by taurus on 2008-11-30
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

When you get a java licensing screen, just press Tab to highlight the <OK> at the bottom and hit Return to accept it.

---

### Post by blondielegs on 2008-11-30
thank you but now it says its the latest version and its set to manually install and that i need to remove the old ones

---

### Post by taurus on 2008-11-30
So you don't want the version in the repos; instead, you want to install it manually.  What's the name of the file that you've download and where did you save it on your computer?

---

### Post by blondielegs on 2008-11-30
im not sure which one i needed so i got both. and they are saved to the desktop. one is jre-6u10-linux-i586-rpm.bin and the other is jre-6u10-linux-i586.bin

---

### Post by blondielegs on 2008-11-30
if it helps i got it from java.com. i was getting it to play games on iwon.com.

---

### Post by taurus on 2008-11-30
You want the jre-6u10-linux-i586.bin since the other version is for rpm distros.  The best way is to move it to /opt and unpack it from there.

```
cd ~/Desktop
sudo mv jre-6u10-linux-i586.bin /opt
cd /opt
sudo ./jre-6u10-linux-i586.bin
```
Now, you need to configure your machine to use the new java version.

```
sudo update-alternatives --config java
```
You should see the new version on the list and make sure you make it is the default one.

```
java -version
```

---

### Post by blondielegs on 2008-11-30
it keeps saying bash: cd: /desktop: no such file or directory everytime i try to enter cd ~/desktop
so now what am i doing wrong?

---

### Post by blondielegs on 2008-11-30
is there anyway for you to get into my computer and show me how to do it?

---

### Post by madsmeg on 2008-11-30
Capital "D" so 

cd /home/username/Desktop

You should always ensure you have the correct case for the folder/file you are working with

---

### Post by blondielegs on 2008-11-30
still not working. and i used a capitol D. what now?

---

### Post by taurus on 2008-11-30
Don't forget the ~ in front.

```
cd  **[COLOR="Blue"]~[/COLOR]**/Desktop
```

---

### Post by blondielegs on 2008-11-30
i did that and it says bash: cd: /root/Desktop: no such file or directory
is it possible im in the wrong thing
im in [root@dani-desktop:~#

---

### Post by drubin on 2008-11-30
This might help [http://ubuntuforums.org/showthread.php?p=6095988](http://ubuntuforums.org/showthread.php?p=6095988)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by taurus on 2008-11-30
Why are you logged in as root?  When you downloaded those two files, were you logged in as root also or with your regular account?

What's the output of this command from a terminal now?

```
ls -la
```

---

### Post by gandaran on 2008-11-30
are you running a ubuntu version that is not english? cd to 'Desktop' only works for english versions!

---

### Post by blondielegs on 2008-11-30
cause the directions said to loggin with my root password and i dont know what those commands were for that you just gave me. how do i get out of root. and yes i have been in it the whole time

---

### Post by blondielegs on 2008-11-30
im pretty sure it is english i live in nevada

---

### Post by blondielegs on 2008-11-30
that ls -la thing brought up this:
total 48
drwxr-xr-x  8 root root 4096 2008-07-04 10:58 .
drwxr-xr-x 21 root root 4096 2008-11-28 13:25 ..
-rw-r--r--  1 root root 2227 2006-12-20 07:50 .bashrc
-rw-------  1 root root   16 2008-07-04 10:04 .esd_auth
drwx------  2 root root 4096 2008-11-28 13:25 .gconf
drwx------  2 root root 4096 2008-11-28 13:25 .gconfd
drwx------  3 root root 4096 2008-07-04 09:59 .gnome2
drwx------  2 root root 4096 2008-07-04 09:59 .gnome2_private
-rw-r--r--  1 root root  141 2006-12-20 07:50 .profile
-rw-------  1 root root 1024 2008-07-04 10:58 .rnd
drwx------  3 root root 4096 2008-11-18 15:27 .synaptic
drwxr-xr-x  2 root root 4096 2008-07-05 05:30 .wapi

---

### Post by blondielegs on 2008-11-30
okay im not signed into root anymore. and the cd ~/Desktop thing worked. now what

---

### Post by taurus on 2008-11-30
Now do the steps in my post #7.

---

### Post by blondielegs on 2008-11-30
only the first one then this is what i did and its response.
dani@dani-desktop:~/Desktop$ sudo mv jre-6u10-linux-i586.bin /opt
mv: cannot stat `jre-6u10-linux-i586.bin': No such file or directory

---

### Post by jgoguen on 2008-11-30
Can you give the output of "ls -l" again?

---

### Post by blondielegs on 2008-11-30
total 19148
drwxr-xr-x 3 dani dani     4096 2008-11-08 16:14 dani
-rw-r--r-- 1 dani dani 19559162 2008-11-30 11:42 jre-6u10-linux-i586-rpm.bin
-rw-r--r-- 1 dani dani      296 2008-07-20 16:13 LimeWire.desktop
-rw-r--r-- 1 dani dani     8574 2008-06-13 10:00 rhythmbox.desktop

---

### Post by gandaran on 2008-11-30
> **blondielegs said:**
> only the first one then this is what i did and its response.
dani@dani-desktop:~/Desktop$ sudo mv jre-6u10-linux-i586.bin /opt
mv: cannot stat `jre-6u10-linux-i586.bin': No such file or directory
you don't have to move it to /opt! what for?
you just run the install from desktop! just make sure you spell the correct file name

---

### Post by taurus on 2008-11-30
> **blondielegs said:**
> total 19148
drwxr-xr-x 3 dani dani     4096 2008-11-08 16:14 dani
-rw-r--r-- 1 dani dani 19559162 2008-11-30 11:42 jre-6u10-linux-i586-rpm.bin
-rw-r--r-- 1 dani dani      296 2008-07-20 16:13 LimeWire.desktop
-rw-r--r-- 1 dani dani     8574 2008-06-13 10:00 rhythmbox.desktop

I thought you said you downloaded both versions!

> 
im not sure which one i needed so i got both. and they are saved to the desktop. one is jre-6u10-linux-i586-rpm.bin and the other is jre-6u10-linux-i586.bin


You need to go back and download the **jre-6u10-linux-i586.bin** and then try those commands again.

---

### Post by blondielegs on 2008-11-30
i did i ran it again and this is what it said.
total 38784
-rw-r--r-- 1 dani dani 20102631 2008-11-30 13:10 jre-6u10-linux-i586.bin
-rw-r--r-- 1 dani dani 19559162 2008-11-30 11:42 jre-6u10-linux-i586-rpm.bin
 
i have no idea what any of this means. and i tried your instructions again and it still doesnt work.

---

### Post by blondielegs on 2008-11-30
i just did what taurus told me i have no idea what im doing. i dont understand any of these commands. i came over from windows. and still havent figured this ubuntu thing out yet.

---

### Post by taurus on 2008-11-30
> **gandaran said:**
> you don't have to move it to /opt! what for?
you just run the install from desktop! just make sure you spell the correct file name

Yes, you can just unpack it in your $HOME directory and run it from there BUT what if you have other users on your machine and you want them to use the new java version.  However, you don't want people to browse your $HOME so you set the permissions to 700 to lock them all out.  Then, they won't be able to use java version in your $HOME then.  

So, there is a right way (logical way) to do things in Unix/Linux and there is a half-@$$ way to accomplish the same task.  It's up to you which method you want to employ.  If you feel comfortable with your method, use it.

---

### Post by blondielegs on 2008-11-30
i am the only user and is it usually this hard?

---

### Post by blondielegs on 2008-11-30
okay i was in the opt command and typed in ls -la and it said this:
total 38792
drwxr-xr-x  2 root root     4096 2008-11-30 13:06 .
drwxr-xr-x 21 root root     4096 2008-11-28 13:25 ..
-rw-r--r--  1 dani dani 20102631 2008-11-30 13:10 jre-6u10-linux-i586.bin
-rw-r--r--  1 dani dani 19559162 2008-11-30 11:42 jre-6u10-linux-i586-rpm.bin
and when i typed it in in the desktop command it said this:
total 28
drwxr-xr-x  3 dani dani 4096 2008-11-30 13:11 .
drwxr-xr-x 46 dani dani 4096 2008-11-30 12:58 ..
drwxr-xr-x  3 dani dani 4096 2008-11-08 16:14 dani
-rw-r--r--  1 dani dani  296 2008-07-20 16:13 LimeWire.desktop
-rw-r--r--  1 dani dani 8574 2008-06-13 10:00 rhythmbox.desktop

---

### Post by Elfy on 2008-11-30
If you are getting errors please post what they say.

No it's not usually this hard :)

---

### Post by jgoguen on 2008-11-30
It's actually usually quite simple.  But I have to ask, is there a reason you have to install this version, or would it be OK to install from repositories?  The repository method doesn't require anything special, can be done from command-line or a graphical application, and gets automatically updated when necessary.

---

### Post by blondielegs on 2008-11-30
i did exactly what they said. and nothing is working. where am i going wrong?

---

### Post by Elfy on 2008-11-30
You need to follow taurus post #7 from here, you've moved the files so if you try again it will fail.

cd /opt
sudo ./jre-6u10-linux-i586.bin

and then do the rest

---

### Post by blondielegs on 2008-11-30
well i want to play games on iwon.com and it said i had to download the new java version 6 update 10 and i only have version 6 update 6. so it wont let me play games. but neither will anyother site. well except myspace. so can you help

---

### Post by blondielegs on 2008-11-30
it says command not found

---

### Post by blondielegs on 2008-11-30
can anyone read this? what am i doing wrong?

dani@dani-desktop:/opt$ cd ~/Desktop
dani@dani-desktop:~/Desktop$ sudo mv jre-6u10-linux-i586.bin /opt
dani@dani-desktop:~/Desktop$ cd /opt
dani@dani-desktop:/opt$ sudo ./jre-6u10-linux-i586.bin
sudo: ./jre-6u10-linux-i586.bin: command not found
dani@dani-desktop:/opt$ ls -l
total 38784
-rw-r--r-- 1 dani dani 20102631 2008-11-30 13:10 jre-6u10-linux-i586.bin
-rw-r--r-- 1 dani dani 19559162 2008-11-30 11:42 jre-6u10-linux-i586-rpm.bin
dani@dani-desktop:/opt$ 
dani@dani-desktop:/opt$ ls -la
total 38792
drwxr-xr-x  2 root root     4096 2008-11-30 13:06 .
drwxr-xr-x 21 root root     4096 2008-11-28 13:25 ..
-rw-r--r--  1 dani dani 20102631 2008-11-30 13:10 jre-6u10-linux-i586.bin
-rw-r--r--  1 dani dani 19559162 2008-11-30 11:42 jre-6u10-linux-i586-rpm.bin
dani@dani-desktop:/opt$ 
dani@dani-desktop:/opt$ 
dani@dani-desktop:/opt$ 
dani@dani-desktop:/opt$ cd ~/desktop
bash: cd: /home/dani/desktop: No such file or directory
dani@dani-desktop:/opt$ cd ~/Desktop
dani@dani-desktop:~/Desktop$ ls -la
total 28
drwxr-xr-x  3 dani dani 4096 2008-11-30 13:11 .
drwxr-xr-x 46 dani dani 4096 2008-11-30 12:58 ..
drwxr-xr-x  3 dani dani 4096 2008-11-08 16:14 dani
-rw-r--r--  1 dani dani  296 2008-07-20 16:13 LimeWire.desktop
-rw-r--r--  1 dani dani 8574 2008-06-13 10:00 rhythmbox.desktop
dani@dani-desktop:~/Desktop$ cd /opt
dani@dani-desktop:/opt$ sudo ./jre-6u10-linux-i586.bin
[sudo] password for dani: 
sudo: ./jre-6u10-linux-i586.bin: command not found
dani@dani-desktop:/opt$ sudo./jre-6u10-linux-i586.bin
bash: sudo./jre-6u10-linux-i586.bin: No such file or directory
dani@dani-desktop:/opt$ sudo ./jre-6u10-linux-i586.bin
sudo: ./jre-6u10-linux-i586.bin: command not found
dani@dani-desktop:/opt$ sudo ./jre-6u10-linux-i586.bin
sudo: ./jre-6u10-linux-i586.bin: command not found
dani@dani-desktop:/opt$ sudo ./jre-6u10-linux-i586.bin
sudo: ./jre-6u10-linux-i586.bin: command not found
dani@dani-desktop:/opt$

---

### Post by gandaran on 2008-11-30
> **taurus said:**
> Yes, you can just unpack it in your $HOME directory and run it from there BUT what if you have other users on your machine and you want them to use the new java version.  However, you don't want people to browse your $HOME so you set the permissions to 700 to lock them all out.  Then, they won't be able to use java version in your $HOME then.  

So, there is a right way (logical way) to do things in Unix/Linux and there is a half-@$$ way to accomplish the same task.  It's up to you which method you want to employ.  If you feel comfortable with your method, use it.
nope I don't agree! installing the file from desktop with **sudo** will install java in root file system (and i believe it won't be able to install anywhere else) where all users can use it and this is the correct way of installing things in linux

---

### Post by blondielegs on 2008-11-30
okay i went back to the instructions and i put this into the terminal:
chmod a+x jre-6u10-linux-i586.bin
and then i put the other command that you guys kept telling me to put in and it worked!!!
thank you guys.

---


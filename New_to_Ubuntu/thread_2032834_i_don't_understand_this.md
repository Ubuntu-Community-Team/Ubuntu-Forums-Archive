---
title: "i don't understand this"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by NightScreams on 2012-07-24
ubuntu 12.04 64bit.

i'm trying to install "bleeding edge script" basically. i'm told Open terminal, cd the folder where you downloaded the script and then make it executable

sudo chmod +x BleedingEdge12_4_8.sh

i know cd means change directory...but i don't understand what to type in.
the .sh file is in folder /home/mike/downloads/BleedingEdge12_4_19.sh

what exactly do i type in Terminal to make that thing happen? Everything i try says "no such file or directory" :(

---

### Post by nothingspecial on 2012-07-24
```
cd Downloads
```

probably.

Watch out though. It's case sensitive. [COLOR="Red"]d[/COLOR]ownloads and [COLOR="Red"]D[/COLOR]ownloads are different.

---

### Post by NightScreams on 2012-07-24
> **nothingspecial said:**
> ```
cd Downloads
```

probably.

Watch out though. It's case sensitive. [COLOR="Red"]d[/COLOR]ownloads and [COLOR="Red"]D[/COLOR]ownloads are different.

this is what i got

> mike@Linux:~$ cd Downloads
mike@Linux:~/Downloads$ sudo chmod +x BleedingEdge12_4_8.sh
[sudo] password for mike: 
chmod: cannot access `BleedingEdge12_4_8.sh': No such file or directory
mike@Linux:~/Downloads$ 


what exactly is it i'm supposed to type in? i don't even understand what i'm copying n pasting but the instructions tell me to do this:

> 1- Download the script

Download Bleeding Edge script

2- Open terminal, cd the folder where you downloaded the script and then make it executable

sudo chmod +x BleedingEdge12_4_8.sh
3- Run the script using the command:

sudo ./BleedingEdge12_4_8.sh

i already downloaded the script btw.

---

### Post by nothingspecial on 2012-07-24
Try using the tab complete feature
```

chmod +x ~/Downloads/Ble<Tab>
```

ie, type the first few letters, press the Tab key, and the terminal will finish it off for you.

---

### Post by NightScreams on 2012-07-24
> **nothingspecial said:**
> Try using the tab complete feature
```

chmod +x ~/Downloads/Ble<Tab>
```

ie, type the first few letters, press the Tab key, and the terminal will finish it off for you.

the tab thing worked, thanks for your help btw. however i must be retarded cause i still can't make the instructions happen. where do you guys learn all these weird commands and how to organize them into a functional unit? not that i actually want to learn commands, i very much hate them atm.

maybe someone needs to explain what the instructions are telling me to do. i'm just copying and pasting the codes.
this is what i did
> mike@Linux:~/Downloads$ chmod +x ~/Downloads/BleedingEdge12_4_19.sh 
mike@Linux:~/Downloads$ sudo ./BleedingEdge12_4_8.sh
sudo: ./BleedingEdge12_4_8.sh: command not found
mike@Linux:~/Downloads$ 


i assume i type sudo ./BleedingEdge12_4_8.sh after i hit enter?

---

### Post by nothingspecial on 2012-07-24
The instructions seem to have been written when Bleeding Edge was at version 12_4_8


You have version 12_4_19

11 versions later :)

Change the last 8 to 19 in everything you are trying to do :)

---

### Post by NightScreams on 2012-07-24
> **nothingspecial said:**
> The instructions seem to have been written when Bleeding Edge was at version 12_4_8


You have version 12_4_19

11 versions later :)

Change the last 8 to 19 in everything you are trying to do :)

i see. i didn't realize those numbers were a version. that worked thank you.:D
I must admit. the only reason i'm installing this is so i can use it to easily install Java. most of the directions i found for installing java were over my head. lol
So many different instructions for doing things make Linux confusing for me.

---

### Post by nothingspecial on 2012-07-24
No problem

---

### Post by Cheesemill on 2012-07-24
I don't know what guide you're using but the best way to install Java is with the following 3 commands. If you do it this way it will always stay up to date along with the rest of your system.
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by NightScreams on 2012-07-26
> **Cheesemill said:**
> **I don't know what guide you're using** but the best way to install Java is with the following 3 commands. If you do it this way it will always stay up to date along with the rest of your system.
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

lol, you serious? i went to Java's main website of course. And here is what they tell me

> Install
Java for Linux Platforms
Java for RPM based Linux Platforms
Note: The instructions below are for installing Java 7. If you are installing another version, make sure you change the version number appropriately when you type the commands at the terminal. 
Example: For Java 6 replace 7u with 6u. 

Java for Linux Platforms
Follow these instructions:
Change the permission of the file you downloaded to be executable. Type:
chmod a+x jre-7u<version>-linux-i586.tar.gz
where <version> is to be replaced by the version downloaded. 
Example: For jre-7u3, the command is 
chmod a+x jre-7u3-linux-i586.tar.gz
Verify that you have permission to execute the file. Type:
ls -l
Change to the directory in which you want to install. Type:
cd <directory path name>
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/

Note about root access: To install Java in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the Java in your home directory or a subdirectory for which you have write permissions.
Unpack the tarball and install Java Type:
% tar zxvf jre-7u<version>-linux-i586.tar.gz

The license agreement is displayed. Review the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.

Java is installed into its own directory. In this example, it is installed in the /usr/java/jre1.7.0_<version> directory. When the installation has completed, you will see the word Done.
 

Verify that the jre1.7.0_<version> sub-directory is listed under the current directory. Type:
ls


Now maybe you understand why Linux is hard for some of us. Its pretty sad when the developer of such apps gives us super hard and long instructions. Besides, command lines?......its 2012 for crying out loud. Can't the linux community offer everything most users need without touching the Terminal?:mad:

---

### Post by Cheesemill on 2012-07-27
> **NightScreams said:**
> lol, you serious? i went to Java's main website of course. And here is what they tell me



Now maybe you understand why Linux is hard for some of us. Its pretty sad when the developer of such apps gives us super hard and long instructions. Besides, command lines?......its 2012 for crying out loud. Can't the linux community offer everything most users need without touching the Terminal?:mad:
This isn't Ubuntu's fault, it's Oracle's.

It use to be easy to install Sun Java from the Software Centre, no terminal needed. But when Oracle bought out Sun they changed the Java licensing terms in such a way that it had to be removed from the Software Centre otherwise Canonical would be breaking the law.

Because of the complexity of the new official way of installing Java (the instructions you quoted) some nice developers have written a script that does all of this work for you. The instructions that I gave you will install this script and run it for you, whilst also ensuring that every time there is a Java update it will be automatically downloaded and installed.

---

### Post by mastablasta on 2012-07-27
> **NightScreams said:**
>  
Now maybe you understand why Linux is hard for some of us. Its pretty sad when the developer of such apps gives us super hard and long instructions. Besides, command lines?......its 2012 for crying out loud. Can't the linux community offer everything most users need without touching the Terminal?:mad:
 
oh sure it can. but think of this. command line works wheather you use Ubuntu, Kubuntu, Xubuntu., Lubunut, Debian, Chrunchbang... They all use different GUI (and desktop environments) yet this command works in all of them. otherwise they would have to write instructions for dozzen or so different user interfaces. instead they just give two command lines you can copy and paste into terminal.
 
for example the thing you were trying to do... you would open file browser, right click on the file and select propperties. then you would in proppertie set the file to executable. then you would double click the file in the file manager. a windows would pop up asking you to enter your password. once you do that the script would run.

---

### Post by 3rdalbum on 2012-07-27
Ubuntu is generally easier than what it seems - there's always a hard way and an easy way and because the hard way is the same on every distribution, that's what gets publicised.

Always look for the easier way.

Speaking of easier ways, in the start of your question you were trying to type the filename into the terminal, and then someone suggested using the Tab key to autocomplete. There's an even easier way - just drag the file into the terminal window to fill its whole path in.

Or find a PPA (repository) for the software and then it will be installable using Ubuntu Software Center.

---

### Post by NightScreams on 2012-07-27
> **Cheesemill said:**
> This isn't Ubuntu's fault, it's Oracle's.

It use to be easy to install Sun Java from the Software Centre, no terminal needed. But when Oracle bought out Sun they changed the Java licensing terms in such a way that it had to be removed from the Software Centre otherwise Canonical would be breaking the law.

Because of the complexity of the new official way of installing Java (the instructions you quoted) some nice developers have written a script that does all of this work for you. The instructions that I gave you will install this script and run it for you, whilst also ensuring that every time there is a Java update it will be automatically downloaded and installed.

Oracle is not alone. I'm finding more and more of these so called "not ubuntu's fault" applications.
The problem is, its in relation to using Ubuntu. So to the user, the blame makes no difference.

Obvious to me i would find very strong defenders of Linux in forums like this one, but you can't really deny the reality a user faces when choosing to use it. I like it overall, i just hate the mish mash of info. **Its not a good way to learn....i can't learn anything by copying and pasting tons of random data i'm finding in obscure places.** So what am i gonna do if i want to reinstall/format to another distro? I can't just click on a simple "app history" like i do on iOS for Ipad and get all my apps in one shot. But why should that not be possible?

> **3rdalbum said:**
> 

Speaking of easier ways, in the start of your question you were trying to type the filename into the terminal, and then someone suggested using the Tab key to autocomplete. There's an even easier way - just drag the file into the terminal window to fill its whole path in.

Or find a PPA (repository) for the software and then it will be installable using Ubuntu Software Center.

thats a very handy tip. i'll try to remember that. But i still say the Terminal is not something your average soccer mom cares to deal with.

> **mastablasta said:**
> oh sure it can. but think of this. command line works wheather you use Ubuntu, Kubuntu, Xubuntu., Lubunut, Debian, Chrunchbang... They all use different GUI (and desktop environments) yet this command works in all of them. otherwise they would have to write instructions for dozzen or so different user interfaces. instead they just give two command lines you can copy and paste into terminal.
 
for example the thing you were trying to do... you would open file browser, right click on the file and select propperties. then you would in proppertie set the file to executable. then you would double click the file in the file manager. a windows would pop up asking you to enter your password. once you do that the script would run.

i was thinking of a more robust "App store". The software center is a great start, but there seems to be lots of things i need that i can't find there. But Googling around is a time consuming process, especially when an app requires you to compile it..etc.
like JRipper. When you need something like good AAC codec conversion and you find yourself spending hours to obtain it, well don't blame those like me for being quite frustrated.

---

### Post by Cheesemill on 2012-07-27
> **NightScreams said:**
> i was thinking of a more robust "App store". The software center is a great start, but there seems to be lots of things i need that i can't find there. But Googling around is a time consuming process, especially when an app requires you to compile it..etc.
like JRipper. When you need something like good AAC codec conversion and you find yourself spending hours to obtain it, well don't blame those like me for being quite frustrated.

That's exactly what PPA's do, it's a way of adding more applications to the Software Centre. For the Java commands I posted above you could have instead done it all from the Software Centre like so:

1 - Open the Software Centre

2 - Go to Edit > Software Sources > Other Software

3 - Click on Add and enter the line that corresponds to the PPA you wish to add, in this case:
```
deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
```
(This line can be found on the PPA web page).

4 - Search the Software Centre for 'java' and install the package oracle-java7-installer

You can see from what I have just typed why people prefer to give terminal commands as answers, they are easier and quicker to type. Also what if you were using Lubuntu or Kubuntu which have their own different versions of the Software Centre? I would have to have modified what I had written above whereas the terminal commands would be the same no matter what you were using.

If you ever need an application that isn't included in the Software Centre then a quick google for 'appname ppa' will usually get you what you need to get it added.

---

### Post by Kelvari on 2012-07-27
> **NightScreams said:**
> **Its not a good way to learn....i can't learn anything by copying and pasting tons of random data i'm finding in obscure places.**
I'd like to recommend the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/index_main.html")

> **NightScreams said:**
> So what am i gonna do if i want to reinstall/format to another distro? I can't just click on a simple "app history" like i do on iOS for Ipad and get all my apps in one shot. But why should that not be possible?
Actually, it is. In the Ubuntu Software Center, you can go into the File menu and choose either "Reinstall Previous Purchases..." for paid-for software, or "Sync Between Computers..." if you have Ubuntu installed on two or more computers.

---

### Post by NightScreams on 2012-07-28
> **Cheesemill said:**
> That's exactly what PPA's do, it's a way of adding more applications to the Software Centre. For the Java commands I posted above you could have instead done it all from the Software Centre like so:

1 - Open the Software Centre

2 - Go to Edit > Software Sources > Other Software

3 - Click on Add and enter the line that corresponds to the PPA you wish to add, in this case:
```
deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
```
(This line can be found on the PPA web page).

4 - Search the Software Centre for 'java' and install the package oracle-java7-installer

You can see from what I have just typed why people prefer to give terminal commands as answers, they are easier and quicker to type. Also what if you were using Lubuntu or Kubuntu which have their own different versions of the Software Centre? I would have to have modified what I had written above whereas the terminal commands would be the same no matter what you were using.

If you ever need an application that isn't included in the Software Centre then a quick google for 'appname ppa' will usually get you what you need to get it added.

ppa. i'll remember that thank you. It seems theres tons of handy tricks that i don't see when googling for things to do after installing Linux, i just wish it was more "in my face" so to speak. Is there a reason this "ppa" is not a simple default option i can just click on from softare center? Again, the problem i typically find when searching anything for Linux is too much variety of technical information, much of it seems to revolve around command lines that i will never beable to remember.
I like stuff i can easily remember so i can do it again if i ever say upgrade to Ubuntu 13.04 in the future or some other reason.

but thanks to your mentioning of "ppa" i came across this handy site providing me updated apps.
[http://netgator.blogspot.com/2010/11/10-ppa-links-for-ubuntu-linux.html](http://netgator.blogspot.com/2010/11/10-ppa-links-for-ubuntu-linux.html)

---

### Post by kd5mkv on 2012-07-30
The java install looks pretty cool, I have been manually installing java to keep it recent. I understand it takes time for java and other programs to come down from repositories.

---

### Post by cottfcfan on 2012-07-31
NightScreams...
I have been using linux for 4 years, and still find handy tips & ideas that I haven't seen before.
What I would recommend is starting a document in LibreOffice called linux tips or something, and saving all the useful tips you find, because I can guarantee if you come to reinstall a newer version in the future, you'll never remember everything or be able to find it again.
Keep a note of all the ppas you use, programs you install, commands you use etc..
I have just condensed mine to 6 pages, but they make life so much easier in the long run.

---


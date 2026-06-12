---
title: "How to install Netbeans 5.5 on Fiesty manually for newbies by a newbie"
date: 2007-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Tsega on 2007-07-28
Hello people! If you are like me an X-Windows user with no connection to the internet from your Ubuntu machine and would like to install anything the old fashioned way, I suggest you read this [COLOR="Blue"][http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")[/COLOR]

Now I'm going to show you how you can install **Netbeans 5.5** on Fiesty manually. 

**1.** For Netbeans to work you would need the Java SDK. By default Ubuntu has its own version of java installed with it, however, netbeans requires that you have the SUN version of the SDK. So you need to get that first and install it. 
You can download it here: [COLOR="Blue"][http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp") [/COLOR]
Just select any one of the SDK's. You can even get with Netbeans 5.5.1 bundled together with it but if you have  Netbeans already just select the first one, **JDK 6 Update 2**.(The version numbers may be different depending on when you visit the site, because this page provides only the latest versions of the SDK and Netbeans) 

**2.** After acquiring your copy of  the SDK. You would need to install it. Here's how you do it.
    (I am assuming that the file resides in your **"home"** folder)
**    2.1** Right click on the file, and select properties. In the properties dialog go to Permissions tab and select the "Allow executing file as a program" option. Close the dialog. 
**    2.2 **Simply double click on the file and a dialog will appear, click on the "Run in Terminal" button. The terminal fires up and the extraction of the file will begin. 
**    2.3** When the installation finishes you will have a jdk-x.x folder (your newly installed jdk)
**    2.4** [COLOR="Blue"]*(Optional but I highly recommend it)*[/COLOR] you need to copy this folder in a very convenient place say /usr/lib/jvm/. You can see in the folder /usr/lib/ that there is no folder named jvm, so you need  to create that too. Here how you do it; right click in your "home" folder, and create a new folder name jvm. Cut/Paste the jdk-x.x folder in to this folder. Fire up the terminal Applications->Accessories->Terminal and type in the following code 
```
sudo cp /home/"home name"/jvm -R /usr/lib/ 
```
in the above code the "home name" is usually your user name for example my user name is "tsega" so I should write the command as 
```
sudo cp /home/tsega/jvm -R /usr/lib/ 
```
What this command does it copies the jvm folder along with its contents (that's what the -R option is for, i.e "copy recursively") to the /usr/lib/ folder. 
 
**3.** Now here's the important part.
When every an application is installed and the it leaves behind a symlink file in you home directory so it can be easily accessed. (i don't know the details about it). However you need to create this symlink file for you java sdk/jvm to be detected by application that require it to function. Application such as netbeans. Now here what you do. In the menu bar of your home folder go to "View" and drop down list select the "view hidden files" option and you will see a host of files starting with the '.xxx" these I believe are the symlink files. Find the file "**.bashrc**" as well as "**.bashrc~**" (I know this one is just a temporary file but that's how it worked for me.) open them by double clicking put in the following code at the end of the file.
```
#Java
export JAVA_HOME="your choice of directory"
export PATH=$PATH:$JAVA_HOME/bin
```
now here what you are doing in the second line **export JAVA_HOME="you choice"/jdk-x.x** is that you are telling the system where you jvm is located. So if you have followed me through the whole thing you have put your jvm in "/usr/lib/jvm/jdk-x.x" (keep in mind that the -x.x is the just a place holder for your version numbers, i.e jdk-1.6.1_u1 might be your folder name.) so instead of "your choice of directory" put something like this 
```

#Java
export JAVA_HOME=/usr/lib/jvm/jdk-1.6.1_u1 
export PATH=$PATH:$JAVA_HOME/bin
```

Save these files and close them.

So that's about it concerning your jvm. Now let us install Netbeans shall we!

**4.** As usual I assume you have a copy of the linux version of netbeans in your home folder if not that is if you don't have a copy of netbeans you can download a copy here. [COLOR="Blue"][http://www.netbeans.info/downloads/all.php?b_id=3095](http://www.netbeans.info/downloads/all.php?b_id=3095)[/COLOR]
After that what we need to is right click on the netbeans file and go to properties in the properties dialog that comes up select the permissions tab and select the "Allow executing file as a program" option and close dialog. 
**5.** Open up your terminal in the main menu bar of the Ubuntu desktop go to Applications->Accessories->Terminal then write the following code.
```
sudo ./"the name of your netbeans file" 
```
"the name of your netbeans file" would be something like this netbeans-5.5-linux.bin so you should type in
```
sudo ./netbeans-5.5-linux.bin 
```
 Now if you have done everything the right way, the installation will start with detection of the jvm, and since we have a symlinked our jvm installation form our home folder, the installation will find it and will continue to install using its own installation wizard that would be fairly intuitive. 
After installing netbeans you can also install the other components such as the mobility pack and the profiler etc.. the same way.

I hoped this was more helpful than painful if you have any question I would be more than willing to answer them, i.e if I can. :) CIAO

Tsega

---


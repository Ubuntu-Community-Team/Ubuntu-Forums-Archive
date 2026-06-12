---
title: "java compilation"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by dharmes on 2013-03-01
hey friends,
I am new to java,
can anyone help me with that,
i know how to write java programs, in windows JDk,
but not in Ubuntu,
can someone please tell me the whole procedure, from writing to compiling to running the program?
thnx :)

---

### Post by slickymaster on 2013-03-01
You are unlikely to encounter much differences between Windows and Linux if you use the language right.

Java is supposed to be  totally portable, but the truth is that is not quite totally portable. There are difference between Java programming in Linux and Windows. At least four differences cross my mind:
[LIST]
[*]Different path separator, ; on DOS and Windows, : on Linux Unix and Mac.
[*]Different line end, 0xd 0xa (\r\n) on DOS and Windows, 0xa (\n) on Linux, not sure on Mac.
[*]Different file separator \ on DOS and Windows, / on Mac Unix and Linux
[*]Different end-of-file, something with ctrl-Z on DOS and Windows, something with ctrl-D on Mac Unix and Linux.
[/LIST]

---

### Post by dharmes on 2013-03-01
i mean  to ask that, what do i need to install in Ubuntu so as to run my java program, and also how to compile them and run them..

---

### Post by slickymaster on 2013-03-04
Before installing Java, check first your operating system architecture to see if it's 32-bit or 64-bit. To do this open up a terminal and enter the following command:
```
file /sbin/init
```
The bit version of your operating system architecture will display whether it is 32-bit or 64-bit.
Then, download the [Oracle Java JDK for Linux]("http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html"). Make sure you select the correct compressed binaries for your system architecture 32-bit or 64-bit (which end in tar.gz). You mustn't forget that 64-bit Java binaries do not work on 32-bit Linux operating systems, you will receive multiple system error messages, if you attempt to install 64-bit Java on 32-bit Ubuntu.
Copy the Java binaries into the **/usr/local/java** directory. In most cases, they are downloaded to: **/home/"your_user_name"/Downloads**.
Then, to install them, and assuming you're running on a 32-bit platform, run the following commands, one at a time:
```
cd /home/"your_user_name"/Downloads
sudo -s cp -r jdk-7u15-linux-i586.tar.gz /usr/local/java
cd /usr/local/java
```
After that, run the following command on the downloaded Oracle Java tar.gz files:
```
sudo -s chmod a+x jdk-7u15-linux-i586.tar.gz
```
Unpack the compressed binaries, in the directory **/usr/local/java**
```
sudo -s tar xvzf jdk-7u15-linux-i586.tar.gz
```
Edit your system path file **/etc/profile** and add the following system variables to your system path. Use geany, nano, gedit or any other text editor as root, to open up **/etc/profile**.
```
gksudo geany /etc/profile
```
Once the file is open, scroll down to the end of it and add the following lines to the end of your **/etc/profile file**:
```
JAVA_HOME=/usr/local/java/jdk1.7.0_15
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
```
Save the **/etc/profile** file and exit.
Now, you'll have to let your system know where your Java JDK/JRE is located:
```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.7.0_15/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_15/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.7.0_15/bin/javaws" 1
```
Define your system's default Java:
```
sudo update-alternatives --set java /usr/local/java/jdk1.7.0_15/bin/java
sudo update-alternatives --set javac /usr/local/java/jdk1.7.0_15/bin/javac
sudo update-alternatives --set javaws /usr/local/java/jdk1.7.0_15/bin/javaws
```
Finally, reload your system wide path **/etc/profile** by typing the following command:
```
. /etc/profile
```
Note that just after the reboot of your system **/etc/profile** will reload.

You compile and run your java programs at a terminal window, just like you would at a command-prompt window in Windows. The commands are exactly the same.

---

### Post by vamp774 on 2013-03-04
Or just use OpenJDK that's what I use.  

sudo apt-get install openjdk-7-jdk

---

### Post by vamp774 on 2013-03-04
and compile with javac <file>
and run with java <file>

---

### Post by veroslav on 2013-03-05
> **slickymaster said:**
> You are unlikely to encounter much differences between Windows and Linux if you use the language right.

Java is supposed to be  totally portable, but the truth is that is not quite totally portable. There are difference between Java programming in Linux and Windows. At least four differences cross my mind:
[LIST]
[*]Different path separator, ; on DOS and Windows, : on Linux Unix and Mac. 
[*]Different line end, 0xd 0xa (\r\n) on DOS and Windows, 0xa (\n) on Linux, not sure on Mac. 
[*]Different file separator \ on DOS and Windows, / on Mac Unix and Linux 
[*]Different end-of-file, something with ctrl-Z on DOS and Windows, something with ctrl-D on Mac Unix and Linux. 
[/LIST]


It is quite portable regarding the above as well, if one uses the appropriate system calls, such as System.lineSeparator(), File.pathSeparator and so on. You shouldn't need to worry about such things as those above.

---


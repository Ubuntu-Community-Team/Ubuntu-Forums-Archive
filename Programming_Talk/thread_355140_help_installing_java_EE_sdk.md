---
title: "help installing java EE sdk"
date: 2007-02-06
forum: Programming Talk
---

### Post by onewaytrip on 2007-02-06
i have been using windows since i can remember and have java EE sdk 5 installed on my windows machine. since i enjoy the java language so much and im making the tranistion from windows to ubuntu can any of ya help me get java up and running? i wanna stick to the offical java language from sun, so im not looking to installed the opensoure version of java. also in windows i had to set up my paths so i could run my program off the commad prompt and would like to have the same set up with the terminal in ubuntu.

thanks in advance.

---

### Post by phossal on 2007-02-06
If you're familiar with installing the SDK in Windows, why haven't you simply downloaded the J2EE SDK from SUN? Directions for installing it are at the SUN site.

---

### Post by onewaytrip on 2007-02-06
i figure they was another way of installing using the "apt-get" feature. im just looking for clarity before i do anything because im still new to the os.

---

### Post by lloyd mcclendon on 2007-02-07
there is but it rarely works.  if you search here, you'll see 400000 people having problems getting it to work.  debian packages aren't really necessary for java based software anyway, just download & run works everytime.

download the sdk (linux, .bin) from suns website.  type chmod 755 <filename>.bin to give yourself executable permissions on it, and then type ./<filename>.bin to run it.  after that, you'll have a new directory there, move that to either /usr/local or /opt (wherever really, i just keep it in /home/lloyd/apps/jdk).  then to add it to your path, i'm pretty sure you can just type  echo 'PATH=${PATH}:/that/directory/jdk/bin/directory' >> ~/.bashrc  ... close the terminal & open another one for that to take affect.  hope that helps

---

### Post by onewaytrip on 2007-02-07
thanks ill try it out and let you know what happens.

---

### Post by isionous on 2007-02-11
ok, so we add the new jdk folder to our path...but that means that there's multiple java and javac executables in our path.  So, how do we make sure that using javac will use the newer javac? 

Update:  I tried adding /usr/share/jdk1.6.0/bin/ to the end of my PATH variable and it still uses the old javac like I feared.

---

### Post by phossal on 2007-02-11
**Which Java?**
If you have multiple executables of the same name available in the list of paths contained in your $PATH environment variable, [COLOR="SlateGray"]your system will use the one it finds *first*[/COLOR]. 

**Method 1: Set $PATH and $JAVA_HOME**
I have multiple Java's installed on my system (JDK 2, JDK 5, JDK 6), but I configure my $PATH environment variable in my ~/.bashrc file so that I can choose the one I want. 

Here is an example:
```
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) -----------------
export JAVA_HOME='/usr/lib/Java6'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:'/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/bin:/sbin'
```
Every time I open a terminal it sets my path to exactly the same thing. If I change the value of the *export JAVA_HOME* line, and reopen a terminal, the new java is used.


**Method 2: update-alternatives**
The package managers are supposed to configure your system to give you the ability of choosing which java, too. The system it uses is *update-alternatives*. If you had multiple java executables, you should be able to choose the one you want to use by using the *sudo update-alternatives --config java* option. Whether or not you install from a package, it's possible to include your java among the choices available.

---

### Post by cuco2772 on 2007-12-14
Hey, phossal, I tried doing that, ie, going into my .bachrc and changing the path so that $JAVA_HOME came first but it screwed up my shell so
that it couldn't find any programs !  No ls, no vim.  I thought I was screwed. Luckily I had more than one terminal open and was able to edit my .bashrc from another terminal back to the way it was.

I had set my new $JAVA_HOME to /opt/SDK/jdk which was where the jre was located of my new Java install. 
I had downloaded the new Java ee5 SDK with jdk for linuk from this page:

[http://java.sun.com/javaee/downloads/?intcmp=1282](http://java.sun.com/javaee/downloads/?intcmp=1282)

I'm pretty sure this comes with a jvm. (Everything installed into a SDK
folder). update-alternatives didnt show the new Java.

My other Java, that I installed a while back using apt-get (Java 1.5 se)
was installed into my /usr/lib directory. All my shell programs are off
my /usr directory, as far as I know. I'm wondering if I had installed the new Java into /usr/lib instead, if that would have made a difference.
Then maybe I would have been able to put $JAVA_HOME first
without such disastrous consequences. Right now my $JAVA_HOME
is last in my path. If I were to move my directory over to /usr,
should I then set my $JAVA_HOME to the bin directory of my new
install, ie, as in /usr/SDK/jdk/jre/bin ? Thanks

---

### Post by jagrock on 2011-11-24
> **phossal said:**
> **Which Java?**
If you have multiple executables of the same name available in the list of paths contained in your $PATH environment variable, [COLOR=SlateGray]your system will use the one it finds *first*[/COLOR]. 

**Method 1: Set $PATH and $JAVA_HOME**
I have multiple Java's installed on my system (JDK 2, JDK 5, JDK 6), but I configure my $PATH environment variable in my ~/.bashrc file so that I can choose the one I want. 

Here is an example:
```
# ~~~~~~~~~~~~~~~~~ JAVA (JDK,JRE) -----------------
export JAVA_HOME='/usr/lib/Java6'
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:'/usr/local/sbin:/usr/local/bin:/usr/bin:/usr/sbin:/bin:/sbin'
```Every time I open a terminal it sets my path to exactly the same thing. If I change the value of the *export JAVA_HOME* line, and reopen a terminal, the new java is used.


Thank you very much!

---


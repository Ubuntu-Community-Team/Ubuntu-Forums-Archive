---
title: "Basic questions regarding file storage, symlinks and update alternatives"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by amartin903 on 2013-07-15
Hi folks,

When you don't have enough information to do something it can be very tough knowing where to start. However, if you have *too* much information it can be just as confusing and that's where I'm finding myself.

I'm doing a university project where I am downloading a mass amount of tweets and analysing them using the Ubuntu operating system, along with Apache Hadoop, Flume, Oozie and Hive. I've gotten as far as downloading the tweets although have yet to study enough about sentimentality analysis to analyse them. I have to do a write up of everything I'm doing in a dissertation, right down to the finest detail and therefore I had a couple of important questions.

Firstly, I've read on multiple sites multiple different interpretations of where a user should store their folders: /usr/local, /opt, /usr/bin, /home/[user name]. Is there a good guide for storage locations? If I want something like Maven or Java to be accessible to EVERY user, where should I store it? Similarly, if I want something like Hadoop and Flume to be accessible to a single user, where should I store it? 

Secondly, in the various guides I've followed so far, when installing Java I've used the -update alternatives to set the location of Java like this:

        *sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0/bin/java" 1*
        *sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0/bin/javac" 1*
        [I]sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0/bin/javaws" 1
[/I]        *sudo chmod a+x /usr/bin/java *
        *sudo chmod a+x /usr/bin/javac *
        s*udo chmod a+x /usr/bin/javaws*
        [I]sudo chown -R root:root /usr/lib/jvm/jdk1.7.0

[/I]From my understanding this installs the java file at location jdk1.7.0 into the /usr/bin/java folder with the name java. As the /usr/bin/ is in the system PATH this means it can be accessed directly from the terminal like so: java -version. Additionally, it gives system wide read and write privileges to all users with the owner set as root. 
When installing Maven however, the guide I used created a sym link like so:
        [I]sudo ln &#8211;s /usr/local/apache-maven/bin/mvn /usr/bin/mvn
[/I]
From my understanding this added the location apache-maven/bin/mvn to /usr/bin/mvn and as it's on the system PATH it can be accessed directly from the terminal.

What is the difference between these? Can update-alternatives only be used on certain programs? Is it preferable to use update-alternatives over symlinks or the other way around? What's the main difference?

---

### Post by Cheesehead on 2013-07-15
> **amartin903 said:**
> Firstly, I've read on multiple sites multiple different interpretations of where a user should store their folders: /usr/local, /opt, /usr/bin, /home/[user name]. Is there a good guide for storage locations? If I want something like Maven or Java to be accessible to EVERY user, where should I store it? Similarly, if I want something like Hadoop and Flume to be accessible to a single user, where should I store it?

See [http://wiki.debian.org/FilesystemHierarchyStandard](http://wiki.debian.org/FilesystemHierarchyStandard)

/usr/local/ : Tertiary hierarchy for local data installed by the system administrator
    /usr/local/bin : locally compiled binaries, local shell script, etc.
    /usr/local/src : Source code (place where to extract and build non debian'ized stuffs) 

/opt/
    Add-on application software packages
    Pre-compiled, non ".deb" binary distribution (tar'ed..) goes here. 

/usr/
    Secondary hierarchy for shareable, read-only data (formerly from UNIX source repository, now from UNIX system resources)
    (files that are not-required to boot or rescue the system) 
/usr/bin/ : Same as for top-level hierarchy 

/home/
    Users' home directories 


In your example, I would put the applications in /usr/local/projectname, the raw data (read-only) in /usr/local/projectname_data, and each user's working files in /home/username/projectname.
Your preferences may vary, and the system can be configured to whatever you prefer.



> **amartin903 said:**
> What is the difference between [update-alternatives and symlink]? Can update-alternatives only be used on certain programs? Is it preferable to use update-alternatives over symlinks or the other way around? What's the main difference?

update-alternatives is a rather specialized front end that does more than a normal symlink, and is also more complicated. See man update-alternatives.
If there are no alternatives to choose from, using an ordinary symlink is quite acceptable, easy to do, and easy to remove.

---


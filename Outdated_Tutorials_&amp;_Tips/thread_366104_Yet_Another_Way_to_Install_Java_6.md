---
title: "Yet Another Way to Install Java 6"
date: 2007-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by jonathan_c on 2007-02-20
There are so many guides to install Java 6 manually on the Ubuntu forums that I kinda got lost between them all (but I did get Java 6 working). I'm writing this guide in order to make it simple to install and easy to understand (through the shell script).

**Note: There are 2 ways to install java6 nowadays b/c java6 has been added to the repositories (multiverse)**

The following method is if you have the multiverse repository enabled/added to your /etc/apt/sources.list (I won't go covering how to do that here)

To install:
```
sudo apt-get update
# To install the mozilla plugin remove the # on the next line
sudo apt-get install sun-java6-jdk #sun-java6-plugin
update-java-alternatives --list
# The line above should produce output somewhat similar to:
# java-6-sun 63 /usr/lib/jvm/java-6-sun
# Add the first part of the line above to the end of the next line
sudo update-java-alternatives --set java-6-sun

```

Now if you want to change java versions just do:
```
update-java-alternatives --list
sudo update-java-alternatives --set <one of the java versions>
```

----------------------------------------------------------------------------------------------------------------------------

The following method shows how to install java 6 manually (in case you don't want multiverse repo. enabled for security reasons or if you just want to learn how to do it)

1. Download the Java 6 SDK (Make sure you download the "Linux self-extracting file") from [http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp")
2. After it has finished downloading you will have a file called jdk-6-linux-i586.bin
3. Run the following in the directory that the file is located in (Change any variables as you see fit)
```
JDKFILE=jdk-6-linux-i586.bin
JDKFOLDER=jdk1.6.0
JDKPATH=/opt

chmod +x $JDKFILE
sh $JDKFILE
sudo mv $JDKFOLDER $JDKPATH

# Uncomment the following line to have Mozilla browsers (i.e. Firefox) load the Java 6 plugin
# ln -s $JDKPATH/$JDKFOLDER/jre/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins

echo "export JAVA_HOME=$JDKPATH/$JDKFOLDER" >> ~/.bashrc
echo "PATH=\$JAVA_HOME/bin:\$JAVA_HOME/jre/bin:\$PATH" >> ~/.bashrc

source ~/.bashrc
```

Now you can test to see if java 6 is installed by running: `java -version` and `javac -version`
This should print out something similar to:
```
joncfoo@A3200:~$ java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

joncfoo@A3200:~$ javac -version
javac 1.6.0
```


Now if you have other versions of Java installed and want to use them, the easiest way to do is would be to change the JAVA_HOME variable by doing:
```
export JAVA_HOME=/another/java/directory
```
After you have done this, just launch whatever application(s) you need under that version of Java


I hope this is straightforward and to the point. If not feel free to ask me any questions.

---

### Post by mr.blacke on 2007-02-22
Simply understandable! too comprehensive guide. Thank you!

---

### Post by glennric on 2007-02-22
Isn't it easier to add the edgy-backports repository to your sources.list and install the sun-java6 packages?

---

### Post by jonathan_c on 2007-02-22
I did an `apt-cache search java6` right after I saw your post. You're right, it is in the repository. It wasn't there 2 days ago though :)

Thanks!

---

### Post by phossal on 2007-02-22
Installing Java 6 from the *backports* is an unworkable method if you need multiple instances, or need to capture the latest updates from SUN as soon as possible. Besides, the package is prepared by a third party using the .bin file from SUN anyway. You suffer any security breaches inherent in the .bin file *plus* any included in the packaging script - thus explains its placement in *backports.*

In addition, using the package isn't an option if you need an older version. The backports option is *easy*, but it isn't easier than just installing the .bin file by yourself. Food for thought.

---

### Post by the.phantom on 2007-02-22
> sudo apt-get update
# To install the mozilla plugin remove the # on the next line
sudo apt-get install sun-java6-jdk #sun-java6-plugin
update-java-alternatives --list
sudo update-java-alternatives --set <java version from the command above>

ok the original dummy here
i would just enter this in the terminal


sudo apt-get update
# To install the mozilla plugin remove the # on the next line
sudo apt-get install sun-java6-jdk sun-java6-plugin
update-java-alternatives --list
sudo update-java-alternatives --set sun-java6-jdk

that is after making the changes you show in the comments, and think i did it right?

i have a older sun java on here and i have read about not uninstalling or overwriting the old with a new???

thanks for any help confimrming that is the right command
i have the older version working and don't want to blow out java as i need it

---

### Post by jonathan_c on 2007-02-23
the.phantom,
    If you used apt-get to install the new java6 then it **shouldn't** overwrite any other java versions. All the older versions should still be installed along-side the new version.

On my machine `update-java-alternatives --list` produces:
```
joncfoo@A3200:~$ update-java-alternatives --list
java-6-sun 63 /usr/lib/jvm/java-6-sun
```
Running `sudo update-java-alternatives --set java-6-sun` would be the correct command for me to run.

If by chance the output on your `update-java-alternatives --list` shows "sun-java6-jdk <some number> <path to sun-java6-jdk>" then it is perfectly ok for you to run `sudo update-java-alternatives --set sun-java6-jdk`

---

### Post by neptune on 2007-02-27
Wow this is awesome! Works like a charm.

Thanks!

---

### Post by mmceldowney on 2008-02-11
If you have or prefer, as I do, to manually install the latest from Sun and you have followed the manual installation instructions above, then you can update your system alternatives as such:

(I'm assuming you've moved the jdk directory to /opt)

```
update-alternatives --install java java /opt/jdk1.6.0_04/bin/ 1
update-alternatives --config java
```

Then select the number for your newly installed jdk.

Mike

---

### Post by mymessiah on 2009-09-12
Thank you so much OP I have been trying to download java for 2 days now nothing worked except your help. I am new to linux this saved my life.

---

### Post by spliceroverlord on 2010-07-24
Hi, when I execute the command line:
sudo apt-get install sun-java6-jdk #sun-java6-plugin
I receive an error message at the end of the process list, stating:
[B]Errors were encountered while processing:
 sun-j2re1.6[/B]
E: Sub-process /usr/bin/dpkg returned an error code (1)
These are the last three lines of the process, then, when I try to run the [B]"sudo update-java-alternatives --set java-6-sun
"[/B] command in the list, the whole process list(4 lines) is just errors:
[B]update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: no alternatives for mozilla-javaplugin.so.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.[/B]
Although the terminal displays error messages, it still allows me to carry on with the commands following, and displays:

[B]java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)
oliver@Oliver:~$ javac -version
javac 1.6.0_20[/B]
when I try to run the java version command, and then, for the javac version, it states:
**javac 1.6.0_20**
It would appear that Java installed correctly, but when I go into firefox, I tried to run a java game, and it wouldn't install, I also attempted installing the iced tea plugin when I realised that java wasn't working, but that displayed exactly the same error message that I first noted, Is there something wrong with my system, or am I juat not installing correctly?
Cheers.

---

### Post by Pete B on 2011-03-06
I want to install jdk on Ubuntu 10.10 Pretty much a newbie to Linux and was hoping to find it in the Software Centre - but no deal.

Are these suggestions still relevant?

Cheers,

Pete

---


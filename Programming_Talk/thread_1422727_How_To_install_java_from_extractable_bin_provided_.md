---
title: "How To: install java from extractable bin provided by sun"
date: 2010-03-05
forum: Programming Talk
---

### Post by kotoro on 2010-03-05
This is not an explanation of how to use rpm, but rather a somewhat manual option for installing the newest jdk or jre (if you don't want to wait for the ubuntu crew to put it on their repository.)

**_edit:** One reason you might want to do this is if, like me, you tried various other forum or blog posts attempting to explain how to use alien or some other tool to produce a debian-friendly installer package, but what you wound up getting was very faulty and resulted in incomplete installs with error messages. 

**Step 1: ***Install latest sun-java available from Ubuntu*
Install the latest jre or jdk available from the repository, because that sets up some things that will make the job easier.

I don't know for sure how the packages are structured on Ubuntu, but Sun jdk usually contains all of the jre binaries as well as the  jdk binaries. You may not need to install the jre if you are going to install the jdk. ***(if anybody knows the details to this feel free to post it)***

The following command will install the most recent java6 jre stored in the ubuntu repositories

*sudo apt-get install sun-java6-jre*


The following command will install the most recent java6 jdk stored in the ubuntu repositories

*sudo apt-get install sun-java6-jdk*


You will need to agree to the license, (hit tab and press enter when the "ok" is highlighted)

When this is finished, if you do not feel the need to install the newest package from sun, you can just stop. Ubuntu's installer should have set up everything for you. 

**Step 2: *** Getting and unpacking the Java extractable bin*

Otherwise, you need to go to the sun developer website and get a file that looks like this: (i.e. not *.rpm.bin)

**For 32 bit:**
_jdk-6u18-linux-i586.bin_
or
_jre-6u18-linux-i586.bin_

**For 64 bit:**
_jdk-6u18-linux-x64.bin_
or
_jre-6u18-linux-x64.bin_

As I am writing this, you can access the jre and jdk files from:
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) (you can skip registering if you don't want to)

**Run the self-extractor:**
*chmod +ax your_java_bin.bin*
*./your_java_bin*

it will extract itself to a subfolder with a name like: _jdk1.6.0_18_

**Step 3: ***Moving your Java folder to the correct location*

**Copy the java directory to the jvm location:** (I use copy because it creates new files under the ownership of root)
*sudo cp java_directory /usr/lib/jvm*

**Step 4: ***Creating a new *.jinfo file based on the one created by the Ubuntu package*
*(This file is used by the update-java-alternatives system to switch all java binary alternatives at once.)*
the next step is tricky, navigate to the jvm directory
run the command *ls -al* , there  should be a file  with a name like:
_.java-6-sun.jinfo_

you need to make a copy of this and modify it so it refers to the new installation
Change the name of your copied to match your installation folder plus a preceding period character.
Change the contents to match your new install directory. I'm not entirely sure what the alias refers to, but I don't think it has to be different from the real folder install name. Make sure your new score is higher than the old one, and remember it, you need to use it when adding your installation to the update-alternatives system.

**Step 5: ***Registering your binaries with the update-alternatives system*
*(This is necessary to get update-java-alternatives to work for your installation)*

These things need to be added to the update-alternatives system, make a note of the priority score in the original jinfo file, and make sure your new one is larger than the old one.

To add these new items to the update-alternatives system I copied the bottom part of the jinfo file into a new perl script file, removed the first "column" from each line (in terms of a whitespace separated value table), and modified it to run update-alternatives --install on each item (except for the plugin, which didn't seem to have an update-alternatives entry.)
**Syntax: ***update-alternatives --install <link> <name> <path> <priority>*

I will provide my code for you to modify for your own purposes at the bottom of the post. Once you run this command, as long as your update-alternatives is set to auto and the score you put in is bigger than the score for ubuntu's repository version, your system will already be set to use the new java preferentially. (it uses the alternative with the highest score automatically). I don't think, though, that the plugin will have been switched.

**Step 6: ***Running update-java-alternatives*

if you can run the command: *update-java-alternatives -s jdk1.6.0_18* replacing the name I wrote with the name of your java installation folder under _/usr/lib/jvm_ and it can complete without error, everything should be set up properly. I think it is supposed to switch the plugin as well, but I'm not 100% sure how the plugin settings are managed, as I couldn't find an  update-alternatives entry for it.


```
#!/usr/bin/perl
my $cmd_start="update-alternatives --install /usr/bin/";
my $score="65";
sub install_alternative($){
my @strs=split("\\s",$_[0]);
my $cmd=$cmd_start.$strs[0]." ".$strs[0]." ".$strs[1]." ".$score."\n";
print($cmd);
system($cmd);
};
install_alternative("ControlPanel /usr/lib/jvm/jdk1.6.0_18/jre/bin/ControlPanel");
install_alternative("java /usr/lib/jvm/jdk1.6.0_18/jre/bin/java");
install_alternative("java_vm /usr/lib/jvm/jdk1.6.0_18/jre/bin/java_vm");
install_alternative("javaws /usr/lib/jvm/jdk1.6.0_18/jre/bin/javaws");
install_alternative("jcontrol /usr/lib/jvm/jdk1.6.0_18/jre/bin/jcontrol");
install_alternative("keytool /usr/lib/jvm/jdk1.6.0_18/jre/bin/keytool");
install_alternative("pack200 /usr/lib/jvm/jdk1.6.0_18/jre/bin/pack200");
install_alternative("policytool /usr/lib/jvm/jdk1.6.0_18/jre/bin/policytool");
install_alternative("rmid /usr/lib/jvm/jdk1.6.0_18/jre/bin/rmid");
install_alternative("rmiregistry /usr/lib/jvm/jdk1.6.0_18/jre/bin/rmiregistry");
install_alternative("unpack200 /usr/lib/jvm/jdk1.6.0_18/jre/bin/unpack200");
install_alternative("orbd /usr/lib/jvm/jdk1.6.0_18/jre/bin/orbd");
install_alternative("servertool /usr/lib/jvm/jdk1.6.0_18/jre/bin/servertool");
install_alternative("tnameserv /usr/lib/jvm/jdk1.6.0_18/jre/bin/tnameserv");
install_alternative("jexec /usr/lib/jvm/jdk1.6.0_18/jre/lib/jexec");
install_alternative("HtmlConverter /usr/lib/jvm/jdk1.6.0_18/bin/HtmlConverter");
install_alternative("appletviewer /usr/lib/jvm/jdk1.6.0_18/bin/appletviewer");
install_alternative("apt /usr/lib/jvm/jdk1.6.0_18/bin/apt");
install_alternative("extcheck /usr/lib/jvm/jdk1.6.0_18/bin/extcheck");
install_alternative("idlj /usr/lib/jvm/jdk1.6.0_18/bin/idlj");
install_alternative("jar /usr/lib/jvm/jdk1.6.0_18/bin/jar");
install_alternative("jarsigner /usr/lib/jvm/jdk1.6.0_18/bin/jarsigner");
install_alternative("java-rmi.cgi /usr/lib/jvm/jdk1.6.0_18/bin/java-rmi.cgi");
install_alternative("javac /usr/lib/jvm/jdk1.6.0_18/bin/javac");
install_alternative("javadoc /usr/lib/jvm/jdk1.6.0_18/bin/javadoc");
install_alternative("javah /usr/lib/jvm/jdk1.6.0_18/bin/javah");
install_alternative("javap /usr/lib/jvm/jdk1.6.0_18/bin/javap");
install_alternative("jconsole /usr/lib/jvm/jdk1.6.0_18/bin/jconsole");
install_alternative("jdb /usr/lib/jvm/jdk1.6.0_18/bin/jdb");
install_alternative("jhat /usr/lib/jvm/jdk1.6.0_18/bin/jhat");
install_alternative("jinfo /usr/lib/jvm/jdk1.6.0_18/bin/jinfo");
install_alternative("jmap /usr/lib/jvm/jdk1.6.0_18/bin/jmap");
install_alternative("jps /usr/lib/jvm/jdk1.6.0_18/bin/jps");
install_alternative("jrunscript /usr/lib/jvm/jdk1.6.0_18/bin/jrunscript");
install_alternative("jsadebugd /usr/lib/jvm/jdk1.6.0_18/bin/jsadebugd");
install_alternative("jstack /usr/lib/jvm/jdk1.6.0_18/bin/jstack");
install_alternative("jstat /usr/lib/jvm/jdk1.6.0_18/bin/jstat");
install_alternative("jstatd /usr/lib/jvm/jdk1.6.0_18/bin/jstatd");
install_alternative("native2ascii /usr/lib/jvm/jdk1.6.0_18/bin/native2ascii");
install_alternative("rmic /usr/lib/jvm/jdk1.6.0_18/bin/rmic");
install_alternative("schemagen /usr/lib/jvm/jdk1.6.0_18/bin/schemagen");
install_alternative("serialver /usr/lib/jvm/jdk1.6.0_18/bin/serialver");
install_alternative("wsgen /usr/lib/jvm/jdk1.6.0_18/bin/wsgen");
install_alternative("wsimport /usr/lib/jvm/jdk1.6.0_18/bin/wsimport");
install_alternative("xjc /usr/lib/jvm/jdk1.6.0_18/bin/xjc");
```

---

### Post by kotoro on 2010-03-08
I can confirm that in my run through, the final update-java-alternatives run did in fact adjust the browser plugin. Everything seems to work appropriately.

-edit1: To adjust the script I think a few simple find/replace for the folder name, plus adjusting any other parameters appropriately, would be all that is necessary. I recommend commenting out the system($cmd) line (near the top of the code inside the subroutine) until you are sure that the output is properly formed. (for those who don't know, use a # sign on the line to comment everything that comes after the # on that line).

-edit2: If you really want, you can follow the convention that Ubuntu's team does and define a .jinfo file with a simpler name and provide a soft-link to the "real" folder with that name. You might even consider redirecting the existing java6 soft link to the new folder, and avoid the whole file registration process I explained above, but I don't know if messing with the settings related to an installed package is a good idea.

-edit3: If you make a mistake and somehow register incorrectly with update-alternatives, or you would like to de-register you java installation, you should be able to modify the command string in the above perl script a bit and running the perl script with a properly formatted "*update-alternatives --remove <name> <path>*" command will de-register all of your java binaries.

---

### Post by supershin on 2010-05-19
*You may not need to install the jre if you are going to install the jdk. (if anybody knows the details to this feel free to post it)*

[http://java.sun.com/javase/downloads/index.jsp]("http://java.sun.com/javase/downloads/index.jsp")

From their site under "**What do I need?**" [I]
To develop Java applications and applets, you need the JDK  (Java Development Kit), which includes the JRE.[/I]

So you DO NOT need to install the JRE if installing the JDK, JDK installs it for you.

I only extracted the files in my Donwnloads to ensure its good. I was gonna put them in bin and link them. So your copy to jvm steps and below have me confused. Why are we to do that?

---

### Post by kotoro on 2010-05-22
The idea is to put everything where the normal java installations go, so the system knows where to find it.

---


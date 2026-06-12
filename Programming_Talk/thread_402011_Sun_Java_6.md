---
title: "Sun Java 6"
date: 2007-04-05
forum: Programming Talk
---

### Post by snowjunkie on 2007-04-05
Hi,

I'm trying to install the java 6 sdk on my laptop.  I have feisty installed and I've used synaptics to install java 6.  From my terminal window, in my home directory I can use javac ok but I cannot use java.  The sdk install did install the jre as well, as the package was selected in synaptics.

Do I need to set up a path to the jre folder?  How do I do that?  I used the normal search utility and it couldn't find the executable, although using beagle does, but it doesn't give it's location on the disk.

I feel pretty wick.  I just got my scjp at the weekend and I can't even install java! :oops: 

Can anyone help?

---

### Post by samjh on 2007-04-05
> **snowjunkie said:**
> I feel pretty wick.  I just got my scjp at the weekend and I can't even install java! :oops: :lolflag: 

Chin up. :)

You probably need to create a symlink in your usr/bin directory.

Ubuntu installs Sun's Java in usr/lib/jvm.  Go there and you will find a directory called sun-java-somethingsomething.

On my machine, it's installed at /usr/lib/jvm/java-6-sun-1.6.0.00

All you need to do is navigate to the /usr/bin directory, and if your Java is installed at the same location as mine, type this in terminal:
```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.00/bin/javac ./
```
That will create a symbolic link to the javac command, so you can use it from the command line without giving the full path all the time.

You can create links for the jar utility too.  Just substitute javac with jar in the code I gave you.

Also to be on the safe side, do:
```
sudo update-alternatives -config java
sudo update-alternatives -config javac
```to set the correct versions of java and javac you want to run.

---

### Post by lvizard on 2007-04-05
You should rather use:

```
update-java-alternatives
```

it updates **all** Java alternatives.

---

### Post by snowjunkie on 2007-04-05
The symlink did the trick.

Not sure how to use the update-java-alternatives line.  It doesn't seem to work.

Also, I seem to have two sun java folders in /usr/lib/jvm.  I have the one you mentioned, plus java-6-sun... they look to be the same.  Can I simply delete one of them?

Thanks for your help.

---

### Post by samjh on 2007-04-06
> **snowjunkie said:**
> The symlink did the trick.

Not sure how to use the update-java-alternatives line.  It doesn't seem to work.Type ```
sudo update-java-alternatives --jre -l
```that lists your available JRE installations.  If it comes up with java-sun-6, then you can type ```
sudo update-java-alternatives --jre -s java-sun-6
```and it will set all your JRE-related tools to run the Sun Java 1.6 tools (it creates the symlinks automatically in usr/bin).

But it doesn't set up javac or jar, so you still need to create those symlinks yourself.

> Also, I seem to have two sun java folders in /usr/lib/jvm.  I have the one you mentioned, plus java-6-sun... they look to be the same.  Can I simply delete one of them?The java-6-sun is an alias that links to the proper directory for Sun Java 1.6.  In my installation, it links to /usr/lib/jvm/java-6-sun-1.6.0.00.

Don't delete it, in case one or more of your symlinks or system configurations refer to the java-6-sun directory instead of the full java-6-sun-1.6.0.00 one.  It does no harm. ;)

---

### Post by snowjunkie on 2007-04-06
Ok, did that.  Thanks again for your help.

---


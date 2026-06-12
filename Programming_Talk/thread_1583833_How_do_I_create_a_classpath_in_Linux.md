---
title: "How do I create a classpath in Linux?"
date: 2010-09-28
forum: Programming Talk
---

### Post by s3a on 2010-09-28
I haven't tried it but in Windows it, apparently, is *set classpath=.;c:\theDirectory;*. The way my teacher explained it, however, is to right click on "My computer", then to select "Properties", click "Advanced, click "Environment variables", choose "CLASSPATH", then edit the line and put *.;C:\ClassPathDir;* for example.

I am lost on the basics, so it would be greatly appreciated if someone could explain to me the theory and especially how to do it in Linux!

Thanks in advance!

---

### Post by PaulM1985 on 2010-09-28
I know this doesn't exactly answer your question, but if you are using something like Netbeans and not compiling from command line you can include a library into your Netbeans project.  By doing this you don't have to add the location of the Jar file to your class path.

If you are compiling from the command line, sorry for the wasted post. :-(

Paul

---

### Post by spjackson on 2010-09-28
> **s3a said:**
> I haven't tried it but in Windows it, apparently, is *set classpath=.;c:\theDirectory;*. The way my teacher explained it, however, is to right click on "My computer", then to select "Properties", click "Advanced, click "Environment variables", choose "CLASSPATH", then edit the line and put *.;C:\ClassPathDir;* for example.

I am lost on the basics, so it would be greatly appreciated if someone could explain to me the theory and especially how to do it in Linux!

Thanks in advance!
If you want to set the environment variable CLASSPATH for your own user, then edit the file .bashrc in your home directory and add:
```

export CLASSPATH=/path/to/first/object:/path/to/second/object:etc

```However, please read [http://download.oracle.com/javase/tutorial/essential/environment/paths.html](http://download.oracle.com/javase/tutorial/essential/environment/paths.html) and note in particular "The preferred way to specify the class path is by using the -cp command line switch.  This allows the  CLASSPATH to be set individually for each application without affecting other applications. *Setting the CLASSPATH can be tricky and should be performed with care."*

---

### Post by dileepm on 2011-01-27
If you are seeking an solution generic for all linux flavours here is this

in your /root/.bash_profile you can set the classpath as

CLASSPATH=.:/whatever

If the solution is specific to Ubuntu

you can set the classpath in /etc/evironment file as

CLASSPATH=.:/whatever

You need to restart your box for both things. ':' is the path separator for linux.

---

### Post by slavik on 2011-01-27
> **dileepm said:**
> If you are seeking an solution generic for all linux flavours here is this

in your /root/.bash_profile you can set the classpath as

CLASSPATH=.:/whatever

If the solution is specific to Ubuntu

you can set the classpath in /etc/evironment file as

CLASSPATH=.:/whatever

You need to restart your box for both things. ':' is the path separator for linux.
this is a _bad_ way to do this.

---

### Post by Bodsda on 2011-01-27
> **dileepm said:**
> You need to restart your box for both things.
 
Really? I would have thought restarting your bash session would do the trick.
 
Bodsda

---

### Post by dileepm on 2011-01-28
> this is a _bad_ way to do this.

Whats the good way?

---


---
title: "Java Scanner import from java.util not working"
date: 2008-05-20
forum: Programming Talk
---

### Post by JustAnotherVagueAnon on 2008-05-20
I installed Eclipse using Synaptic but the Scanner import won't work. Does Eclipse use its own compiler by default? I'm using Eclipse 3.2.2.

---

### Post by 65daysofstatic on 2008-05-20
hi,
I think it's because you are using jdk 1.4, try to upgrade to jdk 1.6.


edit: i think it's better to download eclipse from their site, because that version is a bit old and comes with java 1.4, try downloading only eclipse for java developers [http://www.eclipse.org/downloads/]("http://www.eclipse.org/downloads/") and install jdk 1.6 from terminal
"sudo apt-get install sun-java6-jdk"

---

### Post by JustAnotherVagueAnon on 2008-05-20
The JRE Eclipse is currently using is "java-1.5.0-gcj-4.2-1.5.0.0". This is not the runtime environment to use?

---

### Post by 65daysofstatic on 2008-05-20
I suggest you to uninstall that version of eclipse, and then install java6 and download eclipse from their site

---

### Post by achelis on 2008-05-20
+1 for installing from eclipse's own site.

You can see the compiler compliance level under:

Window -> Preferences.. -> Java -> Compiler

As for system library you should have an entry for that in your projects Package Explorer, this shows which jar-files is available for your project.

---

### Post by NormR2 on 2008-05-20
> Java Scanner import from java.util not working
Are you getting an error compiling or executing? ie what's not working?
If you'd copy the full text of the error message here, it'd help solve the problem.

If you read the doc, you'll see that java.util.Scanner is as of version 1.5

---

### Post by JustAnotherVagueAnon on 2008-05-22
Compilation error importing Scanner ("Import cannot be resolved"). Using the library from 1.5.0.

---

### Post by JustAnotherVagueAnon on 2008-05-22
Ah, I got it. Changed from GCJ to Sun's JRE 1.6.

---

### Post by Lzanki on 2010-03-07
I am a new programmer and i am trying to learn how to make Black Berry Application, so if you have any advise on good videos to watch that would be great.  but for right now i'm trying to do some basic java coding and i'm having trouble with Scanner.

Here is the error that i am getting:

Exception in thread "main" java.lang.Error: Unresolved compilation problems: 
    Scanner cannot be resolved to a type
    Scanner cannot be resolved to a type

    at apples.main(apples.java:6

Im doing this in Eclipse 3.4.1

here is a link to a video that i am trying to follow:  

[http://www.youtube.com/watch?v=5DdacOkrTgo&feature=SeriesPlayList&p=FE2CE09D83EE3E28](http://www.youtube.com/watch?v=5DdacOkrTgo&feature=SeriesPlayList&p=FE2CE09D83EE3E28)


Please help

---


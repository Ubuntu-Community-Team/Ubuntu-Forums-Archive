---
title: "Hoe to: Google Video Uploader jar file"
date: 2005-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by notos on 2005-05-19
Google Video uploader is a progran that lets you upload videos to google server that can be found in [http://video.google.com](http://video.google.com)

in google video help page is no tutorial on how to install this :( so i used google to search for help and these are the results :)

note: you can see the how to install Java run time you _NEED_ Java Runtime 1.4.x    or superior :) in [http://ubuntuguide.org](http://ubuntuguide.org)

You also need to have a google account to login
First we neeed to grab a copy of the Jar File

```
wget https://upload.video.google.com/dllin
```

is this stops to work you can dowload from [here](https://upload.video.google.com/video_instructions.html#downloadinglinux)

now you must have a file named GoogleVideoUploader.jar
make this in a terminal

```

mv Google*.jar /opt

```

You can now run on terminal this

```
java -jar /opt/GoogleVideoUploader.jar
```

---

### Post by pdk001 on 2005-05-25
thanks for good tip
that's what i want

---

### Post by rwabel on 2005-06-15
thanks, sweet tool

---

### Post by macewan on 2005-11-27
thanks for that howto

---

### Post by faizan on 2006-01-06
when i try to get the jar file using wget, i get a no-certificate error. works when i change the command to

```
wget https://upload.video.google.com/dllin --no-check-certificate
```

---

### Post by Vurdak829 on 2006-01-11
I have a seriouse problem..

```
$ java -jar /opt/GoogleVideoUploader.jar 
** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted

```

Any ideas?

---

### Post by Vurdak829 on 2006-01-15
[QUOTE=Vurdak829]I have a seriouse problem..

```
$ java -jar /opt/GoogleVideoUploader.jar 
** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted

```

Any ideas?[/QUOTE]

No one? :(

---

### Post by NeonPulse on 2006-03-04
If you didn't install JRE through the repositories, and instead installed it using the instructions on the java website, that you can run the .jar file by doing:

```
/usr/java/jre1.5.0_06/bin/java -jar /opt/GoogleVideoUploader.jar
```

---

### Post by beerorkid on 2006-05-23
thanks for this.

Really sucks that theinclude no info on how to use it in linux.

---

### Post by vratnica on 2007-03-06
Thank you very much!


Great stuff!!!!

---

### Post by pure fusion on 2007-03-18
I have everything installed fine, but I can't seem to log in. I am behind a proxy, but java is set up for that. it just says "logging in to....as...." forever.

---

### Post by ederic on 2008-02-05
Thanks for the tip. It worked well for me. ;)

---

### Post by Stargazer989 on 2008-04-07
nice title, nice quick 'HoeTo' also :D

---

### Post by bcmiller on 2008-06-07
thank you...

the process in the first post worked for me with the latest version of the google uploader and Hardy Heron.

Yeah for consistency!

I then made a launcher for the uploader and put it in the Sound and Video category.

---

### Post by SebMKd on 2008-06-23
Great tip, that finally works! :guitar:
Been struggling with that one. Didn't know if it's because I have installed both IcedTea and Sun Java.
Anyway that did the trick for me.

Then I just created a new entry in my menu and added java -jar /opt/GoogleVideoUploader.jar to the command line. Now I can launch it from my Internet application menu.

---


---
title: "tar.gz file can't tar this thing!"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by dtay on 2011-10-16
hey, pretty new here and having problem. :confused:

i downloaded the Eclipse IDE and now I want to install the ruby plugin for it, i downloaded the plugin, and i'm trying to tar it but i keep getting the message:

$ tar -xzvf rubyeclipse-0.9.0.707021729NGT.tar.gz
tar (child): rubyeclipse-0.9.0.707021729NGT.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

I extracted it to the desktop and am in that directory so it's not a location issue (i think)...can anyone help??

---

### Post by gsmanners on 2011-10-16
Well, if you extracted it already then you certainly don't need to do "tar -xzvf" to it. Feel free to skip to the next step.

---

### Post by dtay on 2011-10-16
and that would be?

---

### Post by Bmonsterboy on 2011-10-16
Remember linux is case sensitive.

---

### Post by gsmanners on 2011-10-16
Hmm... Interesting. Okay...

So, where did you acquire that file?

---

### Post by dtay on 2011-10-16
easyeclipse.org 

i'm trying to get the ruby plugin for eclipse

---

### Post by gsmanners on 2011-10-16
I think I see where you're going here.

> To install on Linux, download and extract the tar archive (extension .tar.gz) in any folder. The extracted folder contains a install.sh shell script. From a terminal command line, run this script, giving as argument the installation folder of your EasyEclipse (or another installation of Eclipse).
For example, if you are extracted the archive for the Tomcat Launcher 3.1 plugin in your home directory, and you have installed EasyEclipse Expert Java Edition directly in your home directory, run:

```
cd ~/tomcat-launcher-3.1
./install.sh ~/easyeclipse-expert-java-1.2.1
```

After installation, you must exit and restart EasyEclipse (or other Eclipse) to see the new plugin.

---


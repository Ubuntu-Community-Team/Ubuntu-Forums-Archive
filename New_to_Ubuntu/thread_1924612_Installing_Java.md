---
title: "Installing Java"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by interkin3tic on 2012-02-13
Using release 11.04

I'm trying to get onto freenet, which requires java runtime environment to be installed.  

I'm following the instructions here ([http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)) but am getting an error message in terminal from the first step.

I downloaded the linux (self extracting file), the installation instructions say 

"Change the permission of the file you downloaded to be executable. Type:
                   chmod a+x jre-6u<version>-linux-i586.bin
 <version> refers to Java update version you just downloaded. 
 For Example: To install jre-6u30, above command will become 
 chmod a+x jre-6u30-linux-i586.bin"     

So I paste that chmod a+x jre-6u30-linux-i586.bin into the terminal.

"chmod: cannot access `jre-6u30-linux-i586.bin': No such file or directory"

No idea what I'm supposed to do.  Kind of losing it because I can't even get through step one of how to install a program.  Very close to breaking the computer physically out of frustration, I already slammed my fist on it and part of the side popped open.  Not the most constructive response I realize, so please if you wouldn't mind giving instructions as if you're instructing an ape.  I mean, I can't even figure out how to make that bullet point next to chmod go away.  

Getting back to it, if there's a way to install via software center, I haven't found it.  Open JDK also gives me error messages while trying to install.

---

### Post by howefield on 2012-02-13
Open the terminal and navigate to where you saved the file, eg if you saved the file into your Downloads folder, type..

```
cd Downloads
```

then use the command.

---

### Post by sadaruwan12 on 2012-02-13
You can install java by going to the ubuntu software center. Go to software cent in the seach box type java and press enter.

This show you a result with the oracals free counter part openJDK install that it'll perform just like the oracal one try this ans let us know.

---

### Post by HiImTye on 2012-02-13
just use the [ppa]("http://www.ubuntugeek.com/install-sun-java-6-in-ubuntu-11-10-using-ppa.html")

---

### Post by Rrory on 2012-02-14
just used the ppa, thanks a lot! that was dead easy
rory

---


---
title: "Change Java Version on the Fly"
date: 2012-09-04
forum: Packaging and Compiling Programs
---

### Post by dj1202 on 2012-09-04
Hello All,
I am trying to setup an android development environment. Unfortunately it needs java6. I have java7 installed and i added java6 as well. I am trying to make a small bash script that changes my path to use java6 only when i am going to compile android. 

Here is what i added to .bashrc

#added as function to automatically set java for android development
function android_env {
  PATH=$PATH:/usr/lib/jvm/jdk1.6.0_34/bin/java
  export PATH
  cd ~/Programming/android_os
}

however it does not seem to work but i am not sure why... Any tups would be appreciated, thanks!

---

### Post by drmrgd on 2012-09-04
I'm not sure about the script.  However, rather than making a script, you should be able to change the default java on the fly using 'alternatives'.  See the "Choosing the default java to use" section of the Community Documentation:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

This will allow you to just run:

```
sudo update-alternatives --config java
```

and choose which you want from a menu.

---


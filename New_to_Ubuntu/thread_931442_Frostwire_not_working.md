---
title: "Frostwire not working"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Baldemar on 2008-09-27
I get this message when I run frostwire to open.

baldemar@baldemar-laptop:~$ frostwire
HOSTNAME IS baldemar-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by linux6994 on 2008-09-27
You need to install java, go to

System > Administration > Synaptic Package Manager then search for sun-java6-bin and install it. Accept yes to terms and once its complete you are ready to go.

---

### Post by Baldemar on 2008-09-27
I guess I already had it. I reinstalled and my frostwire sill does not open.

---

### Post by WWSmith36 on 2008-09-27
Then open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo aptitude update
sudo apt-get upgrade
sudo aptitude install sun-java6-bin sun-java6-jre sun-java6-plugin

---

### Post by konungursvia on 2008-09-27
When you have a few jre modules, you have to run a config script to manually choose which one to default to. I can't find it now, but using the keywords in this answer you can find it. It's sort of a multiple choice thing, I've done it, one or two times. After selecting the appropriate one, it should work.

---

### Post by Baldemar on 2008-09-27
I still have not been able to get it running, It was working before, I think after I started using banshee and transferred files into it it quite working. Maybe its just an coincidence in don't know
.

---

### Post by gjoellee on 2008-09-27
Try install LimeWire. It comes with Java as well, that should work:)

---

### Post by Baldemar on 2008-09-27
I am still unable to open frostwire, I tried to reinstall and still no luck.

---

### Post by Baldemar on 2008-09-27
I still have not got it going, any help?

---

### Post by Baldemar on 2008-09-28
got it to work with this command.

sudo update-java-alternatives -s java-6-sun

---


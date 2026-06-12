---
title: "Howto: Install Sun's Java (SDK/JRE) the easy way (using the plf repos)"
date: 2006-03-06
forum: Outdated Tutorials &amp; Tips
---

### Post by hod139 on 2006-03-06
**EDIT:** Dapper now includes the official Sun java packages in the *multiverse* repositories.  To install the runtime environment simply type    ```
 sudo apt-get install sun-java5-jre
```.  For development ```
 sudo apt-get install sun-java5-jdk
``` and for the firefox plugin ```
 sudo apt-get install sun-java5-plugin
```I have seen this question asked many times, but have not found a simple howto to refer people to. Here is my first attempt at making one.  I should add that these instructions only work for i386 machines.  AMD64 users can follow the instructions found [here]("http://ubuntuforums.org/showthread.php?t=76735"), substituting amd64 for i386 in that howto.


** To install Sun's JRE version 1.5**: (for the SDK see below)
```
sudo apt-get install sun-j2re1.5
```  **Step 2**. Make Sun's JRE the system default
```
sudo update-java-alternatives -s java-1.5.0-sun
```Next, edit /etc/jvm and add 
 ```
/usr/lib/j2re1.5-sun/
``` to the top of the file

** To install Sun's SDK version 1.5 (which includes a JRE):**
```
sudo apt-get install sun-j2sdk1.5
```  [B]
Step 2[/B]. Make Sun's JRE the system default
```
sudo update-java-alternatives -s java-1.5.0-sun 
```Next, edit /etc/jvm and add 
```
/usr/lib/j2sdk1.5-sun/jre
```to the top of the file

---


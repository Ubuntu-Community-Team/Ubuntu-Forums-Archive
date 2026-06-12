---
title: "setting the PATH variable for Java"
date: 2005-09-09
forum: Programming Talk
---

### Post by tidemann on 2005-09-09
I just installed java JDK 1.5.0 for my studies in informatics. I've got it all running smoothly, but I'm not sure how to add the PATH varibale.

To run a java program in terminal i need to type:
$ /opt/jdk1.5.0_04/bin/java Program

When the path variable is set, I should be able to run it like this:
$ java Program

Probably a simple question, but the online guides that I've found differ from eachother, so if someone could simple tell me how its done in Ubuntu 5.04 I would really appreciate it! Thanks

---

### Post by ebrowne on 2005-09-09
There are a couple of places
Global for all users
edit /etc/profile and add
PATH=${PATH}:/opt/jdk1.5.0_04/bin/;
export PATH

for individual users add the same thinkg to /home/user/.bash_profile

You'll have to restart your session for this to work the first time.

---

### Post by vcrfix on 2006-08-15
Or,

sudo vi /etc/profile

Now add at the end of the file by moving the cursor down arrow, then press the 'i' key.

PATH=/usr/java/jdk1.5.0_08/bin:${PATH}
export PATH
JAVA_HOME=/usr/java/jdk1.5.0_08
export JAVA_HOME

Then press the ":" (colon key) followed by the 
"wq" keys.

Logout and relogin.

Open a terminal window, enter the java -version
command, and should see the update Java JDK version.

---


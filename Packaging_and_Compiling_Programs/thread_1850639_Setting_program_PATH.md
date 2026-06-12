---
title: "Setting program PATH"
date: 2011-09-26
forum: Packaging and Compiling Programs
---

### Post by bverly on 2011-09-26
I have some problem setting some program path?? i am not sure i do the right thing or not >,<
i did
echo ‘export ACTIVEMQ_HOME=/home/lambo/apache-activemq&#8242; > /etc/profile.d/activemq
echo ‘export PATH=$ACTIVEMQ_HOME/bin:$PATH’ >> /etc/profile.d/activemq
source /etc/profile.d/activemq

for the first time , it runs well but after that, it require me to repeat source /etc/profile.d/activemq.


another question, i install Open-jdk through sypnatic, how can i find openJDk/bin/jdk.sh?? i want to make JAVA_HOME path too >,<

(Basically how to set program path :D)

---

### Post by SevenMachines on 2011-09-27
You need to give the files in profile.d a .sh extension otherwise they dont get processed, can't remember why (you may need to log out and back in after that)

---

### Post by mvs1207 on 2011-09-27
> **bverly said:**
> 


another question, i install Open-jdk through sypnatic, how can i find openJDk/bin/jdk.sh?? i want to make JAVA_HOME path too >,<



This should give you complete path
```
readlink -f `which java`
```

---

### Post by SevenMachines on 2011-09-27
Although, you do seem to be adding a user path to the system wide profile.d, I'd suggest that for user installed programs you stick to adding those exports to the per-user ~/.bashrc instead

---


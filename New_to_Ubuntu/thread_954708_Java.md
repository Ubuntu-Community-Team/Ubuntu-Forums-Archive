---
title: "Java"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by deejaypip on 2008-10-21
Sorry, I know you probably get lots of these questions.

I can't do anything that involves java, such as uploading photos to Facebook or seeing embedded Youtube videos. (I can watch them on Youtube just fine, though.)

I see a message that says, "The required plug-in is missing." When Firefox asks me if I want to install the missing plug-in and I say "yes," my computer says that I already have it installed.

I got this error message just now:

> 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre-lib_6b10-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre-lib_6b10-0ubuntu1_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre-headless_6b10-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre-headless_6b10-0ubuntu1_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre_6b10-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openjdk-6/openjdk-6-jre_6b10-0ubuntu1_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/icedtea-gcjwebplugin/icedtea-gcjwebplugin_1.0-0ubuntu7_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/icedtea-gcjwebplugin/icedtea-gcjwebplugin_1.0-0ubuntu7_amd64.deb)
  404 Not Found [IP: 91.189.88.31 80]






Thanks

---

### Post by wolfen69 on 2008-10-21
search synaptic for jre. then install the java plugin.

---

### Post by kansasnoob on 2008-10-21
I go to synaptic and search for sun-java6. Then I install ALL sun-java6-*** **EXCEPT sun-java6-doc and sun-java6-source**.

---

### Post by gandaran on 2008-10-21
> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb)
404 Not Found [IP: 91.189.88.31 80]

deejaypip
this error message raisers some questions
are you running ubuntu 64-bits?
did you add this or any other repository to synaptic?

(404 Not Found [IP: 91.189.88.31 80) means the repository server is out or doesn't exist, maybe try again tomorrow
if you have ubuntu 64-bits then you have to install open-java as there is no sun-java plugin for 64-bits firefox, just install the **ubuntu-restricted-extras** this package will take care to install java and other necessary plugins

---

### Post by penguin17 on 2008-10-21
try this in terminal:-

sudo apt-get install ubuntu-restricted-extras

---


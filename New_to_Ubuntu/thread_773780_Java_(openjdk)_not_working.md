---
title: "Java (openjdk) not working"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jepong on 2008-04-29
I freshly installed Ubuntu Hardy on my thinkpad.

I tried to upload my photos in multiply.com but java won't start.

need help...

This also goes with my HP Pavilion desktop... upgraded from Gutsy.

---

### Post by rockerphil on 2008-04-29
run this code in your terminal

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

that should do the trick

---

### Post by Michael.Godawski on 2008-04-29
Run the code stated above. You can also install the restricted extras to have the most media codecs installed.
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by rockerphil on 2008-04-29
good call Michael

---

### Post by jepong on 2008-04-29
thanks for the very quick reply guys... :KS

whats up with openjdk anyway?

---

### Post by thenes on 2008-04-29
I presume you are using firefox.

How does your about: plugins in firefox turn out?

If ice tea is listed before java, this can prevent java from working properly because firefox will try to run the java on the webpage through ice tea in stead of java. If you have installed both ice tea and java, this can be the reason why the java on the webpage is not working.

---

### Post by jepong on 2008-04-29
would you suggest that i remove any java components then install what Michael.Godawski and rockerphil suggestd awhile ago?

---

### Post by gandaran on 2008-04-29
don't install the ubuntu-restricted-extras as that package will install open java.
go to synaptic, look up all java packages, uninstall all of them, then just select ' sun-java6-plugin ' and ' sun-java6-jre ' for install and click apply, synaptic will install all the necessary java dependencies.

---


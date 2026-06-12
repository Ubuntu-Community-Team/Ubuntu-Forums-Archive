---
title: "cannot install package"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by rdh61 on 2012-06-02
Hi,

I am using ubuntu 12.04. I have downloaded the package wuala_current_i386.deb to my home folder. If I double click on it, it opens in the software centre but the install button is greyed out and will not work. The same in the File menu. How do I get round this?

Thank you.

---

### Post by inashdeen on 2012-06-02
Several .deb seems not to work harmonically with USC. may i suggest the use of dpkg? it is command line.

---

### Post by matt_symes on 2012-06-02
Hi

Open a terminal and type

```
sudo dpkg -i ~/wuala_current_i386.deb
```

Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by inashdeen on 2012-06-02
other tips, get gdebi :)or even deepin software center

---

### Post by rdh61 on 2012-06-02
Perfect. Thank you.

---

### Post by inashdeen on 2012-06-02
don't forget to mark as [solved]

---

### Post by matt_symes on 2012-06-02
Hi

If using dpkg gives you any problems, start a new thread and PM me the link.

Kind regards

---


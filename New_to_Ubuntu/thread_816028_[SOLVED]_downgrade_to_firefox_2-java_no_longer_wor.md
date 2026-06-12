---
title: "[SOLVED] downgrade to firefox 2-java no longer works..."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2008-06-02
After i removed forefox 3 and installed firefox 2, the java plugin no longer works. However, 
```
sudo apt-get install sun-java6-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
but some web pages say "additional plugins required to display the media on this page" and it tries to download java...then it fails and says try manual install :(

---

### Post by gn2 on 2008-06-02
Use synaptic to check open jdk isn't installed.
If it is remove all traces of it then re-install the sun java jdk.

---

### Post by e1ektrob0y on 2008-06-02
Synaptic wont let me remove java runtime environment. It says other apps depend on it. I removed all other java traces like browser plugin etc. But its still broken :(

---

### Post by e1ektrob0y on 2008-06-03
bump?

---

### Post by franzsalvador on 2008-06-09
This can solve your problem. click [here]("http://franzsalvador.multiply.com/journal/item/13/Installing_Java_on_Firefox_for_Ubuntu_Linux_users")

---

### Post by e1ektrob0y on 2008-06-11
Thanks that worked :)

---


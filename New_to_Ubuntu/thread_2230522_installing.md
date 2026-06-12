---
title: "installing"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by trav9595 on 2014-06-19
I downloaded a file to my desktop called unitlauncher100.sh
then I made a folder called unit and put it in there.
What is the exact terminal command to extract and run this program????

---

### Post by oldos2er on 2014-06-19
A shell script is a text file that's executable, no extraction needed. So ```
cd unit

chmod +x unitlauncher100.sh

./unitlauncher100.sh
``` should work. I'm assuming you trust the source where unitlauncher100.sh came from that it isn't something potentially malicious.

---


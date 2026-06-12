---
title: "How to copy simple .sh file to profile.d?"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-22
I created java.sh which contains setting the paths of environment variables for JDK. I need to place it in /etc/profile.d to run Intellij IDEA but the option is grayed out. How do I grant permissions to be able to do this?

---

### Post by ajgreeny on 2015-01-22
Go to the folder where the java.sh is sitting and run the command ```
sudo cp java.sh /etc/profile.d/java.sh
```
Using sudo as a prefix to a command raises your permissions temporarily to root allowing you to do anything, so take care as you can do great damage if you are not careful.

---


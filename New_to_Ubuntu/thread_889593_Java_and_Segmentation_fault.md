---
title: "Java and Segmentation fault"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by MrGoose on 2008-08-14
For some reason, whenever i try to run java jar files now, all i get returned is Segmentation fault and I'm not quite sure how to fix it. I've tried completely removing and reinstalling the java6 and OpenJDK packages through synaptic package manager, and using the (sudo update-alternatives --config java) command to change jre but neither has had any success. I think this happens only with jar files which try to access the internet. This hasn't always happened as they would run quite happily up to a day or two ago. Bit of an ubuntu noob so any help would be appreciated.

---

### Post by finer recliner on 2008-08-14
did you develop these jar files yourself? if so, you have a run-time error in your code.

if you got this code from an official project webpage, what is the project/application?

---

### Post by MrGoose on 2008-08-14
I did develop it myself. As for seeing any run time errors all that gets returned from the command line is Segmentation Fault and nothing more. Do i need to give java some argument so it gives me a more useful error message?

---

### Post by finer recliner on 2008-08-14
its time to step through your code and find out where and why a seg fault is being thrown. most IDEs, such as eclipse, can do this for you. another (less appealing option) is to add a lot of println statements to narrow down where your code is throwing the seg fault.

(side note: this question would have been better placed in the programming sub-forum)

---

### Post by MrGoose on 2008-08-14
Its not just that application though. I tried running a tiny snippet of java code which downloads a webpage which has the same error. Also I've just tried azureus (only other java program i can think of that accesses the internet) which also returns the same error.

---

### Post by ds[de] on 2008-08-14
You should try if your java binary works at all.

So does a 'java --version' return useful output or a 'Segmentation fault' as well?

---

### Post by MrGoose on 2008-08-14
That works fine. I've also tried a few other little java applications which work fine. As far as i can tell, its only the java programs which try to access the internet which are having problems.

---


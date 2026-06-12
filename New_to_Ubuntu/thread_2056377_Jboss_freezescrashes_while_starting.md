---
title: "Jboss freezes/crashes while starting"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by siddharth007 on 2012-09-11
I have installed jboss on my ubuntu 12.04 64-bit system.When i try to start Jboss using run.sh file in bin folder,it freezes on the line "Core system initializing".I have set the JAVA_HOME and CLASSPATH correctly and don't have multiple java alternatives.What could possibly be the problem.Plz help.......:confused::(

---

### Post by siddharth007 on 2012-09-12
I got the solution.It was the CPU resource issue.I had earlier allocated 1 CPU in the Proxmox virtual environment.Changed it to 2 and it worked :lolflag:

---


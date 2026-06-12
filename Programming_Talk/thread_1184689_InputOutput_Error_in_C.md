---
title: "Input/Output Error in C"
date: 2009-06-11
forum: Programming Talk
---

### Post by Gramlich on 2009-06-11
I have been programming a Dynamixel robot in C using the associated Dynamixel USB adapter for the input wires, and it has been working well. However, recently, in an attempt to make the robot walk, it managed to pull some wires out and the USB. Ever since this incident, whenever I attempt to run the code, I get this error: open: Input/output error .
 There is nothing wrong with my code nor my robot, the USB adapter itself, or wires. When I connect it to another computer and run the code, it works just fine, and I get no errors. I'm also referencing the correct USB port. I'm new to both C and ubuntu, and I would appreciate any help anyone could lend me.

---

### Post by Zugzwang on 2009-06-11
Try to find out what component produces the error, i.e., where is is it written (console, error log) when (e.g., when running program xyz with the parameters abc)? Also type "dmesg" in the terminal after the error to find out if there's some relevant error message in there.

---

### Post by randallecook on 2009-06-11
Also, does this happen even after power cycling everything? Does the USB port on your host machine still work?

---


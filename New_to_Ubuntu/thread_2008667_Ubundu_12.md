---
title: "Ubundu 12"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by PAUL ZAD on 2012-06-23
ubundu 12  blank black screen after  install  reboot
can someones help

---

### Post by Bucky Ball on 2012-06-23
Welcome.

* At boot hit shift until you get to the list of kernels;
* Highlight the kernel you want to boot and press 'e' to edit it;
* Find the line that ends with 'quiet splash' or one or both of those words;
* Add a space at the end of that line and then add 'nomodset';
* Press control+x to reboot (instructions bottom of screen).

Question:
* Did you 'Try Ubuntu' running from the CD first and did it run okay?
* Did the install go smoothly (as expected, no problems)?

Let us know what happens.

---

### Post by PAUL ZAD on 2012-06-25
no i try 6 diferent times  from cd ,dvd from hard drive files
it is no diferent

---

### Post by Bucky Ball on 2012-06-25
Does it work when you boot from the CD and 'Try Ubuntu'?
Have you performed the steps in my last post (editing the kernel line by adding 'nomodset')?

---


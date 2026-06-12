---
title: "Cursor"
date: 2016-05-11
forum: New to Ubuntu
---

### Post by Siddhesh_Urkude on 2016-05-11
I have installed ubuntu 15.10 in my laptop. My laptop config is :-
3 gb RAM
500 gb HDD
i3 processor

Many times cursor gets hang and stop moving. Firstly i thought it is due to improper installation, but after installing it again the problem persist. What is wrong i am doing?
or is it the issue with the version?

I recently shifted from windows to ubuntu for coding purpose as I find it easy to do [c programming]("http://www.codingplex.com") in ubuntu.

Kindly help.

---

### Post by QDR06VV9 on 2016-05-11
When you mention Ubuntu I assume Unity as a desktop.
But you could try using a lite DE like XFCE or Mate or LXDE to see if the problem is related to Unity.
And one other thing to check is this a hybrid GPU IE: Intel and Nvidia?

---

### Post by Siddhesh_Urkude on 2016-05-11
yes its intel and nvidia.
I will try with the unity one idea.

---

### Post by Bucky Ball on 2016-05-11
Welcome. Off-topic but worth a mention as, being a new-comer, you may not be aware: 15.10 is out of support in about a month and a half, at which point you'll need to upgrade to 16.04 LTS or do a clean install of it. 

Might be better to cut to the chase and install 16.04 LTS now rather than installing an almost dead release. LTS releases have five years support so you will be supported until 2021.

Just throwing that in. Carry on. :)

---

### Post by Siddhesh_Urkude on 2016-05-11
I was not knowing about this. But i also tried 16.04 LTS but i observed the same problem.

---

### Post by QDR06VV9 on 2016-05-11
With the hybrid GPU's I have tested lately with out installing the right Nvidia driver i have also noticed slight freezes for a moment.
But with out knowing what card you have I can not advise a proper driver.

---

### Post by mörgæs on 2016-05-12
Yes, we need to know the hardware details. Please run```
 sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---


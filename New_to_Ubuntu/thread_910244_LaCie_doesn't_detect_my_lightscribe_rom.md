---
title: "LaCie doesn't detect my lightscribe rom"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by MarlonDean on 2008-09-04
Hi,

I installed laCie using the method found here : [http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html](http://onlyubuntu.blogspot.com/2008/05/howto-install-lightscribe-in-ubuntu.html). It starts up but it doesn't detect my drive. I have a HP Pavillion DV6611ei but i am unsure which drive i have. Any suggestions?

---

### Post by cespinal on 2008-09-04
I had a similar problem. I solved it launching the program as a root user (using "gksudo").

COuld you give us more details on this?

---

### Post by MarlonDean on 2008-09-04
I tried launching it using gksudo. I inserted my image and when I click print, the part next to 'device' is greyed out with the words 'no device detected'

That is basically it

---

### Post by MarlonDean on 2008-09-05
bump, been about 16 hours

---

### Post by james7dean on 2008-09-15
Hi Marlon,
          I too had this problem with Lacie

I managed to get my lightscribe working , apparently if you have Ubuntu 7.04 or newer, you need to install the old c library.

enter this code into the terminal :-
sudo apt-get install libstdc++5

it will then ask for your password, enter it and the library is installed

After doing this my lightscribe drive was finally recognised by Lacie lightscribe labeller

hope this works for u,

James

---

### Post by McSpenceHouse on 2008-10-06
> **james7dean said:**
> 

enter this code into the terminal :-
sudo apt-get install libstdc++5



That work for me!
I've been looking for a while now and it finally works!
Thank you!

---


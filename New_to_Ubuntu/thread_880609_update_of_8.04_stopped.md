---
title: "update of 8.04 stopped"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by hazman on 2008-08-05
did fresh install of 7.10 and started upgrade to 8.04 when it stopped at   generating locales...
             en_AU.UTF-8...        and been stuck there all night help plz

---

### Post by Cypher on 2008-08-05
You might find it easier to download the Hardy (8.04) Alternate CD, burn it and then use that to upgrade to 8.04. Once upgraded, you will then be able to get the latest updates..

---

### Post by hazman on 2008-08-05
it seem this is something to do with dpkg. tried dpkg --cofigure -a but just stops there now i can not use update manager or synaptics any way to rectify this with out a fresh install

---

### Post by snowpine on 2008-08-05
Hi Hazman, is this by any chance a low-memory system? There is a bug that sounds familiar, let me know if you are indeed low on ram, and I will try to find the launchpad link for you.

---

### Post by hazman on 2008-08-05
i have about 186mb. 64internal and 128 added .had ubuntu on before tho

---

### Post by snowpine on 2008-08-05
> **hazman said:**
> i have about 186mb. 64internal and 128 added .had ubuntu on before tho

Hi Hazman, here is a link to the bug: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/202959)

Scroll down to the post from FactTech on 7-16 and you will see exactly the problem you describe. There are a couple of possible fixes mentioned in people's posts there, but overall, it is considered an Open bug with high priority. :(

---


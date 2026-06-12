---
title: "how to install jdk on ubuntu 7.1?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by franziss123 on 2008-05-28
Hi, how do I install the latest java jdk on ubuntu 7.1?

Thanks alot! I am super newbie to ubuntu and linux. =)

---

### Post by omi291 on 2008-05-29
type

```
sudo apt-get install sun-java6-jdk
```

into the terminal. You can also find it in add/remove applications

---

### Post by franziss123 on 2008-05-29
ya, i tried both but it states it can't find the package. there is also no java on my add/remove applications section

---

### Post by NovaAesa on 2008-05-29
In Add/Remove Programmes, make sure that you have it set to show all available applications rather than only supported applications.

---

### Post by Linux_noob616 on 2008-05-29
(dumb statement i'm about to make i know) are you connected to the internet?

and have you enabled the multi and universe repositories?

if not thats your problem i believe and to enable it you'll need to go to system > administration > software sources, and check the two boxes either in the first menu. or second. (sorry i use Kubuntu now so i'm not help in looking)

after that do ```
 sudo apt-get install sun-java6-jdk 
```

or use the package manager and search for "sun" or go to add and remove and look for "ubuntu restriced extras"

Hope this helps

---

### Post by franziss123 on 2008-05-29
> **NovaAesa said:**
> In Add/Remove Programmes, make sure that you have it set to show all available applications rather than only supported applications.

ya, i set to show all available applications. but still can't find it. 

it is possible that ubuntu 7.1 don't support java? or should i download version 8?

---

### Post by LaRoza on 2008-05-29
> **franziss123 said:**
> ya, i set to show all available applications. but still can't find it. 

it is possible that ubuntu 7.1 don't support java? or should i download version 8?

No, Ubuntu 7.10 should have it.

Go to Add/Remove and change it to "All Available Applications". Close that window.

Run this in a terminal:

```

sudo apt-get update && sudo aptitude install sun-java6-jdk

```

(If you have no specific reason for using that version of Ubuntu, I would recommend using 8.04)

---

### Post by Linux_noob616 on 2008-05-29
> **franziss123 said:**
> ya, i set to show all available applications. but still can't find it. 

it is possible that ubuntu 7.1 don't support java? or should i download version 8?

7.10 does indeed support it (i had a little bit of trouble on my older machine with it though, no trouble in 8.04 though)

---

### Post by stchman on 2008-05-29
> **franziss123 said:**
> Hi, how do I install the latest java jdk on ubuntu 7.1?

Thanks alot! I am super newbie to ubuntu and linux. =)

Do this in a terminal.

```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

This will do the trick for 32 bit.  Exclude the plugin if running 64 bit.

---

### Post by franziss123 on 2008-05-29
yea, it's working fine now. thanks alot guys!

---


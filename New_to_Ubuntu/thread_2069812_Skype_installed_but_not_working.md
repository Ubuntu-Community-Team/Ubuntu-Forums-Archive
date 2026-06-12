---
title: "Skype installed but not working"
date: 2012-10-11
forum: New to Ubuntu
---

### Post by Florio on 2012-10-11
Yesterday I managed to find and install Skype 4.0 onto lubunto 12.04 (it was not contained in the synaptic package manager as I had read elsewhere!!), but I've now discovered that I cannot get into the programme.

After installing it, I added a couple of contacts and then left it until today. When I now try to open Skype, the main panel appears for about one second, and then closes immediately. I've tried removing Skype and then reinstalling it, but the result is the same.

Does anyone have any helpful suggestions (seeing as I'm an absolute newbie, you'll have to explain anything involving the terminal in very simple terms!!!!);)

---

### Post by NikTh on 2012-10-11
> **Florio said:**
>  (it was not contained in the synaptic package manager as I had read elsewhere!!), but I've now discovered that I cannot get into the programme.

Hi , 

Uninstall skype and install it from software-center.(or terminal) Yes it is included BUT first you must enable the partners repository . 

```
gksudo software-properties-gtk
```Goto "Other software" and mark (tick the box) "Canonical Partners". 

Then run in terminal 

```
sudo apt-get update 
sudo apt-get install skype
```Thanks

---

### Post by Florio on 2012-10-11
Thanks very much NikTh for your quick and very helpful reply. Had no trouble following your instructions, but Skype still won't open. The small user panel appears for a split second and then disappears again. Very strange, since I had installed the programme yesterday, carried out the microphone test, and added a couple of contacts.  Any ideas?

---

### Post by Florio on 2012-10-11
Have managed to solve the problem, which was apparently widespread last year.

The solution is here:

[http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html](http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html)

Florio

---


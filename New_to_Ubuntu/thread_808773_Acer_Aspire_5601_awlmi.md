---
title: "Acer Aspire 5601 awlmi"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by dragonspitfire0 on 2008-05-26
I recently installed Ubuntu 8.04 and ran into some difficulty , I'm trying to get several things straighten out . I want to know if i can run compiz fusion on this laptop and how ? i looked in many forums but never found a way , i have some knowledge of Linux but not enough to get me this working .. help will be greatly appreciated..

---

### Post by iaculallad on 2008-05-26
> **dragonspitfire0 said:**
> I recently installed Ubuntu 8.04 and ran into some difficulty , I'm trying to get several things straighten out . I want to know if i can run compiz fusion on this laptop and how ? i looked in many forums but never found a way , i have some knowledge of Linux but not enough to get me this working .. help will be greatly appreciated..

Check first if you meet the minimum requirement to run Compiz, then read this [HowTo]("http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml") for the instructions on installing it to your system.

---

### Post by oedha on 2008-05-26
what is your display adapter ?
type in terminal :==> sudo lshw -short -C display

---

### Post by dragonspitfire0 on 2008-05-26
H/W path               Device      Class       Description
==========================================================
/0/100/2                           display     Mobile 945GM/GMS, 943/940GML Expr
/0/100/2.1                         display     Mobile 945GM/GMS/GME, 943/940GML

---

### Post by dragonspitfire0 on 2008-05-26
iaculallad i looked at the guide and ran into some issue , i believe i am able to use compiz fusion because i remember on 7.10 Ubuntu it worked properly ...

---

### Post by ardvark71 on 2008-05-26
Hi...

Looks like he (or she) has a Intel GMA 50 or something close to it.

[http://www.superwarehouse.com/Acer_Aspire_5601AWLMi_Notebook/LX.AB10J.005/ps/1492216](http://www.superwarehouse.com/Acer_Aspire_5601AWLMi_Notebook/LX.AB10J.005/ps/1492216)

What is the output of "glxinfo," out of curiousity?

Best Regards...

---

### Post by oedha on 2008-05-26
intel.......right
now....in terminal type :==> glxinfo | grep render
if the answer yes then your driver is already installed
now you have to install compiz 
from terminal :==> sudo apt-get install compizconfig-settings-manager

---

### Post by dragonspitfire0 on 2008-05-26
What's the command in terminal to view glxinfo ? because when i typed that in i got a long list of information ..

---

### Post by iaculallad on 2008-05-26
> **dragonspitfire0 said:**
> What's the command in terminal to view glxinfo ? because when i typed that in i got a long list of information ..

Code:

> glxinfo | grep render

---

### Post by dragonspitfire0 on 2008-05-26
Thank u , for all your help it's currently working correctly ... 
now that the compiz is working .. and may someone help me with my wireless lol ...  i read the forum for wireless acer laptop but i had no luck there ...

---

### Post by oedha on 2008-05-26
you must specify the adapter type......what is that ?
sudo lshw -short -C network

---


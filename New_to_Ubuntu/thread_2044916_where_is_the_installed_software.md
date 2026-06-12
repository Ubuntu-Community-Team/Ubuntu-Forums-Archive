---
title: "where is the installed software?"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by ame82 on 2012-08-20
iam trying to find the pre installed software like games and etc
where i can find it , and how to uninstall programes
so confused about the system instruction
i have ubuntu 12.04 on latitude e6500 , i have also finger print installed , but it never worked , 
it never works with win7 as well cos never found its driver

---

### Post by Wim Sturkenboom on 2012-08-20
Not using 12.04 but is there not something called 'software center' from where you can install / uninstall. It is the preferred way and only if one really has to, one can install by different means.

---

### Post by kc1di on 2012-08-20
> **ame82 said:**
> iam trying to find the pre installed software like games and etc
where i can find it , and how to uninstall programes
so confused about the system instruction
i have ubuntu 12.04 on latitude e6500 , i have also finger print installed , but it never worked , 
it never works with win7 as well cos never found its driver

Well there are several ways in Linux to find installed programs.

I find the easiest way is to install synaptic. and run that it has a tab to show all software that is installed . If your talking about finding the actual executable then most programs place that in /usr/bin. 

Lots of other ways to do it also, but perhaps that may be of help.

---

### Post by rosswmcgee on 2012-08-20
Soft ware center is on your panel left side. You can also try the dash board and

query synaptic. Then you can drag synaptic to your panel.

---

### Post by cortman on 2012-08-20
See [here]("http://www.google.com/search?btnG=1&pws=0&q=how+to+install+software+in+ubuntu").

---

### Post by ame82 on 2012-08-21
> **Wim Sturkenboom said:**
> Not using 12.04 but is there not something called 'software center' from where you can install / uninstall. It is the preferred way and only if one really has to, one can install by different means.

i ment when i install some programe how can i find it to run it

---

### Post by NikTh on 2012-08-21
> **ame82 said:**
> i ment when i install some programe how can i find it to run it

You can click on Dash (Ubuntu Icon up-left on Launcher) and write the name of the program you have been install. 

**Tip:** When you are on the Ubuntu Desktop workspace ,  place the cursor on top bar and you will see "help" option. Click it , it will open "Ubuntu Desktop Guide" you will find a lot of stuff there.
Thanks

---

### Post by Zvezdica27 on 2012-08-21
there are several ways to uninstall stuff:
1) Software center
2)Synaptic (it's not installed by default: sudo apt-get install synaptic should do the trick)
3) apt get: sudo apt-get remove program_name_or_package

if you install your own stuff (tarballs) it depends... if it integrates in the system, read the info files on what to do.

If not (standalone app), it's just a matter of deleting the folder and config files (usually in home or in the folder).

zz

---


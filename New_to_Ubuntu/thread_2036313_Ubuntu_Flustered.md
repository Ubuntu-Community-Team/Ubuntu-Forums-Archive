---
title: "Ubuntu Flustered"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by gord66 on 2012-08-01
I downloaded Ubuntu 12, now I can`t get back to my Windows site. Also, I can`t
download any software as Ubuntu gives me an "error" message for every download
I try. Would like to uninstall,but looks like I`ll have to get a new  hard drive, as this has 
no uninstall. It`s a great program but I don`t have a choice of using Ubuntu or Windows.

---

### Post by 1204 on 2012-08-01
> **gord66 said:**
> I don`t have a choice of using Ubuntu or Windows.You weren't too spesific but maybe this helps [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Gone fishing on 2012-08-01
Windows should be listed in grub you just select Windows. If it isn't there try openning a terminal and running ```
sudo update-grub
```. 
When you try to install software (using Ubuntu software centre) and it gives an error what is the error? it is probably very easy to fix.

To uninstall Ubunt simply put in your Windows install CD and go to repair consol and run fixmbr (XP) or Bootrec.exe /FixMbr (Vista or 7). You can remove the Linux partitions in disk management.

---

### Post by gord66 on 2012-08-02
Thx for the info. I`ll be back to let you know how it went.

---

### Post by gord66 on 2012-08-02
Hi gone fishing,
How do I open up a terminal?

---

### Post by Breadified on 2012-08-02
You can either press CTRL-ALT-T to open terminal, or alternately you could go into "Dash home" in the top left of your screen and start to type "Terminal" into the search bar. It'll come up - click on it and there you go!

---

### Post by gord66 on 2012-08-02
To Breadified:
Thank You

---

### Post by Breadified on 2012-08-02
Not a problem, you're welcome. 

As well, if you're using the "Dash home" method then to bring up that menu without clicking you can use your "Super key" (i.e. the Windows logo on most keyboards).

Hope Gone Fishing's advice works out for you.

Cheers.

---


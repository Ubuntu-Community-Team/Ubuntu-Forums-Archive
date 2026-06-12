---
title: "basic help require please"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by pd123 on 2008-10-16
Hi Guys,

I have been on here all night and not found my answers, i am new to ubuntu, I have all my progams on my flash drive and have mobile broadband in the form of a t mobile web n walk stick.

If anyone could tell me how to install my programs i am compltely lost.

Also I hav an internet conection running windows, so can get th laptop running ubuntu online

Paul

---

### Post by zidane2 on 2008-10-16
What programs?
If they are windows .exe programs then you are going to need wine to run them.

---

### Post by pd123 on 2008-10-16
they all are .exe is thi possible?

paul

---

### Post by zidane2 on 2008-10-16
Open the applications menu and click on the bottom button it says add/remove. Search for wine and install it then you might be able to run some of those programs, but not all are supported you can see more about that [here]("http://appdb.winehq.org/").

Hope this helps

---

### Post by Sarmacid on 2008-10-16
It's possible to run a lot of .exes with wine, but not all. To try it out, go to a console and run

```
cd /path/to/the/exe
wine yourprogram.exe
```

I would look for linux programs that do what you need natively instead of forcing them to run with wine.

---

### Post by oldos2er on 2008-10-16
> **pd123 said:**
> they all are .exe is thi possible?

paul

 Windows executables do not run natively on Linux. But as was mentioned, Wine will run some Win* apps. You should look into Linux apps to take the place of your Win* apps: [http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---


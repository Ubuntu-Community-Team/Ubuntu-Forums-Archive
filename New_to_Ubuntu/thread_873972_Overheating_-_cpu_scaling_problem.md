---
title: "Overheating - cpu scaling problem"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Esben Kramer on 2008-07-29
Hello fellow Ubuntians. 

Since I upgraded from 7.10 to 8.04, I have had some problem with overheating on my laptop. The fan works a lot harder than it used to, but it used to be almost soundless. When I try to add the CPU frequency scaling-applet to the panel, it tells me that it is either not supported or some module(s) may be missing. I have a Centrino 1.7ghz intel computer. 

Is it safe to try out some of the other CPU scaling tools (like 'cpudyn') or should I take some other route?

Thanks in advance!

---

### Post by Diabolis on 2008-08-02
Check which process is using so much the CPU.
```
top
```

press **q** to close it.

---

### Post by sayakb on 2008-08-02
Press Alt+F2, type in **gconf-editor**.
Navigate to **/apps/gnome-power-manager/cpufreq**
Change the **policy_ac** and **policy_battery** values to lower values and see if this works.

---

### Post by Francewhoa on 2009-01-31
Same here with Ubuntu 8.04 and Toshiba A8 laptop. [This post]("http://ubuntuforums.org/showpost.php?p=6654274&postcount=8") worked for me.

---


---
title: "Installation Problems"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by mustardseedcba on 2012-02-13
[FONT=Liberation Serif, Times New Roman, serif]I am able to download software but it will not install. 
 Here is the popup I receive.[/FONT]
 

 [FONT=Liberation Serif, Times New Roman, serif]"Cannot Open Location[/FONT]
 [FONT=Liberation Serif, Times New Roman, serif]file: ///(name)_setup.exe: Error stating file '/ (location/name) _setup.exe: No such file or directory[/FONT]"


[FONT=Liberation Serif, Times New Roman, serif]Is there software available to guide installation and overcome this problem?[/FONT]


[FONT=Liberation Serif, Times New Roman, serif]Thank you for your assistance.
[/FONT]

---

### Post by winh8r on 2012-02-13
That is a .exe executable file for Windows, this is not a native linux filetype.

You will need to install wine to run this file in ubuntu


```
sudo apt-get install wine
```

---

### Post by drmrgd on 2012-02-13
> **winh8r said:**
> That is a .exe executable file for Windows, this is not a native linux filetype.

You will need to install wine to run this file in ubuntu


```
sudo apt-get install wine
```

Just to add to Winh8r's excellent advice, you might also check the program at [Wine HQ]("http://www.winehq.org/") to verify it will run under Wine (not everything will, unfortunately) as well as to find out any kind of installation tips and tricks to get it working.

---


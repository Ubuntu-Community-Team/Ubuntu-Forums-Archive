---
title: "[SOLVED] have to run a windows program"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by mankoskidesu on 2008-07-11
This is my first time ever trying out linux and so far I like Ubuntu, but...

I tried to search for wine in the synaptic package manager but the only thing that showed up was kde-guidance.  I then added the wine repository:

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

Now I can see 1.1.0, but when I try to install it I get this message:

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

I am in china, and my internet service provider requires that I run a program in order to use the internet.  The program is "supplicant 1.1.1" and they don't have a linux version.  I cannot tell any more details about the program because it is in chinese.  Anyway, I am able to use the internet because I have another computer hooked up to my router and it is running the program.  I would like to run the program from my computer so that I dont need to have 2 computers on at all times.  It is a pretty simple program.  I think wine should be able to handle it, but I don't know.  Should I use wine for this, if so, how can I get around the error message I pasted above?

---

### Post by aktiwers on 2008-07-11
Hi and wecome,

Do you use the supplicant application to logon to the internet?

Maybe this will help
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
In terminal (applications => Accessories => Terminal) type:
```
sudo apt-get install wpasupplicant
```

To install wine, you should be able to simply type:
```
sudo apt-get install wine
```

---

### Post by sujoy on 2008-07-11
check this page for wine problems in hardy 
[http://forum.winehq.org/viewtopic.php?p=8887&sid=0010a3423df040a5e84a3927a2d35a78](http://forum.winehq.org/viewtopic.php?p=8887&sid=0010a3423df040a5e84a3927a2d35a78)

---


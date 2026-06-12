---
title: "HOWTO: Steam Tables (SteamTab Companion) on Linux"
date: 2008-02-16
forum: Outdated Tutorials &amp; Tips
---

### Post by djgrandmarquis on 2008-02-16
As far as I know, there are no (good) Linux applications for obtaining water properties (steam properties). However, ChemicaLogic's SteamTab Companion is very handy freeware, but it is Windows-only. Fortunately it is compatible with WINE. Generally I do not advocate WINE but in this case it works quite well. This is how I installed SteamTab on my system.

**Running SteamTab Companion**

1. Download SteamTab Companion (free, registration required):
[http://www.chemicalogic.com/...]("http://www.chemicalogic.com/steamtab/companion/default.htm")

2. Install wine from your package manager, or install it via the command line:
```
sudo apt-get install wine
```

3. Run SteamTab Companion using WINE:
```
cd /path/to/SteamTab.exe
wine SteamTab.exe
```

**Optional: Create *steamtab* Command**

I chose to install SteamTab for my entire system.

4. Create the system's SteamTab executable:
```
sudo mkdir /usr/local/bin/win32
sudo cp /path/to/SteamTab.exe /usr/local/bin/win32/steamtab.exe

```

5. Create the steamtab command. Using your favorite text editor (I used vim), create the script file:
```
/usr/local/bin/steamtab
```

in my case I created it like this:
```
sudo vim /usr/local/bin/steamtab
```

Now inside the steamtab file insert this text:
```
#!/bin/sh
wine /usr/local/bin/win32/steamtab.exe
```

6. Make steamtab executable:
```
sudo chmod 755 /usr/local/bin/steamtab
```

7. Now you may call the SteamTab Companion system-wide:
```
steamtab
```

---

### Post by bhavi on 2008-03-24
Thanks for the detailed info My freind wanted to install steam tables so I will send this link to hm...

---


---
title: "I am unable to launch Programs downloaded from the software centre"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Warrio1209 on 2013-02-14
Solved

---

### Post by iMac71 on 2013-02-14
you might use synaptic instead of ubuntu software centre for installing applications```
sudo apt-get install -y synaptic
```

---

### Post by oldos2er on 2013-02-14
> **Warrio1209 said:**
>  I can't access steam, latex etc so if someone could please help it would be much appreciated.


Can you open a terminal (Ctrl-Alt-t), run ```
steam
``` and post the output here?

---

### Post by Warrio1209 on 2013-02-15
Here it is Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1360775438_client)
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  12
xerror_handler: X failed, continuing
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  19 (X_GLXQueryServerString)
Serial number of failed request:  41
xerror_handler: X failed, continuing
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadRequest (invalid request code or no such operation)
Major opcode of failed request:  154 (GLX)
Minor opcode of failed request:  14 (X_GLXGetVisualConfigs)
Serial number of failed request:  70
xerror_handler: X failed, continuing
Looks like steam didn't shutdown cleanly, scheduling immediate update check
Installing breakpad exception handler for appid(steam)/version(1360775438_client)
Installing breakpad exception handler for appid(steam)/version(1360775438_client)

---

### Post by oldos2er on 2013-02-15
For help with Steam, try here: [https://support.steampowered.com/](https://support.steampowered.com/)

I'm not sure I understand what exactly your problem is, because Software Center is just a front-end to the APT system, same as Synaptic, or apt-get, etc. If you start Software Center in a terminal with ```
software-center
``` and install a program, it could show any potential problems.

---

### Post by grahammechanical on 2013-02-15
This may be related to certain applications that you have installed, even through the software Centre. You have tried loading from the terminal. That usually provides error messages that we do not usually see when simply clicking an icon in the Dash.

Please select one of these problem programs and load it from the terminal and then paste the error messages here (enclosed in code tags). Other than Steam.

I found this in relation to GLX

[http://www.ntlug.org/archive/tp/glx_ccox/glx.html]("http://www.ntlug.org/archive/tp/glx_ccox/glx.html")

The issue might not be due to the software Centre at all but down to the video card and/or its drivers.

Regards.

---

### Post by Warrio1209 on 2013-02-16
Thankyou, I'll try synaptic

---

### Post by Warrio1209 on 2013-02-16
You are right, I just downloaded the most basic program I could find, an "angband" game and had no issues with it. The problem is not with the software center but the programs. The case is closed. Thankyou all for your help.

---

### Post by oldos2er on 2013-02-17
> **Warrio1209 said:**
> Solved

I'm glad your problem is solved, but I wish you had not deleted your post. We like to leave solved threads around to help others who might be having the same problems. Also the proper way to mark a thread solved is under the Thread Tools menu at the top of the thread.

---

### Post by Krytarik on 2013-02-27
> **oldos2er said:**
> [QUOTE=Warrio1209;12509187]SolvedI'm glad your problem is solved, but I wish you had not deleted your post. We like to leave solved threads around to help others who might be having the same problems.[/QUOTE]
Since the OP didn't put it back since 10 days now, just for the record (pulled from Google's cache back then):
> **Warrio1209 said:**
> The title says it all really. I am new to ubuntu, having used it for about a week. I'm running 12.04 Quantel Quetzel. Its on a laptop so I have used the /grub powersaver fix and have jupiter. All of the time I have had ubuntu I have been unable to launch a single program downloaded from the software centre. They download fine, and after I click on them the updating/patching screens come up but then, nothing happens. This is the case no matter where I run them from, be it dash, the terminal or launcher. It seems that the programs think they are running because if I try to open multiple copies of some they say they cannot because a copy is already open. I have tried checking the workspaces but there isn't anything open there either. The default third party software runs fine and if I download something directly or install it via a package that works too, so long as, at no point in its installation it is redirected to the software centre. I've checked the forums and nobody else appears to be having the same or similar problems. This is becoming quite an issue seeing as it means I can't access steam, latex etc so if someone could please help it would be much appreciated.

Thanks,
Warrio out.Regards.

---

### Post by oldos2er on 2013-02-27
Nice, thank you!

---


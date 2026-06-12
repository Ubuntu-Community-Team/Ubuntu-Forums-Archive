---
title: "HOWTO: SSH Tunneling"
date: 2007-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by LookTJ on 2007-10-23
I did this on Firefox. But you can set it up on other apps such as pidgin. It's simple. This HOWTO is avaibable only on Linux(I'll do a Windows HOWTO video once I get my hands on a windows recording app.

YouTube Videos:

[Linux - Part 1]("http://www.youtube.com/watch?v=oDl1WXRoC1g")
[Linux - Part -2]("http://www.youtube.com/watch?v=hzHAg1DUaoI")

Linux: (refer to video if you don't understand)

**STEP 1:**

Open a terminal or use a TTY. then type ```
ssh -D port-number-you-like(ex.8081) user@host
```

**STEP 2:**

Open Firefox

> Edit->Preferences->Advanced->Network Tab-> Settings

then click on manual proxy configuration. On the SOCKS host box

host: **localhost**
Port: **port number you picked(ex.8081)**

Simple

Windows:

**STEP 1:**

Download PuTTY and install it. follow the installation steps.

On Hard drive: [http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe)

If you want to use Putty at work, you can install the portable edition on the usb flash drive: [http://downloads.sourceforge.net/portableapps/PuTTY_Portable_0.60.paf.exe?download](http://downloads.sourceforge.net/portableapps/PuTTY_Portable_0.60.paf.exe?download)

**STEP 2:** type the hostname you want to connect to

**STEP 3: **Now on the sidebar, you should see "[+]SSH". hit the + and look for tunneling. Now choose the port like 8085 then click dynamic. Add it.

Optional: If you want to save your settings, go back to the Session tab and name the config and save it.[B]

STEP 4:[/B] Open your browser you use. Go to connection settings.

If on IE(Internet Explorer) Click LAN Settings then click Advanced. In the SOCKS host, enter: host as localhost and port as whatever you picked(ex. 8081)


If on Firefox: Tools->Options->Advanced->Network tab->Settings. in the SOCKS host; localhost in the host box, and port as whatever you picked/entered in PuTTY(ex.8081)

---

### Post by LookTJ on 2007-10-29
BUMP:  for the newbs.

---


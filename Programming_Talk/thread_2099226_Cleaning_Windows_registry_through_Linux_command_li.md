---
title: "Cleaning Windows registry through Linux command line interface"
date: 2012-12-29
forum: Programming Talk
---

### Post by s3a on 2012-12-29
Is it possible to remove unused registry entries in a Windows installation by using the CLI in Linux? For example, when one uninstalls a program, not everything is removed from the Windows registry. If it's possible, how can make it so that everything that is unused is removed? My goal is to have a script that automates this hence the command line requirement.

Any input would be greatly appreciated!

---

### Post by PaulM1985 on 2012-12-29
Why use linux CLI? It seems to be a job much more suited to actually be done in Windows.

---

### Post by ofnuts on 2012-12-29
> **s3a said:**
> Is it possible to remove unused registry entries in a Windows installation by using the CLI in Linux? For example, when one uninstalls a program, not everything is removed from the Windows registry. If it's possible, how can make it so that everything that is unused is removed? My goal is to have a script that automates this hence the command line requirement.

Any input would be greatly appreciated!
- How can you tell a registry entry is "unused". AFAIK There is no "last access timestamp" for these.
- See [http://commandwindows.com/reg.htm](http://commandwindows.com/reg.htm) for .BAT. if you use python there is also a _winreg (2.7) or winreg (3.x) module: [http://docs.python.org/2/library/_winreg.html](http://docs.python.org/2/library/_winreg.html)

---

### Post by cwsnyder on 2012-12-29
I have seen more damaged Windows installations caused by BAD registry 'cleaner' type programs than I have seen Windows installations helped by registry cleaners.  The ONLY cleaners which I have had good, consistent results from is the registry cleaning portion of Piriform's CCleaner, or Glarysoft's Glary Utilities run from within Windows.

---

### Post by s3a on 2012-12-29
Thanks for the replies but, I haven't encountered any problems with registry cleaners before and, I really want to get this done in Linux if possible.

Will the winreg module allow me to modify the registry of a Windows installation on one hard drive by using a Linux installation on another hard drive? I have a feeling that it won't natively but, what if I run it using wine?

---

### Post by cwsnyder on 2012-12-29
As I recall, there was mention of 'fixing' or at least restoring a backup of the registry in the instructions for the System Rescue CD.  You might try there.

---

### Post by Habitual on 2012-12-29
> **s3a said:**
> Is it possible to remove unused registry entries in a Windows installation by using the CLI in Linux?...

If they are unused, why are you wanting to remove them?
Wine won't work.

Your best bet is to export the hive of any keys you are interested in, edit them in a safe environment such as Linux, and re-import the hive back into the target host's Registry.

---

### Post by fyfe54 on 2012-12-29
+1 for CCleaner.  

I have used it for years without incident - It has a feature that allows you to backup your registry changes just in case you have to undo them.  I have never had to.

---


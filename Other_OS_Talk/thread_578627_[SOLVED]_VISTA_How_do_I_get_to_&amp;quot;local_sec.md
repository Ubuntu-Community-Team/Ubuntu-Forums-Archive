---
title: "[SOLVED] VISTA: How do I get to &amp;quot;local security policies&amp;quot;"
date: 2007-10-17
forum: Other OS Talk
---

### Post by mister_lister on 2007-10-17
The core of this issue is some communication issues between Samba and Vista. I found a solve here, take a quick peek it is not long winded and will give you background on my question:

[http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746](http://www.builderau.com.au/blogs/codemonkeybusiness/viewblogpost.htm?p=339270746)

BUT the first step, getting to the "local security policy" setting, does not work in Vista Home Premium, when I type that filename in the run command it says it could not find the file. I am looking for a way to get to "local security policy" settings in that flavor of Vista and thus far I have not found it. Could it be it is not available with this flavor of M$ crap?

I have searched control panel, mmc snap ins, and "manage computer" with no luck. If anyone knows a way to get to "local security policies" with Vista Home Premium or Home please let me know.

---

### Post by ddrichardson on 2007-10-18
Yes, this appears to have disappeared from my Vista Premium install, apparantly this is a workaround:

[I]1. Run the registry editor and open this key: 
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa 
1. If it doesn't already exist, create a DWORD value named 
LmCompatibilityLevel 
3. Set the value to 1 
4. Reboot[/I]

---

### Post by mister_lister on 2007-10-18
Thanks, will give it a try.

---


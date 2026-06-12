---
title: "msi file"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Sham885 on 2008-06-07
I'd like to install a weather program I used all the time on windows but it downloaded as a .msi file.  I tried going through wine and clicking the file and got "There is no application installed for this file type".  So after searching google and the forums I tried using "wine msiexec /i" command in the terminal and got this string of error messages:

```
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:msi:copy_package_to_temp failed to copy package L"weatherbugsetupz6167.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"weatherbugsetupz6167.msi"

```

Is it possible (or worth the trouble) to install this program?

---

### Post by Fedz on 2008-06-07
Your choice obviously but isn't Ubuntu weather [screenlets](http://www.screenlets.org/index.php/Home) suitable?

Available from Ubuntu > System > Admin > Synaptic Package Manager.

---

### Post by Sham885 on 2008-06-07
Since I don't really see much of a description on the screenlets I wouldn't know.  Weatherbug is based here and has many very reliable stations across the state.  Their radar is usually better than weather.com or watching the news and it updates constantly.  The forecast is nearly always perfect and the custom alerts is great when you have a stable full of horses to worry about.  Now if someone can find me the equivalent of that then great but I don't see much info on any weather program for ubuntu.  I'm getting tired of relying on weather.com and it wasn't even that accurate or else just behind when it came to the storm on thursday.

---


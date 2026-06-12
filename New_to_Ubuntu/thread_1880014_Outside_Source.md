---
title: "Outside Source?"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Mikesla on 2011-11-12
I am looking for an external way to download the proper drivers without the Software Center, is there such a trusted site?

 Reason why I am asking this is I want a hard copy for all the drivers, updates, patches in case I no longer have the ability of an internet connection. 

Is there a way in Ubuntu, and in the Software center to save the files to the harddrive instead of having them install directly? If I can do that then no problem I can get all the files I need, but if I can't then I guess I am out of luck.

 On another note, I am looking for modem drivers, and I am pretty sure I can do this but when I try to install certain  .deb files I am told that I am missing files to do a proper install. I don't understand why all the required lib files are not installed in Ubuntu 11.10. For instance I am trying to install modem drivers which I do know work, but the error is telling me I require a C compiler even though it's a .deb file. I have no idea where to get the lib files. I need those files to install the proper modem drivers, but without the internet whats the point.

Anyway, if anyone has a website I can visit to get the proper drivers I need please, please let me know.

Thank You.

---

### Post by cgroza on 2011-11-12
You can download them using apt and then go to /var/cache/apt and copy them from over there.
Then, you can put the packages in the /var/cache/apt of the target machine and when you will do an apt-get install, it will use those packages. Plus, you get the dependency resolution of apt.


You can also use dpkg or the Software Center to manually install the packages, but you may have to install the packages in the right order yourself.

---

### Post by Mikesla on 2011-11-12
> **cgroza said:**
> You can download them using apt and then go to /var/cache/apt and copy them from over there.
Then, you can put the packages in the /var/cache/apt of the target machine and when you will do an apt-get install, it will use those packages. Plus, you get the dependency resolution of apt.


You can also use dpkg or the Software Center to manually install the packages, but you may have to install the packages in the right order yourself.

 Thank You.

I'm wondering if all the drivers can be packaged with an export function, then have a program that would import them into a new copy of Unbuntu like one large .deb package.

Now that would be a cool util.

Again thank you, now I know where to begin. :)

---


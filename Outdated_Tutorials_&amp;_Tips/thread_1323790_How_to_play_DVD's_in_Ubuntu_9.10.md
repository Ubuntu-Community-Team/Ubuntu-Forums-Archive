---
title: "How to play DVD's in Ubuntu 9.10"
date: 2009-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by zkriesse on 2009-11-12
To play DVD's in Ubuntu 9.10 first you will need to install the following packages. The reason that you have to install these packages is because most DVD's are copyright protected or some such stuff. To "bypass" this protection you must install packages. As such, [COLOR=Red]**Please go to the following page to read about [COLOR=Blue][Restricted Formats]("https://help.ubuntu.com/9.10/add-applications/C/#restricted-software")[/COLOR] BEFORE following these steps. **[COLOR=Black]Now for the packages.

1. You will need to install the following packages. To install them just click on the package name. [/COLOR][/COLOR]**[libdvdnav4]("apt:libdvdnav4")** **[libdvdread4]("apt:libdvdread4")** **[gstreamer0.10-plugins-bad]("apt:gstreamer0.10-plugins-bad")** and then [B][gstreamer0.10-plugins-ugly]("apt:gstreamer0.10-plugins-ugly")
[/B]  
2. For playing Encrypted DVD's you will need to do this. Open up your terminal which can be found by going to Applications -> Accessories -> Terminal. In the terminal type the following,
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```[COLOR=Red][COLOR=Black] 
NOTE: When you type the above in the terminal it will most likely ask you for your password, enter it but note that as you enter it you WILL NOT SEE IT. This is normal and not an error. Just enter your password as normal and then hit enter. After that you're done! Just stick a DVD of your choice in your drive and then enjoy. Don't forget the popcorn!
[/COLOR][/COLOR]

---


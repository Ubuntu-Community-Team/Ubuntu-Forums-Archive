---
title: "Samba fix and question"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-11-10
I am posting this as a lot of people seem to have trouble accessing Windows shares with samba. I did a lot of research and tweaks and still no files. But what finally fixed it was something I tried on my own and was never mentioned in any of the directions I saw. After setting it up on windows and Ubuntu 11.04 I clicked on Places-Connect to server. Then under service type at top-click on drop down box and select Windows Share, then in same window type name of windows computer (computer name not network or share name) which you get my right clicking my computer on windows start menu and selecting properties.Then click connect and wow I had my shares. Maybe this isn't mentioned as it is too obvious but it wasn't to me. I kept trying to connect through Places-Network with no luck.Now my question: this is a public library and I would like our librarian's Ubuntu 11.04 machine to be able to stay connected or reconnect after boot without her having to type all the stuff in on the connect to server window. Is that possible? Thank you

---

### Post by capscrew on 2011-11-10
> **cmcanulty said:**
> I am posting this as a lot of people seem to have trouble accessing Windows shares with samba. I did a lot of research and tweaks and still no files. But what finally fixed it was something I tried on my own and was never mentioned in any of the directions I saw. After setting it up on windows and Ubuntu 11.04 I clicked on Places-Connect to server. Then under service type at top-click on drop down box and select Windows Share, then in same window type name of windows computer (computer name not network or share name) which you get my right clicking my computer on windows start menu and selecting properties.Then click connect and wow I had my shares. Maybe this isn't mentioned as it is too obvious but it wasn't to me. I kept trying to connect through Places-Network with no luck.Now 

my question: this is a public library and I would like our librarian's Ubuntu 11.04 machine to be able to stay connected or reconnect after boot without her having to type all the stuff in on the connect to server window. Is that possible? Thank you

Samba is a suite of protocols.  The ***[COLOR="Blue"]smbd[/COLOR]*** daemon (process) handles the SMB protocol to interact with the shares.  The daemon ***[COLOR="DarkGreen"]nmbd[/COLOR]*** is what handles the name services and populates the Browse List.

You need both processes working correctly to a) [COLOR="DarkGreen"]browse for shares[/COLOR] and b) [COLOR="Blue"]interact with the shares[/COLOR] 

If Samba is setup correctly then the shared directories should appear and can be bookmarked for future use.

---

### Post by HermanAB on 2011-11-10
> my question: this is a public library and I would like our librarian's Ubuntu 11.04 machine to be able to stay connected or reconnect after boot without her having to type all the stuff in on the connect to server window. Is that possible?

Yes of course.  Add a mount point in /mnt and add a cifs line to /etc/fstab to mount the share.

---

### Post by Morbius1 on 2011-11-10
You've got 2 solutions so far so how about a 3rd: Gigolo

If you are currently using the "connect to server" method and are fine with how it mounts the remote share, Gigolo can do this automatically at boot. Here's a mini HowTo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Note: If for some reason you can't browse to the share in Gigolo either then there is a "Connect to Server" function in that utility as well:
Gigolo > Actions > Connect

---

### Post by capscrew on 2011-11-10
> **Morbius1 said:**
> You've got 2 solutions so far so how about a 3rd: Gigolo

If you are currently using the "connect to server" method and are fine with how it mounts the remote share, Gigolo can do this automatically at boot. Here's a mini HowTo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Note: If for some reason you can't browse to the share in Gigolo either then there is a "Connect to Server" function in that utility as well:
Gigolo > Actions > Connect

Gigolo brings Gnome (Nautilus) functionality to other desktops (Xfce, KDE, etc.).  Quoting the developer; *[COLOR="DarkSlateGray"]"Gigolo is a frontend to easily manage connections to local and remote filesystems using GIO/GVfs" [/COLOR]*.  It's still dependent upon setting up Samba and name services correctly.  I have Gigolo installed on my desktop machine just to play around with it.  

On the other hand @HermanAB's method is a common hack to eliminate the need for browsing.  I find it idiosyncratic to that particular share.  I would prefer to set the system up correctly.  Then shares can be may be added or deleted and the system will continue to "just work".

---


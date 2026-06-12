---
title: "[SOLVED] there must be someone who could help (updating software)"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-17
> **nakama85 said:**
> hi guys.
I am using 8.04
I am really in need of two software updates.

The First is Gimp 2.62

This is really a must for me. I really need the latest version. Is there any way I could get it.

The second is Vlc 9.6
While it is not as important as Gimp it would be nice because I was used to using 9.6 in Windows and because 8x is no longer supported by the videolan team it would be nice to have it.

Perhaps I am asking the impossible. If so Please let me know 

Thanks

The Gimp Problem was Solved (please see 5th post in this thread for the solution)

However I am still desperately searching for a way to install vlc 9.6

Please any help would be great. thanks

_*Just a side note. I have no idea how to compile source and getdeb.net is down------but thanks for the advice OutOfReach... I know you were trying to help and I appreciate that. :)*_

---

### Post by OutOfReach on 2008-11-17
The way I see it, you have 3 options:
1. Wait until the packages come available in the repositories
2. Compile the programs from source
3. Possibly find the programs on getdeb.net or some other (trusted) source.

---

### Post by nakama85 on 2008-11-17
> **OutOfReach said:**
> The way I see it, you have 3 options:
1. Wait until the packages come available in the repositories
2. Compile the programs from source
3. Possibly find the programs on getdeb.net or some other (trusted) source.

Thanks for the response i will give #3 a try. Is there anywhere I could get directions to compile from source

---

### Post by nakama85 on 2008-11-17
getdeb.net is not loading... are there any other places i could check?

---

### Post by nakama85 on 2008-11-17
well the gimp part is solved at least

I simply followed the directions from

[http://www.ubuntugeek.com/how-to-install-gimp-261-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-gimp-261-on-ubuntu-804-hardy-heron.html)

I am still looking for vlc though

---

### Post by nakama85 on 2008-11-17
bump

---

### Post by bennachie on 2008-11-18
Have a look at [http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

You want the "unstable" branch, which should contain 0.9.6. The two sources identified in the website need to be added to your list of third-party repositories (look under the system menu in Gnome for the application) after which you could either use the normal "add/remove" mechanism or open a terminal window and use the apt-get commands recommended on the website.

---

### Post by nakama85 on 2008-11-18
> **bennachie said:**
> Have a look at [http://www.videolan.org/vlc/download-debian.html](http://www.videolan.org/vlc/download-debian.html)

You want the "unstable" branch, which should contain 0.9.6. The two sources identified in the website need to be added to your list of third-party repositories (look under the system menu in Gnome for the application) after which you could either use the normal "add/remove" mechanism or open a terminal window and use the apt-get commands recommended on the website.

thanks so much that worked!!!!:KS:guitar:\\:D/

---


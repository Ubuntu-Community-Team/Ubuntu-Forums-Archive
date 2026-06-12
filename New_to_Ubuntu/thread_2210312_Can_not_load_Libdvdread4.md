---
title: "Can not load Libdvdread4"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by seagiant on 2014-03-10
Hi,
      Trying to get DVD's to play after installing Ubuntu 12.04LTS and when I go to Terminal to get this program downloaded,it tries but wont download??? Any ideas on this? I have Movie player and VLC.

Hi,
     This is what I get on Terminal

eg@greg-HP-G60-Notebook-PC:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for greg: 
--2014-03-10 08:38:55--  [http://download.videolan.org/pub/debian/stable//Packages](http://download.videolan.org/pub/debian/stable//Packages)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... failed: Connection timed out.
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:0:2|:80... failed: Network is unreachable.
Dynamic fetch failed; Falling back to static fetch
--2014-03-10 08:41:03--  [http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb](http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... failed: Connection timed out.
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:0:2|:80... failed: Network is unreachable.
greg@greg-HP-G60-Notebook-PC:~$

---

### Post by ibjsb4 on 2014-03-10
Is this how you installed it?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Installing_libdvdcss)

---

### Post by seagiant on 2014-03-10
Hi,
     Yes!  Thanks!

---

### Post by ibjsb4 on 2014-03-10
Good deal

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

### Post by seagiant on 2014-03-10
Hi,
     Houston! I think we have a problem!

   That is how I TRIED to install it and the copy of the Terminal transcript is what I got back! No matter what I try I cannot get it to download!!! Please notice in transcript "Network is unreachable???" Thanks!

---

### Post by Frogs Hair on 2014-03-10
If you have installed the ubuntu-restricted-extras the package is included per the restricted formats link.

---

### Post by seagiant on 2014-03-10
Hi,
     Ok,then why are the DVD's not playing? Any other ideas? Thanks again!

---

### Post by Frogs Hair on 2014-03-10
I only had success with original the libdvdcss2 package from the now closed medibuntu repository . Fortunately I don''t watch movies from dvd on my computer . I was using the default movie player at the time.

---

### Post by seagiant on 2014-03-10
Hi,
     Still looking for an answer to this. Thanks!

---

### Post by oldos2er on 2014-03-10
The videolan server might have been down temporarily, I just tried it and it seems to be working. Give this command another try: ```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by seagiant on 2014-03-10
reg@greg-HP-G60-Notebook-PC:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for greg: 
--2014-03-10 19:01:41--  [http://download.videolan.org/pub/debian/stable//Packages](http://download.videolan.org/pub/debian/stable//Packages)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... failed: Connection timed out.
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:0:2|:80... failed: Network is unreachable.
Dynamic fetch failed; Falling back to static fetch
--2014-03-10 19:03:53--  [http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb](http://download.videolan.org/pub/debian/stable/libdvdcss2_1.2.13-0_i386.deb)
Resolving download.videolan.org (download.videolan.org)... 88.191.250.9, 2a01:e0d:1:3:58bf:fa02:0:2
Connecting to download.videolan.org (download.videolan.org)|88.191.250.9|:80... failed: Connection timed out.
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:0:2|:80... failed: Network is unreachable.
greg@greg-HP-G60-Notebook-PC:~$ 
Hi,
     Gave me the same message?

---

### Post by deadflowr on 2014-03-10
Your posted links are totally fine, from my end at least.
So, I would think something between you and videolan is blocking your connection.
Where are you trying to connect from?
(Sometimes universities and school block sites like that, or could also be the ISP too.)

---

### Post by seagiant on 2014-03-11
Hi,
      Thanks, no I'm just on a private cable hook up and I totally wiped out Windows when I went to Ubuntu 12.04 LTS! Is there a way to go to another location on another computer and just load this to a USB chip and transfer straight to this computer?  Thanks again!

---

### Post by deadflowr on 2014-03-11
If you click on the second link in orange in post number 12
(the link with .deb at the end)
while using firefox(or any other browser)
Does it ask you to save the file?

Or does nothing happen at all.

If it asks to save it, then it'll save the deb file in the Downloads folder.
From there simply double click on the package and the installation process will start.
(it'll open the software center, and eventually ask to install)

If nothing happens, then it is quite a possible that your ISP is simply blocking you for that site.
(I'm doubtful of this but it is a possibility nonetheless)

---

### Post by seagiant on 2014-03-11
Hi,
     Neither one of those sites will come up for me???? This is getting wierd! I have NO idea why the conputer wont have anything to do with Videolan.org??? Thanks again!

Hi DF,
          I went back and tried your "DEB" link and it worked! I now have the apps I needed and my computer will play DVD's in the VLC Player!!! Thank you very much and problem now is SOLVED (Thank you Houston!)

---

### Post by bapoumba on 2014-03-12
> **seagiant said:**
> Thank you very much and problem now is SOLVED (Thank you Houston!)

Then you can mark your thread as solved, as suggested earlier ;)

---

### Post by seagiant on 2014-03-12
Hi,
     How do you do that? Tutorial is gone! Sorry!

---

### Post by bapoumba on 2014-03-12
> **seagiant said:**
> Hi,
     How do you do that? Tutorial is gone! Sorry!

Ah.. here you go [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


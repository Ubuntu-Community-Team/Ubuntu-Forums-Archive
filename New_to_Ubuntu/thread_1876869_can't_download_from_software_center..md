---
title: "can't download from software center."
date: 2011-11-07
forum: New to Ubuntu
---

### Post by Keshav2050 on 2011-11-07
I am not able to download anything from Ubuntu software center.
When I typed the command 'sudo apt-get update' in the terminal I got the following error.



**"**W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.**"**



What should I do?

---

### Post by wildmanne39 on 2011-11-07
Hi, this is how to replace the GPG key error when installing packages.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID
```
and replace KEYID with the number shown in the error message.
Thank you

---

### Post by Keshav2050 on 2011-11-07
I have replaced KEYID with '40976EAF437D05B5' as it was in the error. Then I tried the command 
'sudo apt-get update' but then I got the following error.


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.



What should I do?

---

### Post by Keshav2050 on 2011-11-07
Can anyone help me? I am not able to download anything from ubuntu software center.
I've typed the command 'sudo apt-get update' and I got the error
[B]

"[/B]Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
[B]"


[/B]what should I do, can anyone help me?

---

### Post by Sef on 2011-11-07
I would try a different server. Open the Software Center > Edit > Software Sources > change to a different one

---

### Post by Keshav2050 on 2011-11-07
**Thanks for your advice.**


It's not like I can't open the software center, when I click the button 'Install' it gives messages 
[B]
"failed to download package files[/B]
  check your internet connection[B]"

[/B]and then,

[B]"Requires Installation Of untrusted Packages
[/B]The action would require the installation of packages from not authenticated sources.**"**

and in details it gives**"**libcddb2 libdvbpsi7 libebml3 libiso9660-7 libmatroska4 libsdl-image1.2 libtar0 libupnp3 libva-x11-1 libvcdinfo0 libxcb-keysyms1 libxcb-randr0 libxcb-xv0 videolan-doc**"**

What are untrusted packages and to what sources I should use so that computer will be safe?

---

### Post by wildmanne39 on 2011-11-07
Hi, try it this link please:
[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)
Thank you

---

### Post by amjjawad on 2011-11-07
> **wildmanne39 said:**
> hi, try it this link please:
[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)
thank you

+1

---

### Post by Keshav2050 on 2011-11-15
Solved in another thread 
 				[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 				**Can't install from software center**

---

### Post by Keshav2050 on 2011-11-15
Solved in another thread 
 				[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] 				**Can't install from software center**

---

### Post by the.phantom on 2011-11-15
3 post on the same topic by same person and just says "solved in another post"
usually people post what fixed it, not just "solved"

---

### Post by lisati on 2011-11-15
Threads merged. Please do not start multiple threads for the same problem, it dilutes the community's efforts to help.

---

### Post by Keshav2050 on 2012-01-27
Sorry, I'll remember that for the next time.

---


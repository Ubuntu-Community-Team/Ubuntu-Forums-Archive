---
title: "Access to Windows files"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-06-17
While I am a single booter (Ubuntu of course) my gf dual boots so she can use Word, Excel and a few other things she prefers in Windows. However, she is using Ubuntu more and more these days but she needs access to "My Documents" on Windows from her Ubuntu.

I know how to get to this through Places>Media...etc.etc. but I don't know how to make a permanent shortcut on the desktop. 

It would be good whether she's working from Windows or Ubuntu she could access the same folder. 

Please tell me how to make a link/shortcut for her please.

---

### Post by hyper_ch on 2008-06-17
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by iaculallad on 2008-06-17
Using your terminal:

```
ln -s /mnt/windows/windows/User_Profiles_Document /home/username/Desktop/win_document
```

---

### Post by hyper_ch on 2008-06-17
Oh, I skipped the shortcut part ;) anyway, iaculled provided the syntax for it.

---

### Post by shuttleworthwannabe on 2008-06-17
install ntfs configuration tool (it is in synaptic), ntfs-3g, and ntfsprogs. NTFS config tools will appear in Applications>System Tools>NTFS Configuration Tool. This is the gui front end for above ntfs apps.
Reboot and all your ntfs drives will apear on the desktop. now u can access everythin on the windows drive, inc my documents;
but the direct link above take u here as well.

PS: I also dual boot for the same reasons, but lately, after installing MSOffice2003 using Wine in Ubuntu, I have not booted in wondows for a while now...try it it may be exactly what your gf needs...

HTH

---

### Post by ukripper on 2008-06-17
> **shuttleworthwannabe said:**
> 

PS: I also dual boot for the same reasons, but lately, after installing MSOffice2003 using Wine in Ubuntu, I have not booted in wondows for a while now...try it it may be exactly what your gf needs...

HTH
Does MS OFFICE 2003 works fine under wine? i was thinking to use that.

---

### Post by shuttleworthwannabe on 2008-06-17
Word and PPT (and perhaps excel..not tried it fully) work fine on my wine config; when you install wine; also install wine-doors (in synaptic), it allows installtion of other MS software you may need to make wine work fully with windows software. Wine website give msoffice 2003 a dodgy approval; what works well is MSOffice2000.
Also try using the latest wine-rc5 if you can 
hth

---

### Post by ukripper on 2008-06-17
> **shuttleworthwannabe said:**
> Word and PPT (and perhaps excel..not tried it fully) work fine on my wine config; when you install wine; also install wine-doors (in synaptic), it allows installtion of other MS software you may need to make wine work fully with windows software. Wine website give msoffice 2003 a dodgy approval; what works well is MSOffice2000.
Also try using the latest wine-rc5 if you can 
hth

i use alot of VBA so was wondering if excel under wine can cope up with that.

---

### Post by shuttleworthwannabe on 2008-06-17
I am afraid VBA is not supported. but I hear that OOo 3 spreadsheet may have this facility built in...I can;t remember where I read this.

---

### Post by ukripper on 2008-06-17
> **shuttleworthwannabe said:**
> I am afraid VBA is not supported. but I hear that OOo 3 spreadsheet may have this facility built in...I can;t remember where I read this.

yeh i do use VBA in OO 2.4 and 2.3

using Option VBASupport 1

but certain functions don't work. so thought to use MS office under ubuntu for that purpose. i guess i will give office 2000 a try as it is better supported under wine.

Thanks

---

### Post by Jimmy9pints on 2008-06-18
Thank you for your help everyone.

---


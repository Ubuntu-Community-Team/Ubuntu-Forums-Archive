---
title: "Kword auto corrupting files in Ubuntu 8.04"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by mjdava on 2008-06-11
I'm migrating from Mandrake 10.1 where I used Kword for word processing.  I had hardware (motherboard) trouble so I ended up updating a lot of hardware and decided I should really move into the 21st century and downloaded Ubuntu 8.04.  It's beautiful.  But the newer version of Kword that I added through the add/remove application allows me to create a new Kword document allows me to save it, but then when I try to open the saved document it gives me this error message: "Could not open /home/username/Desktop/blablabla22.kwd
Reason: Parsing error in root at line 1, column 1
Error message: unexpected end of file "

I removed Kword that was initially installed and tried again (reinstalled Kword) but I'm getting the same result.  

Any ideas?  

Thanks in advance.  It's all good;-)

---

### Post by st33med on 2008-06-11
Are you, by chance, doing these commands as root? Rooting apps can potentially lynch them in Ubuntu. If you want to use an app as root:
```
gksudo <whatever>
```

---

### Post by mjdava on 2008-06-11
I don't think I'm root.  All I've done is through the add/remove application.  No terminal stuff at all.  I tried to play w/the terminal but it wouldn't recognize my password (this was for another glitch:-)

---

### Post by cariboo on 2008-06-11
When you enter your password in a terminal it is not echoed, so if nothing happens except another command prompt, your password has been excepted.

Jim

---


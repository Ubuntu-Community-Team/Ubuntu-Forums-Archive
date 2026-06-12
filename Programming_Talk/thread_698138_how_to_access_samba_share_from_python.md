---
title: "how to access samba share from python"
date: 2008-02-15
forum: Programming Talk
---

### Post by glok_twen on 2008-02-15
hi. i am writing a simple python script where i'd like to reference i file out on a samba share.

in my konqueror its directory shows up as:
smb://hs-d123as/share

but when i use that in a python statement:
f=open('smb://hs-d123as/share/workfile', 'w')

it says it can't find the file.

does anyone know how to reference this?

btw it's on a terstation.

---

### Post by moephan on 2008-02-15
Hmmm. The "smb://" makes me think it's a url, which makes me think that urllib might dot he trick for you.  

Here's the reference:
[http://docs.python.org/lib/module-urllib.html](http://docs.python.org/lib/module-urllib.html)

Here's a sample:
[http://docs.python.org/lib/module-urllib.html](http://docs.python.org/lib/module-urllib.html)

HTH

Cheers, Rick

---

### Post by ghostdog74 on 2008-02-15
if you want to do it in Python, try to look for some Python equivalent module. You can try [this]("http://sourceforge.net/project/showfiles.php?group_id=193998").

From the shell, the smbclient command can do what you want. Check the man page for its basic syntax. something like :
```

# smbclient //host/share -Uusername -Ppassword -W domain .......

```

Lastly, you can just provide a call to smbclient command through Python's subprocess module or popen()....however, i would recommend this to be the last resort.

---

### Post by glok_twen on 2008-02-15
thanks to you both, i used the mount command as indicated; now looking into how to make that permanent. i think it's somehow in fstab so will work on that next. thanks again.

---


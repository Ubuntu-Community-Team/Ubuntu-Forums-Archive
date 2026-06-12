---
title: "Libreoffice impress problem"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by Sraigux on 2012-12-03
I used to open powerpoint files fine on impress, but now, suddenly, when trying to open .ppt files in LibreOffice, they open a "ASCII Filter Options" menu and when I click OK, they open with LibreOffice Writer instead of Impress and just display a bunch of weird symbols. Ive tried opening them from the filesystem and from within impress itself and nothing seems to be working. Any ideas guys?

Thanks,
Sraigux

---

### Post by levlaz on 2012-12-03
This seems to be a [bug ]("http://comments.gmane.org/gmane.linux.arch.general/45183")

I think they just did another upgrade to LibreOffice - you could try downgrading and see if it resolves the issue for now.

---

### Post by Sraigux on 2012-12-03
> **levlaz said:**
> This seems to be a [bug ]("http://comments.gmane.org/gmane.linux.arch.general/45183")

I think they just did another upgrade to LibreOffice - you could try downgrading and see if it resolves the issue for now.
Complete beginner here. I uninstalled and reinstalled libreoffice before you responded. Don't know if that's relevant to downgrading. But I still dont know how to downgrade anyway :P

---

### Post by levlaz on 2012-12-03
Sorry should have been more clear. :) 

First, which version of Ubuntu are you using? 

Second, have you messed with the sources when it comes to LibreOffice? In other words, is the version that you currently have the same one that came by default or did you manually download it from the LibreOffice website or add any PPA's? (PPA's are software sources that allow you to upgrade or install various software through "third party" channels.)

---

### Post by Sraigux on 2012-12-04
> **levlaz said:**
> Sorry should have been more clear. :) 

First, which version of Ubuntu are you using? 

Second, have you messed with the sources when it comes to LibreOffice? In other words, is the version that you currently have the same one that came by default or did you manually download it from the LibreOffice website or add any PPA's? (PPA's are software sources that allow you to upgrade or install various software through "third party" channels.)
Dont be sorry, you're the one helping me!

I am using an up to date 12.10

Nope, no sources have been messed with. It was downloaded from the software centre!

---

### Post by levlaz on 2012-12-05
Help -- rollback LibreOffice 

Since you are using 12.10 You are most likely using LibreOffice 3.6, here is what I would do to downgrade it.

1. Go to the package manager or software center and remove LibreOffice completely. 

[Or you can try using the commands here]("http://askubuntu.com/questions/180403/how-can-i-uninstall-libreoffice") -- this is my preferred method because I think it will ensure no lingering files hang around. :)

2. Then go to the LibreOffice website and download LibreOffice 3.5, make sure you get the correct version for your system (32bit vs 64bit) if you are unsure open a terminal and type in ```
file /sbin/init 
``` if this is confusing let me know. If  you installed the default version of Ubuntu 12.10 or 12.04 then you should have the 32bit version.

3. Install the package, this should be pretty simple -- once again if you have problems let me know.

After this, you will have LibreOffice 3.5 , and your problem "should" be resolved.

---


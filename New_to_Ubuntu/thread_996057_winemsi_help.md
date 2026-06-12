---
title: "wine/msi help"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by brandon.sifford on 2008-11-28
im trying to install a windows game on wine. this is what i did and what i get as a result:

brandon@brandon-laptop:~$ cd /media/BPSTH2007
brandon@brandon-laptop:/media/BPSTH2007$ wine msiexec /i setup.msi
fixme:advapi:LookupAccountNameW (null) L"brandon" (nil) 0x32f7fc (nil) 0x32f800 0x32f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"brandon" 0x1317f8 0x32f7fc 0x12dc40 0x32f800 0x32f7f4 - stub
err:msi:call_script Could not find CLSID for Windows Script
err:msi:call_script Could not find CLSID for Windows Script
err:msi:call_script Could not find CLSID for Windows Script

it will start the setup wizard, ill press the next button till it asks me the path of which to save and thats when the err:msi:call_script could not find CLSID for windows script. please help

---


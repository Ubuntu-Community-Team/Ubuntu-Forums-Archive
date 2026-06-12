---
title: "Getting an Error Message"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-09-05
Installed Crysis in Wine, when i try to run the "Crysis.exe" file, i get this error message. I looked around and it has something to do with the registry files, but any way to fix them in linux/wine?

---

### Post by ad_267 on 2008-09-05
You can change the wine registry by running regedit (from Alt-F2 or a terminal).

This page might be useful if you haven't read it already: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107)

---

### Post by vikramaditya on 2008-09-05
Found this [here]("http://hehe2.net/linux-general/wine/crysis-running-on-wine/")...
> Hey, this is Steven707. I&#8217;m not the first person to get Crysis running in Wine, just the first person to make a youtube video of it. 

I had to set this registry key:
HKEY_CURRENT_USER\Software\Wine\Direct3D\UseGLSL = enabled 

Then I had to put d3dx9_34.dll and xinput1_3.dll (can be found with a google search) in ~/.wine/drive_c/Windows/System32

I don&#8217;t deserve much credit for it, though. I simply followed instructions I found at the Wine AppDB
Hope it's of some help to you.

---


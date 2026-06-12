---
title: "Steam Install / tahoma font"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by chaddiesel on 2008-06-18
Well, I've been able to get this working before but no luck on this one yet.

```
chadwick@Beast-desktop:~$ msiexec /i /home/chadwick/Desktop/SteamInstall.msi
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\chadwick\\Local Settings\\Temporary Internet Files".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\chadwick\\Local Settings\\History".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\chadwick\\Cookies".
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:msi:copy_package_to_temp failed to copy package L"/home/chadwick/Desktop/SteamInstall.msi"
fixme:advapi:LookupAccountNameW (null) L"chadwick" (nil) 0x33f7fc (nil) 0x33f800 0x33f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"chadwick" 0x1294d0 0x33f7fc 0x128988 0x33f800 0x33f7f4 - stub
err:msi:ITERATE_Actions Execution halted, action L"WiseStartup" returned 1627
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msidd4.tmp"
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi3ba.tmp"
chadwick@Beast-desktop:~$ wineserver: could not save registry branch to /home/chadwick/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/chadwick/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/chadwick/.wine/user.reg : Permission denied
```

This in turn causes a "Fatal Error" window to pop up.

I also remember having to put a tahoma font folder somewhere and I don't know if this could be the problem.

---

### Post by Rocket2DMn on 2008-06-18
The tahoma font is now included if wine, so you don't need to deal with that anymore.  Check ownership on your .wine folder:
```
sudo chown -R <yourusername>:<yourusername> ~./wine
```

---

### Post by chaddiesel on 2008-06-18
well, I can't exactly figure out where wine is.
I found one that is in "/usr/lib/wine" but that is a folder and not the file to start the program.

---

### Post by chaddiesel on 2008-06-18
Also found "/home/chadwick/.wine" but that doesn't work either

---

### Post by Rocket2DMn on 2008-06-18
Sorry, I mistyped, it is ~/.wine - you are correct, it is the hidden .wine folder in your home directory.  Have you chown-ed that directory recursively with :
```
sudo chown -R <yourusername>:<yourusername> ~/.wine
```

---

### Post by chaddiesel on 2008-06-19
Well, i've tried to do it several ways but no luck :/

```
chadwick@Beast-desktop:~$ sudo chown -R <chadwick>:<chadwick> ~/.wine
bash: chadwick: No such file or directory>
```

```
chadwick@Beast-desktop:~$ sudo chown -R <chadwick>:<chadwick> ~/home/chadwick/.wine
bash: chadwick: No such file or directory

```

---

### Post by Rocket2DMn on 2008-06-19
LOL, ok, when something is inside of <> it means that it is the outline of how to do it.  The command should be
```
sudo chown -R chadwick:chadwick ~/.wine
```
~ references your home directory, so in your case, ~ is equivilant to /home/chadwick
The reason we are changing ownership of the .wine directory is because since it won't allow it to write (Permission denied) the chances are it is owned by root:root instead of by your username.

---

### Post by chaddiesel on 2008-06-21
My bad. I'm a noob and a half. I'll get the results of that command on monday. :confused:

---

### Post by nowshining on 2008-06-21
i suggest setting up an alias - and use the alias as 

me directory/file, etc..

and another for root. :) much easier typing. and rem. in terminal u can use the TAB key for completion.

---

### Post by chaddiesel on 2008-06-22
Ok. I got it to except the command but it does nothing again. Just gives me the a new prompt.

---

### Post by nowshining on 2008-06-22
see my site [http://www.freewebs.com/gutsygibbon](http://www.freewebs.com/gutsygibbon) on how to set up aliases and if need be add sudo. then it should when done kcik u back @ the command line equating to it's finished.

---


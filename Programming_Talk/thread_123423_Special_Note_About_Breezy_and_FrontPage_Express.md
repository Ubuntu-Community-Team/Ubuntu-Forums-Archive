---
title: "Special Note About Breezy and FrontPage Express"
date: 2006-01-30
forum: Programming Talk
---

### Post by SuperMike on 2006-01-30
I found I couldn't get the old Microsoft FrontPage Express to work with the latest **wine** that comes with Breezy. It would abend. I had to do this to get it to work. Took a long time to figure out, so I hope it benefits you if you use this tool.

(Essentially, I have to throw myself back to Hoary's version of wine in order to get it to work with FrontPage Express. Otherwise, you end up with an abend in wine. Never thought a new version of wine would break something that worked previously with it.)

1. ```
sudo apt-get remove wine --purge
```
2. Look for ~/.wine and remove that folder from whatever user profile you are seeking to reinstall wine on.
3. ```
sudo gedit /etc/apt/sources.list &
```
4. Copy your two Breezy universe lines and paste again. Then, change "Breezy" on those lines to "Hoary". Then, make certain Breezy universe is commented out, but Hoary universe is not. Save the file.
5. ```
sudo apt-get update
```
6. ```
sudo apt-get install wine
```
7. ```
sudo gedit /etc/apt/sources.list &
```
8. Comment the Hoary universe lines out and save the file.
9. ```
sudo apt-get update
```
10. ```
/usr/share/wine/wineinstall
```
11. Answer the questions when prompted. This creates your ~/.wine directory again.
12. Download FrontPage Express. If you don't have it, you can get it [here]("http://frankscorner.org/index.php?p=fpexpress"). Or, you can snag this from a W98's Program Files folder if you have installed all the options from the W98 CD.
13. Find these DLLs from a Microsoft W2K or W98 system and place them in your newly created frontpage directory _under its own bin folder*_:

ADVAPI32.DLL  KERNEL32.DLL  MFC42ENU.DLL  msvcp60.dll   OLE32.DLL
comctl32.dll    mfc42u.dll    msvcp70.dll   rpcrt4.dll
mf3216.dll    mfc70.dll     msvcr70.dll   shdocvw.dll
mfc30.dll     mfcans32.dll  msvcrt10.dll  SHELL32.DLL
mfc40.dll     mfcsubs.dll   msvcrt20.dll  shlwapi.dll
MFC40.DLL     msvbvm50.dll  msvcrt40.dll  USER32.DLL
mfc40u.dll    MSVBVM60.DLL  MSVCRT.CRW
mfc42.dll     msvcirt.dll   msvcrt.dll
GDI32.DLL     mfc42enu.dll  msvcp50.dll   NTDLL.DLL

* When I say "bin" folder, I mean that if you put your FrontPage Express in ~/apps/frontpage, then you'd want to put these DLLs inside of the ~/apps/frontpage/bin folder.

That's probably more DLLs than you need, but you can drop these DLLs in other application directories as you need them for when you have more Windows programs you want to run, such as Paintshop Pro or some old VB5 or VB6 program you may have had in the past.

Note that I tried putting them in ~/.wine/drive_c/windows/system directory, but the application I was trying to run under Wine couldn't seem to find these files. Therefore, I used the fallback of putting them into the same directory as the executable file.

Note that I still can't get the wine fonts right. They show up as Serif instead of Sans Serif. Got any pointers?

---


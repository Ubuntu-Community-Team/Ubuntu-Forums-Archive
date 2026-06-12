---
title: "vag-com audi/vw diagnostic software"
date: 2005-12-13
forum: Outdated Tutorials &amp; Tips
---

### Post by tay on 2005-12-13
get wine and configure it.

do this in this order.

make some new directories in wine.

$mkdir ~/.wine/drive_c/mozactivex
$mkdir ~/.wine/drive_c/win32dlls
$mkdir ~/.wine/drive_c/vagcom

download mozactive x from here and save to your desktop, do not open with wine
[http://www.iol.ie/~locka/mozilla/MozillaControl177.exe](http://www.iol.ie/~locka/mozilla/MozillaControl177.exe)

$mv ~/MozillaControl177.exe ~/.wine/drive_c/mozactivex/

download these two dlls 
[http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60](http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60)
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

unzip these and move them to the win32dlls dir you just created.

then download the version of vag-com you will need according to your interface
[http://www.ross-tech.com/vag-com/download/](http://www.ross-tech.com/vag-com/download/)

mine was a third party interface, (opto coupler) that was in their downloads archive page.

save the package to disk and mv to your vagcom dir

now install the active x plugin like this

$cd ~/.wine/drive_c/mozactivex/
$wine MozillaControl177.exe

then

$cd ~/.wine/drive_c/vagcom/
$ls
$wine (version of vag..exe)

now to run vag
$cd ~/.wine/drive_c/vagcom/
$wine vagcom.exe

and then your there. 

whew.. this was harder than that for me.

---


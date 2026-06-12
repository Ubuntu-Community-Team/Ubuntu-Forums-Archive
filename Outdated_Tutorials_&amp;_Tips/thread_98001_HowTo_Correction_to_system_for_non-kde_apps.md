---
title: "HowTo: Correction to system:/ for non-kde apps"
date: 2005-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-12-02
With KDE3.5 a ioslave called *system:/* is used instead of */home/$USER*.

Double-clicking on non-kde application files will not open the application. For example double-click on an openoffice file and you will not get past the startup picture. Same goes for .mp3 files if you have them linked to xmmm(xmmm will open but not play the files).

The error is not in kde it lies within the configuration of the **.desktop** files. In the .desktop files there is a line for execution. 
*example:*
```
Exec=ooffice2 -writer %U
``` 
The thing that needs to change is the **%U**. You need to change it to **%f**.
*corrected example:*
```
Exec=ooffice2 -writer **%f**
``` When changing this you will also have to add the line(thanks itmon)
```
 X-KDE-Protocols=http;ftp;smb;
```This is to make sure that these three protocols still handle it with %U.

Now comes the part of knowing which files to change. I will give some short help below(good if you want to change several files).

The most important files lie in */usr/share/applications/*. To know which files you need to edit do the following in konsole.
```
grep -H %[Uu] $(ls /usr/share/applications/*.desktop)
``` 
This will give you which files contain the problem. For me it gives
[INDENT][SIZE=1]/usr/share/applications/firefox.desktop:Exec=firefox %u[/SIZE]
  [SIZE=1]  /usr/share/applications/gftp.desktop:Exec=gftp %u[/SIZE]
  [SIZE=1]  /usr/share/applications/gimp-2.2.desktop:Exec=gimp-remote-2.2 %U[/SIZE]
  [SIZE=1]  /usr/share/applications/ooo2-base.desktop:Exec=ooffice2 -base %U[/SIZE]
  [SIZE=1]  /usr/share/applications/ooo2-draw.desktop:Exec=ooffice2 -draw %U[/SIZE]
  [SIZE=1]  /usr/share/applications/ooo2-impress.desktop:Exec=ooffice2 -impress %U[/SIZE]
  [SIZE=1]  /usr/share/applications/ooo2-math.desktop:Exec=ooffice2 -math %U[/SIZE]
  [SIZE=1]  /usr/share/applications/ooo2-writer.desktop:Exec=ooffice2 -writer %U[/SIZE]
  [SIZE=1]  /usr/share/applications/template.desktop:Exec=oofromtemplate2 %U[/SIZE]
  [SIZE=1]  /usr/share/applications/XMMS.desktop:Exec=xmms %U[/SIZE]
[/INDENT]  Now if we decide to correct a file we can use the following command:
```
 sudo sed -e 's/%[Uu]/%f/' -e '$a\X-KDE-Protocols=http;ftp;smb;' -i **<file(s)>**
``` or to change **every file** in that directory
```
sudo sed -e 's/%[Uu]/%f/' -e '$a\X-KDE-Protocols=http;ftp;smb;' -i `grep -l %[Uu] /usr/share/applications/*.desktop`
``` 
There are more .desktop files in the system that contains %U but not sure if those need changine. If you want to see all files that contain %U run the below script
```
#!/bin/bash
locate *.desktop > result.tmp
for desktopFile in $(cat result.tmp)
do
  output=$(grep -H Exec $desktopFile | grep %[Uu])
  if [ -n "$output" ]
  then
      echo $output
  fi
done
rm result.tmp
``` 
**NOTE!** The correction with %f was something that was mentioned on bugs.kde.org

---

### Post by daller on 2005-12-13
I managed to fix all kde apps this way:

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/kde/*.desktop

```

And OpenOffice2.0

```

sudo perl -pi -e 's|%U|\%f|g' /usr/share/applications/ooo2-*.desktop

```

...A little simplified!

---

### Post by GoldBuggie on 2005-12-13
thanks...I actually didn't see this go posted. I wanted to simplify before someone read it to the above but hey...its changed now anyway to something more useful using nice old sed:)

---

### Post by dejitarob on 2005-12-13
This still is not working for me. I ran both the sed and pearl commands and it will not locate the .desktop which konqueror actually uses for oO. I was unable to locate any .desktop files which seemed to have an affect using your bash script GoldBuggie. Right clicking on the file, clicking the button next to the file type, and editing the command manually changing it to %f through konqueror worked but this is a pain to do for every filetype.

---

### Post by GoldBuggie on 2005-12-13
Wat is your output of grep -H Exec `locate ooo2-writer.desktop`  ?

---

### Post by LauriN on 2005-12-14
hi!

i've executed
```
grep -H %[Uu] $(ls /usr/share/applications/*.desktop)
sudo sed -e 's/%[Uu]/%f/' -i  /usr/share/applications/*.desktop
```
and now my konqueror crashes every time i want to open a pdf file using the embedded kpdf ... :???: 

the output of konqueror is
```
kparts: WARNING: Part '' has a widget view widget with a focus policy of NoFocus. It should have at least a ClickFocus policy, for part activation to work well.
Bogus memory allocation size
QPaintDevice: Cannot destroy paint device that is being painted

```

thanks in advance!

---

### Post by GoldBuggie on 2005-12-14
which files did you change?

do
```
grep -H %[f] $(ls /usr/share/applications/*.desktop)
```
to see which one now has %f

The kde apps should be in the /usr/share/applications/kde directory so strange that you get this error.

---

### Post by ltmon on 2005-12-14
Hi GoldBuggie,

If you add the following to the end of each of the .desktop files:

```

X-KDE-Protocols=http;ftp;smb;

```

then these programs (should) work fine also (assuming the application in question knows how to support the http, ftp and smb protocols natively).

I believe that this is the most technically correct way to fix the system:/ behaviour, because it won't ever possibly interfere with launching these programs from inside Gnome or other environments.

At least that's what I think based on the reading I've done, but there's not much info out there.

Quote from the developer responsible for the System:/ ioslave (Kevin Ottens):

> 
X-KDE-Protocols key in desktop files, which allows to restrict the set of
supported protocols for an applications. Anything not present in this set is
automatically resolved to file:/ URLs if possible before launching the
application.


Can anyone confirm if this is the best way to do it?

L.

---

### Post by daller on 2005-12-14
Reverse kpdf this way:

sudo perl -pi -e 's|%f|\%U|g' /usr/share/applications/kde/kpdf.desktop

...Guess it's the safest way to use it on one app at the time (the ones you can't get to work!)

Anyone knowing why kpdf doesn't run properly with "-f"?

---

### Post by LauriN on 2005-12-14
[QUOTE=GoldBuggie]which files did you change?

do
```
grep -H %[f] $(ls /usr/share/applications/*.desktop)
```
to see which one now has %f

The kde apps should be in the /usr/share/applications/kde directory so strange that you get this error.[/QUOTE]
i get this output:
```
/usr/share/applications/firefox.desktop:Exec=firefox %f
/usr/share/applications/gftp.desktop:Exec=gftp %f
/usr/share/applications/gimp-2.2.desktop:Exec=gimp-remote-2.2 %f
/usr/share/applications/ooo2-base.desktop:Exec=ooffice2 -base %f
/usr/share/applications/ooo2-calc.desktop:Exec=ooffice2 -calc %f
/usr/share/applications/ooo2-draw.desktop:Exec=ooffice2 -draw %f
/usr/share/applications/ooo2-impress.desktop:Exec=ooffice2 -impress %f
/usr/share/applications/ooo2-math.desktop:Exec=ooffice2 -math %f
/usr/share/applications/ooo2-writer.desktop:Exec=ooffice2 -writer %f
/usr/share/applications/qcad.desktop:Exec=qcad %f
/usr/share/applications/qucs.desktop:Exec=qucs %f
/usr/share/applications/scribus.desktop:Exec=scribus %f
/usr/share/applications/template.desktop:Exec=oofromtemplate2 %f
/usr/share/applications/wine.desktop:Exec=wine %f
/usr/share/applications/XMMS.desktop:Exec=xmms %f
/usr/share/applications/XMMS-pl.desktop:Exec=xmms %f
```

[QUOTE=daller]Reverse kpdf this way:

sudo perl -pi -e 's|%f|\%U|g' /usr/share/applications/kde/kpdf.desktop[/QUOTE]
thx, but now my konqueror dies with this message: :confused: 
```
kparts: WARNING: Part '' has a widget view widget with a focus policy of NoFocus. It should have at least a ClickFocus policy, for part activation to work well.
Bogus memory allocation size
Very strange! got a DCOPReply opcode, but we were not waiting for a reply!

```

---

### Post by benplaut on 2005-12-14
ok, folks... OpenDesktop is there for a reason!

sheesh

---

### Post by ltmon on 2005-12-14
[QUOTE=benplaut]ok, folks... OpenDesktop is there for a reason!

sheesh[/QUOTE]

Can you explain what you mean a bit further?

L.

---

### Post by GoldBuggie on 2005-12-14
**LauriN**
I did not see any package there that would give that problem. Are you sure you didn't change anything in the kde directory?
grep -H %[f] $(ls /usr/share/applications/kde/*.desktop) 
Paste this as well please. 

Otherwise just reverting back to the original by doing a
sudo sed -e 's/%[f]/%U/' -i  /usr/share/applications/*.desktop should help.



[B]Itmon
[/B]You are of course totally correct. I saw him mentioning it on bugs.kde but never really understood the use of it. But after doing some thinking ](*,):idea::D I understand it more. I also found this msg which I think explains his view and intention of it all quite well
[http://lists.kde.org/?l=kde-core-devel&m=111973959921885&w=2](http://lists.kde.org/?l=kde-core-devel&m=111973959921885&w=2)

Now only to add it to the howto somehow...*thinking*

---

### Post by LauriN on 2005-12-14
[QUOTE=GoldBuggie]**LauriN**
I did not see any package there that would give that problem. Are you sure you didn't change anything in the kde directory?
grep -H %[f] $(ls /usr/share/applications/kde/*.desktop) 
Paste this as well please. [/QUOTE]
```
/usr/share/applications/kde/installktheme.desktop:Exec=kdeinstallktheme %f
/usr/share/applications/kde/Kfind.desktop:Exec=kfind %f

```
> Otherwise just reverting back to the original by doing a
sudo sed -e 's/%[f]/%U/' -i  /usr/share/applications/*.desktop should help.
still the same error message ... very strange! :confused:

---

### Post by GoldBuggie on 2005-12-14
At this moment I'm a bit of a loss since you have actually changed back to your original configuration and you never even touched kpdf or kpart configuration from the beginning. So I do think there is something else that has effected your problem. But to look at some configurations for pdf files right-click on the file and choose properties. Click on the button next to the text 'pdf-document'
Under *General* I have *KPDF* at the top and choosing that one and pressing *edit* i have *kpdf %U %i %m -caption "%c"* under the *application *tab.

Under the Embedding tab I have *KPDF(kpdf_part)* at top.

Soory that I can¨t be of much more help at this moment.

---

### Post by LauriN on 2005-12-14
i just found out that the error has nothing to do with embedding kpdf in konqueror. when i try to open a pdf in "standalone" kpdf i get the same error msg:
```
Bogus memory allocation size
```
so the error probably is caused by something else ...
thanks for your help anyway! :)

---


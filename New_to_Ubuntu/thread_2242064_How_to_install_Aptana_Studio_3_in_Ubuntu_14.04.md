---
title: "How to install Aptana Studio 3 in Ubuntu 14.04"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by pratyushpm on 2014-08-30
Steps I folowed to install Aptana Studio 3:

[LIST=1]
[*]Downloaded the standalone(64 bit version) version. 
[*]Extracted the folder from the zip file. 
[*]Gave executable permission to Aptana Studio 3 script. 
[*]Moved the extracted "AptanaStudio3" folder to /opt 
[/LIST]

In order to get the Aptana Launcher icon and make it searchable in Ubuntu dash, I 
[LIST=1]
[*]Made a .desktop file with the following code:
```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Aptana Studio 3
GenericName=Integrated Development Environment
Comment=Aptana Strudio 3 Integrated Development Environment
Exec=/opt/Aptana_Studio_3/AptanaStudio3 %F
TryExec=/opt/Aptana_Studio_3/AptanaStudio3
Icon=/opt/Aptana_Studio_3/icon.xpm
StartupNotify=true
StartupWMClass="Aptana Studio 3"
Terminal=false
Type=Application
MimeType=text/xml;application/xhtml+xml;application/x-javascript;application/x-php;application/x-java;text/x-javascript;text/html;text/plain
Categories=GNOME;Development;IDE;
``` 
[*]Saved it to /usr/share/applications 
[/LIST]

And then I logged out and back in again. Nothing happened. No changes whatsoever. 


If I have to run Aptana now, I have to sudo nautilus /opt/Aptana_Studio_3  (See Attachment 3) and click on the executable (or go to /usr/share/applications and click the icon. See Attachment 1) and it shows the "workspace setup" of Aptana (See Attachment 4)and finally Aptana opens up(See Attchment 5). 
And I pin the icon to the launcher bar and close Aptana. But if I click on the pinned icon again nothing happens.
 This is the current state on my PC.


I even tried some other things like giving the .desktop file executable permissions(following which the icon should have changed to the Aptana icon) but the file just went completely blank. In the Attachment 2 the top one shows the .desktop file with executable permissions and the bottom one shows the file without executable permissions. The file contents are the same, just changed the filename.

I made a .desktop file on my first try but I changed it to one I got from the web, just to see if the problem was solved.

Where did I go wrong?

---

### Post by harivalath on 2014-10-24
I am a Ubuntu Novice. But I noticed .Desktop file is pointing to wrong folder ([COLOR=#000000][FONT=Ubuntu Mono]/opt/Aptana_Studio_3/). I think it should be /opt/AptanaStudio3. Can you retry after correcting it?[/FONT][/COLOR]

---


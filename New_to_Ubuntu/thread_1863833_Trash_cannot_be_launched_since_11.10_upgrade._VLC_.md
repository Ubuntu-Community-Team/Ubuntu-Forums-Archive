---
title: "Trash cannot be launched since 11.10 upgrade. VLC the cause?"
date: 2011-10-18
forum: New to Ubuntu
---

### Post by Filthy Stockings on 2011-10-18
When click on TRASH icon on LAUNCHER I get this message

 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'trash://'. Check the log for details.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Why would VLC, which I believe to be a media player, be involved in my TRASH bin?[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Also VLC seems to be interfering with trying to read folders in my WD EXTERNAL HDD and also my camera memory card.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]As I only seem to watch and listen to files via MOVIEPLAYER can I stop VLC from doing anything?[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]VLC seems to be causing so many problems to general normal usage since installing 11.10 yesterday. Anyone know why and/or if this is significant?[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Currently cannot even get the LAUNCHER to er....launch, and have to minimise all documents/pages to move around.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]Wish had stayed with 11.04 based on highly problematic experiences in the last 24 hours.[/COLOR]

[COLOR=#000000][/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by mc4man on 2011-10-18
Open a terminal & run 
```
gedit ~/.local/share/applications/mimeapps.list
```

In the [Default Applications] section there will be a line starting with
inode/directory=
Delete the line

---

### Post by Filthy Stockings on 2011-10-18
1725 18/10/11

Thanks for reply, just logged on.

Following your advice get this 

                                  [COLOR=#000000][SIZE=3][Added Associations] [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]inode/directory=vlc.desktop;banshee-audiocd.desktop; [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]application/ram=banshee-audiocd.desktop; [/SIZE][/COLOR]
  
  [COLOR=#000000][SIZE=3][Default Applications] [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]inode/directory=nautilus-folder-handler.desktop [/SIZE][/COLOR]
  [COLOR=#000000][SIZE=3]application/ram=banshee-audiocd.desktop[/SIZE][/COLOR]


 but do I delete everything after [Default Applications] ie


*[COLOR=#000000][SIZE=3]inode/directory=nautilus-folder-handler.desktop [/SIZE][/COLOR]*
 *[COLOR=#000000][SIZE=3]application/ram=banshee-audiocd.desktop[/SIZE][/COLOR]*
 
 ALSO could you explain why I am doing this. Does it allow me to access TRASH as did with 11.04 and what is NAUTILUS, which I have seen mentioned in these forums but not aware of its function. I see that BANSHEE gets mentioned in the line of code to, which puzzles me as only VLC have flagged up the ALERT I posted before.

Is VLC not solely implicated, as it seems set to interfere with all my external devices when I have tried to open them up AND it seems to prevent me properly accessing my chosen media player MOVIEPLAYER.

Any advice for a dopey novice much appreciated and thanks for taking time to reply.

SA

---

### Post by pierreyy on 2011-10-18
im still having the same problem as you are but firefix opens my trash:P

[http://ubuntuforums.org/showthread.php?t=1860542](http://ubuntuforums.org/showthread.php?t=1860542)

follow the advice here... it worked for me ( didnt permanently fix the problem but it rarely happens)

 good luck!

---

### Post by Filthy Stockings on 2011-10-18
thanks for reply

Have you only had this since installing 11.10?

Only problem I used to have with my 4 months of 11.04 was Trash APPLET vanishing when booted up some days but didn't bother me much as would correct next time I booted.

But since 11.10 upgrade so many icons I click on LAUNCHER get the VLC grabbing them to stop any further use.....just what IS VLC? I cannot see it in the DASH route to MEDIA APPS INSTALLED....and yet it keeps appearing to dominate so many fucntions...such as trying to open camera memory card and my WB EXTERNAL HDD.

---

### Post by vieux-jules on 2011-11-01
Hello,
I have tried something; it seems to work so far. I added two // before inode/directory to disactivate this function.

[Added Associations]
application/x-sharedlib=firefox.desktop;
x-content/video-dvd=banshee-audiocd.desktop;
application/pdf=libreoffice-writer.desktop;acroread.desktop;
**//inode/directory=vlc.desktop;banshee-media-player.desktop;**
application/xml=qgis.desktop;
application/x-esri-crs=gedit.desktop;
text/x-python=openjdk-6-java.desktop;
application/x-extension-bin=nautilus-browser.desktop;

---


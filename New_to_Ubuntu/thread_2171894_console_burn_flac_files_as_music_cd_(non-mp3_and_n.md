---
title: "console: burn flac files as music cd (non-mp3 and non-flac files at target cd)"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-09-02
Hi all, 

how do I burn flac files as music cd in console (non-mp3 and non-flac files at target cd) ?

---

### Post by newb85 on 2013-09-02
My recommendation is that you try Brasero, starting an Audio Disc Project.

---

### Post by Marchello_Lippi on 2013-09-03
Here is the decision: [URL="http://askubuntu.com/questions/62168/can-how-to-burn-a-flac-to-an-audio-cd"]

http://askubuntu.com/questions/62168/can-how-to-burn-a-flac-to-an-audio-cd[/URL]

[COLOR=#000000][FONT=dejavu sans mono]Procedure:[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Convert FLACs to MP3 with lame (lame recommends -V2, but in your case I'd go with -V5):[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]flac -d -c track.flac | lame -V 5 - track.mp3[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]example for processing all FLAC files in current folder:[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]for f in *.flac ; do flac -d -c "$f" | lame -V 5 - "${f%.*}.mp3" ; done[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Convert MP3 folder structure to Joliet folder structure ISO image[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]After you have converted FLAC files to MP3 arange MP3s in folder structure (i.e. /artist/album/track) than make ISO image like this:[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]mkisofs -J -o /tmp/MP3-CD.iso /path to root of MP3 folder structure/[/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Note: you can't go above 700MB, check for space first [/FONT][/COLOR]

[COLOR=#000000][FONT=dejavu sans mono]Burn ISO image[/FONT][/COLOR]

---


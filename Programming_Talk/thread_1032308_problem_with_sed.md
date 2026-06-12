---
title: "problem with sed"
date: 2009-01-06
forum: Programming Talk
---

### Post by davidtuti on 2009-01-06
Hi,

I have this:

[HTML]<td class=lista align=left title="Bajar:&nbsp;[Capitulos 1-8] House 5
Temporada HDTV x264 720p AC3 5.1 Dual + Subs Dual "><table border=0
cellspacing=0 cell
padding=0 align=left onClick="window.open('download.php?
id=6f0fa8a03a424e203471224a92a1565cefd4a5ee&f=%5BCapitulos+1-8%5D+House
+5%AA+Temporada+HDTV+x264+720p
+AC3+5.1+Dual+%2B+Subs+Dual+.torrent','_self')" style="cursor:pointer;
cursor:hand;"><tr><td style="background-image: url(images/
download.gif); background-re
peat: no-repeat; width:17px; height:17px;" align=center></
td><td>&nbsp;Descargar</td></tr></table></td>

<td class=lista align=left title="Bajar:&nbsp;(.XviDG ) Mundial de
Motogp 2008 - Resumen TVE.DVBRip.XviD.Mp3.Castellano"><table border=0
cellspacing=0 cellpa
dding=0 align=left onClick="window.open('download.php?
id=fcff167524fa499cb02ce820ebc6fe39b36538c6&f=%28.XviDG+%29+Mundial+de
+Motogp+2008+-+Resumen+TVE.DVBRip
.XviD.Mp3.Castellano.torrent','_self')" style="cursor:pointer;
cursor:hand;"><tr><td style="background-image: url(images/
download.gif); background-repeat: no
-repeat; width:17px; height:17px;" align=center></
td><td>&nbsp;Descargar</td></tr></table></td>
[/HTML]


And I do this:

sed "s/.*nbsp;\([^\"]*\)\".*$/\1/g" file

It gives me:

[HTML]<td class=lista align=left title="Bajar:&nbsp;[Capitulos 1-8] House 5&#65533; Temporada HDTV x264 720p AC3 5.1 Dual + Subs Dual "><table border=0 cellspacing=0 cellpadding=0 align=left onClick="window.open('download.php?id=6f0fa8a03a424e203471224a92a1565cefd4a5ee&f=%5BCapitulos+1-8%5D+House+5%AA+Temporada+HDTV+x264+720p+AC3+5.1+Dual+%2B+Subs+Dual+.torrent','_self')" style="cursor:pointer; cursor:hand;"><tr><td style="background-image: url(images/download.gif); background-repeat: no-repeat; width:17px; height:17px;" align=center></td><td>&nbsp;Descargar</td></tr></table></td>
(.XviDG ) Mundial de Motogp 2008 - Resumen TVE.DVBRip.XviD.Mp3.Castellano
[/HTML]


And I would like this:
House 5 Temporada HDTV x264 720p AC3 5.1 Dual + Subs Dual
(.XviDG ) Mundial de Motogp 2008 - Resumen TVE.DVBRip.XviD.Mp3.Castellano

I don't understand because the code html have the same pattern. Any help?

Many thanks,

---


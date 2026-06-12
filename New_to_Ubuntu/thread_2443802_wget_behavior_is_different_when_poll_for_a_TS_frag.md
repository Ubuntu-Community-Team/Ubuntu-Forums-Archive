---
title: "wget behavior is different when poll for a TS fragment"
date: 2020-05-20
forum: New to Ubuntu
---

### Post by Dave1024 on 2020-05-20
[COLOR=#000000][FONT=Verdana]Hello All,[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Today I wrote a simple application in Linux.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]The simple app will execute a wget command with an argument.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The command string looks like as given below.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]wget -O 0_lr.xml -d -S -T 2 --tries=1 --waitretry=0 --header="Content-Type: text/xml" --header="SOAPAction:http://schemas.microsoft.com/" --post-file=0_lc.xml "http://184.72.239.149/vod/smil:BigBuckBunny.smil/playlist.m3u8"[/FONT][/COLOR]


[COLOR=#000000][FONT=Verdana]The intention of this command to make sure that the retry in wget should execute only once when failure noted.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]When I execute this command in a terminal  I got correct result.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]But when I execute the same command via system() api call in a C++ program then I am not getting the correct result.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ie:- wget default retry attempt is 20 and it tries 20 times instead of 1.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]The wget version along with my OS is 1.14.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]What is the special things I should take care when use system() API.?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Is there any other approaches we need to take care to override the wgetrc defaults?[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Kindly help !.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]Regards,[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Dave.[/FONT][/COLOR]

---


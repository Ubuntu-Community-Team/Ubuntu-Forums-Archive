---
title: "getview called when scrolling Listview in Android"
date: 2013-11-01
forum: Programming Talk
---

### Post by chuchi on 2013-11-01
[FONT=Times New Roman, serif][SIZE=3]Hi everyone![/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]I am having problems when scrolling a ListView in Android. Each item in the ListView shows an image downloaded from internet.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Whenever I scroll the ListView, it calls the method “[COLOR=#000000]getView([/COLOR][COLOR=#7f0055]int[/COLOR][COLOR=#000000] position, View convertView, ViewGroup parent)[/COLOR]”, causing the image to be downloaded again.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]How can I prevent this?? I mean, to  call getView only once.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Thank you very much![/SIZE][/FONT]

---


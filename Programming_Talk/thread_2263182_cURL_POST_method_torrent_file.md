---
title: "cURL POST method torrent file"
date: 2015-01-30
forum: Programming Talk
---

### Post by billilechauve on 2015-01-30
[FONT=Helvetica Neue]I would like to make a HTTP POST request with curl, sending data and files.[/FONT]
[FONT=Helvetica Neue]I tried this:[/FONT]
> curl -i -X POST -H "Content-Type: multipart/form-data" -F "name=Bilan" -F "fichier=@file.torrent" [http://localhost/upload.php](http://localhost/upload.php)
[FONT=Helvetica Neue]without success. I think I have a problem with the content-Type, the torrent file was not sent.[/FONT]
[FONT=Helvetica Neue]What should I do?[/FONT]
[FONT=Helvetica Neue]Thanks for your help.[/FONT]

---


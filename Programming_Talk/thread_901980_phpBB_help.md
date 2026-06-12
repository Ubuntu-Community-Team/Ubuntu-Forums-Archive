---
title: "phpBB help"
date: 2008-08-26
forum: Programming Talk
---

### Post by deadlySniper on 2008-08-26
[SIZE=3][B][COLOR=#000000][FONT=Footlight MT Light]Parse error: syntax error, unexpected $end in /home/sierri/public_html/forums/includes/bbcode.php on line 289

[/FONT][/COLOR][/B][COLOR=#000000][FONT=Footlight MT Light]I keep on getting this error and cant click on anything. The code looks fine but I cant really tell.
[/FONT][/COLOR][/SIZE]

---

### Post by henchman on 2008-08-26
This means that there is at least one more opening bracket { than closing bracket }. You may paste the code of this file, so that we can have a look at it (please put it in php-tags). If you use a unmodified version of phpBB, it's very unlikely that such stuff happens. If this only happens on your remote server, then you may try to reupload the file, maybe the transfer was interrupted.

gl

---


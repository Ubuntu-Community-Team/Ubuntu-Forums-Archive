---
title: "sqlite3 REPLACE function missing?"
date: 2007-04-21
forum: Programming Talk
---

### Post by tom-ubuntu on 2007-04-21
Hi there

Wanted to update the paths within the F-Spot database file, because I changed my username.

But if I try to use the replace function I get

"SQL error: no such function: REPLACE"

  SQLite version 3.3.13
  Enter ".help" for instructions
  sqlite> select replace('toto', 'to', 'it');
  select replace('toto', 'to', 'it');
  sqlite> .quit

Using Ubuntu 7.04 Feisty; just did a new installation. That's why I changed the username.

Any help?

Thank you very much!
Tom

---

### Post by tom-ubuntu on 2007-04-30
Ok, if no one has an idea about the replace function; how to I updated the path in the F-Spot database file? Any suggestions about that? Thank you!

---

### Post by tom-ubuntu on 2007-05-03
Found a solution; if someone can use it, feel free. It worked for me:

>sqlite3 photos.db 'update photos set directory_path = "/home/xyz" || substr(directory_path, 11, length(directory_path))'

I changed the user, so the absolute path changed.

---

### Post by Klondike on 2008-04-30
Just so you know, I found this totally helpful.  I used it to migrate my Amarok DB.  Thanks for posting it!

---

### Post by RemcoBoerma on 2008-05-14
in 8.04 i think i still had the problem, but i'm not sure. maybe you can test if the replace function still doesn't work. I forced a reinstall using 
```
sudo apt-get install sqlite3 --reinstall
```
after that i executed 
```
update photos set uri = replace(uri,'/sdb3/','/');
```
without a problem.

---


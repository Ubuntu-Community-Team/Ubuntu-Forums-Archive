---
title: "Mysql sjis character set"
date: 2005-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by somb23 on 2005-12-06
for the past days i been trying to setup my ubuntu to  support SJIS character set in MySQL. I already follow this steps, but still the data in my table is garbage.

1./ in php.ini: uncomment the default_charset and change it to: 
default_charset = "SJIS"

2./ in my.cnf, under [mysqld], add:
default-character-set=sjis
character_set_server=sjis
collation_server=sjis_japanese_ci

3./ in the SQL files, replace TYPE=MyISAM; by TYPE=MyISAM CHARACTER SET 
sjis 
COLLATE sjis_japanese_ci
I follow the same steps with windows2000 and theres no problem. My MySQL version is 4.1...
I really need help from any one... pls.....

---


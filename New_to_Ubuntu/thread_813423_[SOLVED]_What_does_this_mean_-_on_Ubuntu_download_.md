---
title: "[SOLVED] What does this mean - on Ubuntu download site"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by wpshooter on 2008-05-30
user warning: Table 'drupal_ubuntu2.mirror_list' doesn't exist query: select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 1 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'EU' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 2 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'NA' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 3 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'AS' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 4 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'SA' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 5 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'OC' union select mirror_list.location, mirror_list.name, mirror_list.link, mirror_countries.countryname, mirror_countries.continent, 6 as 'o' from mirror_list left join mirror_countries on (mirror_list.location = mirror_countries.location and mirror_countries.officialname = 1) where mirror_countries.continent = 'AF' order by o, countryname in /srv/drupal-farm/www/includes/database.mysql.inc on line 172.

---

### Post by Vicfred on 2008-05-30
[http://ubuntuforums.org/showthread.php?t=813414](http://ubuntuforums.org/showthread.php?t=813414)

---

### Post by wpshooter on 2008-05-30
I think they need to enhance their new enhanced download page !!!

---


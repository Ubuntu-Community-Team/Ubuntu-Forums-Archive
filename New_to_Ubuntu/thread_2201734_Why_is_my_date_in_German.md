---
title: "Why is my date in German ?"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by marx2 on 2014-01-25
My keyboard is Belgian (not too proud  but it works ) my shoes are Italian , the coffee from Colobia but the date in German ??? 
Next thing i'll find SSH in cahotes with the SS .

---

### Post by Lars Noodén on 2014-01-26
You can look in the file [i]/etc/default/locale[/url] and check what your system is using for LC_TIME.  If it's wrong, make a backup copy of the file and then edit in the right setting.  The first part is two-letter [language code](http://www.loc.gov/standards/iso639-2/php/code_list.php) (639-1) followed by [country code](http://www.iso.org/iso/country_codes/iso_3166_code_lists/country_names_and_code_elements.htm) (3166).

---


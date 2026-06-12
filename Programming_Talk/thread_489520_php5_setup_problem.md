---
title: "php5 setup problem?"
date: 2007-07-01
forum: Programming Talk
---

### Post by theorem_hunter on 2007-07-01
i have a 2 part question...

apache2 & php5 & mysql were all installed by following this guide: [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
everything worked properly, including php test...

i made a simple html page & put it in /var/www & then went to [http://localhost/](http://localhost/) & saw the page i made.

then i was fiddling with /etc/apache2/apache2.conf & uncommented this:
```

# UserDir is now a module
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
	AllowOverride FileInfo AuthConfig Limit
	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>

```

then i ran sudo /etc/init.d/apache2 force-reload

so im thinking that i can just place files in my /home/*/public_html folder instead of /var/www because that requires sudo cp -R ...

this is not working like how i thought it would, i changed the page & put it in my /public_html folder & saw the old page in /var/www 

what am i doing wrong here? thanks

then with that php page i made test.php with the following in it...
```

<html>
<body>

<?php
echo "Hello World";
?>

</body>
</html>

```

when i type the explicit path in firefox it asks me if i want to download it...
i ran this: $ sudo a2enmod php5
This module is already enabled!

how can i get php pages to display properly? thanks

---

### Post by nitro_n2o on 2007-07-01
go to ur  php.ini file might be in /etc/php5/apache2/php.ini 
add /home/public_html to the line that says include_path=  in my file this is line 475 don't put a slash at the end

---


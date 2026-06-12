---
title: "Can't access phpmyadmin due to &quot;Fatal error&quot;"
date: 2016-06-15
forum: New to Ubuntu
---

### Post by Andrew_Milne on 2016-06-15
Hello, been googling around and searching through forums for a solution to the error message below with no success. I've always been a windows user so sadly the technical terms being suggested for similar errors haven't been terribly easy for me to follow and understand so I'm hoping someone here is able to help explain in simplton!

I followed instructions for installing the lamp stack on my desktop so I can set up a PHP dev environment. So i've installed PHP7, mySQL and apache2 and they all seem to be working fine. I've installed phpmyadmin, and that seemed to go fine but when I try to go to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) I get the following error...[INDENT]
[B]Fatal error: Uncaught Error: Call to undefined function __() in /usr/share/phpmyadmin/libraries/core.lib.php:245 Stack trace: #0 /usr/share/phpmyadmin/libraries/core.lib.php(321): PMA_fatalError('The [a@./url.ph...') #1 /usr/share/phpmyadmin/libraries/common.inc.php(298): PMA_warnMissingExtension('json', true) #2 /usr/share/phpmyadmin/index.php(12): require_once('/usr/share/phpm...') #3 {main} thrown in[B]/usr/share/phpmyadmin/libraries/core.lib.php on line [B]245

[/B][/B][/B][/INDENT]
My knowledge of installing the lamp stack prior to this consisted of insalling Wamp on Windows 10 before this so I didn't have to worry about installing extensions and phpmyadmin myself. It just sort of worked! As far as I can tell I have installed all the extensions I need to, including the json extension mentioned above so I don't really understand if that is the problem, or if something else is causing the problem and the mention of the extension is a red herring. I have wondered if there is some sort of permissions problem but when it comes to permissions in Linex, I am somewhat clueless!!

Any help or suggestions anyone can offer would be much appreciated!

---

### Post by openlaptop on 2016-08-25
> PMA_warnMissingExtension('json'..

Means that you are missing an extension in PHP. Try to install the json php extention.

---


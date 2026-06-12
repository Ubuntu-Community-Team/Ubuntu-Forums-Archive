---
title: "PHP + gettext + multiple text domains"
date: 2008-10-23
forum: Programming Talk
---

### Post by Sam on 2008-10-23
I have a PHP website that use gettext.

It has multiple text domains for specific parts of the website, and a shared text domain which holds strings used in several parts. For this I use *dgettext($domain, $string)*.
Everything works smoothly when I get the text from the message catalogs, but I have a problem when I extract the strings. I'll explain later. Here is a working example:

[LIST]
[*]Two text domains, 'a' and 'b'. A shared text domain 'share'.
[*]The original strings are in English and the final output will be in French.
[/LIST]
```

File                             Description
------------------------------------------------------------------------------------------

test_a.php                       Uses 'a' and 'share' text domains
test_b.php                       Uses 'b' and 'share' text domains

locale/fr/LC_MESSAGES/a.mo       Compiled message catalog for 'a' text domain in french
locale/fr/LC_MESSAGES/b.mo       Compiled message catalog for 'b' text domain in french
locale/fr/LC_MESSAGES/share.mo   Compiled message catalog for 'share' text domain in french

po/a-fr.po                       Message catalog for 'a' text domain in french
po/b-fr.po                       Message catalog for 'b' text domain in french
po/share-fr.po                   Message catalog for 'share' text domain in french

pot/a.po                         Message catalog template for 'a' text domain
pot/b.po                         Message catalog template for 'b' text domain
pot/share.po                     Message catalog template for 'share' text domain
```

**test_a.php**
[php]<html><head><title>Test A</title>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head><body>
<?php

bindtextdomain('share', "locale/");
bindtextdomain('a', "locale/");
textdomain('a');

setlocale(LC_ALL, "fr_CH.UTF-8");

echo gettext("You are on page test A")."<br/>\n";
echo dgettext('share', "This is a common text.")."<br/>\n";

?>
</body></html>[/php]

**test_b.php**
[php]<html><head><title>Test B</title>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head><body>
<?php

bindtextdomain('share', "locale/");
bindtextdomain('b', "locale/");
textdomain('b');

setlocale(LC_ALL, "fr_CH.UTF-8");

echo gettext("You are on page test B")."<br/>\n";
echo dgettext('share', "This is a common text.")."<br/>\n";

?>
</body></html>[/php]

**po/a-fr.po**
```
msgid ""
msgstr ""
"POT-Creation-Date: 2008-10-24 01:15+0200\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: test_a.php:12
msgid "You are on page test A"
msgstr "Vous êtes sur la page A"
```

**po/b-fr.po**
```
msgid ""
msgstr ""
"POT-Creation-Date: 2008-10-24 01:15+0200\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: test_b.php:12
msgid "You are on page test B"
msgstr "Vous êtes sur la page B"
```

**po/share-fr.po**
```
msgid ""
msgstr ""
"POT-Creation-Date: 2008-10-24 01:15+0200\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: test_a.php:13
#: test_b.php:13
msgid "This is a common text."
msgstr "Ceci est un texte commun."
```

To compile the .po files into .mo
```
msgfmt --output-file="locale/fr/LC_MESSAGES/a.mo" "po/a-fr.po" && \
msgfmt --output-file="locale/fr/LC_MESSAGES/b.mo" "po/b-fr.po" && \
msgfmt --output-file="locale/fr/LC_MESSAGES/share.mo" "po/share-fr.po"
```

When browsing test_a.php
[html]Vous êtes sur la page A
Ceci est un texte commun.[/html]

When browsing test_b.php
[html]Vous êtes sur la page B
Ceci est un texte commun.[/html]

As I said, this works.


Now the problem:

When I use xgettext to extract the strings, they are all put in the same file, regardless of any dgettext calls. I run for text domain 'a':
```
xgettext --default-domain=a --output-dir=pot/ --from-code=utf-8 --language=PHP test_a.php
```and the string from *dgettext('share', "This is a common text.")* is put in **pot/a.po** and not an other file (ie: **pot/share.po**). That's it:

**pot/a.po**
```
<snip>

#: test_a.php:12
msgid "You are on page test A"
msgstr ""

#: test_a.php:13
msgid "This is a common text."
msgstr ""
```

For the working example above, I had to edit the message collections manually to put the 'share' string in its specific file.


Is there a way to invoke xgettext and have the dgettext strings put in the right file(s) ?? I hope I have given enough information, but ask if you need more details. I've been working on this issue for days...

---

### Post by Sam on 2008-10-24
bump

---

### Post by Sam on 2008-10-25
another bump



I'm pretty sure that this issue is not PHP specific. So if there are any gettext guru here, please give me a hand ! Thank you !!!!

---

### Post by paulut on 2011-03-04
Hi, 

i have a quite similar problem here. I want to give different po files to different translators. But no one should have string in his or her file which should be translated by his or here collegues.

Is there a way to do this ? And How can such "part-po-files" be updated with poedit ?

---


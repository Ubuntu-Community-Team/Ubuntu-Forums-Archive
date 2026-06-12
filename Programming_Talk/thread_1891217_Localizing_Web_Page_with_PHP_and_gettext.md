---
title: "Localizing Web Page with PHP and gettext"
date: 2011-12-05
forum: Programming Talk
---

### Post by dodle on 2011-12-05
I have a website at Sourceforge along with one of my projects. I am trying to localize it for different languages but it is not working. Here is how my folder structure is set up:

[i]/test.php
/locale/en/LC_MESSAGES/dbhome.mo[/i]

In my test "Hello world!" should be changed to "BLAH!!!!". Here is the original .po file:
[php]msgid ""
msgstr ""
"Project-Id-Version: \n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2011-12-05 02:33-0800\n"
"PO-Revision-Date: 2011-12-05 02:35-0800\n"
"Last-Translator: NAME <EMAIL>\n"
"Language-Team: \n"
"Language: \n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"

#: test.php:25
msgid "Hello world!"
msgstr "BLAH!!!!"[/php]

And here is my test.php script:
[php]<html>
<head>
<title>Testing PHP</title>
</head>

<body>
<?php
function GetLanguage()
{
    $lang = preg_split("/,/", $_SERVER["HTTP_ACCEPT_LANGUAGE"]);
    $lang = preg_split("/-/", $lang[0]);
    $lang = $lang[0];
    return $lang;
}

$locale = GetLanguage();
print("$locale<br>");

putenv("LC_ALL=$locale");
setlocale(LC_ALL, $locale);
bindtextdomain("dbhome", "./locale");
textdomain("dbhome");

$hello = _("Hello world!");
print($hello);
?>

</body>
</html>[/php]

I tried following the tutorial I found [here](http://mel.melaxis.com/devblog/2005/08/06/localizing-php-web-sites-using-gettext/), but it is not working. The page displays:

```
en
Hello world!
```

Am I doing something wrong, or maybe Sourceforge does not support gettext?

**----- EDIT -----**

I just tried the following and it returned "False". Does that mean Sourceforge's PHP setup is not using gettext?

[php]if (setlocale(LC_ALL, "en"))
    print("True");
else
    print("False");[/php]

**----- EDIT -----**

Oh well, I think I found an easier way to localize my page:

[i]test.php
locale/en.php
locale/es.php[/i]

en.php:
[php]<?php
// English
$greeting="Hello World!";
?>[/php]

es.php:
[php]<?php
// Spanish
$greeting="¡Hola Mundo!";
?>[/php]

test.php:
[php]...
<body>
<?php
function GetLanguage()
{
    $lang = preg_split("/,/", $_SERVER["HTTP_ACCEPT_LANGUAGE"]);
    $lang = preg_split("/-/", $lang[0]);
    $lang = $lang[0];
    return $lang;
}

$locale = GetLanguage();
print("$locale<br>");
$locale_file = "locale/" . $locale . ".php";
print("$locale_file<br>");

include $locale_file;
print($greeting);
?>

</body>
...[/php]

---


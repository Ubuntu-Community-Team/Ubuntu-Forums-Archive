---
title: "The list and the actual applications on Ubuntu"
date: 2021-11-10
forum: New to Ubuntu
---

### Post by bostjan-cadej on 2021-11-10
[COLOR=#000000][FONT=Arial]Please let me understand:[/FONT][/COLOR]


```
$ apt list --installed
```
[COLOR=#000000][FONT=Arial]It does not list the composer.[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Arial]$ apt search composer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]composer/impish,impish 2.0.9-2ubuntu2 all[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  dependency manager for PHP[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]it returns (among other) the composer 2.0.9[/FONT][/COLOR]


```
[COLOR=#000000][FONT=Arial]$ composer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Composer version 2.1.12 2021-11-09 16:02:04[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]it returns other version[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]Which ‘composer’ other applications are using?[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by Impavidus on 2021-11-10
The first command tells you that the package "composer" has not been installed through the package manager.

The second command tells you that the package "composer", version 2.0.9[COLOR=#000000][FONT=Arial]-2ubuntu2,[/FONT][/COLOR] is available for installation by the package manager.

The third command tells you that composer, version 2.1.12, is installed on your computer, but aparently not by the package manager. How you installed it is something you know best. Assuming only one version of composer is installed on your system, that is the version used whenever someting calls composer.

---

### Post by bostjan-cadej on 2021-11-10
Thank you for elaboration. It helped a lot.

I've installed composer through this steps:
```
$ sudo apt install php-cli unzip
$ cd ~
$ curl -sS https://getcomposer.org/installer -o composer-setup.php
$ HASH=`curl -sS https://composer.github.io/installer.sig`
$ php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
$ sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
$ composer
```

---


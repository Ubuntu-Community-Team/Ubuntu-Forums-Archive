---
title: "Problem with Bash Script to Compile PHP"
date: 2009-01-18
forum: Programming Talk
---

### Post by cybrid on 2009-01-18
Hi everyone, I have a problem with a bash script I'm trying to code; one of the things I always do in the machine I use as home server, is to build apache and php from sources (using the latests ones) and I also like to try diferent distros, so with the time I became tired of doing the same compilation process all over again each time I tested a new distro, so I said to myself, "Hey you sure can automate it with a bash script, why not try it?", so there I put myself to work, but It crashes just at the very begining and I'm unable to see why...

Does anybody see something wrong in the code?.
```

#!/usr/bin/env sh

####################################################
# Author: xabier.burgos@gmail.com
# Date: 18/01/2009
# Version: 0.1
# License: GPLv3
####################################################

############## Initial vars ########################
DEFAULT_PHP_INSTALL_DIR="/usr/local/php"
CONFIGURE_COMMAND="--with-install-dir="

############## Script start ########################
echo "Especifica directorio de instalacion para PHP: "
read PHP_INSTALL_DIR
if [ -n "$PHP_INSTALL_DIR" ]; then
	$CONFIGURE_COMMAND="${CONFIGURE_COMMAND}${PHP_INSTALL_DIR}"
else
	echo "No has especificado un directorio de instalacion para PHP, se utilizara $DEFAULT_PHP_INSTALL_DIR en su lugar"
	mkdir $DEFAULT_PHP_INSTALL_DIR
fi
echo '¿Deseas soporte para GD?: [yes/no]'
read GD
if [ $GD=='yes' ]; then
	echo 'Especifica directorio de instalacion de GD:'
	read GD_INSTALL_DIR
	if [ -n "$GD_INSTALL_DIR" ]; then
		$CONFIGURE_COMMAND="${CONFIGURE_COMMAND} --with--gd=${GD_INSTALL_DIR}"
		echo 'Especifica directorio de instalacion de libjpeg:'
		read LIBJPEG_INSTALL_DIR	
		if [ -n "$LIBJPEG_INSTALL_DIR" ]; then
			$CONFIGURE_COMMAND="${CONFIGURE_COMMAND} --with-jpeg-dir=${LIBJPEG_INSTALL_DIR}"
			echo 'Especifica directorio de instalacion de libpng:'
			read LIBPNG_INSTALL_DIR
			if [ -n "$LIBPNG_INSTALL_DIR" ]; then
				$CONFIGURE_COMMAND="${CONFIGURE_COMMAND} --with-png-dir=${LIBPNG_INSTALL_DIR}"
			else
				echo "libpng es necesario para incluir soporte para GD, la ruta introducida no es valida, luego  el soporte para GD sera eliminado"
			fi
		else
			echo "libjpeg es necesario para incluir soporte para GD, la ruta introducida no es valida, luego  el soporte para GD sera eliminado"
		fi
	fi
fi
echo '¿Deseas soporte para CURL?: [yes/no]'
read CURL
if [ $CURL=='yes' ]; then
	echo 'Especifica directorio de instalacion de CURL:'
	read CURL_INSTALL_DIR
	if [ -n "$CURL_INSTALL_DIR" ]; then
		$CONFIGURE_COMMAND="${CONFIGURE_COMMAND} --with-curl-dir=${CURL_INSTALL_DIR}"
	fi
fi
echo '¿Deseas soporte para MySQL?: [yes/no]'
read MYSQL
if [ $MYSQL=='yes' ]; then
	echo 'Especifica directorio de instalacion de MySQLi:'
	read MYSQLI_INSTALL_DIR
	if [ -n "$MYSQLI_INSTALL_DIR" ]; then
		$CONFIGURE_COMMAND="${CONFIGURE_COMMAND} --with-mysql-dir=${MYSQLI_INSTALL_DIR}"
	fi
fi
echo '¿Deseas instalar PHP como modulo de Apache 2?: [yes/no]'
read APACHE
if [ $APACHE=='yes' ]; then
	echo 'Especifica directorio de instalacion de APACHE:'
	read APACHE_INSTALL_DIR
	if [ -n "$APACHE_INSTALL_DIR" ]; then
		$CONFIGURE_COMMAND="${CONFIGURE_COMMAND' --with-apxs2=${APACHE_INSTALL_DIR}"
	fi
fi
echo "Configurando PHP..."
echo "./configure $CONFIGURE_COMMAND"
echo 'Compilando PHP...'
make
echo "Instalando PHP..."
make install

```

P.S: The script isn't finished yet.

---

### Post by Reiger on 2009-01-18
From what I gathered:
```

#!/usr/bin/bash

```
Should probably be:
```

#!/usr/bin/env sh

```

The env program/utility/command is used to resolve the sh interpreter of choice at run time which therefore will make your script more portable (env is nearly always at /usr/bin/env IIRC), and will make it play by the rules of the end-user system configuration better. Case in point:
On Debian and Debian-based distro's such as Ubuntu, the defualt sh **is not** bash, but _dash_ (or ash, either of the two) a much more lightweight shell and therefore a much better (because faster/less resource consuming) environment for your script as it will not need the full plethora of features BASH provides in 99% of the cases anyways.

On a more serious note: AFAIK PHP already *has* this (the tools to (re-)compile and pre-configure PHP at build time), it's what the PECL environment is for.

---

### Post by cybrid on 2009-01-18
Oops, sorry, I'm afraid I should have been more specific about the "crash".

When I lauch the script, I do it using sh, so I do "sh php_install.sh", and it crashes just after entering the install directory I want, here:

```
$CONFIGURE_COMMAND="${CONFIGURE_COMMAND}${PHP_INSTALL_DIR}"
else
```

the exit being:
```
':not a valid identifier: read: `PHP_INSTALL_DIR
./php.install.sh: line 19: syntax error near unexpected token `else'
./php_install.sh: line 19: `else'

```

P.S: Reiger, thanks for the tip.

---

### Post by cybrid on 2009-01-19
Bump. Nobody has an idea of what can it be?.

---

### Post by skoorbevad on 2009-01-24
You're attempting to define your variables improperly.  Remember, the leading "$" in front of a bash variable or variable interpretation is only needed if you're referencing the contents of it.

In the case of setting it, you need to do something like:

```

FOO="$VAR1$VAR2"

```

**NOT**

```

$FOO="$VAR1$VAR2"

```

If you start it with the $, bash is going to assume you mean you're making a reference to the contents of $FOO, which if it doesn't exist, it's going to error out.  If it does exist, it's going to try to execute it (also not what you want).

You've got that in a few places in your script -- you may want to correct them.



> **cybrid said:**
> 
```
$CONFIGURE_COMMAND="${CONFIGURE_COMMAND}${PHP_INSTALL_DIR}"
else
```


---

### Post by cybrid on 2009-01-26
Thanks for the correction, I finally managed to get the script right about a week ago but thanks anyway. Now I'm having trouble compiling libjpeg from sources XD, but that's another story.

---


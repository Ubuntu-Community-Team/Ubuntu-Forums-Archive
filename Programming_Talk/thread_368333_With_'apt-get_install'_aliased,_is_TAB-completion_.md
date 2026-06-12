---
title: "With 'apt-get install' aliased, is TAB-completion possible?"
date: 2007-02-23
forum: Programming Talk
---

### Post by Enselic on 2007-02-23
As you know, 'apt-get install' has TAB-completion for packages.

I have an alias for apt-get install, namely 'alias sagi='sudo apt-get install'. With the alias, the TAB-completion doesn't work.

Does anyone know of a way to make TAB-completion work with aliases?

---

### Post by louis_nichols on 2007-02-23
You can make a script with the command and place it in /usr/bin. I'm not good with scripts, so the actual details of the following might be wrong, but what you have to do is:

```
gksudo gedit /usr/bin/sagi
```
inside it put:
```
#!/bin/bash
apt-get install $*
```
and it should work.

---

### Post by Enselic on 2007-02-23
Hmm, I'm not sure that should do what I want, I don't know any bash, but it seems to me as if that script simply would pass parameters on to sudo apt-get install.

In any case, I tested it and it didn't work :/

Thank you for your answer anyway.

---

### Post by duff on 2007-02-23
edit the "_apt_get" function in /etc/bash_completion

---

### Post by louis_nichols on 2007-02-23
> **Enselic said:**
> Hmm, I'm not sure that should do what I want, I don't know any bash, but it seems to me as if that script simply would pass parameters on to sudo apt-get install.

In any case, I tested it and it didn't work :/

Thank you for your answer anyway.

Actually, it works. :)

I just tried it. Jut that I forgot about making the file executable. This is done this way:

sudo chmod +x /usr/bin/sagi

Then it works exactly as intended. ;)

---

### Post by Enselic on 2007-02-23
> **duff said:**
> edit the "_apt_get" function in /etc/bash_completion

Ah, there's where to start looking. Through that tip, I came up with a solution which involved me making my first bash-script:

Put this in e.g. /etc/apt_completion
```

#   apt_completion - APT-related completion functions for bash
#
#   Copyright (C) 2007 Martin Nordholts <enselic@gmail.com>
#
#   This file heavily based on 'bash_completion' which is
#   Copyright (C) Ian Macdonald <ian@caliban.org>
#
#   This program is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation; either version 2, or (at your option)
#   any later version.
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software Foundation,
#   Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.
#
#   Last edited: 2007-02-23

# features supported by bash 2.05 and higher
if [ ${BASH_VERSINFO[0]} -eq 2 ] && [[ ${BASH_VERSINFO[1]} > 04 ]] ||
   [ ${BASH_VERSINFO[0]} -gt 2 ]; then
	filenames="-o filenames"
fi

# declare the aliases
alias sagi='sudo apt-get install'
alias sagr='sudo apt-get remove'
alias acsh='apt-cache show'

#does not require completion, but is useful to have aliased
alias acs='sudo apt-cache search'



#
# initialize completion
#

# This function checks whether we have a given program on the system.
# No need for bulky functions in memory if we don't.
#
have()
{
	unset -v have
	PATH=$PATH:/sbin:/usr/sbin:/usr/local/sbin type $1 &>/dev/null &&
		have="yes"
}

have apt-get &&
_apt_get_install()
{
	local cur

	COMPREPLY=()
	cur=${COMP_WORDS[COMP_CWORD]}

	COMPREPLY=( $( apt-cache pkgnames $cur 2> /dev/null ) )
	return 0
} &&
complete -F _apt_get_install $filenames sagi

have apt-get &&
_apt_get_remove()
{
	local cur

	COMPREPLY=()
	cur=${COMP_WORDS[COMP_CWORD]}

	if [ -f /etc/debian_version ]; then
		# Debian system
		COMPREPLY=( $( _comp_dpkg_installed_packages \
				$cur ) )
	else
		# assume RPM based
		_rpm_installed_packages
	fi

	return 0
} &&
complete -F _apt_get_remove $filenames sagr

have apt-cache &&
_apt_cache_show()
{
	local cur

	COMPREPLY=()
	cur=${COMP_WORDS[COMP_CWORD]}
	
	COMPREPLY=( $( apt-cache pkgnames $cur 2> /dev/null ) )

	return 0
} &&
complete -F _apt_cache_show $filenames acsh



#
# setup get-packages functions
#

have dpkg && {
have grep-status && {
_comp_dpkg_installed_packages()
{
	grep-status -P -e "^$1" -a -FStatus 'install ok installed' -n -s Package
}
} || {
_comp_dpkg_installed_packages()
{
	grep -A 2 "Package: $1" /var/lib/dpkg/status | \
		grep -B 2 'ok installed' | grep "Package: $1" | cut -d\  -f2
}
}
}

have rpm &&
_rpm_installed_packages()
{
	local ver nodig nosig

	if [ -r /var/log/rpmpkgs -a \
		/var/log/rpmpkgs -nt /var/lib/rpm/Packages ]; then
		# using RHL 7.2 or later - this is quicker than querying the DB
		COMPREPLY=( $( sed -ne \
		's|^\('$cur'.*\)-[0-9a-zA-Z._]\+-[0-9a-z.@]\+.*\.rpm$|\1|p' \
				/var/log/rpmpkgs ) )
	else
		nodig=""
		nosig=""
		ver=$(rpm --version)
		ver=${ver##* }
	  
		if [[ "$ver" > "4.0.4" ]]; then
			nodig="--nodigest"
		fi
		if [[ "$ver" > "4.0.99" ]]; then
			nosig="--nosignature"
		fi

		COMPREPLY=( $( rpm -qa $nodig $nosig | sed -ne \
		's|^\('$cur'.*\)-[0-9a-zA-Z._]\+-[0-9a-z.@]\+$|\1|p' ) )
	fi
}

```

Add this to the end of ~/.bashrc
```

# enable APT related aliases and setup tab-completion on all of them
if [ -f /etc/apt_completion ]; then
    . /etc/apt_completion
fi

```

Now simply reload ~/.bashrc
```

$ source ~/.bashrc
```

This works fine for me, but it would be nice to hear if the script works out-of-the-box for someone else.

> **louis_nichols said:**
> Actually, it works. :)

Well that's totally weird, when I try, it won't work:
```

martin@martin-laptop:~$ sudo echo -e '#!/bin/bash\napt-cache show $*' | sudo tee /usr/local/bin/acshow
#!/bin/bash
apt-cache show $*
martin@martin-laptop:~$ sudo chmod +x /usr/local/bin/acshow
martin@martin-laptop:~$ acshow gi<PRESSES TAB, BUT NO COMPLETION>

```

In any case, I learned a bit about how bash-scripting works ;)

---


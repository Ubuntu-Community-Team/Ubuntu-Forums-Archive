---
title: "[BASH] Server Information Script"
date: 2008-06-11
forum: Programming Talk
---

### Post by altonbr on 2008-06-11
Because of the recent tragedies and lack of information at a shared-hosting environment, I decided to make a small script that tests programming language availability, software versions and hardware information.

Right now it is only for the server (so nautilus and wine are excluded (although some people may run wine on the server)) and outputs simple text files.

Also, due to the nature of shared hosting where you're often chrooted in, even with SSH, I'm looking to run executables rather than print path information (such as /proc/meminfo and /proc/cpuinfo).

```
#!/bin/bash
#!/bin/sh

# <description>
# find_info.sh
# Copyright (C) 2008  Brett Alton <brett.jr.alton@gmail.com>

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

if [ $# -ne 1 ]; then
	echo " !! Exiting: incorrect number of parameters."
	echo " -- USAGE: $0 save_to_dir"
	exit
fi

save_to_dir=$1
cd $save_to_dir

[ -f 'prog_langs.txt' ] && rm prog_langs.txt

# VERSION TESTS
bash --version > bash.txt || rm bash.txt
cat /proc/cpuinfo > cpuinfo.txt || rm cpuinfo.txt
cat /proc/meminfo > meminfo.txt || rm meminfo.txt
df -h > disk_usage.txt || rm disk_usage.txt
#nautilus --version > nautilus.txt || rm nautilus.txt
uname -a > uname.txt || rm uname.txt
#wine --version > wine.txt || rm wine.txt

# PROGRAMMING LANGUAGES
#perl
echo 'print "Hello World!;"' > test.pl && perl test.pl ; rm test.pl
if [ $? -eq 0 ]; then
	echo 'perl' >> prog_langs.txt
	#perl --version >> prog_langs.txt
fi

#php
echo '<?php echo "Hello World!"; ?>' > test.php && php test.php ; rm test.php
if [ $? -eq 0 ]; then
	echo 'php' >> prog_langs.txt
	#php --version >> prog_langs.txt
fi

#python
echo 'print "Hello World!"' > test.py && python test.py ; rm test.py
if [ $? -eq 0 ]; then
	echo 'python' >> prog_langs.txt
	#python --version >> prog_langs.txt
fi

#ruby
echo 'puts "Hello World!"' > test.rb && ruby test.rb ; rm test.rb
if [ $? -eq 0 ]; then
	echo 'ruby' >> prog_langs.txt
fi
```

What are your thoughts?

---

### Post by dtmilano on 2008-06-11
I guess that you are trying to test if the script run, not if the rm was successful.
> $ echo 'puts "Hello World!"' > test.rb && ruby test.rb ; rm test.rb
The program 'ruby' is currently not installed.  You can install it by typing:
sudo apt-get install ruby
-bash: ruby: command not found
$ echo $?
0


Move the rm after the if, or much better use a trap.

---

### Post by altonbr on 2008-06-11
Hmm, thanks, I'm researching trap ([http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_12_02.html)) as we speak.

What else would you want to know about a Linux server when you first hop on it?

---

### Post by ghostdog74 on 2008-06-11
actually, why don't just search for the binary executable itself. For Perl, the  executable interpreter is perl, for Python its python etc
```

find /usr -name python or perl or java or ruby etc.......... 

``` 
because if you do this for eg: ruby test.rb, sometimes ruby interpreter may not be in the PATH of the user executing the script. However most executables would be in /usr, such as /usr/local/bin eg

---

### Post by dtmilano on 2008-06-12
You can find any file named as an interpreter an erroneously believe that the interpreter is present.
Why don't just figure out what distribution are you in, and then use the platform package manager to realize what's instaled and what's not.

But, what are you trying to discover ?
What information are you looking for ?

---

### Post by ghostdog74 on 2008-06-12
> **dtmilano said:**
> You can find any file named as an interpreter an erroneously believe that the interpreter is present.
its trivial, interpreters are executables. a small eg
```

find /usr/bin -name "perl" | xargs file -N "{}" | awk '/executable/{print "perl executable exists"}'

```

---

### Post by altonbr on 2008-06-13
> **ghostdog74 said:**
> its trivial, interpreters are executables. a small eg
```

find /usr/bin -name "perl" | xargs file -N "{}" | awk '/executable/{print "perl executable exists"}'

```

That code makes sense, but the reason why I have to use 'perl' as an executable is because on some shared systems, you're chrooted so you can't search root directories.

I'm also looking for the BASH version and what not because I've found a fair bit of BASH 2.0 / Linux 2.4 boxes floating around, and that difference between BASH 2.0 and 3.0 can kill scripts (ie: {a..z} not being supported in 2.0)

---

### Post by geirha on 2008-06-13
Why does your script have two sh-bangs?

bash sets it's version in several variables. Search for BASH_VERSINFO and BASH_VERSION in bash's man-page. They are easier to parse than `bash --version`.

Try "type -a perl" etc (bash builtin). It will list all executables named perl in $PATH. You might find several versions of perl for instance ...

---


---
title: "Bash Script Help"
date: 2009-12-10
forum: Programming Talk
---

### Post by Ocxic on 2009-12-10
I have a bash script to install the old "smooth" gtk theme engine that is no longer included with ubuntu, but some theme's still use.

i've run into a small issue; this is what happens when i run the script(tracing is turned on):

```

ikrel@xilti:~$ sudo install_smooth-engine 
[sudo] password for ikrel: 
+ tmp_dir=/tmp/smooth/
++ id -u
+ '[' 0 '!=' 0 ']'
++ smooth_install
++ mkdir /tmp/smooth/
++ cd /tmp/smooth/
++ '[' '' '!=' '' ']'
++ '[' -f gtk2-engines_2.14.3-0ubuntu2_i386.deb ']'
++ '[' -f gtk2-engines_2.14.3-0ubuntu2_amd64.deb ']'
++ echo 'File not found! Please download:'
++ echo 'gtk2-engines_2.14.3-0ubuntu2_amd64.deb or gtk2-engines_2.14.3-0ubuntu2_i386.deb'
++ exit 1
+ File not 'found!' Please download: gtk2-engines_2.14.3-0ubuntu2_amd64.deb or gtk2-engines_2.14.3-0ubuntu2_i386.deb
/usr/local/bin/install_smooth-engine: line 57: File: command not found
ikrel@xilti:~$ 

```line 57 from the script is:
```

# Check if user is root
if [ $(id -u) != "0" ];
then
    echo "This script must be run as root. Aborting!"
    exit 1
else
    $(smooth_install)  <---line 57
fi

```This is the script:

```

#!/bin/bash -x

# This installs the missing "smooth" theme engine.
# This script must be run as root

# Constants
tmp_dir=/tmp/smooth/


function smooth_install {

mkdir $tmp_dir
cd $tmp_dir
    
while [ "$1" != "" ]; do
    case $1 in
        --i386 )        wget http://mirrors.kernel.org/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.14.3-0ubuntu2_i386.deb
                ;;
        
        --amd64 )       wget http://launchpadlibrarian.net/16133561/gtk2-engines_2.14.3-0ubuntu2_amd64.deb
                ;;
        
        --help | -h | * ) echo "Usage: install_smooth-engine [--i386] or [--amd64]" ;;
    esac
done

    
    
if [ -f gtk2-engines_2.14.3-0ubuntu2_i386.deb ];
    then
        ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb
        
elif [ -f gtk2-engines_2.14.3-0ubuntu2_amd64.deb ];
    then
        ar x gtk2-engines_2.14.3-0ubuntu2_amd64.deb
else
    echo "File not found! Please download:"
    echo "gtk2-engines_2.14.3-0ubuntu2_amd64.deb or gtk2-engines_2.14.3-0ubuntu2_i386.deb"
    exit 1
fi  
          
tar xf data.tar.gz
cp usr/share/gtk-engines/smooth.xml /usr/share/gtk-engines
cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so /usr/lib/gtk-2.0/2.10.0/engines

cd ..
rm -rf $tmp_dir

}
    
# Check if user is root
if [ $(id -u) != "0" ];
then
    echo "This script must be run as root. Aborting!"
    exit 1
else
    $(smooth_install)
fi

```any ideas on how to fix this issue would be greatly helpful and appreciated, thanks.

---

### Post by Brandon Williams on 2009-12-10
> **Ocxic said:**
> line 57 from the script is:
```

# Check if user is root
if [ $(id -u) != "0" ];
then
    echo "This script must be run as root. Aborting!"
    exit 1
else
    $(smooth_install)  <---line 57
fi

```

The "$(...)" in line 57 performs command substitution, which means that the expression will be substituted on the command line with the output from the command inside the parentheses. In this case, smooth_install produces "File not 'found!'..." as output, and then "File not 'found!'..." is executed as a command. There is no command 'File', so bash is reporting this error.

I think you just want to remove "$(" and ")" from the expression and run smooth_install on its own.

---

### Post by Ocxic on 2009-12-10
OK, that worked, and with a light revision now i have:
```

#!/bin/bash

# This installs the missing "smooth" theme engine.
# This script must be run as root

# Constants
tmp_dir=/tmp/smooth/


function smooth_install {

if [ -f gtk2-engines_2.14.3-0ubuntu2_i386.deb ];
    then
        ar x gtk2-engines_2.14.3-0ubuntu2_i386.deb
        
elif [ -f gtk2-engines_2.14.3-0ubuntu2_amd64.deb ];
    then
        ar x gtk2-engines_2.14.3-0ubuntu2_amd64.deb
else
    echo "File not found! Please download:"
    echo "gtk2-engines_2.14.3-0ubuntu2_amd64.deb or gtk2-engines_2.14.3-0ubuntu2_i386.deb"
    exit 1
fi  
          
tar xf data.tar.gz
cp usr/share/gtk-engines/smooth.xml /usr/share/gtk-engines
cp usr/lib/gtk-2.0/2.10.0/engines/libsmooth.so /usr/lib/gtk-2.0/2.10.0/engines

cd ..
rm -rf $tmp_dir
exit 0
}

function temp_dir {
mkdir $tmp_dir
    cd $tmp_dir
}    

# Check if user is root
if [ $(id -u) != "0" ];
then
    echo "This script must be run as root. Aborting!"
    exit 1
else
    

    
while [ "$1" != "" ]; do
    case $1 in
        --i386 )        temp_dir
                        wget http://mirrors.kernel.org/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.14.3-0ubuntu2_i386.deb
                        smooth_install
                        exit 0
                ;;
        
        --amd64 )       temp_dir
                        wget http://mirrors.kernel.org/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.14.3-0ubuntu2_amd64.deb
                        smooth_install
                        exit 0
                ;;
        
        --help | -h | * ) echo "Usage: install_smooth-engine [--i386] or [--amd64]"
                          exit 1;;
    esac
done

fi

```and it works, but "[ --help | -h | * ) echo "Usage: install_smooth-engine [--i386] or [--amd64]" ;; ]" does not show usage when there are no arguments supplied in the command line ( -h and --help both work)


P.S. if anyone has any other recommendation to improve the script let me know, thanks.

---

### Post by geirha on 2009-12-11
If there are no arguments, [ "$1" != "" ] will return false, and the while loop will be skipped. Now, the while-loop itself is useless. You only check one argument, and regardless of what it is, you call exit.

BTW, you should use **[[** (string comparison and file checks) or **((** (arithmetic comparison) instead of the **[**/**test** command when scripting for bash. Only use [ if you are scripting for POSIX sh. Also, bash keeps the effective uid of the user running the script in the special shell variable EUID, so no need to execute the external id command.

```

if ((EUID == 0)); then 
    echo you are root.
else
    echo $EUID is not root\'s uid.
fi
```

---

### Post by Ocxic on 2009-12-11
could you elaborate a little more about this subject geirha?

---

### Post by geirha on 2009-12-13
> **Ocxic said:**
> could you elaborate a little more about this subject geirha?

[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

Also, I highly recommend the bash guide at that wiki. [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---


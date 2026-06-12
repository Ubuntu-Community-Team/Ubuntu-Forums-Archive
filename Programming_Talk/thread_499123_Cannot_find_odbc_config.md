---
title: "Cannot find odbc_config"
date: 2007-07-12
forum: Programming Talk
---

### Post by ranmanh on 2007-07-12
Hi,

trying to compile a piece of code Advanced Stock Tracker (AST)) ,but missing that particular config file odbc_config.
"Presumably" I got the unixODBC dev installed in the system.. But I cannot find that particular one..

Any idea?

Thanks

Gonzalo.

---

### Post by ukripper on 2007-07-12
What lang code is written in?

---

### Post by ranmanh on 2007-07-17
Hi,

Ubuntu feisty fawn comes with a bug.. when installing  ODBC libraries for UNIX (development files) (2.2..11-13 feisty)  odbc_config is missing from /bin, which are the script necessary for compilation.

I got it from other sources, and....It worked perfectly fine.

Just to let know everyone.

Thanks

Gonzalo.

---

### Post by cikic on 2007-09-23
Hello!

I have the same Problem on Edgy.  Just apt-geted unixodbc but no odbc_config file. How have you got the File? I tred to compile unixodbc from source getting the file but compilation fails. 

CAbout.h:15:21: error: qwidget.h: No such file or directory

Is there an other deb repository for getting a working unixodbc?

Thanks
chris

---

### Post by djkork on 2008-01-08
Here. A copy of the script. You have to copy it to /usr/bin/odbc_config and give  it execute permission.

You have to have unixodbc-dev package installed.

And now..... the script :):

> 
#! /bin/sh

# This shell script saves various pieces of information about the
# installed version of unixODBC.  Packages that interface to
# unixODBC can use it to configure their build.
# This file replaces the standard odbc_config, which is not
# relocatable
#
# Author:  Alberto Di Meglio <alberto.di.meglio@cern.ch> 
# Public domain

me=`basename $0`
mydir=`dirname $0`
mydir=${mydir%/bin}

# stored configuration values
val_prefix="$mydir"
val_bindir="$mydir/bin"
val_includedir="$mydir/include"
val_libdir="$mydir/lib"
val_libs="-L$mydir/lib -lodbc"
val_version='2.2.11'

help="\
$me provides information about the installed version of unixODBC.

Usage:
  $me OPTION...

Options:
  --prefix              show the installation prefix
  --exec-prefix         show the installation prefix
  --bin-prefix          show location of user executables
  --include-prefix      show location of C header files of the client
                        interfaces
  --lib-prefix          show location of object code libraries
  --libs                show link arguments
  --version             show the unixODBC version, then exit
  --help                show this help, then exit"

advice="\
Try \"$me --help\" for more information."

if test "$#" -eq 0 ; then
    echo "$me: argument required" 1>&2
    echo "$advice" 1>&2
    exit 1
fi

show=

for opt
do
    case "$opt" in
        --prefix)       show="$show \$val_prefix";;
        --exec-prefix)  show="$show \$val_prefix";;
        --bin-prefix)   show="$show \$val_bindir";;
        --include-prefix)
                        show="$show \$val_includedir";;
        --lib-prefix)   show="$show \$val_libdir";;
        --libs)         show="$show \$val_libs";;
        --configure)    show="$show \$val_configure";;

	--version)      echo "$val_version"
                        exit 0;;
	--help|-\?)     echo "$help"
                        exit 0;;
        *)              echo "$me: invalid argument: $opt" 1>&2
                        echo "$advice" 1>&2
                        exit 1;;
    esac
done

for thing in $show
do
    eval "echo $thing"
done

# end of odbc_config



---


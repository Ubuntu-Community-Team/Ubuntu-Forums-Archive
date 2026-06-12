---
title: "[bash] [code review] Script to download and update iso's"
date: 2011-08-28
forum: Programming Talk
---

### Post by toobuntu on 2011-08-28
I created a script to grab and checksum the latest iso images of lubuntu (alternate installer), debian testing (using installer build from sid), lmde (gnome) and crunchbang (openbox).

Hoping for a code review. Try "./isodl.sh -d d" twice and you'll see what I mean.

[UPDATE] Seem to have solved it. See Post #2 below for the diff. Immediately below is the current version of the script.
```

#! /bin/sh
set -u
set -e

# isodl.sh created on 27-Aug-2011
# copyright 2011 Todd Schulman
# grabs the current daily build image for installing debian testing,
# using the debian-installer build from sid. extended to optionally
# grab the lubuntu alternate daily build image.

# Modification History
# 08/27/2011 TS create original script
# 08/27/2011 TS save bandwidth by using curl instead of lwp-download 
#		and only download the remote file if the remote file 
#		has a more recent timestamp than the local file
# 08/27/2011 TS add -a arch option and test that $ISOFILE exists before
#		invoking curl with the -z timestamp checking option
# 08/28/2011 TS	always grab the current remote checksum file (because
#		the Debian checksum file has different contents depending
#		upon arch but the filename is the same; by contrast, the
#		Ubuntu checksum file contains all architectures), and
#		replace an existing local copy of it atomically
# 08/28/2011 TS	add -f force download option, and add a warning message
#		(and helpful suggestion) if the checksums do not match.
# 08/28/2011 TS	add LMDE and Crunchbang
# 08/29/2011 TS bugfixes: use cp for atomic updating of the iso, trap 
#		user interrupts (INT) and kills (TERM) but not exits, 
#		add syncs for safety
# 08/29/2011 TS	code cleanup, better help message, stable release

#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.

#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.

#    You should have received a copy of the GNU General Public License
#    along with this program.  If not, see <http://www.gnu.org/licenses/>.

distro=
arch=amd64
force=
CURLOPTS="-ROL"

 print_help()	{
          cat >&2 << EOF
usage: $0 [-v] [-h] -d [d|debian|l|lubuntu|m|lmde|c|crunchbang] [-a amd64|i386] [-f]
  -v verbose
  -h help
  -d distro, options are [d|debian|l|lubuntu|m|lmde|c|crunchbang]
  -a arch, options are [amd64|i386]
  -f force download, even if the file is already present on the local filesystem
EOF
          exit 1
		}

[ $# -lt 1 ] && print_help || :

while getopts vhd:a:f opt
do
    case "$opt" in
      v)  set -x ; CURLOPTS=${CURLOPTS}v ;;
      h)  print_help;;
      d)  distro="$OPTARG";;
      a)  arch="$OPTARG";;
      f)  force=y;;
      \?) # unknown flag
	  print_help;;
      :)
      	  printf "option $OPTARG requires an argument\n" >&2
     	  exit 1
      	  ;;
    esac
done
shift $( expr $OPTIND - 1 )

# test for mandatory -d option
if [ "x" == "x$distro" ]; then
  message="-d [option] is required"
  printf >&2 "%s " $message
  printf >&2 "\n"
  message=
  print_help
fi

CHECKSUMFILE=
CHECKSUMURL=
CHECKSUMPROTO=
ISOFILE=
ISOURL=
case $distro in
  d|debian)
	ISOFILE=debian-testing-${arch}-netinst.iso
	ISOURL=http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/arch-latest/${arch}/iso-cd/${ISOFILE}
	CHECKSUMFILE=SHA512SUMS.small
	CHECKSUMURL=http://cdimage.debian.org/cdimage/daily-builds/sid_d-i/arch-latest/${arch}/iso-cd/${CHECKSUMFILE}
	CHECKSUMPROTO=512
	;;
  l|lubuntu)
	ISOFILE=oneiric-alternate-${arch}.iso
	ISOURL=http://cdimage.ubuntu.com/lubuntu/daily/current/${ISOFILE}
	CHECKSUMFILE=SHA256SUMS
	CHECKSUMURL=http://cdimage.ubuntu.com/lubuntu/daily/current/${CHECKSUMFILE}
	CHECKSUMPROTO=256
	;;
  m|lmde)
	if [[ ${arch} = amd64 ]] ; then arch=64bit
	else arch=32bit
	fi
	ISOFILE=linuxmint-201108-gnome-${arch}-rc.iso
	ISOURL=http://linuxfreedom.com/linuxmint/linuxmint.com/testing/${ISOFILE}
	CHECKSUMFILE=sha256sum.txt
	CHECKSUMURL=http://linuxfreedom.com/linuxmint/linuxmint.com/testing/${CHECKSUMFILE}
	CHECKSUMPROTO=256
	;;
  c|crunchbang)
	printf "Crunchbang Linux 10 \"statler\" is currently only available as a torrent\nSee http://crunchbanglinux.org/downloads/\n"
	exit 0
esac

cd $HOME/Downloads/
sync
[[ -e ${CHECKSUMFILE} ]] && cp -a ${CHECKSUMFILE} ${CHECKSUMFILE}.old || :
curl ${CURLOPTS} ${CHECKSUMURL}
if [[ -e ${CHECKSUMFILE} ]]
then if [[ -e ${CHECKSUMFILE}.old ]]
     then rm -f ${CHECKSUMFILE}.old
     fi
else 
   mv ${CHECKSUMFILE}.old ${CHECKSUMFILE}
fi
sync

iso_rollback()	{
	sync
	[[ -e ${ISOFILE}.old ]] && mv ${ISOFILE}.old ${ISOFILE} || :
	sync
	printf >&2 "aborted\n"
	exit 3
		}
trap iso_rollback INT TERM
remove_old_iso()	{
   sync
   [[ -e ${ISOFILE} ]] && rm -f ${ISOFILE}.old 2> /dev/null || :
   sync
			}
if [[ $force = y ]]
then curl ${CURLOPTS} ${ISOURL}
elif [[ -e ${ISOFILE} ]] ; then
	cp -a ${ISOFILE} ${ISOFILE}.old
	curl -z ${ISOFILE}.old ${CURLOPTS} -C - ${ISOURL}
	remove_old_iso
else curl ${CURLOPTS} -C - ${ISOURL}
fi
trap - INT TERM EXIT

checksum_error()	{
	printf >&2 "WARNING: computed checksum did NOT match\nTry again with the -f option to force a re-download\n"
	exit 2
			}

sync
shasum -a ${CHECKSUMPROTO} -c ${CHECKSUMFILE} ${ISOFILE} 2> /dev/null | grep 'OK$' || checksum_error
exit 0
```

---

### Post by toobuntu on 2011-08-29
This seems to fix it:

```
$ diff -Nru ../isodl-orig.sh ../isodl.sh 
--- ../isodl-orig.sh	2011-08-29 00:36:35.000000000 -0400
+++ ../isodl.sh	2011-08-29 00:35:28.000000000 -0400
@@ -23,6 +23,9 @@
 # 08/28/2011 TS	add -f force download option, and add a warning message
 #		(and helpful suggestion) if the checksums do not match.
 # 08/28/2011 TS	add LMDE and Crunchbang
+# 08/29/2011 TS bugfixes: use cp for atomic updating of the iso, trap 
+#		user interrupts (INT) and kills (TERM) but not exits, 
+#		add syncs for safety
 
 #    This program is free software: you can redistribute it and/or modify
 #    it under the terms of the GNU General Public License as published by
@@ -125,26 +128,29 @@
 else 
    mv ${CHECKSUMFILE}.old ${CHECKSUMFILE}
 fi
+sync
 #lwp-download ${ISOURL}
 
 iso_rollback()	{
-	if [[ -e ${ISOFILE}.old ]] ; then
-	   mv ${ISOFILE}.old ${ISOFILE}
-	fi
+	sync
+	[[ -e ${ISOFILE}.old ]] && mv ${ISOFILE}.old ${ISOFILE} || :
+	sync
 	printf >&2 "aborted\n"
 	exit 3
 		}
-trap iso_rollback INT TERM EXIT
+trap iso_rollback INT TERM
 remove_old_iso()	{
-   if [[ -e ${ISOFILE} ]] ; then rm -f ${ISOFILE}.old ; fi
+   sync
+   [[ -e ${ISOFILE} ]] && rm -f ${ISOFILE}.old 2> /dev/null || :
+   sync
 			}
 if [[ $force = y ]]
 then curl ${CURLOPTS} ${ISOURL}
 elif [[ -e ${ISOFILE} ]] ; then
-	mv ${ISOFILE} ${ISOFILE}.old
-	curl -z ${ISOFILE}.old ${CURLOPTS} ${ISOURL}
+	cp -a ${ISOFILE} ${ISOFILE}.old
+	curl -z ${ISOFILE}.old ${CURLOPTS} -C - ${ISOURL}
 	remove_old_iso
-else curl ${CURLOPTS} ${ISOURL}
+else curl ${CURLOPTS} -C - ${ISOURL}
 fi
 #   [ -e ${ISOFILE} ] && ( mv ${ISOFILE} ${ISOFILE}.old && curl -z ${ISOFILE}.old ${CURLOPTS} ${ISOURL} && rm -f ${ISOFILE}.old ) || curl ${CURLOPTS} ${ISOURL}
 trap - INT TERM EXIT
@@ -154,5 +160,6 @@
 	exit 2
 			}
 
+sync
 shasum -a ${CHECKSUMPROTO} -c ${CHECKSUMFILE} ${ISOFILE} 2> /dev/null | grep 'OK$' || checksum_error
 exit 0
```

---


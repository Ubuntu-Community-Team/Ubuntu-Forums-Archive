---
title: "Mirror Speed Tester Script"
date: 2006-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by LanceRushing on 2006-09-05
I always like to use the fastest mirrors for myself and to take some traffic off of the main servers.  But I never know which mirror to choose.  So I wrote this little script to test all of the mirrors.  (**Requires curl: apt-get install curl **)

Just save this script as mirror_test.sh and then run it with either:

$ bash mirror_test.sh
or 
$ chmod +x mirror_test.sh
$ ./mirror_test.sh

```

#!/bin/bash

# mirror_test.sh
# This script tests a list of ubuntu mirrors for speed
#
# I never could find anything in  Ubuntu to automatically test and setup  mirrors.
# There might  be something  already there,  but I  decided to  write this  little
# script for myself.  Hope you enjoy.
#
# @TODO Automatically pull mirror list from https://wiki.ubuntu.com/Archive
# @TODO Write resuts to /etc/apt/sources.list
# @TODO Add command line parsing for above options
#
# @AUTHOR Lance Rushing <lance_rushing@hotmail.com>
# @SINCE 9/1/2006
# This script is covered under the GNU Public License: http://www.gnu.org/licenses/gpl.txt


## get list from: https://wiki.ubuntu.com/Archive
MIRRORS="ftp://ftp.osuosl.org/pub/ubuntu/
ftp://ftp.ussg.iu.edu/linux/ubuntu/
ftp://mirror.clarkson.edu/pub/distributions/ubuntu/
ftp://mirror.mcs.anl.gov/pub/ubuntu/
ftp://mirrors.cat.pdx.edu/ubuntu/
ftp://mirrors.xmission.com/ubuntu/
ftp://ubuntu.cs.utah.edu/pub/ubuntu/ubuntu/
ftp://ubuntu.mirrors.tds.net/ubuntu/
http://ftp.ale.org/pub/mirrors/ubuntu/
http://ftp.osuosl.org/pub/ubuntu/
http://ftp.ussg.iu.edu/linux/ubuntu/
http://lug.mtu.edu/ubuntu/
http://mirror.clarkson.edu/pub/distributions/ubuntu/
http://mirror.mcs.anl.gov/pub/ubuntu/
http://mirrors.cat.pdx.edu/ubuntu/
http://mirrors.cs.wmich.edu/ubuntu/
http://mirrors.xmission.com/ubuntu/
http://ubuntu.cs.utah.edu/ubuntu/
http://ubuntu.mirrors.tds.net/ubuntu/
http://ubuntu.secs.oakland.edu/
http://www.opensourcemirrors.org/ubuntu/
http://mirror.cs.umn.edu/ubuntu/"

## Any moderatly sized file to pull to run the speed test
FILE="dists/dapper/main/binary-i386/Packages.bz2"

## Number of seconds before the test is considered a failure
TIMEOUT="5"

## Sting to store results in
RESULTS=""

for MIRROR in $MIRRORS ; do
	
	echo -n "Testing ${MIRROR} "
	
	URL="${MIRROR}%{FILE}"
	
	TIME=`curl --max-time $TIMEOUT --silent --output /dev/null --write-out %{time_total} $URL`
	
	if [ "$TIME" == "0.000" ] ; then
		echo "Fail";
	else 
		echo $TIME
		RESULTS="${RESULTS}${TIME}\t${MIRROR}\n";
	fi

done;

echo "\nResults:"
echo -e $RESULTS | sort -n 

```

---


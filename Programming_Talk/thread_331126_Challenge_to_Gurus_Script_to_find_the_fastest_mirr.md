---
title: "Challenge to Gurus: Script to find the fastest mirrors of ubuntu-update"
date: 2007-01-04
forum: Programming Talk
---

### Post by 3togo on 2007-01-04
As we all know, the Taiwan earthquake damaged the optical fiber and making internet very very slow in Asia. I want a script that could locate the fastest mirror. Below is a very bad one I wrote. Could anyone provide me with a better version. Any programming language is welcome.
jc@jc-desktop:~$ cat mirrortest
```
#!/bin/sh
##### script to locate the fastest mirrors ########
##### written by 3 togo ###########################
SUCCESS=0
FAILURE=1

function integer()
{
echo $( expr match "$1" '\([0-9]*\)' )

}
IsNumeric () {
case "$1" in
*[!0-9,.]*) return 1;; # invalid
*) return 0;; # valid
esac
}

function findmin {
#echo "zzz=$2"
if  ! ( IsNumeric "$2" ) || [ -z $2 ] 
then
return $FAILURE
fi


int_fastesttime=$( integer $(echo "$fastesttime *1000" |bc)) 
int_temp=$( integer $(echo "$2 * 1000" |bc) ) 
#echo "aaa= $int_temp"
#echo "bbb= $int_fastesttime"
if [[ $int_temp  -lt $int_fastesttime ]]
then
        fastesttime=$2
        fastestsite=$1
fi
return $SUCCESS
#echo $min
}

function pingtest {
abc=$(ping -c 2 $1)
#[[ $abc =~  'time ([^ ]*)' ]]
[[ $abc =~ mdev\ =\ ([^/]*)/([^/]*)/ ]]
#echo "$1 ping=${BASH_REMATCH[1]}ms"
#echo "${BASH_REMATCH[0]}"
if [ -z ${BASH_REMATCH[1]} ]
then 
        echo "$fastesttime"
else     
        echo "${BASH_REMATCH[1]}"
fi
echo "ping time : ${BASH_REMATCH[2]}"
}

function getsite {
if [ "$mirrors_web" ]
then 
#echo "running function getsite"
teststring='a class="external" href="(http|ftp)://([^/]*)(.*)'
[[ $mirrors_web =~ $teststring  ]]
#[[ "$mirrors_web" =~ '(.*)' ]]
#       echo "${BASH_REMATCH[0]}"
#       echo "${BASH_REMATCH[1]}"
#       echo "${BASH_REMATCH[2]}"
#       echo "${BASH_REMATCH[3]}"

   if [ "${BASH_REMATCH[2]}" ]
        then
         echo ping ${BASH_REMATCH[2]}
         site="${BASH_REMATCH[2]}"
         time=$( pingtest "$site" )
         protocol="${BASH_REMATCH[1]}"
         echo -n $protocol://$site $time ms   
         echo -e "$time ms\t$protocol://$site" >> $fresult
         findmin $site $time
         echo "[ $fastestsite $fastesttime ms ]"  

                 
        fi
mirrors_web="${BASH_REMATCH[3]}"
fi

}

fresult="mirrors_test_result.txt"
fresultsorted="mirrors_test_result_sorted.txt"
echo -n "" > $fresult
fastesttime=100000
wget http://www.ubuntu.com/download -O mirrors2.txt
mirrors_web=$( cat mirrors2.txt )
i=0
maxloop=1000
while [ "$mirrors_web" ] && [[ "$i" -lt "$maxloop" ]] 
do
        #echo "get sites"
   getsite
        i=$( expr $i + 1 )

done
sort -g $fresult > $fresultsorted
head mirrors_test_result_sorted.txt | cat -n
################ script end ####################################
```

---

### Post by gpolo on 2007-01-04
Done with Python using threads so ping doesnt take a lot of time, did in a hurry, so I will make it   better later ;)

```

#!/usr/bin/env python

import os
import sys
from time import time
from urlparse import urlsplit
from threading import Thread

class tping(Thread):
    def __init__(self, domain):
        Thread.__init__(self)
        self.domain = domain
        self.status = -1
    def run(self):
        ping = os.popen("ping -q -c2 "+self.domain, "r")
        lines = ping.readlines() 
        try:
            count = 0
            chars = 0
            begin = 0
            end = 0
            # gets avg ping
            for char in lines[4]:
                if char == '/':
                    count += 1
                if count == 3:
                    begin = chars
                if count == 4:
                     end = chars
                chars += 1
            self.status = lines[4][begin+2:end+1]
        except:
            pass

def main():
    print "Getting mirror list"

    stamp = time()
    os.system("wget http://www.ubuntu.com/download -O %s" % (str(stamp)+"mirrors.txt"))

    mirrors_file = open(str(stamp)+"mirrors.txt", 'r')
    
    print "Getting mirrors..."
    for line in mirrors_file:
        if len(line) < 23:
            continue
        if line[:23] == """<table class="mirrors">""":
            break

    mirrors = [ ]
    for line in mirrors_file:
        # ignoring DVD mirrors
        if len(line) == 24 and line[:23] == """<table class="mirrors">""":
            break
        if len(line) > 4 and line[:4] == "<p><":
            mirrors.append(line[29:-9])

    mirrors_file.close
    os.remove(str(stamp)+"mirrors.txt")

    to_ping = [ ]
    print "Testing domains..."
    for mirror in mirrors:
        div = mirror.find('>')
        host = mirror[:div-1]
        #location = mirror[div+1:]

        ping_it = urlsplit("%s" % host)
        current = tping(ping_it[1])
        to_ping.append(current)
        current.start()
        # print "%s -> %s" % (host, location)

    best = 100000.0
    for result in to_ping:
        result.join()
        try:
            #print float(result.status)
            if float(result.status) < best and float(result.status) != -1:
                best = float(result.status)
                host = result.domain
        except:
            pass

    print "Best mirror for your location: %s -> %sms" % (host, best)

if __name__ == "__main__":
    main()

```

---

### Post by gpolo on 2007-01-04
somewhat better version

```

#!/usr/bin/env python2.4
# -*- coding: UTF-8 -*-
## script to check what is the fastest ubuntu host for you,
## if you want to force getting a new mirror list run this
## program as: ./ubuntu-mirror-speed.py -n
##
## Version: 0.2
## Author: Guilherme H. Polo Goncalves <ggpolo@gmail.com>

import os
import sys
from time import time
from urlparse import urlsplit
from threading import Thread

class tping(Thread):
    def __init__(self, domain):
        Thread.__init__(self)
        self.domain = domain
        self.status = -1
    def run(self):
        ping = os.popen("ping -q -c2 "+self.domain, "r")
        lines = ping.readlines() 
        try:
            count = 0
            chars = 0
            begin = 0
            end = 0
            # gets avg ping
            for char in lines[4]:
                if char == '/':
                    count += 1
                if count == 3:
                    begin = chars
                if count == 4:
                     end = chars
                chars += 1
            self.status = lines[4][begin+2:end+1]
        except:
            pass

def main():
    MAX_THREADS = 20

    print "Getting mirror list"

    # check for new list forced
    force = 0
    if len(sys.argv) == 2:
        if sys.argv[1] == "-n":
            force = 1

    # check if there is a "good" mirror list
    no_slow = 1
    if os.stat("good-mirrors.txt")[6] > 1 and not force:
        print "There is a \"good\" mirror list, nice!"
    else:
        stamp = time()
        os.system("wget http://www.ubuntu.com/download -O %s" % (str(stamp)+"mirrors.txt"))
        mirrors_file = open(str(stamp)+"mirrors.txt", 'r')
        no_slow = 0
    
    if no_slow:
        mirrors_file = open("good-mirrors.txt", "r")

    print "Getting mirrors..."
    if not no_slow:
        for line in mirrors_file:
            if len(line) < 23:
                continue
            if line[:23] == """<table class="mirrors">""":
                break

    mirrors = [ ]
    for line in mirrors_file:
        if no_slow:
            mirrors.append(line[:-1])
        else:
            # ignoring DVD mirrors
            if len(line) == 24 and line[:23] == """<table class="mirrors">""":
                break
            if len(line) > 4 and line[:4] == "<p><":
                mirrors.append(line[29:-9])

    mirrors_file.close
    if not no_slow:
        os.remove(str(stamp)+"mirrors.txt")

    to_ping = [ ]
    amount = len(mirrors)

    print "Testing all %d domains..." % amount

    count = 0
    best = 100000.0

    # list of good mirrors
    good_mirrors = [ ]

    for mirror in mirrors:
        if no_slow:
            current = tping(mirror)
        else:
            div = mirror.find('>')
            host = mirror[:div-1]
            # get domain only
            ping_it = urlsplit("%s" % host)
            current = tping(ping_it[1])

        to_ping.append(current)
        current.start()

        # check for MAX_THREADS or done
        wait_threads = 0
        if len(to_ping) > MAX_THREADS:
            wait_threads = 1
        if count == amount-1:
            wait_threads = len(to_ping)

        # reap domains that already responded, if possible
        if wait_threads == 1:
            posn = 0
            while posn < len(to_ping):
                also = to_ping[posn]
                if also.status > -1:
                    also.join(1.0)
                    
                    good_mirrors.append(also.domain)
                    if also.status and float(also.status) < best:
                        best = float(also.status)
                        best_host = also.domain
                    del to_ping[posn]
                    wait_threads -= 1
                else:
                    posn += 1

        # reap any threads necessary
        for reap in range(wait_threads):
            go_ping = to_ping[0]
            to_ping = to_ping[1:]
            print "   (slow) Waiting for", go_ping.domain

            go_ping.join(5.0)
            if go_ping.status and float(go_ping.status) < best and float(go_ping.status) != -1:
                best = float(go_ping.status)
                best_host = go_ping.domain
        count += 1
    
    print "\nAll mirrors alive tested"

    if not no_slow:
        print "Generating a list with good mirrors"
    else:
        print "Generating a list with very good mirrors"
    output = open("good-mirrors.txt", "w")
    for mirror in good_mirrors:
        output.write("%s\n" % mirror)
    output.close
    print "List generated"

    if len(good_mirrors) < 1:
        print "Really best mirror for your location: %s -> %sms" % (best_host, best)
    else:
        print "Best mirror for your location: %s -> %sms" % (best_host, best)

if __name__ == "__main__":
    main()

```

---

### Post by cgrebeld on 2007-01-04
Nice script, thanks.  On my system it throws on the call to os.stat because the file doesnt exist.  I added an extra test of os.access to your if statement to fix that:

```

#!/usr/bin/env python2.4
# -*- coding: UTF-8 -*-
## script to check what is the fastest ubuntu host for you,
## if you want to force getting a new mirror list run this
## program as: ./ubuntu-mirror-speed.py -n
##
## Version: 0.2
## Author: Guilherme H. Polo Goncalves <ggpolo@gmail.com>

import os
import sys
from time import time
from urlparse import urlsplit
from threading import Thread

class tping(Thread):
    def __init__(self, domain):
        Thread.__init__(self)
        self.domain = domain
        self.status = -1
    def run(self):
        ping = os.popen("ping -q -c2 "+self.domain, "r")
        lines = ping.readlines() 
        try:
            count = 0
            chars = 0
            begin = 0
            end = 0
            # gets avg ping
            for char in lines[4]:
                if char == '/':
                    count += 1
                if count == 3:
                    begin = chars
                if count == 4:
                     end = chars
                chars += 1
            self.status = lines[4][begin+2:end+1]
        except:
            pass

def main():
    MAX_THREADS = 20

    print "Getting mirror list"

    # check for new list forced
    force = 0
    if len(sys.argv) == 2:
        if sys.argv[1] == "-n":
            force = 1

    # check if there is a "good" mirror list
    no_slow = 1
    if os.access("good-mirrors.txt",os.R_OK) and os.stat("good-mirrors.txt")[7] > 1 and not force:
        print "There is a \"good\" mirror list, nice!"
    else:
        stamp = time()
        os.system("wget http://www.ubuntu.com/download -O %s" % (str(stamp)+"mirrors.txt"))
        mirrors_file = open(str(stamp)+"mirrors.txt", 'r')
        no_slow = 0
    
    if no_slow:
        mirrors_file = open("good-mirrors.txt", "r")

    print "Getting mirrors..."
    if not no_slow:
        for line in mirrors_file:
            if len(line) < 23:
                continue
            if line[:23] == """<table class="mirrors">""":
                break

    mirrors = [ ]
    for line in mirrors_file:
        if no_slow:
            mirrors.append(line[:-1])
        else:
            # ignoring DVD mirrors
            if len(line) == 24 and line[:23] == """<table class="mirrors">""":
                break
            if len(line) > 4 and line[:4] == "<p><":
                mirrors.append(line[29:-9])

    mirrors_file.close
    if not no_slow:
        os.remove(str(stamp)+"mirrors.txt")

    to_ping = [ ]
    amount = len(mirrors)

    print "Testing all %d domains..." % amount

    count = 0
    best = 100000.0

    # list of good mirrors
    good_mirrors = [ ]

    for mirror in mirrors:
        if no_slow:
            current = tping(mirror)
        else:
            div = mirror.find('>')
            host = mirror[:div-1]
            # get domain only
            ping_it = urlsplit("%s" % host)
            current = tping(ping_it[1])

        to_ping.append(current)
        current.start()

        # check for MAX_THREADS or done
        wait_threads = 0
        if len(to_ping) > MAX_THREADS:
            wait_threads = 1
        if count == amount-1:
            wait_threads = len(to_ping)

        # reap domains that already responded, if possible
        if wait_threads == 1:
            posn = 0
            while posn < len(to_ping):
                also = to_ping[posn]
                if also.status > -1:
                    also.join(1.0)
                    
                    good_mirrors.append(also.domain)
                    if also.status and float(also.status) < best:
                        best = float(also.status)
                        best_host = also.domain
                    del to_ping[posn]
                    wait_threads -= 1
                else:
                    posn += 1

        # reap any threads necessary
        for reap in range(wait_threads):
            go_ping = to_ping[0]
            to_ping = to_ping[1:]
            print "   (slow) Waiting for", go_ping.domain

            go_ping.join(5.0)
            if go_ping.status and float(go_ping.status) < best and float(go_ping.status) != -1:
                best = float(go_ping.status)
                best_host = go_ping.domain
        count += 1
    
    print "\nAll mirrors alive tested"

    if not no_slow:
        print "Generating a list with good mirrors"
    else:
        print "Generating a list with very good mirrors"
    output = open("good-mirrors.txt", "w")
    for mirror in good_mirrors:
        output.write("%s\n" % mirror)
    output.close
    print "List generated"

    if len(good_mirrors) < 1:
        print "Really best mirror for your location: %s -> %sms" % (best_host, best)
    else:
        print "Best mirror for your location: %s -> %sms" % (best_host, best)

if __name__ == "__main__":
    main()


```

---

### Post by 3togo on 2007-01-04
Very Nice Script!

Could it show the best 10 mirrors? Sometimes, the best mirror don't have the right distro.

Also, is it possible to update the /etc/apt/sources.list
after checking the specific distro say "feisty" is really existed in that best mirror.

:)

---

### Post by gpolo on 2007-01-05
Yes, I can make a top list =] and about checking for specific distro and updating sources.list, I will do it later, maybe this weekend ;)

cgrebeld: thanks for the fix, but you changed the os.stat value from [6] to [7], [6] shows the filesize ;)

this line:

if os.access("good-mirrors.txt",os.R_OK) and os.stat("good-mirrors.txt")[7] > 1 and not force:

should be:

if os.access("good-mirrors.txt",os.R_OK) and os.stat("good-mirrors.txt")[6] > 1 and not force:

---

### Post by pmasiar on 2007-01-05
I really don't like magic numbers like 6 and 7 in your script. I looked it up but did not found any constants poinint into os.stat() results. I was expecting ST_SIZE constant. Docs mentions st_size etc, but I did not found it. Did I missed something?

---

### Post by gpolo on 2007-01-05
[6] isn't a magic number, os.stat returns an array, and [6] is the position for filesize

os.stat("file.txt").st_size does the same

[edit]
os.stat returns a list, sorry

---

### Post by gpolo on 2007-01-05
hmm.. Got a problem here. Well, right now the mirror list I'm getting is to download ubuntu, not to use with apt. Is there a list of apt mirrors anywhere ?

Or a list with all countries that got ubuntu mirrors ?

---

### Post by gpolo on 2007-01-05
new version!

new features and bug fixes:
  - help message showing how to run the program
  - list top nn fastest mirrors
  - discover your distro
  - minor fixes

features that should be implemented but aren't:
  - return mirrors just for your distro or for a specified distro  *
  - update sources list  **

*: Problem I reported in previous reply
**: Will be fixed after * is fixed ;)

```

#!/usr/bin/env python2.4
# -*- coding: UTF-8 -*-
## script to check what is the fastest ubuntu host for you.
## how to use this program, run: ./ubuntu-mirror-speed.py -h
##
## Version: 0.3
## Author: Guilherme H. Polo Goncalves <ggpolo@gmail.com>
## Changes from version 0.2:
##  - reduced thread timeout from 5 seconds to 3.5 seconds
##  - added several options to use, check using -h
##  - several minor fixes

import os
import sys
from time import time
from urlparse import urlsplit
from threading import Thread

class tping(Thread):
    def __init__(self, domain):
        Thread.__init__(self)
        self.domain = domain
        self.status = -1
    def run(self):
        ping = os.popen("ping -q -c2 "+self.domain, "r")
        lines = ping.readlines() 
        try:
            count = 0
            chars = 0
            begin = 0
            end = 0
            # gets avg ping
            for char in lines[4]:
                if char == '/':
                    count += 1
                if count == 3:
                    begin = chars
                if count == 4:
                     end = chars
                chars += 1
            self.status = lines[4][begin+2:end+1]
        except:
            pass

def main(argv=sys.argv):
    MAX_THREADS = 20

    use_msg = """You can run this program using these parameters:
    
    -h               Show this message
    -s               Show best mirror or mirrors for you and leave
    -l nn            Show a list with nn fastest mirrors
    -d distro        Specify a distro, "edgy" or "dapper" for example. You can use the "especial" distro any here, e.g. -d any, will ignore distro and show best mirrors overall
    -n               Get a new mirror list forced
    -u               Update your sources.list with best mirror (not working yet)
    
WARNING: If you don't specify a distro this program will try to find it automatically, if it doesn't find you will need to run this program specifying one or any.

You can espcify multiple options like: 
%s -n -u -d edgy
But you can't run with options that conflict, like:
%s -u -s
If you just want to check what is the best mirror for your distro, use:
%s -s""" % (argv[0], argv[0], argv[0])

    # control for new list forced
    force = 0
    # control for show and leave
    show = 0
    # control for distro
    distro = None
    # control for sources.list update
    update = 0
    # list for best mirrors
    best_mirrors_len = 1
    
    argv_len = len(argv)
    if argv_len < 2:
        print use_msg
        sys.exit(1)
    else:
        for op in range(argv_len):
            # get new list option
            if argv[op] == "-n":
                force = 1
            # get distro option
            elif argv[op] == "-d":
                # check if distro was especified
                try:
                    distro = argv[op+1]
                except:
                    print "ERROR: No distro especified"
                    sys.exit(1)
                if distro[0] == '-':
                    print "ERROR: Invalid distro especified"
                    sys.exit(1)
            # get top list option
            elif argv[op] == "-l":
                # check if a number was especified
                try:
                    argv[op+1]
                except:
                    print "ERROR: You need to specify a number of fastest mirrors to show"
                    sys.exit(1)
                # check if it is numeric
                if not argv[op+1].isdigit():
                    print "ERROR: You need to specify a number of fastest mirrors to show"
                    sys.exit(1)
                best_mirrors_len = int(argv[op+1])
                if not best_mirrors_len:
                    best_mirrors_len = 1
            # get show option
            elif argv[op] == "-s":
                show = 1
            # get update option
            elif argv[op] == "-u":
                print "WARNING: This option (u) isn't working for now"
                update = 1
                pass
            # get help option
            elif argv[op] == "-h":
                print use_msg
                sys.exit(1)
            # ignore other options
            else:
                pass

    if show and update:
        print "ERROR: Conflicting options, you can't use show and update together"
        sys.exit(1)

    # if no distro was specified, try to find it
    if distro == None and distro != "any":
        try:
            date1 = os.stat("/etc/lsb-release").st_mtime
        except:
            date1 = None
        try:
            date2 = os.stat("/etc/lsb-release.dpkg-dist").st_mtime
        except:
            date2 = None

        # files don't exist
        if date1 == None and date2 == None:
            print "No distro found"
            sys.exit(1)
        else:
            # file /etc/lsb-release.dpkg-dist doesn't exists
            if date1 != None and date2 == None:
                file = "/etc/lsb-release"
            # file /etc/lsb-release doesn't exists
            elif date1 == None and date2 != None:
                file = "/etc/lsb-release.dpkg-dist"
            # both file exists
            else:
                # check for most recent
                if date1 > date2:
                    file = "/etc/lsb-release"
                else:
                    file = "/etc/lsb-release.dpkg-dist"
            # get distro
            distro_f = open(file, 'r')
            for line in distro_f:
                if line[:9] == "DISTRIB_C":
                    distro = line[17:-1]
                    break

#    print best_mirrors_len
    print "Getting mirror list for distro: %s\n" % distro
#    sys.exit(1)

    # check if there is a "good" mirror list
    no_slow = 1
    if os.path.exists("good-mirrors.txt") and \
    os.stat("good-mirrors.txt").st_size > 1 and not force:
        print "There is a \"good\" mirror list, nice!"
    else:
        stamp = time()
        os.system("wget http://www.ubuntu.com/download -O %s" % (str(stamp)+"mirrors.txt"))
        mirrors_file = open(str(stamp)+"mirrors.txt", 'r')
        no_slow = 0
    
    if no_slow:
        mirrors_file = open("good-mirrors.txt", "r")

    print "Getting mirrors..."
    if not no_slow:
        for line in mirrors_file:
            if len(line) < 23:
                continue
            if line[:23] == """<table class="mirrors">""":
                break

    mirrors = [ ]
    for line in mirrors_file:
        if no_slow:
            mirrors.append(line[:-1])
        else:
            # ignoring DVD mirrors
            if len(line) == 24 and line[:23] == """<table class="mirrors">""":
                break
            if len(line) > 4 and line[:4] == "<p><":
                mirrors.append(line[29:-9])

    mirrors_file.close
    if not no_slow:
        os.remove(str(stamp)+"mirrors.txt")

    to_ping = [ ]
    amount = len(mirrors)

    print "Testing all %d domains..." % amount

    count = 0
    best = 100000.0
    fast_ping = 0.0

    # list of good mirrors
    good_mirrors = [ ]
    # speed of mirrors
    speed_mirrors = { }

    for mirror in mirrors:
        if no_slow:
            current = tping(mirror)
        else:
            div = mirror.find('>')
            host = mirror[:div-1]
            # get domain only
            ping_it = urlsplit("%s" % host)
            current = tping(ping_it[1])

        to_ping.append(current)
        current.start()

        # check for MAX_THREADS or done
        wait_threads = 0
        if len(to_ping) > MAX_THREADS:
            wait_threads = 1
        if count == amount-1:
            wait_threads = len(to_ping)

        # reap domains that already responded, if possible
        if wait_threads == 1:
            posn = 0
            while posn < len(to_ping):
                also = to_ping[posn]
                if also.status > -1:
                    also.join(1.0)
                    
                    # append results to lists
                    good_mirrors.append(also.domain)
                    if len(speed_mirrors) < best_mirrors_len:
                        # store the slowest ping from fastest mirrors
                        if float(also.status) > fast_ping:
                            fast_ping = float(also.status)
                        speed_mirrors[also.status] = also.domain
                    else:
                        # check if the current value is lower than the biggest
                        # in this list
                        if also.status and float(also.status) < fast_ping:
                            del speed_mirrors[str(fast_ping)]
                            speed_mirrors[also.status] = also.domain

                            # now get the biggest value inside dict
                            high_value = 0
                            for key in speed_mirrors.keys():
                                if float(key) > float(high_value):
                                    high_value = key
                            fast_ping = high_value

                    if also.status and float(also.status) < best:
                        best = float(also.status)
                        best_host = also.domain

                    del to_ping[posn]
                    wait_threads -= 1
                else:
                    posn += 1

        # reap any threads necessary
        for reap in range(wait_threads):
            go_ping = to_ping[0]
            to_ping = to_ping[1:]
            print "   (slow) Waiting for", go_ping.domain

            go_ping.join(3.5)
            if go_ping.status and float(go_ping.status) < best and float(go_ping.status) != -1:
                best = float(go_ping.status)
                best_host = go_ping.domain
        count += 1
    
    print "\nAll mirrors alive tested"

    if not no_slow:
        print "Generating a list with good mirrors"
    else:
        print "Generating a list with very good mirrors"
    output = open("good-mirrors.txt", "w")
    for mirror in good_mirrors:
        output.write("%s\n" % mirror)
    output.close
    print "List generated\n"

    # check if this isn't the result for really best mirror
    if len(good_mirrors):
        print "Top %d mirror list" % best_mirrors_len
        for mirror in range(len(speed_mirrors)):
            item = speed_mirrors.popitem()
            print "%s -> %sms" % (item[1], item[0])
        print

    if len(good_mirrors) < 1:
        print "Really best mirror for your location: %s -> %sms" % (best_host, best)
    else:
        print "Best mirror for your location: %s -> %sms" % (best_host, best)
        if best_host not in good_mirrors:
            output = open("good-mirrors.txt", "a")
            output.write("%s\n" % mirror)
            output.close

if __name__ == "__main__":
    main()

```

---

### Post by UbuWu on 2007-01-06
There are at least 2 programs in the repositories that do the same: netselect-apt and apt-spy. But of course making your own program is more challenging ;)

---

### Post by gpolo on 2007-01-06
netselect does a cool thing, checking how far you are from server but it seems it doesnt return  results I would expect. All hosts I tested returned 9999ms 0%ok. And it took much more time than my totally beta python program using same hosts, and mine returned what I expected.

apt-spy: I really liked that README.mirrors.txt cause now I can continue my version of these programs in python ;) I "tested" apt-spy now, I got it's source and compiled but it wont run, 

./apt-spy update
fopen: No such file or directory
Error opening mirror file. Exiting.

I don't know if these projects were abandoned or something.

Thanks for the information =)

---

### Post by 3togo on 2007-01-07
ggpolo,

Yours python doesn't sort the top xxx mirrors and therefore I modify it.

Anyhow, well done.

3togo


```
#!/usr/bin/env python2.4
# -*- coding: UTF-8 -*-
## script to check what is the fastest ubuntu host for you.
## how to use this program, run: ./ubuntu-mirror-speed.py -h
##
## Version: 0.3
## Author: Guilherme H. Polo Goncalves <ggpolo@gmail.com>
## Changes from version 0.2:
##  - reduced thread timeout from 5 seconds to 3.5 seconds
##  - added several options to use, check using -h
##  - several minor fixes

import os
import sys
from time import time
from urlparse import urlsplit
from threading import Thread

class tping(Thread):
    def __init__(self, domain):
        Thread.__init__(self)
        self.domain = domain
        self.status = -1
    def run(self):
        ping = os.popen("ping -q -c2 "+self.domain, "r")
        lines = ping.readlines() 
        try:
            count = 0
            chars = 0
            begin = 0
            end = 0
            # gets avg ping
            for char in lines[4]:
                if char == '/':
                    count += 1
                if count == 3:
                    begin = chars
                if count == 4:
                     end = chars
                chars += 1
            self.status = lines[4][begin+2:end+1]
        except:
            pass

def sortedDictValues(adict):
    keys = adict.keys()
    keys.sort()
    return map(adict.get, keys)

def main(argv=sys.argv):
    MAX_THREADS = 20

    use_msg = """You can run this program using these parameters:
    
    -h               Show this message
    -s               Show best mirror or mirrors for you and leave
    -l nn            Show a list with nn fastest mirrors
    -d distro        Specify a distro, "edgy" or "dapper" for example. You can use the "especial" distro any here, e.g. -d any, will ignore distro and show best mirrors overall
    -n               Get a new mirror list forced
    -u               Update your sources.list with best mirror (not working yet)
    
WARNING: If you don't specify a distro this program will try to find it automatically, if it doesn't find you will need to run this program specifying one or any.

You can espcify multiple options like: 
%s -n -u -d edgy
But you can't run with options that conflict, like:
%s -u -s
If you just want to check what is the best mirror for your distro, use:
%s -s""" % (argv[0], argv[0], argv[0])

    # control for new list forced
    force = 0
    # control for show and leave
    show = 0
    # control for distro
    distro = None
    # control for sources.list update
    update = 0
    # list for best mirrors
    best_mirrors_len = 1
    
    argv_len = len(argv)
    if argv_len < 2:
        print use_msg
        sys.exit(1)
    else:
        for op in range(argv_len):
            # get new list option
            if argv[op] == "-n":
                force = 1
            # get distro option
            elif argv[op] == "-d":
                # check if distro was especified
                try:
                    distro = argv[op+1]
                except:
                    print "ERROR: No distro especified"
                    sys.exit(1)
                if distro[0] == '-':
                    print "ERROR: Invalid distro especified"
                    sys.exit(1)
            # get top list option
            elif argv[op] == "-l":
                # check if a number was especified
                try:
                    argv[op+1]
                except:
                    print "ERROR: You need to specify a number of fastest mirrors to show"
                    sys.exit(1)
                # check if it is numeric
                if not argv[op+1].isdigit():
                    print "ERROR: You need to specify a number of fastest mirrors to show"
                    sys.exit(1)
                best_mirrors_len = int(argv[op+1])
                if not best_mirrors_len:
                    best_mirrors_len = 1
            # get show option
            elif argv[op] == "-s":
                show = 1
            # get update option
            elif argv[op] == "-u":
                print "WARNING: This option (u) isn't working for now"
                update = 1
                pass
            # get help option
            elif argv[op] == "-h":
                print use_msg
                sys.exit(1)
            # ignore other options
            else:
                pass

    if show and update:
        print "ERROR: Conflicting options, you can't use show and update together"
        sys.exit(1)

    # if no distro was specified, try to find it
    if distro == None and distro != "any":
        try:
            date1 = os.stat("/etc/lsb-release").st_mtime
        except:
            date1 = None
        try:
            date2 = os.stat("/etc/lsb-release.dpkg-dist").st_mtime
        except:
            date2 = None

        # files don't exist
        if date1 == None and date2 == None:
            print "No distro found"
            sys.exit(1)
        else:
            # file /etc/lsb-release.dpkg-dist doesn't exists
            if date1 != None and date2 == None:
                file = "/etc/lsb-release"
            # file /etc/lsb-release doesn't exists
            elif date1 == None and date2 != None:
                file = "/etc/lsb-release.dpkg-dist"
            # both file exists
            else:
                # check for most recent
                if date1 > date2:
                    file = "/etc/lsb-release"
                else:
                    file = "/etc/lsb-release.dpkg-dist"
            # get distro
            distro_f = open(file, 'r')
            for line in distro_f:
                if line[:9] == "DISTRIB_C":
                    distro = line[17:-1]
                    break

#    print best_mirrors_len
    print "Getting mirror list for distro: %s\n" % distro
#    sys.exit(1)

    # check if there is a "good" mirror list
    no_slow = 1
    if os.path.exists("good-mirrors.txt") and \
    os.stat("good-mirrors.txt").st_size > 1 and not force:
        print "There is a \"good\" mirror list, nice!"
    else:
        stamp = time()
        os.system("wget http://www.ubuntu.com/download -O %s" % (str(stamp)+"mirrors.txt"))
        mirrors_file = open(str(stamp)+"mirrors.txt", 'r')
        no_slow = 0
    
    if no_slow:
        mirrors_file = open("good-mirrors.txt", "r")

    print "Getting mirrors..."
    if not no_slow:
        for line in mirrors_file:
            if len(line) < 23:
                continue
            if line[:23] == """<table class="mirrors">""":
                break

    mirrors = [ ]
    for line in mirrors_file:
        if no_slow:
            mirrors.append(line[:-1])
        else:
            # ignoring DVD mirrors
            if len(line) == 24 and line[:23] == """<table class="mirrors">""":
                break
            if len(line) > 4 and line[:4] == "<p><":
                mirrors.append(line[29:-9])

    mirrors_file.close
    if not no_slow:
        os.remove(str(stamp)+"mirrors.txt")

    to_ping = [ ]
    amount = len(mirrors)

    print "Testing all %d domains..." % amount

    count = 0
    best = 100000.0
    fast_ping = 0.0

    # list of good mirrors
    good_mirrors = [ ]
    # speed of mirrors
    speed_mirrors = { }

    for mirror in mirrors:
        if no_slow:
            current = tping(mirror)
        else:
            div = mirror.find('>')
            host = mirror[:div-1]
            # get domain only
            ping_it = urlsplit("%s" % host)
            current = tping(ping_it[1])

        to_ping.append(current)
        current.start()

        # check for MAX_THREADS or done
        wait_threads = 0
        if len(to_ping) > MAX_THREADS:
            wait_threads = 1
        if count == amount-1:
            wait_threads = len(to_ping)

        # reap domains that already responded, if possible
        if wait_threads == 1:
            posn = 0
            while posn < len(to_ping):
                also = to_ping[posn]
					#### also.status could be empty
                if (also.status > -1) and also.status:
                    also.join(1.0)
                    
                    # append results to lists
                    good_mirrors.append(also.domain)
                    if len(speed_mirrors) < best_mirrors_len:
                        # store the slowest ping from fastest mirrors
                        if float(also.status) > fast_ping:
                            fast_ping = float(also.status)
                        speed_mirrors[also.status] = also.domain
                    else:
                        # check if the current value is lower than the biggest
                        # in this list
                        if also.status and float(also.status) < fast_ping:
                            del speed_mirrors[str(fast_ping)]
                            speed_mirrors[also.status] = also.domain

                            # now get the biggest value inside dict
                            high_value = 0
                            for key in speed_mirrors.keys():
                                if float(key) > float(high_value):
                                    high_value = key
                            fast_ping = high_value

                    if also.status and float(also.status) < best:
                        best = float(also.status)
                        best_host = also.domain

                    del to_ping[posn]
                    wait_threads -= 1
                else:
                    posn += 1

        # reap any threads necessary
        for reap in range(wait_threads):
            go_ping = to_ping[0]
            to_ping = to_ping[1:]
            print "   (slow) Waiting for", go_ping.domain

            go_ping.join(3.5)
            if go_ping.status and float(go_ping.status) < best and float(go_ping.status) != -1:
                best = float(go_ping.status)
                best_host = go_ping.domain
        count += 1
    
    print "\nAll mirrors alive tested"

    if not no_slow:
        print "Generating a list with good mirrors"
    else:
        print "Generating a list with very good mirrors"
    output = open("good-mirrors.txt", "w")
    for mirror in good_mirrors:
        output.write("%s\n" % mirror)
    output.close
    print "List generated\n"
    #print speed_mirrors 
    # check if this isn't the result for really best mirror
    if len(good_mirrors):
        print "Top %d mirror list" % best_mirrors_len
        speed_mirrors_sorted_keys = speed_mirrors.keys()
        speed_mirrors_sorted_keys.sort()		
        for key in speed_mirrors_sorted_keys	:	
        		print "%s -> %sms" % (speed_mirrors[key], key) 
        #for mirror in range(len(speed_mirrors)):
        #     item = speed_mirrors.popitem()
        #     print "%s -> %sms" % (item[1], item[0])
        print

    if len(good_mirrors) < 1:
        print "Really best mirror for your location: %s -> %sms" % (best_host, best)
    else:
        print "Best mirror for your location: %s -> %sms" % (best_host, best)
        if best_host not in good_mirrors:
            output = open("good-mirrors.txt", "a")
            output.write("%s\n" % mirror)
            output.close

if __name__ == "__main__":
    main()
```

---

### Post by grulos on 2007-10-15
ok here is one based on http get response times

```

#!/bin/bash
# ffmirror.sh - http://grulos.blogspot.com
# find fastest mirror (?!?)
# give it a list of hosts and it will sort them
# according to their response time
# no switches (ATM) just ./ffmirror<mirrors.txt
# www.foo.org or http://www.foo.org or
# http://foo.org/page or ...

trap 'printf "\ncaught signal\nGot only ${#slist[@]}\n" &&
  printf "%s\n" "${slist[@]}" && exit 1' 2

while read line; do
  # get host & page
  line=${line/[hH][tT][tT][pP]:\/\//}
  [ "${line#*\/}" == "$line" ] && page="/" || page="/${line#*\/}"
  host="${line%%\/*}"

  # connect to host
  exec 3<>/dev/tcp/$host/80

  # b-a to get time difference.
  # could have used date +%s%N
  # I guess this won't work on a BSD
  a=$(</proc/uptime)
  a=${a%%\ *}
  a=${a/./}

 # send a GET request and read 1st line of response
 printf "GET $page HTTP/1.1\nHost: $host\n\n">&3 &&
   read -u 3 -t 2 -a response &&  exec 3>&- &&
     b=$(</proc/uptime) &&
       b=${b%%\ *} &&
         b=${b/./}

  # printf "%06s%04s%s\n" "$((b-a))0ms ${response[1]} $host"

  # try next if not connected within 2s
  [ $((b-a)) -lt 0 ] && continue

  # this is my lazy sort algorithm (c)
  c=$(((b-a)*100))
  until [ "${slist[$c]}" == "" ]; do
    ((c++))
  done
  slist[$c]="$((b-a))0ms $host$page"

  exec 3>&-

done

printf "%s\n" "${slist[@]}"

```

[FONT="Fixedsys"]grulos@slackd:~# cat s1.txt
[www.google.com](www.google.com)
[www.kernel.org](www.kernel.org)
[www.linux.org](www.linux.org)
[www.microsoft.com](www.microsoft.com)
[www.slackware.org](www.slackware.org)
[www.freebsd.org](www.freebsd.org)
[www.openbsd.org](www.openbsd.org)
[www.netbsd.org](www.netbsd.org)
[www.yahoo.com](www.yahoo.com)
grulos@slackd:~# ./ffmirror.sh<s1.txt
140ms [www.google.com/](www.google.com/)
170ms [www.microsoft.com/](www.microsoft.com/)
280ms [www.yahoo.com/](www.yahoo.com/)
480ms [www.kernel.org/](www.kernel.org/)
500ms [www.slackware.org/](www.slackware.org/)
510ms [www.openbsd.org/](www.openbsd.org/)
530ms [www.linux.org/](www.linux.org/)
1460ms [www.netbsd.org/](www.netbsd.org/)
grulos@slackd:~#[/FONT]

have fun ;)

---

### Post by wcoolnet on 2008-04-03
If anyone is trying the above script on their ubuntu system and wondering why it is not working, it's because it won't. The above script uses /dev/tcp which is disabled on the ubuntu version of BASH

---

### Post by nanotube on 2008-04-03
> **wcoolnet said:**
> If anyone is trying the above script on their ubuntu system and wondering why it is not working, it's because it won't. The above script uses /dev/tcp which is disabled on the ubuntu version of BASH

check my post in [http://ubuntuforums.org/showthread.php?t=743774](http://ubuntuforums.org/showthread.php?t=743774)
i edited grulos's script to simply use wget instead of the fancy /dev/tcp-foo he was using. :) 

wow, one can learn quite some things about shell scripting just from reading grulos's script. nice work dude! :)

---

### Post by EvilGnome on 2008-11-07
gpolo: did you ever continue with your script? I'd be very interested if you had it updating sources.list...

---


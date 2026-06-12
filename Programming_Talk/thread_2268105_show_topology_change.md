---
title: "show topology change"
date: 2015-03-06
forum: Programming Talk
---

### Post by Drenriza on 2015-03-06
Hi all

I got asked yesterday if their is a tool that shows topology change between a source and destination.
I personally dont know a tool that shows this so i decided to play around with a script to show this

My bash skills is quite rusten, so im asking here. How would you uptimize this basic script? So i can learn from what you all think.
Or do you know of a tool that can show topology changes, already made.

Thanks on advance.

```

#!/bin/bash

##This script looks for changes in the topology, from a source to a destination target.
##If a change happends it will be printed to the screen of the device that runs the script.

##The script takes two arguments [destination_target], [sleep_between_traceroutes]

if [[ $EUID -ne 0 ]]; then
    echo "This script must be run as root" 1>&2
    exit 1
fi

destination_target=${1}
sleep_between_traceroutes=${2}
run="1"

path1="/tmp/topologyChange1.txt"
path2="/tmp/topologyChange2.txt"

file1="0"

count="0"

echo "script start up"
if [ -e ${path1} ]; then
    rm -v ${path1}
fi

if [ -e ${path2} ]; then
    rm -v ${path2}
fi
while [ ${run} -eq 1 ]
do
    let "count++"
    echo "Script has runned ${count} times"
    if [ ${file1} -eq 0 ]; then
        traceroute -n -I ${destination_target} |awk '{print $2}' |sed '1d' > ${path1}
        file1="1"
    else
        traceroute -n -I ${destination_target} |awk '{print $2}' |sed '1d '> ${path2}        
    fi

    if [ -e ${path1} ] && [ -e ${path2} ]; then
        
        echo "checking topology"    
        if [[ ! $(diff -s ${path1} ${path2}) == "Files ${path1} and ${path2} are identical" ]]; then
            clear
            echo "topology has changed"

            diff -y ${path1} ${path2}

            mv ${path2} ${path1}
        else
            echo "no topology change"
            echo ""
        fi
    
    fi

    sleep ${sleep_between_traceroutes}
done

exit 0

```

---

### Post by TheFu on 2015-03-06
Network routing can change for all sorts of reasons.  Inside a LAN, your network team should control any changes.
I would use **zenmap** to see how things are connected. It will create a diagram and text can be exported ... if that helps you make a comparison from day to day.

BTW - topology is vague - if you can change the title to include "network topology" - that would be very helpful to getting more eyes, I suspect.

---

### Post by Lars Noodén on 2015-03-08
*if [ ${file1} -eq 0 ]; then*

That might use the [-s test](http://manpages.ubuntu.com/manpages/trusty/en/man1/test.1.html) to see if the file is not empty

```

if [ ${file1} -eq 0 ]; then

```

*        traceroute -n -I ${destination_target} |awk '{print $2}' |sed '1d' > ${path1}*

Then if you are already running awk, it is not necesary to also run sed afterward, the same functions are in awk.  There are many ways to skip the non-addresses, but this is one of them:

```

 traceroute -n -I ${destination_target} | awk '$2 ~ /^[0-9]/ { print $2 }' > ${path1}

```

*if [[ ! $(diff -s ${path1} ${path2}) == "Files ${path1} and ${path2} are identical" ]]; then*

```

if ! diff -s ${path1} ${path2} > /dev/null; then

```

Then after the script is run, depending on what you want, you might want to clean up afterwards by automatically erasing the files.  And speaking of files, if more that one user is going to be running the script at a time you can use [mktemp](http://manpages.ubuntu.com/manpages/trusty/en/man1/mktemp.1.html) to generate the file names.

---


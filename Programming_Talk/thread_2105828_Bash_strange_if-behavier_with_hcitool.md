---
title: "Bash strange if-behavier with hcitool"
date: 2013-01-17
forum: Programming Talk
---

### Post by mirrowwinger on 2013-01-17
Hello ubuntu-community,  i wanted to write a small own bluetooth connector. But i noticed a strange behavier when i scan for bluetooth devices. Here the code:

```
#!/bin/bash

ArrayCounter=0

while [ 0 -eq 0 ]
do
    clear
    ScanResult=`hcitool scan`
    #ScanResult=`ls`
    if [ $ScanResult ]
    then
        echo ${ScanResult[0]}
    fi
    sleep 10
done
```

If I use it in the way above, it complains about:
```
./bluetoothscan.sh: Zeile 10: [: Zu viele Argumente.
```
If i do the same with the command "ls" it workes quite expacted right. Does anyony realize a failure I made?

Thanks

mirrowwinger

---

### Post by sisco311 on 2013-01-17
Please check out:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)
[http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)
and
BashFAQ 082 (link in my signature)

---

### Post by ju2wheels on 2013-01-22
```

#!/bin/bash

while true; do
    clear;
    output=$(/usr/bin/hcitool scan | /bin/grep -v "Scanning ...");
    
    if [ ! -z "${output}" ]; then
	while read baddr devname; do
	    echo -e "Device Name: ${devname}\t Device Bluetooth Address: ${baddr}"
	done <<< "${output}"
    fi
    sleep 10
done

```

---


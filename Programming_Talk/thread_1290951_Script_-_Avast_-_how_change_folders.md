---
title: "Script - Avast - how change folders"
date: 2009-10-14
forum: Programming Talk
---

### Post by Ordes on 2009-10-14
hi, new to linux scripting... trying to make a script for avast AV-scan.

my problem: when i run the script it will always scan the folder where script is saved.

i like to be able that the script:
1) either scans my working directory  --or--
2) let me enter the directory i want to scan

so far my script is like that:


#!/bin/bash

function press_enter
{
    echo ""
    echo -n "Press Enter to continue"
    read
    clear
}

selection=
until [ "$selection" = "0" ]; do
    echo ""
    echo "AV - Scan"
    echo ""
    echo "1 - Folder & Subfolders"
    echo "2 - Folder only"
    echo "3 - See Report"
    echo ""
    echo "0 - exit"
    echo ""
    echo -n "Scan "
    read selection
    echo ""
    case $selection in
	1 ) avast -r /home/xxx/.avast/report.txt ; press_enter ;;
	2 ) avast -dr /home/xxx/.avast/report.txt ; press_enter ;;
        3 ) gedit /home/xxx/.avast/report.txt ; press_enter ;;
	0 ) exit ;;
        * ) echo "Please enter" ; press_enter
    esac
done

---

### Post by Ordes on 2009-10-14
google and try & error...

got it working.. if anyone is interested, or has improvement tips (is my first script ever) here it is,...



#!/bin/bash

function press_enter
{
    echo ""
    echo -n "Press Enter to continue"
    read
    clear
}

clear
selection=
until [ "$selection" = "0" ]; do
    echo ""
    echo "AV - Scan@" 
    pwd                              
    echo ""
    echo "1 - Avast: Scan Folder & Sub                 0000"
    echo "2 - Avast: Scan Folder only                     0"
    echo "3 - Avast: Scan Home                   0000  0000"
    echo "4 - Avast: Scan Filesystem             0  0     0"
    echo "5 - Avast: See Report                  0000  0000"
    echo "6 - Avast: Update"
    echo "7 - Clear: Report"
    echo "0 - exit program"
    echo ""
    echo -n "Scan "
    read selection
    echo ""
    case $selection in
	1 ) avast $pwd -r /home/xxx/.avast/report.txt ; press_enter ;;
	2 ) avast -d $pwd -r /home/xxx/.avast/report.txt ; press_enter ;;
        3 ) avast ~/ -r /home/xxx/.avast/report.txt ; press_enter ;;    
        4 ) sudo avast / -r /home/xxx/.avast/report.txt ; press_enter ;;
        5 ) gedit /home/xxx/.avast/report.txt ; clear ;;   
	6 ) avast-update ;;
        7 ) rm /home/xxx/.avast/report.txt ; echo "Report cleaned" ; press_enter ;;
        0 ) clear ; exit ;;
        * ) echo "Please enter" ; press_enter ;;
    esac
done

---


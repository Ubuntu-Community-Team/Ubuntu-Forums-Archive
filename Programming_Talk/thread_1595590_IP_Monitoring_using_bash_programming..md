---
title: "IP Monitoring using bash programming."
date: 2010-10-13
forum: Programming Talk
---

### Post by threeonethree on 2010-10-13
This code uses ping to check connectivity to a remote location and logs it to a .html file

```
#! /bin/bash
path="$HOME/Desktop/IP_Monitor"                    #Path to write out files
ALT="0"                                            #For styling alternative row
basic="$HOME/Desktop/IP_Monitor/basic.html"        #Basic HTML Template
OF=Monitoring_Output$(date +%d-%m-%Y).html
if [ -e "$path/$OF" ];then
  echo "Continuing from previous file."
fi
function checkdate {                               #Saves in new file if date changed
  if [ ! -e "$path/$OF" ];then
    echo "Saving in New file"
    cat $basic >  $path/$OF
  fi
}


while true; do
  OF=Monitoring_Output$(date +%d-%m-%Y).html
  check=`ping -c 1 -w 1 10.207.4.27 | grep 'icmp_seq=1' || echo 'Request timed out.'`  #Wait 1 second for reply before echo RTO
  checkdate
  if [ $ALT -eq "0" ];then
    echo "<tr><td>$check</td><td>`date`</td></tr>" >> $path/$OF
    ALT="1"
  else
    echo "<tr class="alt"><td>$check</td><td>`date`</td></tr>" >> $path/$OF
    ALT="0"
  fi
done
```

basic.html
```
<HTML>
<TITLE> IP Monitoring </TITLE>
<HEAD>
<LINK rel="stylesheet" type="text/css" href="IP_Monitor.css">
</HEAD>
<BODY>
<TABLE id="customers">
<TR>
<TH>Reply</TH>
<TH>Time Stamp</TH>
</TR>
```

This is my first bash program so please let me know how I can improve it / Any bugs..

Some more features i would like to have.

1) Ability to get ip addresses from a list in text file and have separate log files for each.

2) Automatic compression of completed log files for the day using tar.

---

### Post by conundrumx on 2010-10-13
I think your time would be better spent getting acquainted with Nagios or Icinga.  There's no need to make your own solution for network monitoring.

---

### Post by juancarlospaco on 2010-10-13
Great!, the report is elegant.
I suggest you install and play with "**dialog**" package ;)

---


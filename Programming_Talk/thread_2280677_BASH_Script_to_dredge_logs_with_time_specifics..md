---
title: "BASH: Script to dredge logs with time specifics."
date: 2015-06-01
forum: Programming Talk
---

### Post by the_kernel2 on 2015-06-01
[COLOR=#000000][FONT=Verdana]I think this can be done with something like. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]```

date1=$(date +"%s")
date2=$(date +"%s")
diff=$(($date2-$date1))
echo "$(($diff / 60)) minutes and $(($diff % 60)) seconds elapsed."
```[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]

But basically I need to script something that will count x number of events that happen 60 seconds apart from each other. [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]If we just hand a splunk instance laying around, it'd be easier, but we don't have that kind of funding. (oh well).[/FONT][/COLOR]

---

### Post by Vaphell on 2015-06-01
example of log format?

---

### Post by the_kernel2 on 2015-06-01
[COLOR=#444444][FONT=Helvetica Neue][B]The logs look sort of like this. 

2015-05-29 10:50:59,565 WARN [trap-proc13] processTrapForUpdatedIpAddress: bad number of devices found for MAC address 00 90 ea 05 a0 64: 0: [][/B][/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica Neue]**[B]2015-05-29 10:50:59,582 WARN [http-80-29] PowerAgendAdapter.provisionSysNameLocation: checking 'sysLocation' for device 'FL-RE-SDAD-RE202-A' at 100.65.33.193:161, GET=hDaFHJG7, SET=hDaFHJG7**[/B][/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica Neue]**[B][B]2015-05-29 10:50:59,613 WARN [http-80-29] PowerAgendAdapter.provisionSysNameLocation: 'sysLocation' matches for device 'FL-RE-SDAD-RE202-A' at 100.65.33.193:161, GET=hDaFHJG7, SET=hDaFHJG7**[/B][/B][/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica Neue]**[B][B][B]2015-05-29 10:50:59,728 WARN [http-80-29] SNMPClient.getOidCore: can't get OID: host= 100.65.33.193, port=161, getCommunity=hDaFHJG7**[/B][/B][/B][/FONT][/COLOR]
[COLOR=#444444][FONT=Helvetica Neue]**[B][B][B]2015-05-29 10:50:59,756 WARN [http-80-29] SNMPClient.getOidCore: can't get OID: host= 100.65.33.193, port=161, getCommunity=hDaFHJG7**[/B][/B][/B][/FONT][/COLOR]
**[B]**[/B]

---

### Post by papibe on 2015-06-01
Hi the_kernel2.

I'm not sure what you are looking for, but from your log example, this may help.

For formats:
```
$ date '+%F %T'
2015-06-01 18:26:17

$ date --rfc-3339=seconds
2015-06-01 18:26:34-05:00
```
For math:
```
$ some_date=$( date -d "yesterday" )

$ echo $some_date
Sun May 31 18:36:55 CDT 2015

$ date '+%F %T' -d "$some_date +60secs"
2015-05-31 18:37:55
```
Does that help?
Regards.

---

### Post by the_kernel2 on 2015-06-01
> **papibe said:**
> Hi the_kernel2.

I'm not sure what you are looking for, but from your log example, this may help.

For formats:
```
$ date '+%F %T'
2015-06-01 18:26:17

$ date --rfc-3339=seconds
2015-06-01 18:26:34-05:00
```
For math:
```
$ some_date=$( date -d "yesterday" )

$ echo $some_date
Sun May 31 18:36:55 CDT 2015

$ date '+%F %T' -d "$some_date +60secs"
2015-05-31 18:37:55
```
Does that help?
Regards.

Basically, our log contains the above entries. 

They happen on a 60 second interval. 

I need to count the number of times they happen (when they happen 60 seconds apart). 

I think I've done it here. 

This is what I have so far. 

```

[COLOR=#999988]*#/bin/bash*[/COLOR]
[COLOR=#008080]THISMINUTE[/COLOR]**=****$(**date [COLOR=#BB8844]'+I:%M'[/COLOR]**)**
[COLOR=#008080]LASTMINUTE[/COLOR]**=****$(**date [COLOR=#BB8844]'+%I:%M'[/COLOR] --date**=**[COLOR=#BB8844]"1 minute ago"[/COLOR]**)**
[COLOR=#008080]COUNT[/COLOR]**=****$(**sed -n [COLOR=#BB8844]"/[/COLOR][COLOR=#008080]$LASTMINUTE[/COLOR][COLOR=#BB8844]/,/[/COLOR][COLOR=#008080]$THISMINUTE[/COLOR][COLOR=#BB8844]/p"[/COLOR] /location/of/continuity.txt | grep [COLOR=#BB8844]"bad number of power"[/COLOR] | wc -l**)**
[COLOR=#999999]echo[/COLOR] [COLOR=#BB8844]"[/COLOR][COLOR=#008080]$COUNT[/COLOR][COLOR=#BB8844]"[/COLOR] >> /opt/scxripts/error-count.log
```

---

### Post by papibe on 2015-06-01
Something like this should work:
```
#!/bin/bash
reference_time=$(date -d "1 minute ago" +%s)

number_of_entries=0

while IFS=, read -r time rest
do
    entry_time=$( date -d "$time" +%s)

    if [ "$entry_time" -ge "$reference_time" ]; then
        number_of_entries=$((number_of_entries+1))
    fi
done < ./path/to/log

echo "$number_of_entries"

```
Let us know how that works,
Regards.

---

### Post by the_kernel2 on 2015-06-02
This was more than successful, however two more issues need to be resolved. 

1. The entries that qualify have to be displayed in a dump > sample.txt 
2. Its more than one log file (on one machine there are upwards of 100 of them).

---

### Post by papibe on 2015-06-03
Something like this should work. Let us know if you need help understanding the code.
```
#!/bin/bash

# Logs locations.
ORIGINAL_LOGS_DIR="/path/to/original/logs"
NEW_COUNT_LOGS="/path/to/new/count/logs"

for log_file in "$ORIGINAL_LOGS_DIR"/*.logo
do
    #
    # Work with original filenames to get new filename logs
    #
    log_filename="${log_file##*/}"  # Get original filename with no path in the name.
    new_count_log="$NEW_COUNT_LOGS/$log_filename".count # Set new count filename log with proper path.

    # Set reference time: one minute ago.
    reference_timestamp=$(date -d "1 minute ago" +%s)   # timestap
    printable_reference_time=$(date -d @"$reference_timestamp" '+%F %T') # same time but in 'yy/mm/dd hh:mm:ss' format.

    number_of_entries=0

    while IFS=, read -r time rest
    do
        entry_time=$( date -d "$time" +%s)

        if [ "$entry_time" -ge "$reference_timestamp" ]; then
            number_of_entries=$((number_of_entries+1))
        fi
    done < "$log_file"

    echo "$printable_reference_time $number_of_entries" >> "$new_count_log"
done

```
Regards.

---

### Post by the_kernel2 on 2015-06-09
This worked really well thank you.

---

### Post by Habitual on 2015-06-11
Sorry. I didn't see where you have this (mostly?) working...
> **the_kernel2 said:**
> [COLOR=#000000][FONT=Verdana]If we just hand a splunk instance laying around, it'd be easier, but we don't have that kind of funding. (oh well).[/FONT][/COLOR]
Elasticsearch + logstash + kibana is a good alternative, (and FREE too)

bash date diffs are taxing on the system.

Have a look at 
[Counting varnish 503s for the "last minute"]("http://bournetoraiseshell.com/article.php?story=20131202122038302&query=503s")
for what I used.

Have a Great Day!

---


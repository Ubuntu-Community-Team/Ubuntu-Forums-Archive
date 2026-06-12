---
title: "How convert date from variable to epoch seconds"
date: 2014-04-15
forum: Programming Talk
---

### Post by peter-spolenak on 2014-04-15
Hello everybody,

I'm quite new in bash programming and already at early beginning I have a problem. I'm programming a bash script that must read data from text file and extract data for specific time interval in text file, named with date of interval start. Contents of text file looks like:

0    15/04/2014    09:56:20.0    0x0000    64    %RH    0x0002
1    15/04/2014    09:56:10.0    0x0000    65    %RH    0x0002
2    15/04/2014    09:56:00.0    0x0000    66    %RH    0x0002
3    15/04/2014    09:55:50.0    0x0000    66    %RH    0x0002
4    15/04/2014    09:55:40.0    0x0000    67    %RH    0x0002
5    15/04/2014    09:55:30.0    0x0000    68    %RH    0x0002
6    15/04/2014    09:55:20.0    0x0000    68    %RH    0x0002
7    15/04/2014    09:55:10.0    0x0000    68    %RH    0x0002
8    15/04/2014    09:55:00.0    0x0000    67    %RH    0x0002

I assign date to variable date1:

echo $date1
15/04/2014    09:56:20

Then I want to convert date1 value to epoch seconds:

date1sec=`date --date="15/04/2014 09:56:20" +%s`

But I get error:

date: invalid date `15/04/2014 09:56:20'

I found that problem is in date format 15/04/2014, because 15 is interpreted as %m instead as %d. I changed date format in localization file en_GB (which is used for localization formats configuration on my PC) as described at [http://blog.chewearn.com/2008/11/14/change-date-format-globally-in-ubuntu/](http://blog.chewearn.com/2008/11/14/change-date-format-globally-in-ubuntu/)
I found this trying to change 15/04/2014 with 12/04/2014 and then it was normaly converted to epoch seconds.

Even if I define date format in en_GB as %d/%m/%Y %T, date format is obviously read from somewhere as %m/%d%Y %T and I can't find the way how to work this out. Could someone, please, be so kind and help me find the solution for this ? :oops:

---

### Post by Vaphell on 2014-04-15
time interval? Then you have a really really crappy time format there. For data processing YYYYMMDD is a must, because not only it avoids the collision with the USian system, it also means the alphabetical order is chronological and simple string comparisons would be enough to determine before/after relation.

I'd convert the data with *sed* and maybe *sort* it by day/hr columns if they rows are not in chronological order
```
sed -r 's:([0-9]{2})/([0-9]{2})/([0-9]{4}):\3-\2-\1:' data.txt | sort -k2 -k3
```

example with the epoch seconds
```
while read i day hr stuff
do
    es=$( date -d "$day $hr" +%s )
    echo "$day $hr  =>  @$es ($( date -d "@$es" ))"
done < <( sed -r 's:([0-9]{2})/([0-9]{2})/([0-9]{4}):\3-\2-\1:' data.txt )
```

```
2014-04-15 09:56:20.0  =>  @1397548580 (Tue Apr 15 09:56:20 CEST 2014)
2014-04-15 09:56:10.0  =>  @1397548570 (Tue Apr 15 09:56:10 CEST 2014)
2014-04-15 09:56:00.0  =>  @1397548560 (Tue Apr 15 09:56:00 CEST 2014)
2014-04-15 09:55:50.0  =>  @1397548550 (Tue Apr 15 09:55:50 CEST 2014)
2014-04-15 09:55:40.0  =>  @1397548540 (Tue Apr 15 09:55:40 CEST 2014)
2014-04-15 09:55:30.0  =>  @1397548530 (Tue Apr 15 09:55:30 CEST 2014)
2014-04-15 09:55:20.0  =>  @1397548520 (Tue Apr 15 09:55:20 CEST 2014)
2014-04-15 09:55:10.0  =>  @1397548510 (Tue Apr 15 09:55:10 CEST 2014)
2014-04-15 09:55:00.0  =>  @1397548500 (Tue Apr 15 09:55:00 CEST 2014)
```

---

### Post by steeldriver on 2014-04-15
Yes unfortunately although the *output *format of GNU date is extremely flexible, *input *dates still need to be in one of the formats specified here:

[https://www.gnu.org/software/coreutils/manual/html_node/Calendar-date-items.html#Calendar-date-items](https://www.gnu.org/software/coreutils/manual/html_node/Calendar-date-items.html#Calendar-date-items)

As well, the locale only affects the output format AFAIK. FWIW Python is quite nice for this kind of thing e.g.

```

>>> import time
>>>
>>> with open("spolenak.txt", "r") as f:
...     for line in f:
...             data = line.split()
...             tm = time.strptime(data[1]+" "+data[2],"%d/%m/%Y %H:%M:%S.0")
...             print time.mktime(tm)
...
1397570180.0
1397570170.0
1397570160.0
1397570150.0
1397570140.0
1397570130.0
1397570120.0
1397570110.0
1397570100.0

```

The numbers come out 6hrs difference from Vaphell's - likely the timezone is a factor here, Python provides calendar.timegm() in case the required conversion is from UTC rather than localtime.

---

### Post by ofnuts on 2014-04-16
In the original data there is no timezone, so converting it to epoch is rather virtual... It's OK if it is used only to compute time differences.

---

### Post by peter-spolenak on 2014-04-16
Yes, I must only calculate beginning date/time and extract time intervals in text file. [COLOR=#000000]Below is one complete interval (6 samples, 10 sec sampling rate), complete stored data capacity on remote system is last 8 days, that means about 68000+ lines. When I call a script I also define desired day interval/periode as parameter/argument (for example days 2 and 3 back from beginning script execution). My script must download data from remote system into temporary text file, extract lines with proper time stamp (past days 2 and 3) and write those lines in text files. One text file contains data for 10 min, that is 6 samples/min *10 min = 60 lines = 6 (sampling) intervals, every text file is named by timestamp of beginning of 1st interval in file, from example lines below, name should be [/COLOR][COLOR=#000000]15/04/2014 09:55:00.log
[/COLOR]
[COLOR=#000000]3 15/04/2014 09:55:50.0 0x0000 66 %RH 0x0002[/COLOR]
[COLOR=#000000]4 15/04/2014 09:55:40.0 0x0000 67 %RH 0x0002[/COLOR]
[COLOR=#000000]5 15/04/2014 09:55:30.0 0x0000 68 %RH 0x0002[/COLOR]
[COLOR=#000000]6 15/04/2014 09:55:20.0 0x0000 68 %RH 0x0002[/COLOR]
[COLOR=#000000]7 15/04/2014 09:55:10.0 0x0000 68 %RH 0x0002[/COLOR]
[COLOR=#000000]8 15/04/2014 09:55:00.0 0x0000 67 %RH 0x0002

[/COLOR][COLOR=#000000]
As I described in my 1st post, I have only problems with converting current date to epoch seconds, converting epoch to human readable format works properly:

[/COLOR]pets@pets:~$ date
Wed Apr 16 10:52:10 CEST 2014

pets@pets:~$ date +%s
1397638344

pets@pets:~$ date --date="1970-01-01 UTC +1397638344 sec" +"%d/%m/%Y %T"
16/04/2014 10:52:24

pets@pets:~$ date --date="16/04/2014 10:52:10" +%s
date: invalid date `16/04/2014 10:52:10'

Obviously, the less complicated option is converting start date format to %m/%d/%Y %T, convert to epoch and during extraction of data to log file back to original format.
Or is there maybe beter solution ?

---

### Post by Vaphell on 2014-04-16
> When I call a script I also define desired day interval/periode as parameter/argument

what is it supposed to look like exactly? It's hard to figure out possible inputs from the description.
Precision down to days? Hours? Seconds? Is it (from-to) or (pattern)?

Either way use sed as an intermediary to reorder dd/mm/yyyy to yyyy-mm-dd like in my previous post.

---

### Post by peter-spolenak on 2014-04-16
I simply reorder date1 value format to %m/%d/%Y with command **startDate=`echo $date1 | awk -F" " '{print $1}' | awk -F"/" '{print $2 "/" $1 "/" $3}'`**

And now, when I execute command **startTimeSec=$( date --date="$startDate" +%s )** I get value in epoch seconds. So, I can finaly proceed with programming :guitar:
I was looking for reason for my problems for few days but at least, I learned something new about linux and bash programming. Now I must just parse data that contains desired timestamp in save it in log files. Thanks a lot to everybody who answered to my post.

---

### Post by Vaphell on 2014-04-16
Show your script. What you are doing is rather wasteful, because you are spawning awk process each time you need to reorder numbers in a single data point. You are executing awk 68000 times instead of once.

Instead of something like 
```
while read startDate
do
    d=$( echo $startDate | awk ... )
    s=$( date -d "$d" +%s )
done < input.txt
```

you should be doing something like
```
while read startDate
do
    s=$( date -d "$startdate" +%s )
done < <( sed/awk ... input.txt )
```
preprocess data in 1 go, then do what needs to be done.

---

### Post by peter-spolenak on 2014-04-17
So, my script is (maybe it looks confusing because of my lack of experiences in bash programming and because it is not finished yet, I'm trying to define further "logic"):

```
#!/bin/bash


# Define variables
ipAddr=$1 # AWS IP address
portNum=$2 # Sensor port
chNum=$3 # Sensor channel
beginInterval=$4 # Begining of interval
endInterval=$5 # End of interval


if [ -z $ipAddr ] || [ -z $portNum ]
then echo "IP address or port is missing ..."
fi


# Verify IP Address syntax:
if [ `echo $ipAddr | grep -o '\.' | wc -l` -ne 3 ]; then
        echo "Parameter '$ipAddr' does not look like an IP Address (does not contain 3 dots).";
        exit 1;
elif [ `echo $1 | tr '.' ' ' | wc -w` -ne 4 ]; then
        echo "Parameter '$ipAddr' does not look like an IP Address (does not contain 4 octets).";
        exit 1;
else
        for OCTET in `echo $ipAddr | tr '.' ' '`; do
                if ! [[ $OCTET =~ ^[0-9]+$ ]]; then
                        echo "Parameter '$ipAddr' does not look like in IP Address (octet '$OCTET' is not numeric).";
                        exit 1;
                elif [[ $OCTET -lt 0 || $OCTET -gt 255 ]]; then
                        echo "Parameter '$ipAddr' does not look like in IP Address (octet '$OCTET' in not in range 0-255).";
                        exit 1;
                fi
        done
fi


if [ -z $chNum ]
then echo "Channel number is missing ..."
fi


# Verify channel number syntax
# TO DO


# Read metadata from AWS and create folder for AWS data
printf 'get info\r\n' | nc -w 1 $ipAddr $portNum > tempData
stationCode=($(awk '/code/ {print substr($4, 0, length($4)-1)}' tempData)) # Extract station code and remove ETX character
mkdir $stationCode
echo "Station code: "$stationCode > $stationCode/metadata # Create file metadata


printf 'get mem\r\n' | nc -w 1 $ipAddr $portNum > tempData # Write "get mem" command result to file tempData


procTime=$(awk '/Tp/ {print $2, $3, $4, substr($5, 0, length($5)-1)}' tempData) # Extract processing and sampling time 


echo $procTime >> $stationCode/metadata # Add processing time to file metadata


sampTime=$(awk '/Tp/ {print $6, $7, $8, $9}' tempData)
echo $sampTime >> $stationCode/metadata # # Add sampling time to file metadata
#rm tempData
datum=`printf 'get date\r\n' | nc -w 1 $ipAddr $portNum`
datum1=`echo $datum | cut -c 1-19` #| sed -e 's/\ /.*/' | strings
echo $datum1 # 17/04/2014 10:42:16

printf 'get ta ch00 1000\r\n' | nc -w 1 $ipAddr $portNum > data.log # This command download last 1000 lines from device, this is only for development needs :) 


tempTime=`echo $datum1 | awk -F" " '{print $2}' | awk -F":" '{print $3}'`
echo $tempTime # 16 are seconds from $datum1, this number+10 must be subtracted from $datum1 epoch value (%s), so I get end date/time of last completed sampling interval
startDate=`echo $datum1 |awk -F" " '{print $1}' | awk -F"/" '{print $2 "/" $1 "/" $3}'` # switch day/month position to 04/17/2014 and assign value to variable
startTime=`echo $datum1 |awk -F" " '{print $2}'` # assign time 10:42:16 to variable
startTimeSec=$( date --date="$startDate $startTime" +%s ) # convert time to epoch and assign value to variable 
echo $startDate
echo $startTime
echo $startTimeSec


date --date="1970-01-01 UTC + $startTimeSec sec" +"%d/%m/%Y %T"

# UNDER CONSTRUCTION ;)

```
Just for information, commands, which are sent with netcat are internal commands on devices, from which I download data. I found that each remote device have internal command "get ta chxx -t YYYYMMDDhhmm" and this command returns data for 10 min descending from date and time, specified in command. So, now I must just define start and end date/time of desired period for data downloading (script argument $4 and $5 in range 0 - 8, 0= today) in seconds and create a loop, in which I'll execute command "get ta chxx -t YYYYMMDDhhmm | nc xxxxxxxxxxxx", decrement date/time properly for 10 min for next command "get ta ..." execution and redirect returned data into file with timestamp that is used in command "get ta ...." in folder $stationCode. This loop must run from start date/time to end date/time. It looks easy, but developing readable, optimized and "resources friendly" code takes time and experiences. This is also important because in some cases I download data from some devices via GPRS network.

---

### Post by Vaphell on 2014-04-17
a bit tidier IP check.

```
#!/bin/bash

ip=$1

[[ $ip =~ ^[0-9]+([.][0-9]+){3}$ ]] || { echo "bad IP addr" && exit 1; }
IFS=. read -a octet <<< "$ip"
for oct in "${octet[@]}"
do
  (( oct>=0 && oct<=255 )) || { echo "bad IP addr (bad octet)" && exit 1; }
done
```


```
datum=`printf 'get date\r\n' | nc -w 1 $ipAddr $portNum`
```
i'd feed the string directly without pipes
```
datum=$( nc -w 1 $ipAddr $portNum <<< $'get date' )
```
i'd think about defining these messages in a visible manner, eg

```
#!/bin/bash

_GET_DATE=$'get date\r'
_GET_TA_CH1000=$'get ta ch00 1000\r'
...
datum=$( nc -w 1 "$ipAddr: "$portNum" <<< "$_GET_DATE" )
nc -w 1 "$ipAddr" "$portNum" <<< "$_GET_TA_CH1000" > data.log
```



this thing uses an array, but i don't see it used as an array anywhere. Do you need only 1st elem here?
```
stationCode=[COLOR="#0000FF"]([/COLOR] $(awk '/code/ {print substr($4, 0, length($4)-1)}' tempData) [COLOR="#0000FF"])[/COLOR]
```



back to the original point of this thread: where do you get your desired data in bulk and what does it look like raw? this code
```
datum=`printf 'get date\r\n' | nc -w 1 $ipAddr $portNum`
datum1=`echo $datum | cut -c 1-19` #| sed -e 's/\ /.*/' | strings
echo $datum1 # 17/04/2014 10:42:16
```
seems to extract time from a single data point.



as for style: i suggest dropping deprecated backticks and moving to $() and always quoting "$vars" (good habit that protects against whitespace issues)

---

### Post by peter-spolenak on 2014-04-18
I get desired data in bulk from remote AWS (automatic weather station) with embedded linux "computer", on which runs application for managing several devices/sensors for measuring purposes. This managing application implements commands like "get date", "get ta" and so on, and also takes care for storing measured data on local disc. Yes, I extract time from single data point. Bulk desired data, which I get with execution of commands "get ta ..." looks exactly like this:
 
```
P3045    ch00@cpu_0:60002    016@0035.12.01.22.002    rel_humidity
0    03/04/2014    13:31:50.0    0x0000    60    %RH    0x0002
1    03/04/2014    13:31:40.0    0x0000    60    %RH    0x0002
2    03/04/2014    13:31:30.0    0x0000    61    %RH    0x0002
3    03/04/2014    13:31:20.0    0x0000    60    %RH    0x0002
4    03/04/2014    13:31:10.0    0x0000    60    %RH    0x0002
5    03/04/2014    13:31:00.0    0x0000    59    %RH    0x0002
6    03/04/2014    13:30:50.0    0x0000    59    %RH    0x0002
7    03/04/2014    13:30:40.0    0x0000    59    %RH    0x0002
8    03/04/2014    13:30:30.0    0x0000    59    %RH    0x0002
9    03/04/2014    13:30:20.0    0x0000    59    %RH    0x0002
10    03/04/2014    13:30:10.0    0x0000    60    %RH    0x0002
11    03/04/2014    13:30:00.0    0x0000    60    %RH    0x0002
12    03/04/2014    13:29:50.0    0x0000    61    %RH    0x0002
13    03/04/2014    13:29:40.0    0x0000    61    %RH    0x0002
14    03/04/2014    13:29:30.0    0x0000    61    %RH    0x0002
15    03/04/2014    13:29:20.0    0x0000    61    %RH    0x0002
16    03/04/2014    13:29:10.0    0x0000    60    %RH    0x0002
17    03/04/2014    13:29:00.0    0x0000    60    %RH    0x0002
```

I ignore 1st line (because it doesn't contain any useful information for me). From rest of lines (format of part with date and time is always the same) I want to extract data for choosen time periode (any possible option/length within current date/time and 8 days backward) into files, that contains data for 10 min (for example from 12:09 - 12:00, 11:59 - 11:50, ...) and are named with timestamp of newest/latest line in this file and channel number (for example 18/04/2014_12:09_ch00.log).

> [COLOR=#000000]this thing uses an array, but i don't see it used as an array anywhere. Do you need only 1st elem here?[/COLOR]
[COLOR=#000000]Code:
stationCode=[COLOR=#0000FF]([/COLOR] $(awk '/code/ {print substr($4, 0, length($4)-1)}' tempData) [COLOR=#0000FF])[/COLOR][/COLOR]

Here I only search for line containing station code "|   code:M417", then extract M417, mkdir with this name and assign value to variable stationCode. I need only Mxxx part in this line.

---

### Post by Vaphell on 2014-04-18
is there possibility of 10min intervals that are like 12:05-12:14? because assuming that's not the case the data can be rather trivially sorted using grep (grepping for '15/04/2014 12:1' will yield 12:10-12:19)

representing your data with aws.txt
```
IFS="$IFS@" read _ ch _ < aws.txt
ptn='\d{2}/\d{2}/\d{4}\s+\d+:\d'

readarray -t int < <( grep -oP "$ptn" aws.txt | uniq )

printf 'channel: %s\n' "$ch"
echo "intervals in bulk data:"
printf '%s*\n' "${int[@]}"
echo

for i in "${int[@]}"
do
    IFS="$IFS/" read d m y h <<< "$i"
    out=${y}-${m}-${d}__${h}0-${h}9__${ch}.txt
    echo "$i* => $out"
    grep -F "$i" aws.txt > "$out"
done
```

```
$ ./spolenak.sh 
channel: ch00
intervals in bulk data:
03/04/2014    13:3*
03/04/2014    13:2*

03/04/2014    13:3* => 2014-04-03__13:30-13:39__ch00.txt
03/04/2014    13:2* => 2014-04-03__13:20-13:29__ch00.txt

```



how do you control which part of the potential today - (today-8days) range you get from the server?

---

### Post by steeldriver on 2014-04-18
How about Python? you could do this kind of datetime arithmetic directly - for instance

```

import datetime as dt

dtint = dt.timedelta(seconds=30)
.
.
.
                    if (dtstop - dtdtm) < dtint:
                        sys.stdout.write(line)


```

(I'm using 30secs instead of 10mins here because you've only given us a few lines of data). You could loop over lines something like

```

    with open(infile,'r') as f:
        for line in f:
            # skip anything that does not parse as our expected datetime format
            try:
                dtstr = ' '.join(map(str,line.split()[1:3]))
                dtdtm = dt.datetime.strptime(dtstr, dtfmt + ".0")
            except:
                continue
            
            # process the datetimes
            if dtdtm >= dtmin and dtdtm <= dtmax:
                try:
                    if (dtstop - dtdtm) < dtint:
                        sys.stdout.write(line)
                    else:
                        # indicate start of new interval (could
                        # change to a different outfile here instead)
                        sys.stdout.write("\n")
                        dtstop = dtdtm
                        interval += 1
                except:
                    sys.stdout.write(line)
                    dtstop = dtdtm

```

If you like, you can put some fancy argument handling around that (stolen shamelessly from [getopt &#8212; C-style parser for command line options]("https://docs.python.org/2/library/getopt.html"))

```

#!/usr/bin/env python

import sys,getopt,re
import datetime as dt

dtint = dt.timedelta(seconds=30)

def usage():
    print "usage: ",sys.argv[0]," [-f from-datetime] [-t to-datetime] file" 


def main():
    try:
        opts, args = getopt.getopt(sys.argv[1:], "hf:t:", ["help", "output="])
    except getopt.GetoptError as err:
        # print help information and exit:
        print str(err) # will print something like "option -a not recognized"
        usage()
        sys.exit(2)
    
    dtfmt = "%d/%m/%Y    %H:%M:%S"
    dtmin = dt.datetime.min
    dtmax = dt.datetime.max
    for o, a in opts:
        if o in ("-h", "--help"):
            usage()
            sys.exit()
        elif o in ("-f", "--from"):
            try:
                dtmin = dt.datetime.strptime(a, dtfmt)
            except:
                print sys.argv[0],": could not understand datetime ",a
                sys.exit(1)
        elif o in ("-t", "--to"):
            try:
                dtmax = dt.datetime.strptime(a, dtfmt)
            except:
                print sys.argv[0],": could not understand datetime ",a
                sys.exit(1)
        else:
            assert False, "unhandled option"

    try:
        infile = args[0];
    except:
        usage()
        sys.exit(1)
        
    with open(infile,'r') as f:
        for line in f:
            # skip anything that does not parse as our expected datetime format
            try:
                dtstr = ' '.join(map(str,line.split()[1:3]))
                dtdtm = dt.datetime.strptime(dtstr, dtfmt + ".0")
            except:
                continue
            
            # process the datetimes
            if dtdtm >= dtmin and dtdtm <= dtmax:
                try:
                    if (dtstop - dtdtm) < dtint:
                        sys.stdout.write(line)
                    else:
                        # indicate start of new interval (could
                        # change to a different outfile here instead)
                        sys.stdout.write("\n")
                        dtstop = dtdtm
                        interval += 1
                except:
                    sys.stdout.write(line)
                    dtstop = dtdtm

if __name__ == "__main__":
    main()

```

Then the usage is something like

```

$ ./revtmdiffs.py -f "03/04/2014    13:29:40" -t "03/04/2014    13:31:10" spolenak2.txt 
4    03/04/2014    13:31:10.0    0x0000    60    %RH    0x0002
5    03/04/2014    13:31:00.0    0x0000    59    %RH    0x0002
6    03/04/2014    13:30:50.0    0x0000    59    %RH    0x0002

7    03/04/2014    13:30:40.0    0x0000    59    %RH    0x0002
8    03/04/2014    13:30:30.0    0x0000    59    %RH    0x0002
9    03/04/2014    13:30:20.0    0x0000    59    %RH    0x0002

10    03/04/2014    13:30:10.0    0x0000    60    %RH    0x0002
11    03/04/2014    13:30:00.0    0x0000    60    %RH    0x0002
12    03/04/2014    13:29:50.0    0x0000    61    %RH    0x0002

13    03/04/2014    13:29:40.0    0x0000    61    %RH    0x0002

```

which breaks the specified time range into 30 second sub intervals.

---


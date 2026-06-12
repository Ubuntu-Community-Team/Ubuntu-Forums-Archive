---
title: "URL Comparison in Bash Script"
date: 2012-09-06
forum: Programming Talk
---

### Post by Ryan79 on 2012-09-06
Hey all :)

I'm kind of a noob when it comes to bash (and scripting, to be honest lol) so I apologize in advance:

I've got a URL that changes every 4 hours, and I need to write a script that pulls some files from that URL.

consistencies:

URL is the same up until /gfs.%Y%m%d%H/ directory

directory is always 00, 06, 12, or 18 hour marks (i.e. gfs.2012080600, gfs.2012080606, gfs.2012080612 or gfs.2012080618 )

is there a way to check the URL within the bash script?

I tried the syntax below to see if I could get it to work... but it would seem to only check against a (obviously) invalid local directory:

```
 

url="www.example.com/exampledir/exampledir/gfs."

varDate="$(date +%Y%m%d)"

varZulu=06

if ["$url""$varDate""$varZulu"/ = "$url""varDate"06/] ; then
wget -P /home/localdir "$url""varDate"06/$file

```

thanks for the help :)

---

### Post by Ryan79 on 2012-09-06
wget --spider

so I've been looking through the man for wget, and the --spider option seems like a potential way?

is there a way to use wget --spider results as a means to tell the script to attempt a download?

---

### Post by steeldriver on 2012-09-06
I don't really understand what you're trying to do but there are a couple of obvious errors in your syntax

```
url="www.example.com/exampledir/exampledir/gfs."

varDate="$(date +%Y%m%d)"

varZulu=06

if **[COLOR=Red][ [/COLOR]**"$url""$varDate""$varZulu"/ = "$url""**[COLOR=Red]$[/COLOR]**varDate"06/**[COLOR=Red] ][/COLOR]** ; then
wget -P /home/localdir "$url""**[COLOR=Red]$[/COLOR]**varDate"06/$file
```

---

### Post by Ryan79 on 2012-09-06
Sorry SteelDriver, and thank you for the corrections.
I thought I was clear on my intent on the OP so let me rephrase:

I need a script that pulls specific files generated throughout the day, from a directory that changes four times a day
Directory structure for the site is pretty static until the final directory, where the files are stored...
naming convention for said final directory is gfs.YearMonthDayZuluhour

when a new file batch for the day is run, a new directory is generated, however the name is consistant in that the batches are always 00 06 12 and 18 (zulu hours)

so... first batch of the day resides in directory /gfs.YearMonthDay00 second batch in /gfs.YearMonthDay06 third in /gfs.YearMonthDay12 and forth in /gfs.YearMonthDay18

since the site refuses an FTP connection, I'm attempting to use wget to pull the files, which works when pointed directly to the directory/file

I also noticed that wget --spider is able to test the URLs to see if they are valid

is there a way to use wget --spider's results to tell the script to attempt a file download?

---

### Post by steeldriver on 2012-09-06
sorry I don't really know anything about wget - however I don't see any reason why it shouldn't work with a simple query (pretty much how you have it now) provided the url that you are generating is valid

I guess I don't get why you are needing to test the url? rather than just

```

#!/bin/bash

for i in {00,06,12,18}; do 
  wget -P /home/localdir "www.example.com/exampledir/exampledir/gfs.$(date +%Y%m%d)$i"
done

```

---

### Post by conradin on 2012-09-06
Can you tell us the site?

either way, wget is great, and curl is another good option.

out of curiosity, by knowing the format, you have the option to generate the urls on the fly, or have them all predefined. 
Then again, you could write the url as a regular expression, and pass it as a variable to curl or wget. 
Im a little bit confused, do the files have extensions? Are you getting all the files in the directory, or specific ones? 

the expr command comes to mind:
[http://ss64.com/bash/expr.html](http://ss64.com/bash/expr.html)

---

### Post by Ryan79 on 2012-09-06
> **steeldriver said:**
> sorry I don't really know anything about wget - however I don't see any reason why it shouldn't work with a simple query (pretty much how you have it now) provided the url that you are generating is valid

I guess I don't get why you are needing to test the url? rather than just

```

#!/bin/bash

for i in {00,06,12,18}; do 
  wget -P /home/localdir "www.example.com/exampledir/exampledir/gfs.$(date +%Y%m%d)$i"
done

```

actually... your loop DOES make sense... though I don't want to download the entire directory, just some very specific files listed within them; and if the pull from gfs.$(date +%Y%m%d)18 succeeds it should finish instead of going to the other (older) directories at the site {18,12,06,00}

This does give me a different approach, thanks! :)

---

### Post by Ryan79 on 2012-09-06
> **conradin said:**
> Can you tell us the site?

either way, wget is great, and curl is another good option.

out of curiosity, by knowing the format, you have the option to generate the urls on the fly, or have them all predefined. 
Then again, you could write the url as a regular expression, and pass it as a variable to curl or wget. 
Im a little bit confused, do the files have extensions? Are you getting all the files in the directory, or specific ones? 

the expr command comes to mind:
[http://ss64.com/bash/expr.html](http://ss64.com/bash/expr.html)

the site is [www.ftp.nccp.noaa.gov](www.ftp.nccp.noaa.gov) it's a NOAA site that houses GFS model GRIB weather files.

it's specific files within the directories (about 10/15 out of 100+)

so the scripts tasks would be:
determine current valid site directory
delete old files from local directory (dependent on variables defining current valid site directory)
pull specific files from current valid site directory
rename downloaded files for post-processing work(done)

then cronjob would schedule the script to run at intervals durring the day.

I'll check out that link you listed, see if there's anything I could use in it ;) Thanks!

---

### Post by steeldriver on 2012-09-06
so if you want to try 18,12,06,00 in turn and stop when you find a valid one, you could maybe look at the wget return value, especially if there's an index file or somesuch that you can test for e.g.

```
for i in {18,12,06,00}; do
  wget -P $HOME/localdir "http://www.ftp.ncep.noaa.gov/data/nccf/com/prod/gfs.$(date +%Y%m%d)$i/index.htm"
  if [ $? -eq 0 ]; then
    # delete old local data
    # wget new data
    break;
  fi
done

```[http://www.gnu.org/software/wget/manual/html_node/Exit-Status.html](http://www.gnu.org/software/wget/manual/html_node/Exit-Status.html)

---

### Post by ofnuts on 2012-09-07
> **Ryan79 said:**
> Hey all :)

I'm kind of a noob when it comes to bash (and scripting, to be honest lol) so I apologize in advance:

I've got a URL that changes every 4 hours, and I need to write a script that pulls some files from that URL.

consistencies:

URL is the same up until /gfs.%Y%m%d%H/ directory

directory is always 00, 06, 12, or 18 hour marks (i.e. gfs.2012080600, gfs.2012080606, gfs.2012080612 or gfs.2012080618 )

is there a way to check the URL within the bash script?

I tried the syntax below to see if I could get it to work... but it would seem to only check against a (obviously) invalid local directory:

```
 

url="www.example.com/exampledir/exampledir/gfs."

varDate="$(date +%Y%m%d)"

varZulu=06

if ["$url""$varDate""$varZulu"/ = "$url""varDate"06/] ; then
wget -P /home/localdir "$url""varDate"06/$file

```thanks for the help :)

I would do it completely differently: always try to download all 4 directories with wget using the --noclobber function. So when files appear they are eventually downloaded, and if they have already been obtained they aren't donwloaded a second time.

---

### Post by greenpeace on 2012-09-07
Does this help?  It checks the time that script is run, and adapts the URL to get the latest one.  

You say it changes every 4 hours, but then listed 6hourly intervals, so I've taken the 6 hour one.  It's trivial to change it :)

This just gives a URL, you'll need to adapt your wget to fit it, but again that should be trivial!

```
#!/bin/bash
#
url="http://domain.tld/gfs."
urlDate=`date +%Y%m%d`
hour=`date +%H`

if [ $hour -lt 6 ] ; then
        varZulu=00
fi
if [[ $hour -ge 6 && $hour -lt 12 ]] ; then
        varZulu=06
fi
if [[ $hour -ge 12 && $hour -lt 18 ]] ; then
        varZulu=12
fi
if [[ $hour -ge 18 ]] ; then
        varZulu=18
fi

echo $url$urlDate$varZulu
```

so, right now (10:20AM here) it gives me:

```
gp@mariachi:~/code/bash$ ./variable-urls.sh
http://domain.tld/gfs.2012090706
```

---

### Post by Vaphell on 2012-09-07
```
varZulu=$( printf "%02d" $((10#$hour/6*6)) )
```
will do the job without ifs.
```
$ for hour in {00..23}; do printf "%s=%02d " $hour $((10#$hour/6*6)); done
00=00 01=00 02=00 03=00 04=00 05=00 06=06 07=06 08=06 09=06 10=06 11=06 12=12 13=12 14=12 15=12 16=12 17=12 18=18 19=18 20=18 21=18 22=18 23=18
```

besides you can use if elif elif else instead of 4 independent ifs.
```
if (( hour < 6 )); then ...
elif (( hour < 12 )); then ...
elif (( hour < 18 )); then ...
else ...
fi
```

---

### Post by greenpeace on 2012-09-07
> **Vaphell said:**
> ```
varZulu=$( printf "%02d" $((10#$hour/6*6)) )
```


nice!!  good tip, thanks!

---

### Post by Ryan79 on 2012-09-07
thank you all for your replies, it is helping a lot... so thank you :)

the scripting you guys have for varZulu is interesting... though the upload times and the batch run times are different (batch run times determine the directory... that would be the 00 06 12 18) upload times are usually several hours after the batch run.... for example, yesterdays 00 batch was uploaded at 06:02, 06 was uploaded at 12:02 and so forth... so using system time as the marker would potentially break the scripts ability to download the correct batch... since it would be looking for a directory that doesn't exist yet.

I do like the dynamic means of creating the URL though... going to play with that a bit and see if there's a way to make that work

as for the --no-clober function... I would use that, except that I need the older files to be replaced. the names of the files pulled will always be the same, the parent directory determines if the files are recent or not. Since I'm dealing with forecasted weather files, old forecasts don't do me any good. I will remember the option however, as it may yet prove useful :) thank you!

---

### Post by Ryan79 on 2012-09-07
> **Vaphell said:**
> ```
varZulu=$( printf "%02d" $((10#$hour/6*6)) )
```
will do the job without ifs.
```
$ for hour in {00..23}; do printf "%s=%02d " $hour $((10#$hour/6*6)); done
00=00 01=00 02=00 03=00 04=00 05=00 06=06 07=06 08=06 09=06 10=06 11=06 12=12 13=12 14=12 15=12 16=12 17=12 18=18 19=18 20=18 21=18 22=18 23=18
```

besides you can use if elif elif else instead of 4 independent ifs.
```
if (( hour < 6 )); then ...
elif (( hour < 12 )); then ...
elif (( hour < 18 )); then ...
else ...
fi
```

Vaphell.... since the 18hour batch run is valid until the 00hour run done the next day (which seems to be uploaded around 4-6am) would I be correct in assuming the code:

```
 $ for hour in {00..23}; do printf "%s=%02d " $hour $((10#$hour/6*6)); done
00=00 01=00 02=00 03=00 04=00 05=00 06=06 07=06 08=06 09=06 10=06 11=06 12=12 13=12 14=12 15=12 16=12 17=12 18=18 19=18 20=18 21=18 22=18 23=18 
```

would be a valid means to accomplish this part of the task, if the time tables can be adjusted to look at the previous day's date for the first 3 hours of the current day?

something of a combination of:

```

if ((hour < 4)); then ...
   elif $ for hour in {04..23}; do printf "%s=%02d " $hour ...

```

as this would give the script time to pull the 18zulu model files... which looking at the upload times are usually done at about 23:30-23:50. (roughly a 30-10 minute window to download 15/20 files ranging from 20-200mb lol) but more so... if the script is run every hour, then by the time the 18zulu batch is available, the script would have run again until the next day, because of when they uploaded

---

### Post by steeldriver on 2012-09-07
ah I think I understand what you're trying to do now

how about making use of the gnu date manipulators? something like

```
varZulu=$((6*(($(date '+%H')/6))))
echo $(date --date="$(date '+%Y%m%d') +$varZulu hours" '+%Y%m%d%H')
```

which calculates the most recent 'zulu hour' as per Vaphell's suggestion, then adds it to today's %Y%m%d and outputs the whole thing as +%Y%m%d%H

Since %H is already in 2-digit 24hr format it does the 'printf %02d' for free

---

### Post by Ryan79 on 2012-09-07
```


#! /bin/bash

## Setting initial variables

url="http://www.ftp.ncep.noaa.gov/data/nccf/com/gfs/prod/gfs."
date="$(date +%Y%m%d)"
date2="$(date -d "-1 day" +%Y%m%d)"
hour="$(date +%H)"

## Generating functional URL based on date/time and downloading files

if ((hour < 4)); then
    varURL="$("$url""$date2"18)" rm -r /home/localdir/gfs.* ; wget -p /home/localdir "$varURL"/files
  
      elif varZulu="$( for hour in {04..23} ; do printf "%s=%02d " $hour $((10#$hour/6*6)); done
                        04=00 05=00 06=00 07=00 08=06 09=06 10=06 11=06 12=06 13=06 14=12 15=12 16=12 17=12 18=12 19=12 20=12 21=18 22=18 23=18)" ; 
                        rm -r /home/localdir/gfs.* ; wget -P /home/localdir "$url""$date""$varZulu"/files
fi

```

how does this look? and thanks again for all the help

---

### Post by Vaphell on 2012-09-07
```
**$ for hour in {00..23}; do printf "%s=%02d " $hour $((10#$hour/6*6)); done**
00=00 01=00 02=00 03=00 04=00 05=00 06=06 07=06 08=06 09=06 10=06 11=06 12=12 13=12 14=12 15=12 16=12 17=12 18=18 19=18 20=18 21=18 22=18 23=18
```

this was merely a presentation what happens for numbers in 00..23 range if you go with $((10#$hour/6*6)). It won't do anything worthwhile in your script (especially with the loop output pasted in as well) :)


try this
```
if (( $(date +%-H)<4 ))
then
  delta=4
else
  delta=0
fi
date=$( date -d "-$delta hours" +%Y%m%d)
varZulu=$( printf "%02d" $(( $(date -d "-$delta hours" +%-H)/6*6 )) )
...
wget -P /home/localdir "$url$date$varZulu"/files

```
delta is used to roll the clock back

end value produced by the code above:
```
**$ LANG=C date**
Sat Sep  8 00:49:16 CEST 2012
**$ echo "$url$date$varZulu"/files**
http://www.ftp.ncep.noaa.gov/data/nccf/com/gfs/prod/gfs.2012090718/files

```

even shorter:
```
hr=$( date +%-H )
if ((hr<4)); then ((hr+=6)); else ((hr%=6)); fi
...
wget -P /home/localdir $url$( date -d "-$hr hours" +%Y%m%d%H )/files
```

---

### Post by Ryan79 on 2012-09-10
vaphell -

Not sure what I'm doing wrong... but using the following:

```
hour='date +%H'
varZulu=$( printf "%02d" $((10#$hour/6*6)) )

```

I get an error return stating:

Bash: 10#date: value too great for base (error token is "10#date")

---

### Post by steeldriver on 2012-09-10
```
'date +%H' 
```in single quotes produces a string literal - you probably want

```
$(date +%H)
```You may have been confused by the (sometimes still common) use of `backticks`

```
`date +%H`
```which should also work but is now considered deprecated

---

### Post by Ryan79 on 2012-09-10
ahh... that seems to have been my issue, thanks Steeldriver :)

as an FYI, this is what I've got for the script now:

```


#! /bin/bash

##setting initial variables

url="http://www.ftp.ncep.noaa.gov/data/nccf/com/gfs/prod/gfs."
date=$(date +%Y%m%d)
date2=$(date -d "-1 day" +%Y%m%d)
hour=$(date +%H)
varZulu=$( printf %02d" $((10#$hour/6*6)) )

## Generating functional URL based on date/time and downloading files

if ((hour < 4)); then
    varURL=$("$url""$date2"18)" rm -r /home/localdir/gfs.* ;
    for i in { 180 183 186 189 } ; do
      wget -P /home/localdir $varURL/gfs.t18z.pgrib2f"$i" ;
    done

    else rm -r /home/localdir/gfs.* ; for i in { 180 183 186 189 } ; do
        wget -P /home/localdir "$url""$date""$varZulu"/gfs.t"$varZulu"z.pgrib2f"$i" ;
    done
fi

```

and it seems to be working :) pulled the current files from the correct directory.

I need to work on my instance array... seems to try and download a false file before 180 and after 189... but since the files don't exist it isn't harming anything currently... just happy it's downloading :)

Thanks all for your assistance!!

do I need to mark the title as Solved?

---


---
title: "wget doesn't retry downloads on unresolved host names"
date: 2010-02-02
forum: Programming Talk
---

### Post by braikar on 2010-02-02
Hi,

I have been trying all options of wget to get it to work but it never fires a connection retry is the host address cannot be resolved. even if using the parameter '--retry-connrefused'

I have to explain this error of host resolving is not due to the server I'm downloading from, it comes from my internet connection, once every 20-30mins there is somekind of down time when any hostname resolution doesn't work for 4-5 seconds. and if a scheduled crontab download like the one below happens at that time, wget never does any retry to download again...?

One download example:
```

wget --tries=100 --retry-connrefused --waitretry=10 -O /home/braikar/Documents/Downloads\(Sheduled\)/Segment14_`eval date +%Y%m%d`.zip "http://oiswww.eumetsat.org/IPPS/html/MSG/RGB/EVIEW/SEGMENT14/IMAGESDisplay/24FramesEVIEW-SEGMENT14.zip"

```

gives the output like that when failed
```

--2010-02-03 00:30:00--  http://oiswww.eumetsat.org/IPPS/html/MSG/RGB/EVIEW/SEGMENT14/IMAGESDisplay/24FramesEVIEW-SEGMENT14.zip
Resolving oiswww.eumetsat.org... failed: Name or service not known.
wget: unable to resolve host address `oiswww.eumetsat.org'

```

and wget doesn't retry to connect again?

Is there something I'm doing wrong (the parameters are not correct) or is it normal for wget to abandon the download?

I did a bash script to check the downloaded file and it's size and if it is 0bytes force wget again until the file is no longer of 0bytes, so the problem is sorted...

But I'm just wondering if this is a problem which wget cannot handle or if I'm using wget wrongly?

Cheers

---

### Post by tturrisi on 2010-02-04
From the manual:
[COLOR="Red"]--tries=number’
    Set number of retries to number. Specify 0 or ‘inf’ for infinite retrying. The default is to retry 20 times, with the exception of fatal errors like “connection refused” or “not found” (404), **which are not retried**.[/COLOR]
> once every 20-30mins there is somekind of down time when any hostname resolution doesn't work for 4-5 seconds.
If indeed the failure is caused by your ISP then change your DNS server.  This change can be made locally or at the router.

If not in any rush to grab the files, use wait-seconds.  Set to one minute or six or whatever works.  This will give wget a chance to resolve the hostname if ISP DNS has that "blank period of time when it's down".

[COLOR="Red"]--wait=seconds
    Wait the specified number of seconds between the retrievals. Use of this option is recommended, as it lightens the server load by making the requests less frequent. Instead of in seconds, the time can be specified in minutes using the m suffix, in hours using h suffix, or in days using d suffix.

    Specifying a large value for this option is useful if the network or the destination host is down, so that Wget can wait long enough to reasonably expect the network error to be fixed before the retry.[/COLOR]

---

### Post by braikar on 2010-02-04
> From the manual:
--tries=number’
[COLOR="Red"]Set number of retries to number. Specify 0 or ‘inf’ for infinite retrying. The default is to retry 20 times, with the exception of fatal errors like “connection refused” or “not found” (404), which are not retried.[/COLOR]


I read the manual that's why I added "--retry-connrefused"
With this one it should treat "connection refused" or 404 as a normal error and hence retry.

--wait won't make any difference in avoiding the "name resolution" problem, because wget never does any retries with the error I get :|

The error that happens is none of the 2 stated. So it's as I expected, it's wget that doesn't handle this error even with --retry-connrefused

I don't really see the need to change the DNS (I can't anyway), I just wanted wget to handle that error, but it just can't.

here's the script that forces it to continue until it downloads:
```

FILENAME=$1
DOWNURL=$2

wget -O "`echo $FILENAME`" "`echo $DOWNURL`"
FILESIZE=$(stat -c%s "$FILENAME")

while [ $FILESIZE \< 1000 ]; do
	sleep 3
	wget -O "`echo $FILENAME`" "`echo $DOWNURL`"
	FILESIZE=$(stat -c%s "$FILENAME")
done


```
since it's to download 200-400kb images or zip files, I set the limit at 1kb, to also ignore error html pages


thanks for the help :)

---


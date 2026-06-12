---
title: "How can my bash script download from a website which uses link obfuscation?"
date: 2011-11-23
forum: Programming Talk
---

### Post by kittkatt on 2011-11-23
There is a free daily podcast available on the site [www.schiffradio.com](www.schiffradio.com) that I enjoy listening to, but the site seems to use some sort of link obfuscation/download security scripting (I think to prevent other websites from linking to his content).

I am trying to automate this daily download process for personal use since its annoying to have to go to the website everyday and manually click "Save target as..." etc.  The RSS feed only features clips and does not include the full broadcast featured on the homepage.

This is the bash script I wrote to try and automate the process but wget gets hung up on the filename obfuscation.  The website name is the first command line argument (i.e. script [www.schiffradio.com](www.schiffradio.com))     

```
#!/bin/sh

#This script scrapes a webpage and downloads all the mp3 files on it

echo $1
link=$1
w3m -dump_source $1 | zcat > tempsource
grep --ignore-case --only-matching --regexp="http:\/\/.*\.mp3" tempsource > tempoutput
cat tempoutput | uniq - > duplicatesremoved
rm tempoutput
wget --input-file=duplicatesremoved

```

> Linux:~$ ./getlinks.sh [www.schiffradio.com](www.schiffradio.com)
[www.schiffradio.com](www.schiffradio.com)
--2011-11-22 21:28:05--  [http://www.schiffradio.com/site/rd;jsessionid=44556A76EE1EEE77DB1E1F09C1690225?satype=2&said=1&url=http%3A%2F%2Fwww.schiffradio.com%2Fdownloadsecurity%3Furl%3DaHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3](http://www.schiffradio.com/site/rd;jsessionid=44556A76EE1EEE77DB1E1F09C1690225?satype=2&said=1&url=http%3A%2F%2Fwww.schiffradio.com%2Fdownloadsecurity%3Furl%3DaHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3)
Resolving [www.schiffradio.com](www.schiffradio.com)... 72.26.99.238
Connecting to [www.schiffradio.com|72.26.99.238|:80](www.schiffradio.com|72.26.99.238|:80)... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://www.schiffradio.com/downloadsecurity?url=aHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3](http://www.schiffradio.com/downloadsecurity?url=aHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3) [following]
--2011-11-22 21:28:05--  [http://www.schiffradio.com/downloadsecurity?url=aHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3](http://www.schiffradio.com/downloadsecurity?url=aHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3)
Reusing existing connection to [www.schiffradio.com:80](www.schiffradio.com:80).
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://fetch.noxsolutions.com/schiff/audio/pa_20111122_low.mp3](http://fetch.noxsolutions.com/schiff/audio/pa_20111122_low.mp3) [following]
--2011-11-22 21:28:06--  [http://fetch.noxsolutions.com/schiff/audio/pa_20111122_low.mp3](http://fetch.noxsolutions.com/schiff/audio/pa_20111122_low.mp3)
Resolving fetch.noxsolutions.com... 216.38.170.101
Connecting to fetch.noxsolutions.com|216.38.170.101|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29128359 (28M) [audio/x-mpeg]
rd;jsessionid=44556A76EE1EEE77DB1E1F09C1690225?satype=2&said=1&url=http:%2F%2Fwww.schiffradio.com%2Fdownloadsecurity?url=aHR0cDovL2ZldGNoLm5veHNvbHV0aW9ucy5jb20vc2NoaWZmL2F1ZGlvL3BhXzIwMTExMTIyX2xvdy5tcDMqKnwxMzIyMDI2MDg0NDA2Kip8.mp3: File name too long


Any thoughts?  I'm not familiar with how this link obfuscation download security scripting works.

---

### Post by Lampi on 2011-11-23
try a traffic sniffer tool to understand what this site is doing - there is a popular firefox addon called "live http headers"  - this will allow you to understand the http requests the stream is using. If it's a different protocol than http (e.g. rtmp,rtsp,mms) you'll be better of with a more powerful sniffer like wireshark. You'll need other tools to dump this then as well.

Edit: Turns out you're lucky - it's a http stream - you can use another popular extension to download this kind of stream: DownloadHelper - this will also work on youtube - install the addon from the firefox extention manager, klick the stream to start playback, then the DownloadHelper logo will start to cycle once it has found a valid url.

---

### Post by Habitual on 2011-11-23
To me, it looks like the [www.schiffradio.com/content.mp3](www.schiffradio.com/content.mp3) files are really being served from the fetch.noxsolutions.com host.

the [jsessionid]("http://randomcoder.org/articles/jsessionid-considered-harmful") (probably can be used along with a an [http referrer]("https://en.wikipedia.org/wiki/HTTP_referrer")) is being used as an "authorization" mechanism from the schiffradio.com to get the MP3s from fetch.noxsolutions.com

The bottom-line is:
This *could* be code corrected but may involve a tad bit more than just a passing fancy with bash.
The MP3s don't appear to be stored on [www.schiffradio.com](www.schiffradio.com)

HTH explain what may be going on there.

---

### Post by Lampi on 2011-11-23
@habitual: it's [http://nox.mp3.lee.miisolutions.net/schiff](http://nox.mp3.lee.miisolutions.net/schiff)

so to dump it try sth like this

```
wget -O "The_Peter_Schiff_Show_-_`date`.mpeg" http://nox.mp3.lee.miisolutions.net/schiff
```

hit ctrl+c to stop it once it's done

---

### Post by Habitual on 2011-11-23
good eye Lampi!

---

### Post by Lampi on 2011-11-23
maybe there is some better way to download it than wget? this stream might be some sort of endless loop, don't know a better way to cope with that then hit ctrl+c once it's done and restarts the loop ... since it's pure mpeg audio you can listen to it (even seek forward) while it is dumping

---


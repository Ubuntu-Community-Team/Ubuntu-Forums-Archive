---
title: "sed | awk | sed the propper way to do it please."
date: 2011-08-30
forum: Programming Talk
---

### Post by nothingspecial on 2011-08-30
So, if I do this to remove everything I've installed since the original install

```
sudo apt-get remove $(sed -e 's/([^()]*)//g' /var/log/apt/history.log | sed 's/ ,//g' | awk '!/^Start|^Commandl|^End|^Upgrade:|^Error:/' | sed 's/^Install://g')
```

it works :)

Yes, I can construct something, but I know that all these pipes are due to my limited understanding of the tools I'm using. 

How do I combine this into one (I would think) awk implementation.

I would appreciate an explanation along with an answer.

Cheers

---

### Post by Habitual on 2011-08-30
nothingspecial:

any answer I can't find here at UbFo, I surf over to [http://www.unix.com/shell-programming-scripting/](http://www.unix.com/shell-programming-scripting/) and get some serious help seriously *FAST*.

HTH.

---

### Post by stylishpants on 2011-08-30
First of all, you're only parsing one history file.  There are many, and most of them are gzipped.  Start with some code to dump out the contents of all history files.

Note that the zcat -f option is needed to force zcat to print "history.log", which is not gzipped like the rest.
```
zcat -f /var/log/apt/history.log*
```
The output of this piece is every line from every file matching the glob.
```
bob@cob:~$ zcat -f /var/log/apt/history.log* | head 

Start-Date: 2011-08-25  15:48:15
Upgrade: libwebkit-1.0-common:amd64 (1.2.5-0ubuntu0.10.10.1, 1.2.7-0ubuntu0.10.10.1), chromium-browser:amd64 (14.0.835.94~r96725-0ubuntu1~ucd~beta1~maverick, 14.0.835.109~r97804-0ubuntu1~ucd~beta1~maverick), thunderbird:amd64 (6.0~b3+build1+nobinonly-0ubuntu0.10.10.1~mtn1, 7.0~b1+build1+nobinonly-0ubuntu0.10.10.1~mtn1), foomatic-filters:amd64 (4.0.5-0ubuntu3, 4.0.5-0ubuntu3.1), firefox-branding:amd64 (3.6.18+build2+nobinonly-0ubuntu0.10.10.2, 3.6.20+build1+nobinonly-0ubuntu0.10.10.1), firefox:amd64 (3.6.18+build2+nobinonly-0ubuntu0.10.10.2, 3.6.20+build1+nobinonly-0ubuntu0.10.10.1), chromium-browser-l10n:amd64 (14.0.835.94~r96725-0ubuntu1~ucd~beta1~maverick, 14.0.835.109~r97804-0ubuntu1~ucd~beta1~maverick), xulrunner-1.9.2:amd64 (1.9.2.18+build2+nobinonly-0ubuntu0.10.10.1, 1.9.2.20+build1+nobinonly-0ubuntu0.10.10.1), libwebkit-1.0-2:amd64 (1.2.5-0ubuntu0.10.10.1, 1.2.7-0ubuntu0.10.10.1), chromium-codecs-ffmpeg-extra:amd64 (14.0.835.94~r96725-0ubuntu1~ucd~beta1~maverick, 14.0.835.109~r97804-0ubuntu1~ucd~beta1~maverick), firefox-gnome-support:amd64 (3.6.18+build2+nobinonly-0ubuntu0.10.10.2, 3.6.20+build1+nobinonly-0ubuntu0.10.10.1)
End-Date: 2011-08-25  15:48:57

Start-Date: 2010-10-12  15:58:07

```
Next you are finding all lines that start with Install:, then removing the commas and everything in brackets.  awk would be perfectly fine, personally I prefer perl:
```
... | perl -ne 'next unless s/^Install://; s/\(.*?\)//g; s/ ,//g ; print'
```
This allows you to put all your substitution commands inside one process, and the first one can double as a check for the lines you want.
The output of this part is whitespace and newline separated lists of packages:

```
 linux-image-2.6.32-24-generic linux-headers-2.6.32-24-generic linux-headers-2.6.32-24 
 stellarium-data stellarium 
 openvpn-blacklist libpkcs11-helper1 liblzo2-2 openssl-blacklist openvpn 
 read-edid 
 sharutils 
 libtime-modules-perl 
 canonical-census 
 python-smartpm smartpm-core 
 gparted:amd64 
 libnokogiri-ruby:amd64 libnokogiri-ruby1.8:amd64 
 libxslt1-dev:amd64 
 autofs5:amd64 
 convmv:amd64 
 enca:amd64 
 linux-image-2.6.35-30-generic:amd64 linux-headers-2.6.35-30-generic:amd64 linux-headers-2.6.35-30:amd64 
 rake:amd64 

```

Lastly you are feeding that long package list into and apt-get remove command.  You want apt-get to see the entire list at once so it can plan out the entire package removal optimally for speed.

I'm using xargs to feed that package list into apt-get, this allows me to see the entire command by using the --verbose option for debugging.  xargs also cleans up the newlines from the input.

Another useful option to know is that apt-get remove will do a dry run if you give it the "-s" option.  It will print out exactly what it would remove, and any errors that it sees with that list, but won't actually do the remove.  This is good for testing.

I'd suggest you try it with -s first, then remove that when things look good.
```

... | xargs --verbose sudo apt-get -s remove 

```

That's it.  

```
zcat -f /var/log/apt/history.log* | perl -ne 'next unless s/^Install://; s/\(.*?\)//g; s/ ,//g ; print' | xargs --verbose sudo apt-get -s remove 
```

On my system, it doesn't work though, because it is trying to remove some packages that are no longer there.  The original command would have this problem too, for a system that has been in use for some time.

This is solveable but I'm out of time for now.

---

### Post by kurum! on 2011-08-30
So, here's doing it with only one awk command
```

awk '!/^Start|^Commandl|^End|^Upgrade:|^Error:/ { gsub( /\([^()]*\)/ ,"" );gsub(/ ,/," ");sub(/^Install:/,""); print}' history.log

```

---

### Post by nothingspecial on 2011-09-01
@stylishpants

Thank's for raising those 2 issues about the gzipped history and stuff that's been installed but now removed.

As the logs also contain everything that has been removed, I suppose one could generate a list of removed packages in much the same way and after comparison arrive at a list of installed packages that are still present.

I should be able to manage that......

.....when I don't have a deadline in 12 hours for a really long boring report. :P

Thanks to both of you.

---


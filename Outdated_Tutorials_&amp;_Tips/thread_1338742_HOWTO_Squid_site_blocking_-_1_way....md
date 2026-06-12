---
title: "HOWTO: Squid site blocking - 1 way..."
date: 2009-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Barriehie on 2009-11-26
**[color="red"]See my last post, scripts have been updated...[/color]**

---

### Post by Barriehie on 2009-11-27
**[color="red"]See my last post, gawk routines have been added...[/color]**

---

### Post by Barriehie on 2010-01-02
**Thanks to [color="red"][b]cariboo907**[/color] for moving this thread to the appropriate forum. :)[/b]

*Changelog:*
[color="red"]Edit: 1-4-'10[/color]  Incorporated another download and removed all but one of the logging routines.  These were there for troubleshooting.  Squid still logs it's startup.
[color="red"]Edit: 1-5-'10[/color] Added another download file...

The purpose of this HowTo is block retrievals of unwanted sites in your browser.  I know unwanted is a broad term but using the lists provided via several sites I haven't been troubled in my browsing experience.  We're going to block sites using **squid**, it's in the repos and I'm using version **2.6.STABLE18** and am having no issues with it.

So, install squid via the CLI or Synaptic, whichever you're more comfortable with.  I won't go into the GUI so to install from the CLI, (Applications > Accessories > Terminal)```
sudo apt-get install squid
```

Right now it won't do anything for blocking, you have to have what are known as '**action control lists**'.  These are abbreviated in the squid.conf file by **acl**  The directory that these files are in is hardcoded in the .conf file so I can't give you an install script.  I use $HOME/squid, (no comma!).  So, via the terminal or your file mgr. create your **$HOME/squid** directory.

Now we have to edit the **squid.conf** file which is, for my version at least, located in **/etc/squid/squid.conf**  I've found it best when editing configuration files to comment the original line and then put mine underneath it.  Also a good idea, to find them later, to put another commented line ABOVE those two with your initials or some such unique word on it.  The squid.conf file is heavily documented so it wouldn't hurt to take some time and read through it before doing anything!

My squid.conf looks like this:
```

#
##########################################
# My file of blacklisted/whitelisted sites
#
# **Edit the string between the quotes to reflect your squid path!**
acl mywhitelist dstdomain "**/home/barrie/squid/mywhitelist**"
http_access allow mywhitelist
#
acl blacklist-domains dstdomain "**/home/barrie/squid/domains**"
http_access deny blacklist-domains
#
acl blacklist-urls dstdomain "**/home/barrie/squid/urls**"
http_access deny blacklist-urls
#
acl myblacklist dstdomain "**/home/barrie/squid/myblacklist**"
http_access deny myblacklist
#
acl badregex url_regex -i "**/home/barrie/squid/badregex**"
http_access deny badregex
#
http_access allow localhost

#
# Allow electricsheep screensaver
#
acl Safe_ports port 37669	# Azureus - .sheep

#
# Speed up shutdown - Default is 30 seconds.
#
shutdown_lifetime 1 second

```

My badregex file looks like this: (simple but working on it...)
[color="Green"]~/squid/badregex[/color]
```

.*facebook.*
.*adserving.*
.*advertising.*
.*amateurmatch.*
.*myspace.com
.*/ads/.*
.*/banners/.*
.*doubleclick.*

```


Now you're setup to block the domains/urls listed in the acl's so we have to retrieve them.  This is done via **blupdate.sh**, residing in $HOME/bin and called via /etc/crontab once a week.  The main contributor to these list(s) only updates once a week and has requested the file be downloaded once a week.  Violators will have their IP blocked so please respect that.  The **/etc/crontab** entry looks like this:

Note that STDOUT and STDERR are redirected to provide 2 things:
1) An indication that cron called the script and
2) A log of what happened.

[color="Green"]/etc/crontab[/color]
```

#
# Update my blacklist(s) once a week @ 0100 hours on Friday.
#
# m h dom mon dow user	command
0 1 * * 5 root /home/barrie/bin/blupdate.sh 1>/home/barrie/Desktop/bl1.log 2>/home/barrie/Desktop/bl2.log

```


Here is the **blupdate.sh** script.  Read through it carefully to check the paths being used.  You WILL have to change some items where the bold indications are.

[color="green"]~/bin/blupdate.sh[/color]
```

#!/bin/bash
#
# Script to automate blacklist download and squid incorporation.
# Currently, 1-4-'10, blocking about 1.6 million sites.
#
# Blacklist #1 is downloaded from http://www.shallalist.de/, please
# visit the site and read the usage policy.
#
# Blacklist #2 is downloaded from http://zelut.org/, please
# visit the site and read the usage policy.
#
# Blacklist #3 is downloaded from http://someonewhocares.org/, please
# visit the site and read the usage policy.
#
#
# This script, and others published by me in this thread,
# are released into the public domain and authorized for
# non-commercial, not-for-profit use, providing all comments
# are left intact, per the provider(s) of the downloads.
#
# Usage: blupdate.sh                    # **Must be run as root**
#

#
# **READ/EDIT THIS NEXT LINE !!!**
#
WORKDIR="/home/barrie/squid"
cd $WORKDIR

#
# Get blacklist #1
#
wget -t 25 -O /home/barrie/squid/shallalist.tar.gz [http://www.shallalist.de/Downloads/shallalist.tar.gz](http://www.shallalist.de/Downloads/shallalist.tar.gz) 1>/dev/null 2>/dev/null

#
# Get blacklist #2 and process for squid integration.
#
wget -t 25  -O ./hosts2 [http://zelut.org/projects/misc/hosts](http://zelut.org/projects/misc/hosts) 1>/dev/null 2>/dev/null
# Remove the comments.
gawk '{ if( $0 ~ /^127.0.0.1.*$/) { print $2 } }' $WORKDIR/hosts2 > $WORKDIR/hosts2.use
# Convert to *nix line endings.
gawk '{ sub(/\r$/, "");1 }' $WORKDIR/hosts2.use > $WORKDIR/domains2
rm $WORKDIR/hosts2
rm $WORKDIR/hosts2.use

#
# Get blacklist #3 and process for squid integration.
#
wget -t 25 -O hosts3 [http://someonewhocares.org/hosts/hosts](http://someonewhocares.org/hosts/hosts) 1>/dev/null 2>/dev/null
# Remove the comments.
gawk '{ if( $0 ~ /^127.0.0.1.*$/) { print $2 } }' $WORKDIR/hosts3 > $WORKDIR/hosts3.use
# Convert to *nix line endings.
gawk '{ sub(/\r$/, "");1 }' $WORKDIR/hosts3.use > $WORKDIR/domains3
rm $WORKDIR/hosts3
rm $WORKDIR/hosts3.use

#
# Extract blacklist #1
#
tar -xvvf /home/barrie/squid/shallalist.tar.gz 1>$WORKDIR/tar-output 2>/dev/null

#
# Stop squid
#
/etc/init.d/squid stop 1>/dev/null 2>/dev/null

#
# Remove the old files
#
rm $WORKDIR/domains
touch $WORKDIR/domains
#
rm $WORKDIR/urls
touch $WORKDIR/urls

#
# Process the tar output to concatenate the domains and urls.
#
echo '#!/bin/bash' > $WORKDIR/catfiles.sh
gawk -f ptar.gawk tar-output >> $WORKDIR/catfiles.sh
chmod +x $WORKDIR/catfiles.sh
$WORKDIR/catfiles.sh && sleep 0
rm $WORKDIR/catfiles.sh

#
# Remove the trailing space.
#
gawk -f ntspace.gawk domains > ./domains.nts
mv ./domains.nts ./domains

#
# Combine the hosts files.
#
cat $WORKDIR/domains $WORKDIR/domains2 $WORKDIR/domains3 > $WORKDIR/allbad
mv $WORKDIR/allbad $WORKDIR/domains
rm $WORKDIR/domains2
rm $WORKDIR/domains3

#
# Sort and remove any duplicates.
#
sort -f -i $WORKDIR/domains > $WORKDIR/domains.s
uniq -i -u $WORKDIR/domains.s > $WORKDIR/domains.u
mv $WORKDIR/domains.u $WORKDIR/domains
rm $WORKDIR/domains.s

#
# Remove the trailing space.
#
gawk -f ntspace.gawk urls > ./urls.nts
mv ./urls.nts ./urls

#
# Remove the duplicates.
#
sort -f -i $WORKDIR/urls > $WORKDIR/urls.s
uniq -i -u $WORKDIR/urls.s > $WORKDIR/urls.u
mv $WORKDIR/urls.u $WORKDIR/urls
rm $WORKDIR/urls.s

#
# **Change ownership to your username.**
#
chown barrie:barrie $WORKDIR/domains
chown barrie:barrie $WORKDIR/urls


#
# Start squid.
#
/etc/init.d/squid start 1>$WORKDIR/Squid-start$(date +%m%d%y) 2>>$WORKDIR/Squid-start$(date +%m%d%y)
# **Change ownership...**
chown barrie:barrie $WORKDIR/Squid-start$(date +%m%d%y)

#
# Send email.           **Change to your local email.**
#
if [ -e /var/run/dovecot/master.pid ]; then
    echo "Blacklist/Whitelist updated." | sendmail barrie@localhost
fi

#
# Done
#
exit 0

```

This script removes the trailing spaces that sometimes exist.

[color="green"]~/squid/ntspace.gawk[/color]
```

#!/usr/bin/gawk
##
## ntspace.gawk
## 
## Purpose: Strip trailing space from file(s)
##
## Usage: gawk -f ntspace.gawk <FileIn> > <FileOut>
##

BEGIN { }

{

    if( $0 ~ /^.* $/ ) {
        sub( / *$/, "", $0)
    } else {
    print $0
    }

}

END { }

```

This script process' the output of tar to generate the domain and url files.

[color="green"]~/squid/ptar.gawk[/color]
```

#!/usr/bin/gawk
#
# Process the tar-output file to generate a shell
# script to combine the domain and url files.
#
# Usage: echo '#!/bin/bash' > ./catfiles.sh && gawk -f ptar.awk tar-output >> catfiles.sh; chmod +x ./catfiles.sh
#

BEGIN { FS="//n"; IGNORECASE=1 } {

  for ( i=1; i<=NR; i++) {

      #
      # Strip out the domain lines
      #
      if ( $i ~ /.*\/domains$/ ) {
          sub(/.* ??:?? /, "cat ./", $i)
          print $(i) " >> ./domains"
      }

      #
      # Strip out the url lines
      #
      if ( $i ~ /.*\/urls$/ ) {
          sub(/.* ??:?? /, "cat ./", $i)
          print $(i) " >> ./urls"
      }
  }

}

```

Now, to make all this work run blupdate.sh via sudo.
```

sudo blupdate.sh

```

Depending on your internet connection and server activity it may take several minutes for the script to complete.  Once completed you now need to tell your browser to use the squid proxy for accessing the internet.  I'm only going to explain FF here because it's part of a standard install.

In FF, Edit > Preferences > Advanced > Network > Settings and fill in the blanks to look like the attached png.

You're set!

Barrie

Edit: As of 1/6/'10 running wc --lines ./domains ./urls ./myblacklist yields...
```

 1427620  ./domains
  178751  ./urls
       2  ./myblacklist
 **[color="Red"]1,606,373[/color]**  total

```

---


---
title: "Automated Torrent Downloader in Bash"
date: 2012-03-07
forum: Programming Talk
---

### Post by mastermindg on 2012-03-07
I've put together a script that downloads torrents from a torrent portal based on search criteria. I wanted to emulate what Hulu does for me but on my torrent site. I've got Transmission setup to auto-start downloads that are in ~/Downloads.

I've included the script below. I've removed pertinent info like the site name and my login info but it works fine with it in place. If anybody has any suggestions on how I can improve the flow-control or readability of this script that would be very helpful. Thanks.


```
#!/bin/bash
# 2012 mastermindg
# Automatically downloads torrent file from a torrent portal
# for use by Transmission

# Set variables
today=$(date '+%Y-%m-%d')
#today="2012-03-06"
yesterday=$(date -d 'yesterday' '+%Y-%m-%d')
site=mysite.com
cookie=/home/$(whoami)/.cookies/$site
searchterm=$1
username=myusername
password=mypassword
#searchterm=american.dad

cd /home/$(whoami)/torrentdl

#### Set functions

function fini {
# Make sure we've got a valid date first
grep $today $searchterm.html >> /dev/null
if [ $? -eq 1 ]
then
	echo "Nothing with today's date found"
	cleanup
	exit
fi

# Strip search page
sed -n '/1234/,/\/table>/p' $searchterm.html > $searchterm.stripped.html
echo "Stripped down to table"

# Stripped further
sed -e '1d' $searchterm.stripped.html > $searchterm.stripped2.html
echo "Removed first line"

cat $searchterm.stripped2.html | sed '/<!--/d' | sed '/-->/d' | sed -e 's/^[ \t]*//' | awk '{print $3}' > $searchterm.stripped3.html
echo "Worked everything else"

# Search for entries with todays date
cat $searchterm.stripped3.html | grep -C 5 "$today" > $searchterm.todays.html
echo "Got entries for today"

# Search for files less than 200 MB
lineno=$(cat $searchterm.todays.html | grep -n MB | sed 's/>/:/' | awk -F":" ' $3 < 200 ' | sed q | awk -F":" '{print $1}')
echo "Found match on line "$lineno

# Print download link
# Download link is 6 lines up from size field on this site
linklineno=$(echo $(($lineno-6)))
link=$(sed -n "$linklineno"'p' $searchterm.todays.html | sed "s/download.php/http:\/\/www.$site\/download.php/" | sed 's/.*href="\(.*\)".*/\1/')
echo $link

# Download the torrent and copy for download
echo "Downloading torrent"
wget -bc --load-cookies $cookie -O $searchterm.$today.torrent $link
sleep 2
cp $searchterm.$today.torrent /home/$(whoami)/Downloads
}

function cleanup {
rm $cookie;
rm $searchterm*html
rm wget-log*
}



##### End Set functions

#Verify Torrent
if [ -e $searchterm.$today.torrent ] 
then
	echo "Torrent already exists"
	exit
else
	echo "Torrent doesn't exist"
fi


#Fetch cookie for use 
echo "Fetching cookie"
if [ -e $cookie ]
then
	echo "Old cookie still there...deleting"
	rm $cookie
fi
wget -bc --save-cookies ~/.cookies/$site --post-data "username=$username&password=$password" -O - http://www.$site/takelogin.php > /dev/null
#Verify cookie is valid
sleep 2
grep -q www.$site $cookie > /dev/null
if [ $? -eq 0 ]
then
	echo "Cookie is valid"
else 
	"Cookie is INVALID"
	cleanup
	exit
fi

# Check for search page
if [ -e $searchterm.html ]
then
	echo "Search page exists...skipping"
	cleanup
	exit
else
	echo "Fetching search page"
	wget -bc --load-cookies $cookie -O $searchterm.html http://www.$site/browse.php?search=$searchterm&cat=7
	sleep 2
	# Verify search page is valid
	if grep -q 1234 $searchterm.html
	then
		echo "Search page is valid"
		fini
	else
		echo "Search page is INVALID"
		cleanup		
		exit
	fi
fi
```

---


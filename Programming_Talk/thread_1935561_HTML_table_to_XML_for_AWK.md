---
title: "HTML table to XML for AWK"
date: 2012-03-04
forum: Programming Talk
---

### Post by mastermindg on 2012-03-04
I'm attempting to create a script that will automatically download new torrents based on search criteria. I'm up to the point where I've scraped the results page and need to filter the results to give me the most recent listing.

The format is simple:

<TABLE>
<TR><TD>TYPE</TD><TD>NAME</TD><TD>LINK</TD><TD>DATE</TD></TR>
<TR><TD>SCIFI</TD><TD>AI</TD><TD>AI.TORRENT</TD><TD>021212<TD></TR>
<TR><TD>SCIFI</TD><TD>AI</TD><TD>BC.TORRENT</TD><TD>022912<TD></TR>
</TABLE>

I want to be able to extract the link in rows where the date is within the last 24 hours. I suspect the easiest way to do this would be to convert to xml where the data would be tagged better.

How do I convert this tablet to XML?

---

### Post by Vaphell on 2012-03-04
quick and dirty grep+sed
```
today=$(date '+%m%d%y')
yesterday=$(date -d 'yesterday' '+%m%d%y')
grep -Pi '<td>('$today'|'$yesterday')</td>' index.html | sed -r 's_<TR><TD>(.*)</TD><TD>(.*)</TD><TD>(.*)</TD><TD>(.*)</TD></TR>_type:\1 name:\2 link:\3 date:\4_'
```

example:
```
$ echo "<TABLE>
<TR><TD>TYPE</TD><TD>NAME</TD><TD>LINK</TD><TD>DATE</TD></TR>
<TR><TD>SCIFI</TD><TD>AI</TD><TD>AI.TORRENT</TD><TD>021212</TD></TR>
<TR><TD>SCIFI</TD><TD>XXX</TD><TD>XXX.TORRENT</TD><TD>021912</TD></TR>
<TR><TD>SCIFI</TD><TD>BC</TD><TD>BC.TORRENT</TD><TD>030312</TD></TR>                                                                    
<TR><TD>SCIFI</TD><TD>ZZZ</TD><TD>ZZZ.TORRENT</TD><TD>030412</TD></TR> 
</TABLE>" | grep -Pi '<td>('$today'|'$yesterday')</td>' | sed -r 's_<TR><TD>(.*)</TD><TD>(.*)</TD><TD>(.*)</TD><TD>(.*)</TD></TR>_type:\1 name:\2 link:\3 date:\4_'

type:SCIFI name:BC link:BC.TORRENT date:030312                                                                    
type:SCIFI name:ZZZ link:ZZZ.TORRENT date:030412 

```

---

### Post by Khayyam on 2012-03-04
I'm not sure I understand the question ... are you looking to parse it or convert it? If you want to convert to xml then you can use [htmltidy]("http://tidy.sourceforge.net/") to do this, or [html2text]("http://www.aaronsw.com/2002/html2text/") if you want to strip out the data.

If your looking to parse the data in some way then it depends on how you want to use that data, which particular fields, and how you want to further process them.

Vaphell provided some good pointers, but for the basic data something like the following can be used

```
sed -n '/^$/!{s/<[^>]*>/ /g;p;}' input.txt | column -t
```This will output the following table

```
TYPE   NAME  LINK        DATE
SCIFI  AI    AI.TORRENT  021212
SCIFI  AI    BC.TORRENT  022912
```We can use awk to parse out fields based on a value ...

```
sed -n '/^$/!{s/<[^>]*>/ /g;p;}' input.txt | awk -v date="022912" '{if ($4 == date) {print $3}}'
```

We can use 'date' in a similar manner to what Vaphell is doing above ... the following will output all the 3rd fields ("LINK") that match from dates from yesterday to today.

```
sed -n '/^$/!{s/<[^>]*>/ /g;p;}' input.txt | awk -v yday="$(date -d yesterday +%m%d%y)" -v tday="$(date +%m%d%y)" '{if($4>=yday && $4<=tday) {print $3}}'
```You could use further variables to match "TYPE", "NAME", etc if you so wish

That should give you some idea of how to proceed ...

HTH ... khay

---

### Post by mastermindg on 2012-03-05
Thanks a lot guys! This is going to get me where I need to be and save me a lot of time. 

:popcorn:

---

### Post by Khayyam on 2012-03-05
> **mastermindg said:**
> Thanks a lot guys! This is going to get me where I need to be and save me a lot of time.

Your welcome ... this can be quite easily tied together in some (bash) script:

```
TOR_LIST=$(sed -n '/^$/!{s/<[^>]*>/ /g;p;}' input.txt | \
awk -v yday="$(date -d yesterday +%m%d%y)" -v tday="$(date +%m%d%y)" '{ORS=" "; if($4>=yday && $4<=tday) {print $3}}')

torrentclient ${TOR_LIST}
```

Note that 'ORS' (output record seperator) is set to 'space', so all records are output on one line, if you need to provide one item per line the ORS can be removed and you would the set IFS=$'\n' and use a for loop to iterate through the list.

```
IFS=$'\n'
TOR_LIST=$(sed -n '/^$/!{s/<[^>]*>/ /g;p;}' input.txt | \
awk -v yday="$(date -d yesterday +%m%d%y)" -v tday="$(date +%m%d%y)"  '{if($4>=yday && $4<=tday) {print $3}}')

for i in ${TOR_LIST} ; do
    ....
done
```

best ... khay

---


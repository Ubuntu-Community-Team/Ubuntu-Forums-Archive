---
title: "Bash process optimization"
date: 2014-06-20
forum: Programming Talk
---

### Post by fprietog on 2014-06-20
Hello,

Please, I want suggestions to speed-up a little shell-script I made. I know how to program but I'm just learning how to use bash, so I think some of the commands I use can be improved. That's why I'm calling for help.

This program's goal is very simple; I want a process that changes the file [FONT=courier new]/etc/hosts[/FONT] filling it with a merged hosts file downloaded from several webs that provides a black-list of known "bad" webs (related to spyware, malware, ad's, porn, Justin Bieber's, etc...). These webs (or hosts entries) will be checked before resolving DNS and will be redirected to IP 127.0.0.1 (loopback) in order to not connect to them at all (the [FONT=courier new]/etc/hosts[/FONT] file will be used as a kind of [FONT=courier new]/dev/null[/FONT] for webs). 

It's something I'm using in my android phone & tablet with a program called AdAway, that I find very useful for a personal PC too.

So I start with the idea of having:[INDENT]- A [FONT=courier new]/etc/hosts[/FONT] file to be replaced.[/INDENT]
[INDENT]- A list of url's where I can download a hosts file filled with these "bad" entries. I want to merge all these hosts files downloaded into one "big" file sorted without duplicates.[/INDENT]
[INDENT]- A list of entries that I want to add to these downloaded file (my personal "black-list" of webs).[/INDENT]
[INDENT]- A list of entries that I want to remove from these downloaded file (my personal "white-list" of webs).[/INDENT]
[INDENT]- A list of entries that will be always the first to be used for some cases (mainly the default [FONT=courier new]/etc/hosts[/FONT] file with the loopback direction and my PC host name).[/INDENT]


These are the files:

- file "[FONT=courier new]hosts-urls.txt[/FONT]"; contains the list of url's where I want to download the hosts files:
```
[FONT=courier new]http://adblock.gjtech.net/?format=hostfilehttp://hosts-file.net/ad_servers.asp
http://pgl.yoyo.org/adservers/serverlist.php?hostformat=hosts&showintro=0&mimetype=plaintext
http://securemecca.com/Downloads/hosts.txt
http://someonewhocares.org/hosts/hosts
http://sysctl.org/cameleon/hosts
http://winhelp2002.mvps.org/hosts.txt
http://www.malwaredomainlist.com/hostslist/hosts.txt
https://adaway.org/hosts.txt[/FONT]
```
**Note:** there must be an end of line character at the end of the file (a blank line).

- file "[FONT=courier new]hosts-blacklist.txt[/FONT]"; contains the list of entries that I want to add to these downloaded file (my personal "black-list" of webs):
```
[FONT=courier new]127.0.0.1 microsoft.com
127.0.0.1 [www.microsoft.com]("http://www.microsoft.com")[/FONT]
```
**Note:** there must be an end of line character at the end of the file (a blank line).

- file "[FONT=courier new]hosts-whitelist.txt[/FONT]"; contains the list of entries that I want to remove from these downloaded file (my personal "white-list" of webs).
```
[FONT=courier new]127.0.0.1 rarbg.com
127.0.0.1 [www.rarbg.com]("http://www.rarbg.com")
127.0.0.1 rover.ebay.com[/FONT]
```
**Note:** there must be an end of line character at the end of the file (a blank line).

- file "[FONT=courier new]hosts-default.txt[/FONT]"; it's just my default [FONT=courier new]/etc/hosts[/FONT] file, to be preserved:
```
[FONT=courier new]127.0.0.1 localhost
127.0.0.1 loopback
127.0.1.1 MY_MACHINE
::1     ip6-localhost 
::1     ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters[/FONT]
```


And this is the program (called "[FONT=courier new]change_hosts.sh[/FONT]"). It resides in the folder "[FONT=courier new]~/Programas/change_hosts[/FONT]" along with the above files. It needs to be executed with root to be allowed to replace [FONT=courier new]/etc/hosts[/FONT] file (unless you give [FONT=courier new]/etc/hosts[/FONT] file write permission to the user/group that runs the process).

```
[FONT=courier new]#!/bin/bash
cd ~/Programas/change_hosts
if [ -e ./hosts-temp.txt ]; then[INDENT]DATE1=`date -r ./hosts-temp.txt +%y%m%d`
DATE2=`date +%y%m%d`[/INDENT]
fi 
if [ ! -e ./hosts-temp.txt ] || [ $DATE1 -lt $DATE2 ]; then[INDENT]touch ./hosts-temp.txt
wget -i ./hosts-urls.txt -O ./hosts-temp.txt
cat ./hosts-blacklist.txt >> ./hosts-temp.txt
sed -i 's/#.*//' ./hosts-temp.txt
sed -i 's/^0\.0\.0\.0/127\.0\.0\.1/' ./hosts-temp.txt
sed -i 's/\t/ /g;s/ /#/;s/ //g;s/#/ /g' ./hosts-temp.txt
sort -i -u ./hosts-temp.txt -o ./hosts-temp.txt
cat ./hosts-whitelist.txt | while read line; do[/INDENT]
[INDENT=2]HOST=$(echo ${line})
sed -i s/^"$HOST"/\#"$HOST"/g ./hosts-temp.txt[/INDENT]
[INDENT]done
cp /etc/hosts ./hosts.bak
cat ./hosts-default.txt ./hosts-temp.txt > /etc/hosts
rm ./hosts-temp.txt[/INDENT]
fi[/FONT]
```


[B]
Explanation of the program line by line.[/B]

Magic number for bash:
```
[FONT=courier new]#!/bin/bash[/FONT]
```

Make sure I'm using the PWD where I got the program and all these files during all the process:
```
[FONT=courier new]cd ~/Programas/change_hosts[/FONT]
```

This part is done in order to allow the program to be periodically executed using [FONT=courier new]cron[/FONT] daemon. It checks the existence of a temporary file called "[FONT=courier new]hosts-temp.txt[/FONT]" that will be the file we used to download the hosts files and merge them. If it exists it should means two things:
  - the previous execution of the program was wrong and ended without deleting the file.
  - or the program is running in this precise moment in another instance (the typical cron problem when you have it stopped for several days...).
If that "[FONT=courier new]hosts-temp.txt[/FONT]" file exists I take it's modification date and the system date in order to know it it's and old file or not:
```
[FONT=courier new]if [ -e ./hosts-temp.txt ]; then[INDENT]DATE1=`date -r ./hosts-temp.txt +%y%m%d`
DATE2=`date +%y%m%d`[/INDENT]
fi[/FONT]
```

The program runs only if the "[FONT=courier new]hosts-temp.txt[/FONT]" file doesn't exists or it's date is less than today's date: 
```
[FONT=courier new]if [ ! -e ./hosts-temp.txt ] || [ $DATE1 -lt $DATE2 ]; then[/FONT]
```

First, create the initially empty "[FONT=courier new]hosts-temp.txt[/FONT]" file:
  ```
[FONT=courier new]touch ./hosts-temp.txt[/FONT]
```

Fill that "[FONT=courier new]hosts-temp.txt[/FONT]" file with all the hosts files to download:
```
[FONT=courier new]wget -i ./hosts-urls.txt -O ./hosts-temp.txt[/FONT]
```

Add the entries of "[FONT=courier new]hosts-blacklist.txt[/FONT]" file at the end of the "[FONT=courier new]hosts-temp.txt[/FONT]" file:
```
[FONT=courier new]cat ./hosts-blacklist.txt >> ./hosts-temp.txt[/FONT]
```

Now we have a "[FONT=courier new]hosts-blacklist.txt[/FONT]" filled with all the entries of all the downloaded hosts files, with a lot of commentaries and dupes. We'll try to clean it using sed to replace text. First we deleted the commentaries that are everything at the right of a # character (included). We replace that info with "nothing". For instance, the line:
[FONT=courier new]127.0.0.1 [www.example.com]("http://www.example.com") # This is an example[/FONT]
Will end in a line:
[FONT=courier new]127.0.0.1 [www.example.com]("http://www.example.com") [/FONT]
```
[FONT=courier new]sed -i 's/#.*//' ./hosts-temp.txt[/FONT]
```

Some of the downloaded hosts files uses the IP 0.0.0.0 instead of 127.0.0.1 for loopback, don't know exactly why. We'll change all the 0.0.0.0 redirections to 127.0.0.1 to make it more readable:
```
[FONT=courier new]sed -i 's/^0\.0\.0\.0/127\.0\.0\.1/' ./hosts-temp.txt[/FONT]
```

And now we try to clean a bit the remaining lines. Since some of the lines are exactly the same but there should be a tab separating IP and entry instead of using blank(s) we will:[INDENT]- replace all tabs (\t) by a blank character.[/INDENT]
[INDENT=2][FONT=courier new]s/\t/ /g;[/FONT][/INDENT]
[INDENT]- replace only the first blank found in any line by a # character (character that we know is not used in the file because we have eliminated it before). this is done in order to delete next all the rest of blanks but preserving the original separation from IP and entry.[/INDENT]
[INDENT=2][FONT=courier new]s/ /#/[/FONT][/INDENT]
[INDENT]- replace all remaining blanks with "nothing".[/INDENT]
[INDENT=2][FONT=courier new]s/ //g[/FONT][/INDENT]
[INDENT]- and replace the character # with a blank to separate IP and entry as expected.[/INDENT]
[INDENT=2][FONT=courier new]s/#/ /g[/FONT][/INDENT]
- Everything in one line:
```
[FONT=courier new]sed -i 's/\t/ /g;s/ /#/;s/ //g;s/#/ /g' ./hosts-temp.txt[/FONT]
```

And now we delete the duped lines and sort the entries of the file:
```
[FONT=courier new]sort -i -u ./hosts-temp.txt -o ./hosts-temp.txt[/FONT]
```

**Now we will replace the entries we want to allow using the entries from our "**[FONT=courier new]hosts-whitelist.txt[/FONT][B]" file in order to allow them. For instance, we will replace:
[/B][FONT=courier new]127.0.0.1 rarbg.com[/FONT][B]
With
[/B][FONT=courier new]#127.0.0.1 rarbg.com[/FONT][B]
That is a commented line so it will not be used.
The problem is that I only found how to do this using sed checking the input file line by line for every line of "[/B][FONT=courier new]hosts-whitelist.txt[/FONT]**" file I want to replace. It means that if my white-list has 100 entries the process will read the whole "**[FONT=courier new]hosts-temp.txt[/FONT]**" file 100 times to do all the replaces one by one... This is the part I want to improve but I don't know how...**
  ```
[FONT=courier new]cat ./hosts-whitelist.txt | while read line; do[INDENT]HOST=$(echo ${line})
sed -i s/^"$HOST"/\#"$HOST"/g ./hosts-temp.txt[/INDENT]
done[/FONT]
```

We make a backup of the [FONT=courier new]/etc/hosts[/FONT] file we are going to replace:
```
[FONT=courier new]cp /etc/hosts ./hosts.bak[/FONT]
```

Then replace [FONT=courier new]/etc/hosts[/FONT] file with the contents of the "[FONT=courier new]hosts-default.txt[/FONT]" file at the beginning (the entries we want to preserve) and the "[FONT=courier new]hosts-temp.txt[/FONT]" file at the end:
```
[FONT=courier new]cat ./hosts-default.txt ./hosts-temp.txt > /etc/hosts[/FONT]
```

And delete the "hosts-temp.txt" file and finish:
  ```
[FONT=courier new]rm ./hosts-temp.txt
[/FONT][FONT=courier new]fi[/FONT]
```


Suggestions welcome :)


Thanks and best regards.

---

### Post by sisco311 on 2014-06-20
> **fprietog said:**
> [B]
The problem is that I only found how to do this using sed checking the input file line by line for every line of "[/B][FONT=courier new]hosts-whitelist.txt[/FONT]**" file I want to replace. It means that if my white-list has 100 entries the process will read the whole "**[FONT=courier new]hosts-temp.txt[/FONT]**" file 100 times to do all the replaces one by one... This is the part I want to improve but I don't know how...**


Hi, fprietog!

You can use the** comm**(1) command. For more details and other options check out BashFAQ 036 (link in my signature).

---

### Post by steeldriver on 2014-06-20
Wouldn't it be easier to start with a clean slate and simply construct a list of unique FQDNs from the downloaded lists, and then spit them back out in the format that you require? e.g.

```

while read -r url; do 
  wget -O- "$url"
done < hosts-urls.txt \
| awk '{fqdn[$2]++; next}; END{for (d in fqdn) print d}' > hosts-blacklist.txt

```

(you could do the same with a combination of sort and uniq instead of using an awk array; or even use a bash associative array if you want to be a hardcore shellista). You could then use grep -v to 'subtract' your whitelist e.g.

```

fgrep -vf hosts-whitelist.txt hosts-blacklist.txt > hosts-blacklist-minus-whitelist.txt

```

where hosts-whitelist also just contains the bare FQDNs i.e.

```

$ cat hosts-whitelist.txt 
rarbg.com
www.rarbg.com
rover.ebay.com

```

and then spit the pruned list out in whatever format (with whatever loopback IP is appropriate for your system) you want 

```

localhost="127.0.0.1"

mv /etc/hosts{,.bak}
cp hosts-default.txt /etc/hosts

while read -r fqdn; do 
  printf '%s %s\n' "$localhost" "$fqdn"
done < hosts-blacklist-minus-whitelist.txt >> /etc/hosts

```

---

### Post by fprietog on 2014-06-20
> **sisco311 said:**
> You can use the** comm**(1) command.
Thanks!. It will delete the entries instead of commenting them, but the result is the same.

I discovered, using this command, two problems:

- some of the downloaded lines got a / at the end totally unnecessary, but all downloaded lines got the typical windows character \r. As it was "hidden" I become crazy because comm doesn't find these "identical" lines.
As I need to get rid of that \r characters too I included the replacement changing the line
```
[COLOR=#000000][FONT=courier new]sed -i 's/\t/ /g;s/ /#/;s/ //g;s/#/ /g' ./hosts-temp.txt[/FONT][/COLOR]
```
by
```
[FONT=courier new]sed -i 's/\t/ /g;[COLOR=#ff0000]s/\r/ /g;[/COLOR][COLOR=#ff0000]s/\// /g;[/COLOR]s/ /#/;s/ //g;s/#/ /g' ./hosts-temp.txt[/FONT]
```

- you can't redirect the output of the command **comm** to one of the files used by the command because the result file ends empty (well, maybe it's possible, but I tested several ways without luck).
I finally changed the copy to [FONT=courier new]/etc/hosts[/FONT] in order to use the output of the command **comm** directly against that file, avoiding the necessity of updating the temporary file.
So I replaced this code:
```
[FONT=courier new]cat ./hosts-whitelist.txt | while read line; do[/FONT][INDENT][FONT=courier new]HOST=$(echo ${line})[/FONT][/INDENT]
[INDENT][FONT=courier new]sed -i s/^"$HOST"/\#"$HOST"/g ./hosts-temp.txt[/FONT][/INDENT]
[FONT=courier new]done[/FONT]
[FONT=courier new]cp /etc/hosts ./hosts.bak[/FONT]
[FONT=courier new]cat ./hosts-default.txt ./hosts-temp.txt > /etc/hosts[/FONT]

```By:
```
[FONT=courier new]cp /etc/hosts ./hosts.bak
[/FONT][FONT=courier new]cat ./hosts-default.txt > /etc/hosts[/FONT]
[FONT=courier new]comm -13 ./hosts-whitelist.txt ./hosts-temp.txt >> /etc/hosts[/FONT]
```
And it works way quicker than before.


> **steeldriver said:**
> Wouldn't it be easier to start with a clean slate and simply construct a list of unique FQDNs from the downloaded lists, and then spit them back out in the format that you require?.....
Thanks for your suggestion!. In fact that's the must logical way. Unfortunately my knowledge of awk is null, but it's one of the things I want to learn in the future because seems to be really handy. I will study the way you give in order to learn and improve the process.

Thank you very much.

---


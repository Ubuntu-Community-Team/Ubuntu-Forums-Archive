---
title: "Help cleaning up a bash script."
date: 2008-12-18
forum: Programming Talk
---

### Post by shearn89 on 2008-12-18
Hey all - I wrote a bash script to grab search results off isohunt.com and download them to a folder, for use in conjunction with rtorrent. I was just wondering if anyone could give me any ideas for ways to clean it up a bit - I know it would be better written in perl or something, but at the mo its in bash, and will stay that way until i get around to rewriting it (and learning some perl)! I just want to know if anyone can see ways of doing things better, perhaps neater, in bash.

Code is posted below, for those that want to try it, tar.gz attached. Just download, untar to a folder, edit the $format line to point to the scripts location (for the sed script), and make sure you have a ~/torrents folder. Chmod and run...

Oh - depends on w3m. Should be in the repos somewhere...

```

#!/bin/bash

file="/tmp/isodump"
format="$HOME/.scripts/isosearch/formatting.sed"

if [ "$1" == "--help" ]; then
	echo -e "A simple script to get torrent results from isohunt.\n"
	echo -e "USAGE: \tsearch [QUERY] [OPTIONS] .."
	echo -e "\tQuery may be blank for interactive usage,"
	echo -e "\tbut must be in quotes otherwise."
	echo -e "\t-p  : print first 5 results automatically."
	exit
fi
if [ "$1" == "" ]; then
	echo "enter search term: "
	read tempterm
	term=$(echo $tempterm | tr '[:blank:]' '\053')
else term=$(echo $1 | tr '[:blank:]' '\053')
fi
if [ "$2" == "-p" ]; then
	showres="y"
fi

w3m -no-cookie -dump "http://isohunt.com/js/json.php?rows=40&sort=seeds&ihq="$term | tr '},{' '\n' > $file
echo -e "\n"
cat $file | grep total_results | awk {'print "Total Results: "$2'}

if [ "$showres" = "" ]; then
	echo -e "\nThe following will print the first 5 results ordered by Seeders."
	echo -e "Type \"a\" to print the first 20 results."
	echo -ne "\nPrint results? y/N/a : "
	read showres
fi

if [ "$showres" = "" ]; then
	rm /tmp/isodump
	exit
fi
if [ "$showres" = "y" ]; then
	cat $file | sed -f $format | head -n 34 | grep -v guid > $file
	cat -n $file
fi
if [ "$showres" = "a" ]; then
	cat $file | sed -f $format | grep -v guid > $file
	cat -n $file
fi	

echo -e "\nBy default this will download to ~/torrents/"
echo -e "Enter number to download, hit return to quit: "
read line >/dev/null
if [ "$line" = "" ]; then
	rm /tmp/isodump
	exit
else
	url="`cat $file | sed -n $line\p | awk {'print $2'}`"
	echo "Downloading "$url
fi
wget -nv -nc -U Mozilla/4.0 -P $HOME/torrents/ $url
echo -e "\nTorrents in folder:"
ls $HOME/torrents/*.torrent
rm /tmp/isodump

```

and the formatting.sed file:
```

s/\":\"/: /g
s/\"//g
s/enclosure_url/url/g
/length/,/files/d
/leechers/,/GMT/d
/isoHunt/,/list/d
s/]//g

```

---

### Post by digitalvectorz on 2008-12-18
One suggestion, though trivial, look into using the elif statement;  I see a few places in your code that could alleviate some of the if, fi combos...

However, through quick glance; i'm sure it could possible be compacted/refined, but i don't see any major changes to make.

---

### Post by shearn89 on 2008-12-18
a quick google for "bash elif" shows that it would indeed help to tidy up some of the parameter checking etc. I'll add it in this evening.
I guess without all the usage stuff, its basically:
1. get results
2. sed them into something resembling readability
3. get the selected url.

Not really all that much to change...

---

### Post by ibuclaw on 2008-12-18
Only suggestion I have to make is to cut out the cat pipes in the script, as the apps to which you pipe the streams to are fully capable to open up files themselves.

ie:
```
cat $file | sed -f $format | head -n 34 | grep -v guid > $file
```
To be changed to:
```
sed -f $format $file | head -n 34 | grep -v guid > $file
```

[EDIT]
And another example:
```
cat $file | grep total_results | awk {'print "Total Results: "$2'}
```
Becomes:
```
grep total_results $file | awk {'print "Total Results: "$2'}
```

Regards
Iain

---

### Post by geirha on 2008-12-18
> **tinivole said:**
> 
[EDIT]
And another example:
```
cat $file | grep total_results | awk {'print "Total Results: "$2'}
```
Becomes:
```
grep total_results $file | awk {'print "Total Results: "$2'}
```


awk can do the job of grep in this case as well, so it can be just:
```
awk '/total_results/{print "Total Results: "$2}' "$file"
```

---

### Post by shearn89 on 2008-12-18
awesome! thanks a load guys. This should help to trim it down just a little...

---

### Post by ibuclaw on 2008-12-18
> **geirha said:**
> awk can do the job of grep in this case as well, so it can be just:
```
awk '/total_results/{print "Total Results: "$2}' "$file"
```

If you want to go that far, I suppose I could say the same to the sed command too :)

```
sed -f $format $file | head -n 34 | grep -v guid > $file
```
Becomes...
```
sed -i -f $format -e '34q' -e '/guid/d' $file
```
Although, I would recommend you try it on a dummy file first.

Regards
Iain

---

### Post by eightmillion on 2008-12-18
My advice would be to use a loop and a case statement to go over the command line parameters so that their order won't matter and it will be easier to add switches in the future. Like this:

```

if [ ! "$1" ]; then
        echo "enter search term: "
        read tempterm             
        term=$(echo $tempterm | tr '[:blank:]' '\053')
else                                                  
for i in $@;do                                        
    case "$i" in                                        
          "-p")                                       
               showres="y"                            
               ;;                                     
      "--help")                                       
               echo -e "A simple script to get torrent results from isohunt.\n"
               echo -e "USAGE: \tsearch [QUERY] [OPTIONS] .."                  
               echo -e "\tQuery may be blank for interactive usage,"           
               echo -e "\tbut must be in quotes otherwise."                    
               echo -e "\t-p  : print first 5 results automatically."          
               exit                                                            
              ;;                                                               
             *)                                                                
               term=$(echo "$i" | tr '[:blank:]' '\053')                         
               ;;                                                              
    esac
done                                                                           
fi                              

```

You might also add a check to see if w3m is installed like this:

```

if [ ! `which w3m` ];then
     echo "Please install w3m."
     exit
fi

```

---

### Post by shearn89 on 2008-12-19
> **tinivole said:**
> If you want to go that far, I suppose I could say the same to the sed command too :)

```
sed -f $format $file | head -n 34 | grep -v guid > $file
```
Becomes...
```
sed -i -f $format -e '34q' -e '/guid/d' $file
```
Although, I would recommend you try it on a dummy file first.

Regards
Iain

it didn't quite work, but now i have this:
```

sed -i -f $format $file -e '/guid/d'
cat -n $file | head -n 30

```

also, many thanks to **eightmillion** - made it much better!

new script attached.

---


---
title: "make NFO where its missing from files"
date: 2020-09-21
forum: Programming Talk
---

### Post by klapvogn on 2020-09-21
Hello,

im new to all this. So hope someone can help me clear the issue.

i have some movies where nfo is missing. and i would like mediainfo to make a nfo file in the same directory if possible. i have a piece of code, that make a default nfo but no info about the video itself i i don't know how to make it :(

but if i read this correct it should go under the else statement?
and the issue is also that : /xxx/xxx/category can change.
```
defaultnfo="/home/xxxx/default.nfo"
```

i know it's ugly as hell :D
```
# set nfo files if [[ $(find ${incoming} -maxdepth 1 -iname \*.nfo | wc -l ) -gt 0 ]]; then
        nfo=$(echo $(find ${incoming} -maxdepth 1 -iname \*.nfo))
        echo NFO Exists $(basename "${nfo}") | tee -a log.txt
        timestamp=$(date +%s)
        cp "${nfo}" ${timestamp}.nfo
        nfo=" --form nfo=@${timestamp}.nfo"
        echo "${nfo}" | tee -a log.txt
else
        echo "No NFO found for ${name}" | tee -a log.txt
        nfo=" --form nfo=@${defaultnfo}"
fi
```

This one was a test but i think it's overkill to search all *.mkv
```

#cd /xxx/xxxx/
 #find -name *.mkv -execdir mediainfo --LogFile={}.nfo {} \;

```

---

### Post by yapidumoac on 2020-09-21
What is an nfo ?

---

### Post by klapvogn on 2020-09-22
Hello,

my bad its a txt with info about the movie :)

---

### Post by TheFu on 2020-09-22
Perhaps if you describe the final system you are trying to get the data into, rather than this intermediate step which may not be needed at all, we can better help?

When I looked at creating a filter for NFO files about 10 yrs ago. I considered anything beyond just the basic data to be too complex for the level of effort I was willing to expend. Then I discovered that tools like Kodi will accept a 1-line movie-name.nfo file that just points to the IMDB URL for that movie. Nothing else, just a line like this:
```
[https://www.imdb.com/title/tt1836944/](https://www.imdb.com/title/tt1836944/)
```
That is sufficient for the tool to find the information and load it into the Kodi DBMS.
BTW, that is a fun movie. Not great, but fun.

Please don't run commands as root when it isn't necessary to the OS. That's a good way to trash a system and make access even harder going forward.

---

### Post by TheFu on 2020-09-22
A minimal .NFO file should be this:
```
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<movie>
    <title>28 Weeks Later</title>
</movie>
``` 

I'd make a script that accepts 2 command line arguments, the directory and the title to be used.
That script would look like this:
```
#!/bin/bash

if [ -z "$1" ] ; then
  echo Usage: $0 directory title
  exit 1
fi
if [ -z "$2" ] ; then
  echo Usage: $0 directory title 
  exit 1
fi

OUTFILE="$1/$2.nfo"

echo '<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<movie>' | tee "$OUTFILE"
echo "    <title>$2</title>
</movie>
" | tee -a "$OUTFILE"

```

Wouldn't take much to directly convert the directory name into the title, if that is desired.  There will be issues with some titles and directory names that have some undesirable characters. The worst characters are ' " ! ? & () {} [] which are all special to bash, so those would need to be escaped as needed.  Spaces are a hassle too, but should be handled fine above.  In my world, I just don't name any files or directories using those characters. That's easier.  "Bill & Ted" becomes "Bill_n_Ted".  Since the display of the title comes from a database, not a directory name, that hasn't matter much.  Movie directory tools like Kodi and Plex prefer names like this "The Baytown Outlaws (2012)" ---> The_Baytown_Outlaws-2012 in my world mainly to make scripting much easier.

Anyways, that's what I'd do.  If the script got much more complex, I'd change from bash into a real programming language like Perl.

---


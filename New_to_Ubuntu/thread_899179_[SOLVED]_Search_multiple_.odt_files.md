---
title: "[SOLVED] Search multiple .odt files"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-08-24
Is there a good way to search a ton (well, 268) files in .odt format for a short text string all at once?

---

### Post by eightmillion on 2008-08-24
You might try > grep -l "short text string" *.odt
From what I recall odt is a plaintext xml based format so it should work.

---

### Post by ad_267 on 2008-08-24
> **eightmillion said:**
> You might try 
From what I recall odt is a plaintext xml based format so it should work.

They're a compressed archive so that won't work. I think there's a way to search through archives though but I'm not sure.

---

### Post by eightmillion on 2008-08-24
> They're a compressed archive so that won't work. I think there's a way to search through archives though but I'm not sure.
You are right. They are zip archive. I think zgrep greps zip archives, so try this command instead:
> zgrep -l "short text string" *.odt

---

### Post by ad_267 on 2008-08-24
This will tell you all the files that contain your search term:

```
for file in $(ls *.odt); do
unzip -p "$file" content.xml | grep -l "search term" > /dev/null
if [ $? -eq 0 ]; then
echo "$file"
fi
done
```

Edit: Yeah zgrep would be better, I didn't know about that!

---

### Post by eightmillion on 2008-08-24
Crap. zgrep only works on gzip and bzipped archives it appears. You can use a simple script to unzip all the files and grep them though
```

for i in *.odt;
do unzip -ca $i | grep -q "short text string";
    if [ $? -eq 0 ];
        then echo "string found in $i";
    fi;
done

```
You'll need to save it as something like grepodt and change "short text string" as appropriate. Then make it executable with > chmod +x grepodt
Then drop it in the directory with all the odt files and call it with ./grepodt
Hope this helps.

---

### Post by Rolcol on 2008-08-24
> **ad_267 said:**
> This will tell you all the files that contain your search term:

```
for file in $(ls *.odt); do
unzip -p *.odt content.xml | grep -l "search term" > /dev/null
if [ $? -eq 0]; then
echo "$file"
fi
done
```

Edit: Yeah zgrep would be better, I didn't know about that!

I was just testing that before you posted it.  I was trying to find a way to just show the string without all the XML data but your way is better since you can open the files themselves after you know which contain the string.

---

### Post by ad_267 on 2008-08-24
I made this into a proper script because I thought it might be useful some time. Also I accidentally had "unzip -p *.odt" instead of "unzip -p "$file""

```

#!/bin/bash

if [ $# -ne 1 ]; then
	echo "Usage: searchodt searchterm"
	exit 1
fi

for file in $(ls *.odt); do
	unzip -ca "$file" content.xml | grep -ql "$1"
	if [ $? -eq 0 ]; then
		echo "$file"
	fi
done

```

---

### Post by eightmillion on 2008-08-24
**ad_267**, you should use -ca options for unzip. -a converts text files. You should use -q for grep also. It's quiet mode, so you can get rid of your "> /dev/null. Otherwise it looks good.

---

### Post by ad_267 on 2008-08-24
> **eightmillion said:**
> **ad_267**, you should use -pa options for unzip. -a converts text files. You should use -q for grep also. It's quiet mode, so you can get rid of your "> /dev/null. Otherwise it looks good.

Ok thanks I've modified it to use those options. That's the fun about writing bash scripts, you always learn something new. I saw your script after I posted mine and it looks like it works in a very similar way.

---

### Post by eightmillion on 2008-08-24
They are almost identical. Great minds think alike. :) Just one more thing. I was hasty with the -pa option. -a doesn't work with -p so you'll have to change it to -ca. Sorry.

---

### Post by ad_267 on 2008-08-24
Oh yup I didn't read the man page very carefully. Thanks.

The script still seems to work ok but I guess there could be other issues that come up later without using the a option.

---

### Post by dinostabOMG on 2008-08-27
Wow, ask a question and get a whole script (or two!) written for you! Thanks a ton, guys.

---

### Post by MelIrizarry on 2008-09-26
I made a few changes to your script to allow files names with spaces and to allow the starting search path.

```
#!/bin/bash

if [ $# -ne 2 ]; then
        echo "Usage: searchodt searchpath searchterm"
        exit 1
fi

find $1 -name "*.odt" | while read file
do
        unzip -ca "$file" content.xml | grep -qli "$2"
        if [ $? -eq 0 ]; then
                echo "Found keyword in: " $file
        fi
done
```

You provided part of the solution for me and I ran with it from there.

Thanks!

Mel

---

### Post by triplemaya on 2009-03-26
Post removed

---

### Post by bobpaul on 2010-12-23
> **ad_267 said:**
> 
```
for file in $(ls *.odt); do
unzip -p "$file" content.xml | grep -l "search term" > /dev/null
if [ $? -eq 0 ]; then
echo "$file"
fi
done
```


I like this and made it into a function. Paste this into your ~/.bashrc. Then you can use "odtgrep search\ term" to search all *.odt files for your term. tidy cleans up the XML so grep can return the line result without too much mess.

```

function odtgrep(){
    term="$1"
    for file in *.odt; do
        unzip -p "$file" content.xml | tidy -q -xml 2> /dev/null | grep "$term";
        if [ $? -eq 0 ]; then
            echo $file;
        fi;
    done 
}

```

---


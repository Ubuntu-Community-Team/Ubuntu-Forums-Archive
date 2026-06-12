---
title: "bash search script improvement"
date: 2011-07-03
forum: Programming Talk
---

### Post by sshaharyar on 2011-07-03
Hi,
   I've switched to ubuntu 10.10 a few months ago and have just started tinkering around with bash scripting. Ive been working on a script which searches the filesystem for a specific file or directory, the reason being that I find the gui based search to be a bit too slow. I have no prior programming/scripting experience, and ive written this script which does what I want [ albeit imperfectly] in under 5 seconds. 

My problem is that the search function is imperfect, ie it can only identify directories, if the last character of the directory is provided by the user. I would like some help with that.
Also, I don't know if ive commented the script correctly [too much? too little? ] and most importantly, if the code is wasteful / just plain bad.

Any help along any of these lines would be greatly appreciated...
Thanks :)



```
#! /bin/bash

# Script to search for a specific file or directory in home folder and mounted filesystems, excluding /bin, /var and so on...
# DISCLAIMER- I know zilch, zero, nothing about sed or awk. any sed usage has been copied/modified from google searches, and i dont know how it works 
# [despite having  read a few guides]...
# Whole sript is built around grep for searches, find for compiling file lists, and wc -l for line counts..

# function to make index files, which are searched by grep calls later to locate files....
function makeindex {

echo "Indexing files..."
cd /media
sudo find ./* -type f > /tmp/medialist.txt

cd /home
sudo find ./* -type f > /tmp/homelist.txt

echo "Indexing Directories..."
cd /
sudo find . -type d > /tmp/dirlisttemp.txt

# add a comma to the end of each line in dirlist, so that grep calls [later] can identify specific directory names
# ie, grep searchterm returns "etc-searchterm-etc", but grep "searchterm," returns only searchterm, and NOT subdirs
sed 's/\(.*\)/\1,/' < /tmp/dirlisttemp.txt > /tmp/dirlist.txt
rm -f /tmp/dirlisttemp.txt

# read number of lines in index files to determine total objects indexed, get file sizes (stat) and report to user
set `wc -l /tmp/dirlist.txt`
dirnum="$1"
set `wc -l /tmp/medialist.txt`
medianum="$1"
set `wc -l /tmp/homelist.txt`
homenum="$1"
totalnum=$(($homenum+$medianum))
set `wc -l /tmp/dirlist.txt`
dirnum="$1"

echo "$medianum Files indexed in /media"
echo "$homenum Files indexed in /home"
echo "$dirnum Directories indexed"
size=0
for x in /tmp/homelist.txt /tmp/medialist.txt /tmp/dirlist.txt ; do
    set `stat -t $x`
    size=$(($size+$2))
done
sizef=$(($size/1000000))
echo "Total index size is $sizef Megabytes"
sleep 1

}

# check - missing command line arguments / argument -u to regenerate index
[ "$1" = "-u" ] && { echo "Regenerating Index files..." ; makeindex ; exit ; }


[ "$1" = "" ] && { echo "Missing argument...." ; echo 'Usage: search.sh "File/Dir name" -d[irectory search]' ; echo "Or search.sh -u to rebuild index" ; exit ; }
# assign $1 to variable searchname, because value of $1 is modified later in the script so cannot be used to search
searchname="$1"

# check for index files
    ls /tmp/homelist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }    
    ls /tmp/dirlist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }
    ls /tmp/medialist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }



#search directory matches if $2 is -d
    if [ "$2" = "-d" ]; then
        echo "Searching for directory"
# search for user inputted value followed by comma, so that subfolders are ignored
# however, this means that the last character of the dirname has to be provided by the user, ie
# a dir named "test1" cannot be found with cmd line input of "test"

        grep -i "$searchname""," /tmp/dirlist.txt > /home/$USER/dirsearch.txt
        set `wc -l /home/$USER/dirsearch.txt` 
        dirnum="$1"

        echo ""$dirnum" directories found."
        if [ "$dirnum" -ge "1" ]; then
            echo "Displaying results. Results have also been saved to /home/$USER/dirsearch.txt"
            echo ""
            cat /home/$USER/dirsearch.txt
        fi
        echo "Press enter to continue searching in file lists or Ctrl-C to exit"
        read userwaste
    fi

    
    echo "Searching for ""$1"" in Index..."
    rm -f /home/$USER/searchresults.txt


# search for files | ignore folders [crude code, needs improvement but dont know how] ...
    grep -i "$searchname" /tmp/homelist.txt | grep -i -v "/""$searchname""/" > /home/$USER/searchresults.txt        
    grep -i "$searchname" /tmp/medialist.txt | grep -i -v "/""$searchname""/" >> /home/$USER/searchresults.txt        

    
    set `wc -l /home/$USER/searchresults.txt`
    matchnum="$1"

    [ "$matchnum" = "0" ] && { echo "" ; echo "No results found" ; exit ; }

    echo ""
    echo "Displaying Results..."
    echo ""    
    cat /home/$USER/searchresults.txt
    echo ""
    echo "A total of $matchnum matches found"
    echo "Results saved to /home/$USER/searchresults.txt"



```PS: I've searched all over the forum but I couldnt find a better place to post this. If im wrong, anyone let me know and Ill happily repost it in the correct section...

---

### Post by papibe on 2011-07-03
I took a rough look at the script. It looks you're trying to keep a file and directory cache, so search can be done fast.

What I don't get yet is the problem you have with the script. Could you post an example of a failed search?

Regards.

---

### Post by Vaphell on 2011-07-03
is there any reason why you play with set `...`; var=$1?
can't you capture the output directly with

```
var=$( wc -l ... )
```

adding , is unnecessary, you can check for matches at the end of line
```
echo $'abc\nabc/def' | grep 'abc'
**abc**
**abc**/def
echo $'abc\nabc/def' | grep 'abc$'
**abc**

```
$ is end-of-line in regular expressions and it works in grep

though unnecessary assuming changes to grep, but it's useful to know nonetheless
```
sed 's/\(.*\)/\1,/'
``` can be shortened to
```
sed 's/.*/&,/'
echo $'abc\nabc/def' | sed 's/.*/&,/'
abc,
abc/def,
```
& is a placeholder for the whole matching string


switches can be combined, grep -i -v = grep -iv

---

### Post by sshaharyar on 2011-07-04
Wow, that was a quick response :)

Thanks guys for taking a look at this and helping out, here's the update....

@papibe
Heres a look at the index file the script generates and later uses grep to search for "mydir"
     /mydir
     /mydir/dir1
     /mydir/dir2
     /mydir/dir3
/home/mydir
     

the output I want is - 
1 Directory found.
     /mydir
/home/mydir

the output I get with grep -i "mydir" is 
     5 Directories found...
     /mydir
     /mydir/dir1
     /mydir/dir2
     /mydir/dir3
/home/mydir
and so on

output with grep -i "mydir"$ is
/mydir
/home/mydir

which is ok, but it means that grep -i "mydi"$ will not find any directories, so i always have to know the last letter of the folder I am searching for, so I cannot use "download" to search for folders named "downloads"


@Vaphell

Ok. so have removed the sed command to put commas, am using regexp $ to find end of line...

As for the set ---> `wc -l myfile.txt` gives output 
142 myfile.txt
ie number of lines [space] filename
and I only need the number of lines in the variable, so thats why Im using set instead of directly assigning wc output to the variable.

3rdly, have combined the switches in the script.....

=======================================
Why doesnt ubuntu incorporate such cache based / quick search in the GUI....and how does it search [ ie via cache, ls / find commands, other method? ] and why is it so slow?

Posting the cleaned up code below. Plz comment....

```


#! /bin/bash

# Script to search for a specific file or directory in home folder and mounted filesystems, excluding /bin, /var and so on...
# DISCLAIMER- I know zilch, zero, nothing about sed or awk. any sed usage has been copied/modified from google searches, and i dont know how it works 
# [despite having  read a few guides]...
# Whole sript is built around grep for searches, find for compiling file lists, and wc -l for line counts..

# function to make index files, which are searched by grep calls later to locate files....
function makeindex {

echo "Indexing files..."
cd /media
sudo find ./* -type f > /tmp/medialist.txt

cd /home
sudo find ./* -type f > /tmp/homelist.txt

echo "Indexing Directories..."
cd /
sudo find . -type d > /tmp/dirlist.txt

# read number of lines in index files to determine total objects indexed, get file sizes (stat) and report to user
set `wc -l /tmp/dirlist.txt`
dirnum="$1"
set `wc -l /tmp/medialist.txt`
medianum="$1"
set `wc -l /tmp/homelist.txt`
homenum="$1"
totalnum=$(($homenum+$medianum))
set `wc -l /tmp/dirlist.txt`
dirnum="$1"

echo "$medianum Files indexed in /media"
echo "$homenum Files indexed in /home"
echo "$dirnum Directories indexed"
size=0
for x in /tmp/homelist.txt /tmp/medialist.txt /tmp/dirlist.txt ; do
    set `stat -t $x`
    size=$(($size+$2))
done
sizef=$(($size/1000000))
echo "Total index size is $sizef Megabytes"
sleep 1

}

# check - missing command line arguments / argument -u to regenerate index
[ "$1" = "-u" ] && { echo "Regenerating Index files..." ; makeindex ; exit ; }


[ "$1" = "" ] && { echo "Missing argument...." ; echo 'Usage: search.sh "File/Dir name" -d[irectory search]' ; echo "Or search.sh -u to rebuild index" ; exit ; }
# assign $1 to variable searchname, because value of $1 is modified later in the script so cannot be used to search
searchname="$1"

# check for index files
    ls /tmp/homelist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }    
    ls /tmp/dirlist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }
    ls /tmp/medialist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }



#search directory matches if $2 is -d
    if [ "$2" = "-d" ]; then
        echo "Searching for directory"
# search for user inputted value followed by comma, so that subfolders are ignored
# however, this means that the last character of the dirname has to be provided by the user, ie
# a dir named "test1" cannot be found with cmd line input of "test"

        grep -i "$searchname"$ /tmp/dirlist.txt > /home/$USER/dirsearch.txt
        set `wc -l /home/$USER/dirsearch.txt` 
        dirnum="$1"

        echo ""$dirnum" directories found."
        if [ "$dirnum" -ge "1" ]; then
            echo "Displaying results. Results have also been saved to /home/$USER/dirsearch.txt"
            echo ""
            cat /home/$USER/dirsearch.txt
        fi
        echo "Press enter to continue searching in file lists or Ctrl-C to exit"
        read userwaste
    fi

    
    echo "Searching for ""$1"" in Index..."
    rm -f /home/$USER/searchresults.txt


# search for files | ignore folders [crude code, needs improvement but dont know how] ...
    grep -i "$searchname" /tmp/homelist.txt | grep -iv "/""$searchname""/" > /home/$USER/searchresults.txt        
    grep -i "$searchname" /tmp/medialist.txt | grep -iv "/""$searchname""/" >> /home/$USER/searchresults.txt        

    
    set `wc -l /home/$USER/searchresults.txt`
    matchnum="$1"

    [ "$matchnum" = "0" ] && { echo "" ; echo "No results found" ; exit ; }

    echo ""
    echo "Displaying Results..."
    echo ""    
    cat /home/$USER/searchresults.txt
    echo ""
    echo "A total of $matchnum matches found"
    echo "Results saved to /home/$USER/searchresults.txt"



```

---

### Post by sisco311 on 2011-07-04
I would use updatedb and locate:
```

updatedb -l 0 -o "${HOME}/db_file" -U "${HOME}/"

locate -d "${HOME}/db_file" PATTERN

```

---

### Post by papibe on 2011-07-04
Got it.

There several approaches to accomplish what you're looking for:
[LIST=1]
[*]Regardless of how your script was thought, give you shell and basic commands tips to improve it.
[*]Go deeper and may be suggest a different design.
[*]As sisco311 pointed out, use or install different tools that can automate same of the steps.
[/LIST]

This is a way to solve the directory search by using a more complex grep regular expression.

Let's say this is your directory database:
```
.
./python
./python/BitTorrent-bencode-5.0.8
./python/BitTorrent-bencode-5.0.8/BitTorrent_bencode.egg-info
./python/BitTorrent-bencode-5.0.8/test
./python/print outs
./C
./C/backup
./C/backup/2010-09-30
./C/print outs
```
If your are trying to get the directories with the pattern 'bencode', you can use this grep command:
```

key="bencode"
grep -i -e "$key[^/]*$" ./database.txt

```
-i for case insensitive,
-e to just explicitly say that the next argument is a regular expression.
[^/] means a character that is not /
[^/]* means sequence of characters (including length zero) that doesn't include the / character.
$ means the end of the line.

That would give you this result:
```
./python/BitTorrent-bencode-5.0.8
./python/BitTorrent-bencode-5.0.8/BitTorrent_bencode.egg-info
```
Hope it helps.

BTW, Happy 4th of July!!

---

### Post by sisco311 on 2011-07-04
Well, if you're going to reinvent the wheel :), then you should use the NUL byte as a delimiter in the database:
```
find PATH OPTIONS -print0 > files
```

Then you could search for a file with something like:
```

while IFS= read -d '' -r file
do
  # See: [http://wiki.bash-hackers.org/syntax/ccmd/conditional_expression]("http://wiki.bash-hackers.org/syntax/ccmd/conditional_expression")
  if [[ $file =~ [ERE]("http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap09.html#tag_09_04") ]]
  then
     echo "$file"
  fi
done < files
```

---

### Post by papibe on 2011-07-04
> **sshaharyar said:**
> Why doesnt ubuntu incorporate such cache based / quick search in the GUI....and how does it search [ ie via cache, ls / find commands, other method? ] and why is it so slow?

Well, actually there is. Ubuntu 11.04 includes the [Zeitgeist framework]("http://en.wikipedia.org/wiki/Zeitgeist") (I believe is in [Gnome]("http://gnomejournal.org/article/70/an-introduction-to-gnome-zeitgeist") 3.0 too). Unfortunately, I'm not familiar enough with that to give you any tips.

There are other tools that use Zeitgeist. For example the launcher [Kupfer]("http://kaizer.se/wiki/kupfer/") (in the repositories, but much better from ppa) uses that framework and make searches super fast.

I encourage you to research more about [Zeitgeist]("http://www.andersaaberg.dk/blog/blog/2011/ubuntu-11-04-unity-dashboard-privacy/"), and how to use it on Ubuntu.

Regards.

---

### Post by pafoo on 2011-07-05
> **sisco311 said:**
> I would use updatedb and locate:
```

updatedb -l 0 -o "${HOME}/db_file" -U "${HOME}/"

locate -d "${HOME}/db_file" PATTERN

```

Locate is the way to go. Unless your a Solaris user!  Other wise just use locate and pipe it to grep.

---

### Post by sshaharyar on 2011-07-07
Ok, so finally got it working properly...

Used :
grep -i -e "$key[^/]*$" ./database.txt
Used this grep expression in both the directory search and file search and im happy with the results..

@sisco311

Ok, so it turns out that bash does in fact HAVE a cache based search....*facepalm*

One issue though, my file system has multiple mounted external harddrives in /media/"Harddrive" , which I keep switching, so only one is mounted at any given time. Ive used updatedb but for some reason its not searching the mounted drive. In addition, locate is also outputting directories in the search, so if i search for downloads it gives:

/downloads/file1
/downloads/file2
etc

So, How do I get to search for only files or only directories, and to descend to mounted filesystems?

```

updatedb -l 0 -U "/"
locate -i "part of filename"

```

Finally, Im posted the final script code, [final as in, the script does what I want] and as soon as the locate issue is cleared up...ill label the thread as SOLVED....

Thanks everyone for helping out :) My first experience with forums has been remarkably pleasant thanks to you guys :)


```


#! /bin/bash

# Script to search for a specific file or directory in home folder and mounted filesystems, excluding /bin, /var and so on...
# DISCLAIMER- I know zilch, zero, nothing about sed or awk. any sed usage has been copied/modified from google searches, and i dont know how it works 
# [despite having  read a few guides]...
# Whole sript is built around grep for searches, find for compiling file lists, and wc -l for line counts..

# function to make index files, which are searched by grep calls later to locate files....
function makeindex {

echo "Indexing files..."
cd /media
sudo find ./* -type f > /tmp/medialist.txt

cd /home
sudo find ./* -type f > /tmp/homelist.txt

echo "Indexing Directories..."
cd /
sudo find . -type d > /tmp/dirlist.txt

# read number of lines in index files to determine total objects indexed, get file sizes (stat) and report to user
set `wc -l /tmp/dirlist.txt`
dirnum="$1"
set `wc -l /tmp/medialist.txt`
medianum="$1"
set `wc -l /tmp/homelist.txt`
homenum="$1"
totalnum=$(($homenum+$medianum))
set `wc -l /tmp/dirlist.txt`
dirnum="$1"

echo "$medianum Files indexed in /media"
echo "$homenum Files indexed in /home"
echo "$dirnum Directories indexed"
size=0
for x in /tmp/homelist.txt /tmp/medialist.txt /tmp/dirlist.txt ; do
    set `stat -t $x`
    size=$(($size+$2))
done
sizef=$(($size/1000000))
echo "Total index size is $sizef Megabytes"
sleep 1

}

# check - missing command line arguments / argument -u to regenerate index
[ "$1" = "-u" ] && { echo "Regenerating Index files..." ; makeindex ; exit ; }


[ "$1" = "" ] && { echo "Missing argument...." ; echo 'Usage: search.sh "File/Dir name" -d[irectory search]' ; echo "Or search.sh -u to rebuild index" ; exit ; }
# assign $1 to variable searchname, because value of $1 is modified later in the script so cannot be used to search
searchname="$1"

# check for index files
    ls /tmp/homelist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }    
    ls /tmp/dirlist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }
    ls /tmp/medialist.txt &> /dev/null || { echo "Logfile not found...Generating file index, this may take a while..." ; makeindex ; }



#search directory matches if $2 is -d
    if [ "$2" = "-d" ]; then
        echo "Searching for directory"
        grep -i "$searchname[^/]*$" /tmp/dirlist.txt > /home/$USER/dirsearch.txt
        set `wc -l /home/$USER/dirsearch.txt` 
        dirnum="$1"

        echo ""$dirnum" directories found."
        if [ "$dirnum" -ge "1" ]; then
            echo "Displaying results. Results have also been saved to /home/$USER/dirsearch.txt"
            echo ""
            cat /home/$USER/dirsearch.txt
        fi
        echo "Press enter to continue searching in file lists or Ctrl-C to exit"
        read userwaste
    fi

    
    echo "Searching for ""$1"" in Index..."
    rm -f /home/$USER/searchresults.txt

    for z in /tmp/homelist.txt /tmp/medialist.txt ; do
        grep -i -e "$searchname[^/]*$" $z >> /$HOME/searchresults.txt   # [^/] = character that is not / ,
                                        # [^/]* = sequence of characters doesn't include the / character.
                                        # $ = End of line
    done

    set `wc -l /home/$USER/searchresults.txt`
    matchnum="$1"

    [ "$matchnum" = "0" ] && { echo "" ; echo "No results found" ; exit ; }

    echo ""
    echo "Displaying Results..."
    echo ""    
    cat /home/$USER/searchresults.txt
    echo ""
    echo "A total of $matchnum matches found"
    echo "Results saved to /home/$USER/searchresults.txt"







```

---

### Post by pafoo on 2011-07-07
> Ok, so it turns out that bash does in fact HAVE a cache based search....*facepalm*

One issue though, my file system has multiple mounted external  harddrives in /media/"Harddrive" , which I keep switching, so only one  is mounted at any given time. Ive used updatedb but for some reason its  not searching the mounted drive. In addition, locate is also outputting  directories in the search, so if i search for downloads it gives:

/downloads/file1
/downloads/file2
etc

So, How do I get to search for only files or only directories, and to descend to mounted filesystems?
Me and another guy told you about locate twice ;P

Again locate with grep. use locate with absolute path

example:
locate /home/fi --> results
/home/finish.txt
/home/finger.pop
/home/finishthiscrap

if you want to find just a directory or file lets say... I want to look in home and only find the sub folder "bubblegum"

locate /home | grep bubblegum | grep -v "chewing_gum"

That print everything under /home with the name of bubblegum but exclude those that have the word chewing_gum in it

If you want to do a search in a specific folder to list all files, then use find. locate is for a pre-indexed list of every file on Linux. To get allot more specific use find, it looks recursivley by default. So you could start your search with root dir "/" not root home =P. That would search the entire drive (unless you have all your dir's partitioned like I do, ex /var /home /usr.) The negative to searching by root is the time it takes to search. Thats why "locate" was created. 

man find

example 

find /home -type d -name as* -exec rm {} \;

means look in /home find every directory that starts with "as" end with any char/any number of times then exec rm on each file. Change the flag of type to "f" then it finds only files in selected directory

---

### Post by sshaharyar on 2011-11-30
Me and another guy told you about locate twice ;P

hehe...sorry bout that...got it all working now :D, thanks all for the help :)

---


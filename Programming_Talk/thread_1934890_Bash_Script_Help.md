---
title: "Bash Script Help"
date: 2012-03-03
forum: Programming Talk
---

### Post by Techscape on 2012-03-03
Ok, so I have been trying to create a script that takes the five largest files in my home directory and display them. I am a beginner and I am somewhat doing this from a book I bought, because, well, I just wanted to learn Linux because I have a massive interest in Apache. Figured I would learn how to walk before I could run!

This is what I currently have. When executed through the Linux terminal it pops up, why wouldn't this pop up when I would run the script (when I execute it just seems to echo it...:confused:)? Here it is: 

find . -type f -exec ls -s {} \; | sort -n -r | head -5 > ~/fivelarge.txt 

Obviously, it finds the files sorts them then places them into the text file. Question is, would this work, or would it be better to use something like:

 du -h | head -5 | > ~/fivelarge.txt ? Would that work?

Thanks!

---

### Post by ofnuts on 2012-03-03
> **Techscape said:**
> Ok, so I have been trying to create a script that takes the five largest files in my home directory and display them. I am a beginner and I am somewhat doing this from a book I bought, because, well, I just wanted to learn Linux because I have a massive interest in Apache. Figured I would learn how to walk before I could run!

This is what I currently have. When executed through the Linux terminal it pops up, why wouldn't this pop up when I would run the script (when I execute it just seems to echo it...:confused:)? Here it is: 

find . -type f -exec ls -s {} \; | sort -n -r | head -5 > ~/fivelarge.txt 

Obviously, it finds the files sorts them then places them into the text file. Question is, would this work, or would it be better to use something like:

 du -h | head -5 | > ~/fivelarge.txt ? Would that work?

Thanks!
du does't sort natively by size, and "du -h" makes its output very difficult to sort by size. What you want is more like:
```

du * | sort -rn | head -5

```

---

### Post by Techscape on 2012-03-03
> du does't sort natively by size, and "du -h" makes its output very difficult to sort by size. What you want is more like:
     Code:
     du * | sort -rn | head -5 
What exactly does the * do if you do not mind me asking? Does it match the string or something? 

OK well I was pushing forwards (or trying to and I am sorry for the bad coding...)

I am trying to loop here... for a y/n function, is this right? It just makes it easier every time I run the script. However, is this wise? If it is or is not it will still be cool. :)

echo "-- List five largest in home:"

for FILE in /home/Techscape
for NUM (1 2 3 4 5)  
do
  echo $NUM 1 | head -1 | tail -1
  echo $NUM 2 | head -2 | tail -1
  echo $NUM 3 | head -3 | tail -1 
  echo $NUM 4 | head -4 | tail -1
  echo $NUM 5 | head -5 | tail -1 
done

I mean my reasoning goes as such: it will echo the number in order. However what I am confused about is how the tailing and heads work and getting the output file to display, books are not always so helpful. Would a while function be better than a for/do? Or would the loop for for/do be optimal?

Thank you for your help, sir/madam! I appreciate it heavily!

---

### Post by Vaphell on 2012-03-03
in shell there is that thing called glob. Glob is a pattern that matches files/directories. * in glob context means any char sequence, in other words it matches everything in current directory.
Shell expands * by substituting it with real names. Try *echo **

*du ** in reality becomes *du file1 file2 file3 file4 ... dir1 dir2 dir3 ...*


you can pipe output to awk
```
du * | sort -rn | head -5 | **awk '{ print NR":", $0 }'**
```
NR is record number (records default to lines in awk), $0 is whole record, $1+ - field in record.

---

### Post by ofnuts on 2012-03-03
> **Techscape said:**
> What exactly does the * do if you do not mind me asking? Does it match the string or something? 

OK well I was pushing forwards (or trying to and I am sorry for the bad coding...)

I am trying to loop here... for a y/n function, is this right? It just makes it easier every time I run the script. However, is this wise? If it is or is not it will still be cool. :)

echo "-- List five largest in home:"

for FILE in /home/Techscape
for NUM (1 2 3 4 5)  
do
  echo $NUM 1 | head -1 | tail -1
  echo $NUM 2 | head -2 | tail -1
  echo $NUM 3 | head -3 | tail -1 
  echo $NUM 4 | head -4 | tail -1
  echo $NUM 5 | head -5 | tail -1 
done

I mean my reasoning goes as such: it will echo the number in order. However what I am confused about is how the tailing and heads work and getting the output file to display, books are not always so helpful. Would a while function be better than a for/do? Or would the loop for for/do be optimal?

Thank you for your help, sir/madam! I appreciate it heavily!
"du" wigthout arguments tel the disk usage of thje current directpry as a whole. "du *" with the help the the globbing expounded above, list disk usage for all files.

I don't know what you are trying to achieve with all that code above, since the one-liner I posted does everything:

[LIST]
[*]**[FONT=Fixedsys]du *[/FONT]** lists the size of each file, but the result isn't sorted
[*]**[FONT=Fixedsys]sort -rn[/FONT]** sorts that list by size (-n for "numeric") with biggest first (-r for "reverse")
[*]**head -5** takes the first 5 lines
[/LIST]

---

### Post by Techscape on 2012-03-03
> "du" wigthout arguments tel the disk usage of thje current directpry as a  whole. "du *" with the help the the globbing expounded above, list disk  usage for all files.
 
 I don't know what you are trying to achieve with all that code above, since the one-liner I posted does everything:
 
[LIST]
[*]**[FONT=Fixedsys]du *[/FONT]** lists the size of each file, but the result isn't sorted
[*]**[FONT=Fixedsys]sort -rn[/FONT]** sorts that list by size (-n for "numeric") with biggest first (-r for "reverse")
[*]**head -5** takes the first 5 lines
[/LIST]
 

Just trying to understand how looping works? Like asking the user if he/she would like to remove the file with something as simple as a y/n prompt? I thought that could only be obtained through looping. Is there a way to get that to happen using some kind of loop or perhaps no loop, line by line?  :confused:

---

### Post by Khayyam on 2012-03-03
et al ...

Lets not forget we are looking for the "five largest **files**" ...

```
find -type f -exec du -h {} \; | sort -nr |head -5 > output.txt
```,.. or if we want the file name and its full path

```
find $HOME -type f -exec du -h {} \; | sort -nr | awk '{$1=""; print}' |head -5 > output.txt
```

best ... khay

---

### Post by nothingspecial on 2012-03-03
> **Techscape said:**
> Just trying to understand how looping works? Like asking the user if he/she would like to remove the file with something as simple as a y/n prompt? I thought that could only be obtained through looping. Is there a way to get that to happen using some kind of loop or perhaps no loop, line by line?  :confused:

You would need to investigate the read command for that.

---

### Post by Khayyam on 2012-03-03
> **Techscape said:**
> Just trying to understand how looping works? Like asking the user if he/she would like to remove the file with something as simple as a y/n prompt? I thought that could only be obtained through looping. Is there a way to get that to happen using some kind of loop or perhaps no loop, line by line?

Thats a different question ... but yes, there are various ways to loop.

```
#!/bin/bash

function ask()
{
    echo -n "$@" '[y/n] ' ; read ans
    case "$ans" in
        y*|Y*) return 0 ;;
        *) return 1 ;;
    esac
}

IFS=$'\n'

FILELIST="$(find $HOME -type f -exec du -h {} \; | sort -nr | awk '{$1=""; print}' | head -5)"

for i in ${FILELIST} ; do
    ask "remove ${i}" &&
    # rm -f "${i}"
    echo "${i} removed"
done
```I don't particularly like this kind of thing, the first issue I have with it is that there may be only be 5 "large" files, **but** millions of small files with a greater total size, so ultimately its not particularly fit for purpose. The second issue is that it smells of what we might call "auto-idiocy": the idea that automation is for the sake of sparing the "idiot user" from having to know to use the "idiot computer", both users and computers are normally smarter than "interface" designers.

Anyhow ... there it is (as proof of concept) ... please don't run this from login or Freddy Krueger the universal sys admin will 'while :;' your dream state.

best ... khay

---


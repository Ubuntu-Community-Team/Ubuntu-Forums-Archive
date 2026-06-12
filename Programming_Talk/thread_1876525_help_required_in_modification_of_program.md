---
title: "help required in modification of program"
date: 2011-11-06
forum: Programming Talk
---

### Post by learnbash on 2011-11-06
I have below code, i need to modify it, to search for files (*.php,*.css,*.html) in those directores which have 777 permission, how to modify this code. Because it is moving all files.


```


while true
do
        sleep 60

        DATE=$(date +%Y-%m-%d)

        # Creates dir only if it doesn't already exist
        mkdir -p /garbage/${DATE}/

        find ./ '(' -name '*.php' -o -name '*.css' -o -name '*.html' ')' -exec mv '{}' /garbage/${DATE}/ ';' -print > /tmp/$$

        if [ -s /tmp/$$ ]
        then
                echo "Files moved on $(date)"
                cat /tmp/$$
        fi >> /path/to/logfile

        rm -f /tmp/$$
done


```

---

### Post by learnbash on 2011-11-06
some one understand that what i am trying to say in this thread?

---

### Post by nothingspecial on 2011-11-06
> **learnbash said:**
> some one understand that what i am trying to say in this thread?

Lot's of people I would expect, they just haven't seen it yet.

Please bump your threads every 24 hours or so.

---

### Post by learnbash on 2011-11-06
sir i am not able to add multiple path that have 777 permissions directories, i need to search in 777 permission permission dir that is there any *.php,*.html,*.css file exist if yes then move as mentioned in program but i am not able to add this part.

---

### Post by matt_symes on 2011-11-06
Hi

If nobody helps you, i will help you after my lunch.

Kind regards

---

### Post by sffvba[e0rt on 2011-11-06
> **learnbash said:**
> sir i am not able to add multiple path that have 777 permissions directories, i need to search in 777 permission permission dir that is there any *.php,*.html,*.css file exist if yes then move as mentioned in program but i am not able to add this part.

Post moved to existing thread.


404

---

### Post by Vaphell on 2011-11-06
my idea:
find directories with permissions, use while loop to iterate through the list and use simple mv *.{php,html,css} there

```
find . -perm 777 -type d | while read d; do mv "$d"/*.{php,html,css} /garbage/$DATE; done
```

---

### Post by learnbash on 2011-11-06
i am confuse now, first i want to print that, so i should verify that code is working fine.

---

### Post by ofnuts on 2011-11-06
> **learnbash said:**
> i am confuse now, first i want to print that, so i should verify that code is working fine.it should work OK, even if it outputs unnecessary error messages if there are no php/html/css files in the directory.

---

### Post by Vaphell on 2011-11-06
add echo commands here and there to print out current values of variables and whatnot
and error messages can be silenced with 2>/dev/null at the end of mv command
stat | grep prints out permissions

```
find . -perm 777 -type d | while read d
do
  [B]echo DIR: $d
  stat "$d" | grep -Ewo '[0-9]{4}/.[rwx-]{9}'
  echo Files:
  ls "$d"/*.{php,html,css}"
  echo[/B] mv "$d"/*.{php,html,css} /garbage/$DATE
done
```

---

### Post by learnbash on 2011-11-06
it is giving error. because html,php files not exist. also giving overwrite error.

```


it is giving error

[0-9]{4}/.[rwx-]{9}';   mv "$d"/*.{php,html,css} /garbage/files/$DATE > /tmp/$$; done
DIR: ./s1/uploads
0777/drwxrwxrwx
mv: cannot stat `./s1/uploads/*.php': No such file or directory
mv: cannot stat `./s1/uploads/*.html': No such file or directory
mv: cannot stat `./s1/uploads/*.css': No such file or directory
DIR: ./s1/uploads/sliders
0777/drwxrwxrwx
mv: cannot stat `./s1/uploads/sliders/*.php': No such file or directory
mv: cannot stat `./s1/uploads/sliders/*.html': No such file or directory
mv: cannot stat `./s1/uploads/sliders/*.css': No such file or directory
DIR: ./uploads
0777/drwxrwxrwx
mv: cannot stat `./uploads/*.php': No such file or directory
mv: cannot stat `./uploads/*.html': No such file or directory
mv: cannot stat `./uploads/*.css': No such file or directory
DIR: ./uploads/sliders
0777/drwxrwxrwx
mv: overwrite `/garbage/files/2011-11-06/n11.php'? mv: cannot stat `./uploads/sliders/*.html': No such file or directory
mv: cannot stat `./uploads/sliders/*.css': No such file or directory


```

---

### Post by Vaphell on 2011-11-06
if there are matching files pattern is expanded to the full list of file names. When there are no matching files pattern is treated as an ordinary string and mv throws an error because there is no *.something file.
As i wrote earlier you can get rid of errors by redirecting stderr to /dev/null
mv ... 2>/dev/null
stderr (2) is different than stdout (1)
when you do **command > file** or **command 1>file** you redirect 'normal' output
**command 2>/dev/null** redirects errors to a black hole, so they don't pollute the output. You can redirect errors to a file too if you wish.
```
command >file 2>/dev/null
``` will redirect clean output to file and get rid of any errors 

also if you want to redirect mv output to a file add -v parameter (verbose mode) so you get an output and use >> instead of >.
>> = append
> = overwrite
currently each iteration replaces the contents of the file with current output, so the end result will be a file with the content from last loop (and you want everything).

---

### Post by learnbash on 2011-11-06
Thanks i understand your point but is it possible i will store the output of that command in file, i mean these files are going to move and email that file to [EMAIL="my@mydomain.com"]my@mydomain.com[/EMAIL].

```


mv "$d"/*.{php,html,css} /garbage/files/$DATE 2>/dev/null


```

---

### Post by Vaphell on 2011-11-06
i edited my post above, read it.
add -v parameter (mv -v ... ) to get any output from mv. Mv is silent so there is nothing to redirect.
with -v you will get plenty of `/path/to/file/file.name' -> `/destination/dir/file.name'

---

### Post by learnbash on 2011-11-06
please confirm below code, is it right now.

```


find . -perm 777 -type d | while read d; do    mv -f -v "$d"/*.{php,html,css} /garbage/files/$DATE 2>/dev/null 1> /tmp/$$; done

mail -s "777 files found" myname@mydomain.com < /tmp/$$


```

---

### Post by Vaphell on 2011-11-06
it's not because of the difference between >> and > (explained in #12)

that 777 thing was about directories or files? because '777 files found' makes me wonder.
also do you want to mail the list before moving or message the recipient after the fact? script does the latter.

---

### Post by learnbash on 2011-11-06
script will run daily so > is fine. yes i want the list of moving to email address.

---

### Post by Vaphell on 2011-11-06
you don't quite get what i mean when i say about the difference between > and >>

```
for i in 1 2 3
do
  echo $i > file
done

cat file
**3**

```

each iteration of the loop creates that file from scratch, as in when there is 2 redirected to file, 1 is lost. At the end there will be only 3 in the file. Same thing happens in your case. Only the output made for the last found directory will be there in your log file. If there are N directories, entries from 1 to N-1 will be overwritten and no longer there.
you need to use >> and if you need that file fresh, remove it before going into the while loop - it will be recreated inside the loop and all data will be there at the end.

Alternatively remove that redirection from mv and put it after done, thus the whole output of while loop will be redirected at once.
```
while ...; do ....; done > log.file
```

---

### Post by learnbash on 2011-11-06
Ok thanks, now i understand to use >>

---

### Post by Vaphell on 2011-11-06
i edited my post again, in case you missed it. You can try redirecting whole loop, not mv
while .... done > file

---

### Post by learnbash on 2011-11-06
Thanks, nice suggestion.

---


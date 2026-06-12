---
title: "Check if folder have new files."
date: 2012-08-22
forum: Programming Talk
---

### Post by newbie45 on 2012-08-22
Hi.
I have a problem that has been bothering me for quite awhile. As the title suggested, the problem is how can i check whether a folder has a new file inside.

Problem:
First i had a folder called 'Sample' in:
 /home/user/Pictures/Sample
I had a webcam that will take a picture and stored it in the 'Sample' folder. So, when the script check that there is a new file in the 'Sample' folder, it also means that a picture is taken.
After the script detected that there is a new file inside the folder, i will than began to run another script so as to edit the picture.

Example:
if ( 'Sample' have new file )
run a script to edit the picture
else
do nothing

The script has to be constantly checking the folder for any new files.

Is there anybody that can help?
Thanks in advanced! :D

---

### Post by mehaga on 2012-08-22
Google ftw:
[https://www.google.com/search?q=monitor+folder+for+new+files&aq=0&oq=monitor+folder+&sugexp=chrome,mod=6&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=monitor+folder+for+new+files&aq=0&oq=monitor+folder+&sugexp=chrome,mod=6&sourceid=chrome&ie=UTF-8)


This may be what you're looking for:

[http://unix.stackexchange.com/questions/24952/script-to-monitor-folder-for-new-files](http://unix.stackexchange.com/questions/24952/script-to-monitor-folder-for-new-files)

---

### Post by newbie45 on 2012-08-22
> **mehaga said:**
> Google ftw:
[https://www.google.com/search?q=monitor+folder+for+new+files&aq=0&oq=monitor+folder+&sugexp=chrome,mod=6&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=monitor+folder+for+new+files&aq=0&oq=monitor+folder+&sugexp=chrome,mod=6&sourceid=chrome&ie=UTF-8)


This may be what you're looking for:

[http://unix.stackexchange.com/questions/24952/script-to-monitor-folder-for-new-files](http://unix.stackexchange.com/questions/24952/script-to-monitor-folder-for-new-files)

According to your second link, the person commented that this will work:
```
inotifywait -m /path 2>&- | awk '$2 == "CREATE" { print $3; fflush() }' |
    while read file; do
        echo "$file"
        # do something with the file
    done

```

But how do i edit this script so that check the specific folder that it is suppose to check?
Or do i just make this bash script into the folder and just run it?

---

### Post by Vaphell on 2012-08-22
[http://linux.die.net/man/1/inotifywait](http://linux.die.net/man/1/inotifywait)
example 3.
*inotify -m <path>*
-m = monitor indefinitely
optionally -r = recursive and output format (--format <format>), in case you need the info laid out in a convenient form for further shaping.

---

### Post by newbie45 on 2012-08-22
> **newbie45 said:**
> According to your second link, the person commented that this will work:
```
inotifywait -m /path 2>&- | awk '$2 == "CREATE" { print $3; fflush() }' |
    while read file; do
        echo "$file"
        # do something with the file
    done

```But how do i edit this script so that check the specific folder that it is suppose to check?
Or do i just make this bash script into the folder and just run it?

I wrote a bash script according to the second example and just change the path that i want it to check.

```
#!/bin/sh

inotifywait -m /home/user/output 2>&- | awk '$2 == "CREATE" { print $3; fflush() }' |
    while read file; do
        echo "$file"
    done
```

However, when i copy a file into /home/user/output the script did not display "file". Why is it not working ?

---

### Post by Zugzwang on 2012-08-23
> **newbie45 said:**
> However, when i copy a file into /home/user/output the script did not display "file". Why is it not working ?

Check that:

[LIST=1]
[*]inotifywait is installed on your system: just try to run "inotifywait" on the terminal and see if you get an error message
[*]your script is already running when adding a file to the directory that you are monitoring. The inotifywait solution presented earlier in this thread is precisely for this case. If you want to find new files since the last run of your script, you need a different solution.
[/LIST]

---

### Post by Vaphell on 2012-08-23
i checked i vboxed precise - piping messes it up and you get no output. I don't possess the arcane knowledge required to fix this so i suggest keeping it simple:  leaving the output untouched and moving the logic inside while loop. I added the format so the output is easier to parse (tab as a delimiter to avoid problems with space)

```
while IFS=$'\t' read -r file event
do
  if [ "$event" != "CREATE" ]; then continue; fi
  echo -e "file: $file ($event)"
done < <( inotifywait -m --format $'%f\t%e' ~ 2>&- )
```

---

### Post by newbie45 on 2012-08-23
> **Vaphell said:**
> i checked i vboxed precise - piping messes it up and you get no output. I don't possess the arcane knowledge required to fix this so i suggest keeping it simple:  leaving the output untouched and moving the logic inside while loop. I added the format so the output is easier to parse (tab as a delimiter to avoid problems with space)

```
while IFS=$'\t' read -r file event
do
  if [ "$event" != "CREATE" ]; then continue; fi
  echo -e "file: $file ($event)"
done < <( inotifywait -m --format $'%f\t%e' ~ 2>&- )
```

Im sorry as im am still new to this kind of programming, so i do not know where do i edit your code.

The folder that the code is supposed to check is : /home/user/output
and where do i put my script/code when your code detected new file in /home/user/output?

Sorry for bothering you. :p

---

### Post by Vaphell on 2012-08-23
the only thing that looks remotely like a dir in my code is ~ which is a shorthand for $HOME (/home/current_user). Put your path in its place.
Any logic you need goes between *while ... do* and *done*.

In my code i formatted output to <filename>[TAB]<event> and ordered read command to fill 2 variables using TAB as delimiter: file, event. First line in the loop body is a do-nothing (end current loop run with *continue*) if event is not CREATE, in case you want only creation events. It replaces awk code functionally.

And seriously, you desperately need to lick some basics if you don't know what while loop is and how it works ;-)

---


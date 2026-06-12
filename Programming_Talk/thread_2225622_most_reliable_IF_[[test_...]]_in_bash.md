---
title: "most reliable IF [[test ...]] in bash"
date: 2014-05-22
forum: Programming Talk
---

### Post by Habitual on 2014-05-22
Date math in scripts, you have to "love" it.
I am modifying a backup script to massage some conditionals based on the First Of The Month.

Anyway, I always get jammed up on the possible constructs of "IF" statement in [[ test ]] conditions.
Which of these is the most reliable?

```
DAYOFMONTH=$(date +%d)
if [[ $DAYOFMONTH == "1" ]] ; then echo "it is the 1st" ; else echo "it is not the first" ; fi
if [[ $DAYOFMONTH = "1" ]] ; then echo "it is the 1st" ; else echo "it is not the first" ; fi
if [[ $DAYOFMONTH == 1 ]] ; then echo "it is the 1st" ; else echo "it is not the first" ; fi
if [[ $DAYOFMONTH = 1 ]] ; then echo "it is the 1st" ; else echo "it is not the first" ; fi

```

Thank you for your time.

---

### Post by Vaphell on 2014-05-22
all of these are largely equivalent in this case
unlike [ ], [[ ]] doesn't perform word splitting so you don't have to quote anything and = and == are the same, though they are for strings. Integers are supposed to be used with -eq -ne and such.


either way for numeric comparisons you could just use (())

```
dayofmonth=$(date +%d)
(( dayofmonth==1 )) && echo 1st || echo not 1st
```

---

### Post by Habitual on 2014-05-22
Exactly the answer I am looking for.

IF statements help me with the logical processing of the statement blocks.
Converting my [[ test ]] to your example is causing me pause...
And I didn't expect "that"!

Any pitfalls to be concerned with using
```
if [[ $DAYOFMONTH -eq 1 ]] ; then 
    do stuff
else 
    process in the usual way.
fi
```



Thanks.

---

### Post by Vaphell on 2014-05-22
One. I forgot about issues with octal numbers :-)
You need to use '+%-d' in $( date ). By default 0-padded values are returned by %d and they will be assumed to be in octal due to the leading 0. Long story short 08 and 09 will fail.

```
$ [[ $( date -d '14 days ago' +%d ) -eq 1 ]] && echo true || echo false
bash: [[: 08: value too great for base (error token is "08")
false
$ [[ $( date -d '14 days ago' +%-d ) -eq 1 ]] && echo true || echo false
false
```
alternatively going back to string comparison = and testing for 01 would be ok too.


(()) version of if would be
```
dayofmonth=$(date +%-d)
if ((dayofmonth==1)); then
  stuff
else
  other stuff
fi
```

> Converting my [[ test ]] to your example is causing me pause...
And I didn't expect "that"!

care to explain? you mean you tried to use that pseudo-if/else utilizing &&/|| shortcircuiting and it failed in your code?
That construct is kinda like if/else but not really and there are caveats. Either way it's much shorter to type if you are only concerned with the validity of the condition itself.

---

### Post by Habitual on 2014-05-22
> **Vaphell said:**
> You need to use '+%-d' in $( date ). By default 0-padded values are returned by %d and they will be assumed to be in octal due to the leading 0. Long story short 08 and 09 will fail.
...
```
dayofmonth=$(date +%-d)
if ((dayofmonth==1)); then
  stuff
else
  other stuff
fi
```

care to explain? you mean you tried to use that pseudo-if/else utilizing &&/|| shortcircuiting and it failed in your code?
That construct is kinda like if/else but not really and there are caveats. Either way it's much shorter to type if you are only concerned with the validity of the condition itself.You cause me to wonder if I know anything really about bash scripting, is all. An "I didn't think of that?" moment.
Your pseudo-if/else worked fine. Less typing is what it all about after 20 years in IT.

Thanks for the assist!

You rock!

---

### Post by Habitual on 2014-05-22
Here's what I have so far:
```
export AMIDATE=$(date '+%m%d%Y')
export DAYOFMONTH=$(date +%-d)
export FTBLOG=/path/to/log
echo "$AMIDATE" > "$FTBLOG"


function usual()
{
export DESCRIPTION="automated backups"
ec2-create-image i-ea124bac --name "$AMIDATE""_db1-Master_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
ec2-create-image i-e134e2b8 --name "$AMIDATE""_MongoDB_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
ec2-create-image i-1a565643 --name "$AMIDATE""_NFS_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
ec2-create-image i-6278dc78 --name "$AMIDATE""_Sphinx_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
...
mail -s "Automated Backups" user@domain.com <  "$FTBLOG"
}

function other()
{
export DESCRIPTION="30_60 Day Archive"
ec2-create-image i-ea124bac --name "$AMIDATE""_db1-Master_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
ec2-create-image i-e134e2b8 --name "$AMIDATE""_MongoDB_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
ec2-create-image i-1a565643 --name "$AMIDATE""_NFS_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
ec2-create-image i-6278dc78 --name "$AMIDATE""_Sphinx_Backup" --description "$DESCRIPTION" --no-reboot >> "$FTBLOG"
...
mail -s "30_60 Day Archives" user@domain.com <  "$FTBLOG"
}

if ((DAYOFMONTH==1)); then
  do usual 
else
  do other 
fi
```

Then I just alter my delete script (you helped me out [there]("http://ubuntuforums.org/showthread.php?t=2164483") as well) to ignore anything with "Archive" in it and I should be good to go!

Thanks!

---

### Post by Vaphell on 2014-05-22
looks kinda redundant ;-) granted, i may be missing some details, but that code could be more or less written along the lines of

```
declare -A back=( [i-ea124bac]=db1-Master_Backup
                  [i-e134e2b8]=MongoDB_Backup
                  [i-1a565643]=NFS_Backup
                  [i-6278dc78]=Sphinx_Backup )

backup()
{
    echo "$1"
    for k in ${!backup[@]}
    do
        ec2-create-image "$k" --name "${1}_${back[$k]}" --description "$2" --no-reboot
    done
}

((DAYOFMONTH==1)) && DESC="automated backups" || DESC="30_60 Day Archive"

backup "$AMIDATE" "$DESC" | mail -s "$DESC" user@domain.com 
```

---

### Post by Habitual on 2014-05-23
> **Vaphell said:**
> looks kinda redundant Don't it though? Just means "room for improvement" ;)
After work and before bed, I was thinking something like this:
<snipped>
Thanks for all your input so far.

so far, this seems to be a "go"
```
#!/bin/bash
export TERM=linux
export AWS_ACCESS_KEY=
export AWS_SECRET_KEY=
export EC2_URL=
export EC2_HOME=/home/c9admin/ec2/ec2-api-tools/ec2-api-tools-1.6.6.3
export PATH=$PATH:$EC2_HOME/bin
export JAVA_HOME=/usr
export FTBLOG=/path/to/log.log

export AMIDATE=$(date '+%m%d%Y')
export DAYOFMONTH=$(date +%-d)
echo "$AMIDATE" > "$FTBLOG"

function do_work()
{
ec2-create-image i-ea124bac --name "$AMIDATE""_db1-Master_Backup" --description "$DESCR" --no-reboot >> "$FTBLOG"
ec2-create-image i-es34e2b8 --name "$AMIDATE""_MongoDB_Backup" --description "$DESCR" --no-reboot >> "$FTBLOG"
ec2-create-image i-ea565643 --name "$AMIDATE""_NFS_Backup" --description "$DESCR" --no-reboot >> "$FTBLOG"
ec2-create-image i-ea78dc78 --name "$AMIDATE""_Sphinx_Backup" --description "$DESCR" --no-reboot >> "$FTBLOG"
...
mail -s "$SUBJECT" [EMAIL="user@domain.com"]user@domain.com[/EMAIL] <  "$FTBLOG"
}

if ((DAYOFMONTH==1)); then
    export DESCR="30/60 Day Archives"
    export SUBJECT="FTB AMI 30_60 Archives"
    do_work
else
    export DESCR="automated backups"
    export SUBJECT="FTB AMI Backups"
    do_work
fi
#EOF

```

---

### Post by ofnuts on 2014-05-23
Log to file and use "tail -f" if you want to see the output in real-time?

---

### Post by Vaphell on 2014-05-23
do you really need the file? It looks like it gets overwritten on each run so most likely it's just a vessel that stores text for email at the end.


that block of almost identical
```
ec2-create-image i-ea124bac --name "$AMIDATE""_db1-Master_Backup" --description "$DESCR" --no-reboot >> "$FTBLOG"
```
really really begs to be rolled up into the loop.

---

### Post by Habitual on 2014-05-23
re-edited [post #8]("http://ubuntuforums.org/showthread.php?t=2225622&p=13031309#post13031309")
reload the page please, and thanks!

---

### Post by Vaphell on 2014-05-23
is there a reason why you use export that much? You could just pass params to function, use $1 $2 there and be done with it.

```
do_stuff() { something_with "$1" "$2"; }

if ???; then
    do_stuff "abc" "ABC"
else
    do_stuff "def" "DEF"
fi
```

Also you really should extract the identifiers/names to a dedicated array. It's a part of the config, so it should be in a prominent place, not buried inside the nearly identical lines.

And i still don't know if you need the file or not. Piping could be used instead if the persistence is not required.

---

### Post by Habitual on 2014-05-23
> **Vaphell said:**
> is there a reason why you use export that much?  Habit.

Thanks.

---

### Post by Habitual on 2014-06-01
I went another "way on my delete script:
Since ```
date +"%m%d%Y"
``` gives us mmddyyyy format, We can exclude ***any*** first of the month with ```
grep -v $(date +'01'%Y)
```
in the DATES= assignment.


```
DATES=$(for i in 2 3 ; do date +"%m%d%Y" --date="$i days ago"; done | grep -v $(date +'01'%Y)) # we exclude 01yyyy 
IMAGES=$(ec2-describe-images | awk '{print $2 " "$3}' | grep "$DATES" | awk '{print $1}')
if ((IMAGES=='')) ; then
    exit
else
    SNAPSHOTS=$(ec2-describe-images $IMAGES | grep snap | awk '{print $4}')
    DE_REGISTER
    DEL_SNAPSHOTS
    mail -s "subject here" user@domain.com <  "$REPORT" 
fi

```

---


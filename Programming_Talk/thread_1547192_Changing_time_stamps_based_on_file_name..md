---
title: "Changing time stamps based on file name."
date: 2010-08-06
forum: Programming Talk
---

### Post by leech on 2010-08-06
So we noticed a problem on our server.

We have a script that cleans up old files, based on the +mtime.  

Somewhere along the lines something has caused the time stamp on folders, but not the files inside them to be changed, so this clean up script doesn't work as it should.

So I'm trying to create a script that will modify all the time stamps to what they should be.

The folders all come across as EOM080510 (for example).  There are other folders, some with only two characters, but most with three in these directories.  What I would like the script to do is take the date from the file name (in the example, that's August 5th, 2010) and change the modified time to that date.

This is what I have so far.  the DM0 and DM1 are the ones that have only two characters, so I grep them out to get the correct date.  Later I can write a loop for them too.  The problem is with this currently, it only does the first line.  The ls -1 lists the dates like this;

080410
080510

```
#!/bin/sh
#for /r %f in (EOM??????) touch /d%@left[8,%@name]] %f
date1=`ls -1|grep -v DM0|grep -v DM1|grep -v sh|cut -c 4-9`
#echo $date1
#files1=`ls -1|grep -v DM0|grep -v DM1|grep -v sh`
for folders in "$date1"
do 
        Mth=`echo $date1 |cut -c 1-2`
        Day=`echo $date1 |cut -c 3-4`
        Year=`echo $date1 |cut -c 5-6`
        echo "${Mth}/${Day}/${Year}"
done
#echo "$files1"

```

I haven't gotten quite to where I would need to change the actual timestamps, the reason I was going this route is because touch does not recognize 080510 as a valid date string, it has to be 08/05/10.

Any clues, ideas on how to do this easily?  I've googled it, but unfortunately the only line I found that should work didn't.

```
for /r %f in (??-??-??-??.jpg) touch /d%@left[8,%@name]] %f
```

Any ideas?

Many thanks appreciated.

leech

---

### Post by dwhitney67 on 2010-08-06
Could you post a tar-ball with the directory (folder) structure, containing dummy files.

Then, please enumerate the requirements that the script must perform.  I did not fully understand what these are from your OP.

I would suggest that if possible, you define the dates within your folder names to be in the format of YYMMDD.  It is easier to sort when using this format, should the need arise.  Also, this is the default format accepted by the "touch" command.  Otherwise you are relegated to picking apart the date to obtain the year, month, and day to specify the date with the slashes.  For example:
```

touch -d 100805 file     # If using YYMMDD

touch -d 08/05/10 file   # If using MM/DD/YY

```

---

### Post by leech on 2010-08-06
Directory structure is fairly simple.

There are multiples of each folder.

They are in the format of EOM, EDM, EDR, etc.  WIth a date like MMDDYY after each.

```
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-08-01 03:53 EOD073110A
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-08-03 02:29 EOD080210
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-08-03 23:23 EOD080310
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-08-04 23:26 EOD080410
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-08-05 23:23 EOD080510
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM013109
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM013110
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM022809
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM022810
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM033109
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM033110
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM043009
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM043010
drwxr-xr-x 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM053109
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-07-13 08:33 EOM053110
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:14 EOM063008
drwxr-xr-x 2 ftpuser ftpgroup 4096 2009-08-04 10:14 EOM063009
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-07-13 08:33 EOM063010
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM073108
drwxr-xr-x 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM073109
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-08-02 22:11 EOM073110
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM083108
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM083109
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM093008
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM093009
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM103108
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM103109
drwxrwxrwx 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM113008
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM113009
drwxr-xr-x 2 ftpuser ftpgroup 4096 2009-08-04 10:17 EOM123108
drwxr-xr-x 2 ftpuser ftpgroup 4096 2010-05-13 07:54 EOM123109
drwxr-xr-x 2 ftpuser ftpgroup  133 2010-01-31 03:42 EPI013110

```

As you can see, the one folder that is EOM113008 has the timestamp of 2009-08-04.  I would like it to be changed to 2008-11-30.  Along with fixing the other ones.  

'date' is thoroughly awesome and has a billion different ways to use it.  Unfortunately touch is pretty picky, will do YYMMDD or MM/DD/YY but not MMDDYY like I need.

Thanks for the help.

leech

---

### Post by dwhitney67 on 2010-08-06
See if this will work for you:
```

#!/bin/bash

set -e

dirs=`find . -type d`

for dir in $dirs
do
        if [ "$dir" != "." ]
        then
                basedir=`basename $dir`   # remove the preceding ./

                if [ "$basedir" != "DM0" -a "$basedir" != "DM1" ]
                then
                        date=`echo $basedir | cut -c 4-`

                        MM=`echo $date | cut -c 1-2`
                        DD=`echo $date | cut -c 3-4`
                        YY=`echo $date | cut -c 5-6`

                        echo "Changing date for $dir to $MM-$DD-$YY... "

                        touch -d $YY$MM$DD $dir
                fi
        fi
done

```

---

### Post by leech on 2010-08-06
That works perfect, except for the DM0 and DM1 exceptions.

These will also need to be added in, but I just thought it'd be simpler to use cut to get the dates out.  The DM folders will have need to have the date stamp fix as well, just to make sure we got all the files  (pretty sure the DM ones are the only other files with the 2 Letter + date format)

I'm wondering if the find command has something that would allow a pattern of alpha-numeric matching.  like a AA000000 or AAA000000.  There are also some that have a trailing A or B (I don't think any go beyond that) but the way it's working so far, it's the characters 4-9 or 3-8 for the DMxxxx ones.

Thanks for all your help.

leech

---

### Post by dwhitney67 on 2010-08-07
> **leech said:**
> ...pretty sure the DM ones are the only other files with the 2 Letter + date format...

Earlier you implied that the "DM" directories included a 0 or a 1 in their names, and that you were not interested in them.  Above you are indicating that they actually have a 6-digit date.  Which is it?

If you cannot provide specific/detailed requirements, then you may never get the proper help you need for this script.

Btw, the 'find' command does support the usage of regular expressions, thus this might help you narrow the pool of results to those you require.

For now, I'll *assume* that all of the directories of interest are names with either 2 or 3 characters, followed by a 6-digit date.  Any other files or directories not meeting this criteria are ignored.  If this assumption is correct, then perhaps the following may work for you... but there is no guarantee without having the full requirements!
```

#!/bin/bash

set -e

dirs=`find . -type d -regex '.*[0-9][0-9]*.'`    # Dir must have at least 2 digits in name

for dir in $dirs
do
        date=`echo $dir | awk -F[A-Z] '{print $3}'`

        if [ "$date" == "" ]
        then
                date=`echo $dir | awk -F[A-Z] '{print $4}'`
        fi

        MM=`echo $date | cut -c 1-2`
        DD=`echo $date | cut -c 3-4`
        YY=`echo $date | cut -c 5-6`

        echo "Changing date for $dir to $MM-$DD-$YY... "

        touch -d $YY$MM$DD $dir
done

```

---

### Post by leech on 2010-08-07
I apologize if it sounded like I needed to ignore the DM files, and yes they have a 6 digit date as well.

Here is one example of an entire directory, and yes all of the one with dates would need to be fixed.  Still trying to figure out how they were even changed, the files within, as stated previously.

```
BASEFLEX  CBR062910  DM071410   EDR033110   EOD080210   PID051310
BOM013110   CBR063010  DM071510   EDR043010   EOD080310   PID051410
BOM022810   CBR070110  DM071610   EDR053110   EOD080410   PID051710
BOM033110   CBR070210  DM071910   EDR063009   EOD080510   PID051810
BOM043010   CBR070610  DM072010   EDR063010   EOD080610   PID051910
BOM053110   CBR070710  DM072110   EDR073109   EOM013110   PID052010
BOM063009   CBR070810  DM072210   EDR073110   EOM022810   PID052110
BOM063010   CBR070910  DM072310   EDR083109   EOM033110   PID052410
BOM073109   CBR071210  DM072610   EDR093009   EOM043010   PID052510
BOM073110   CBR071310  DM072710   EDR103109   EOM053110   PID052610
BOM083109   CBR071410  DM072810   EDR113009   EOM063009   PID052710
BOM093009   CBR071510  DM072910   EDR123109   EOM063010   PID052810
BOM103109   CBR071610  DM080210   EOD030810   EOM073109   PID052810A
BOM113009   CBR071910  DM080310   EOD030910   EOM073110   PID060110
BOM123109   CBR072010  DM080410   EOD052610   EOM083109   PID060210
CBR042610   CBR072110  DM080510   EOD052710   EOM093009   PID060310
CBR042710   CBR072210  DM080610   EOD052810   EOM103109   PID060410
CBR042810   CBR072310  DR062210   EOD052810A  EOM113009   PID060710
CBR042910   CBR072610  DR062910   EOD060110   EOM123109   PID060810
CBR043010   CBR072710  DR070610   EOD060210   EPI013110   PID060910
CBR050310   CBR072810  DR071310   EOD060310   EPI022810   PID061010
CBR050410   CBR072910  DR072010   EOD060410   EPI033110   PID061110
CBR050510   CBR080210  DR072710   EOD060710   EPI043010   PID061410
CBR050610   CBR080310  DR080310   EOD060810   EPI053110   PID061510
CBR050710   CBR080410  DRH062210  EOD060910   EPI063009   PID061610
CBR051010   CBR080510  DRH062910  EOD061010   EPI063010   PID061710
CBR051110   CBR080610  DRH070610  EOD061110   EPI073109   PID061810
CBR051210   DM052610   DRH071310  EOD061410   EPI073110   PID062110
CBR051310   DM052710   DRH072010  EOD061510   EPI083109   PID062210
CBR051410   DM052810   DRH072710  EOD061610   EPI093009   PID062310
CBR051710   DM052810A  DRH080310  EOD061710   EPI103109   PID062410
CBR051810   DM060110   ECB013110  EOD061810   EPI113009   PID062510
CBR051910   DM060210   ECB022810  EOD062110   EPI123109   PID062810
CBR052010   DM060310   ECB033110  EOD062210   fvrxml      PID062910
CBR052110   DM060410   ECB043010  EOD062310   GLE013110A  PID063010
CBR052410   DM060710   ECB053110  EOD062410   GLE022810A  PID070110
CBR052510   DM060810   ECB063009  EOD062510   GLE033110A  PID070210
CBR052610   DM060910   ECB063010  EOD062810   GLE043010A  PID070610
CBR052710   DM061010   ECB073109  EOD062910   GLE053110A  PID070710
CBR052810   DM061110   ECB073110  EOD063010   GLE063009A  PID070810
CBR052810A  DM061410   ECB083109  EOD070110   GLE063010A  PID070910
CBR060110   DM061510   ECB093009  EOD070210   GLE073109A  PID071210
CBR060210   DM061610   ECB103109  EOD070610   GLE073110A  PID071310
CBR060310   DM061710   ECB113009  EOD070710   GLE083109A  PID071410
CBR060410   DM061810   ECB123109  EOD070810   GLE093009A  PID071510
CBR060710   DM062110   EDM013110  EOD070910   GLE103109A  PID071610
CBR060810   DM062210   EDM022810  EOD071210   GLE113009A  PID071910
CBR060910   DM062310   EDM033110  EOD071310   GLE123109A  PID072010
CBR061010   DM062410   EDM043010  EOD071410   PID042610   PID072110
CBR061110   DM062510   EDM053110  EOD071510   PID042710   PID072210
CBR061410   DM062810   EDM063009  EOD071610   PID042810   PID072310
CBR061510   DM062910   EDM063010  EOD071910   PID042910   PID072610
CBR061610   DM063010   EDM073109  EOD072010   PID043010   PID072710
CBR061710   DM070110   EDM073110  EOD072110   PID050310   PID072810
CBR061810   DM070210   EDM083109  EOD072210   PID050410   PID072910
CBR062110   DM070610   EDM093009  EOD072310   PID050510   PID080210
CBR062210   DM070710   EDM103109  EOD072610   PID050610   PID080310
CBR062310   DM070810   EDM113009  EOD072710   PID050710   PID080410
CBR062410   DM070910   EDM123109  EOD072810   PID051010   PID080510
CBR062510   DM071210   EDR013110  EOD072910   PID051110   PID080610
CBR062810   DM071310   EDR022810  EOD073010   PID051210   startftp.txt

```

All are directories, except startftp.txt and fvrxml.  

The last script didn't seem to work either.  It stopped on the first line.  Doesn't make much sense, since running

```
find . -type d -regex '.*[0-9][0-9]*.' |awk -F[A-Z] '{print $4}'
```

or with print $3 works perfectly in grabbing the dates.  Somewhere the script doesn't remove the AAA or AA from the folder name and just errors out when trying to run touch -d.

This is awesome so far, and I feel that we are very close on this.

Thanks a million again for all the help.

leech

---

### Post by dwhitney67 on 2010-08-07
I ran the script with the listing of directories and files that you provided in your previous post, and it (appears to have) worked fine.

Is it possible that you may have copied the *second* script incorrectly?

I've attached three files; the first contains the output generated by the script, the other two contain the long-listing of info of the directory contents after running the script.

P.S.  The long-listing of the directory contents was placed into two files so that I could meet size-limits imposed by the Ubuntu Forum for posting text (.txt) files.

------
EDIT:

If your directories have within them sub-directories, of which you do not want to process, then you need to limit the maximum depth that the 'find' command will search.  To examine only the current directory, the script would need to be modified as such:
```

...

dirs=`find . **-maxdepth 1** -type d -regex '.*[0-9][0-9]*.'`    # Dir must have at least 2 digits in name

...

```

---

### Post by leech on 2010-08-07
Well I'll be damned.  

So I kind of noticed this last night, and indeed thought it was odd looking before.

The ls -l command on Debian Squeeze (which is what I am running on my workstation and my system at home that I'm typing this on now) has quite the different output.

-rw-r--r-- 1 root  root         19 10.07.2010 14:26 resolv.conf

As you can see, the date stamp is 10.07.2010.  Now I wouldn't have thought this would affect this particular problem, since we weren't really parsing that bit anyhow.

But Debian Squeeze also uses bash 4.1.5.  Lenny is using bash 3.2.39.  I was looking at you script for hours last night thinking, that should work, why is it giving me this unexpected operator?

The output from the script on Debian Squeeze is 

```
[: 23: unexpected operator
Changing date for ./CBR061610 to --... 
touch: invalid date format `./CBR061610'
```

I was thinking I may need to add in the -maxdepth as well.  

So out of curiosity, what version of Bash are you using?

You rule, by the way!  Thanks a million.  Explains why I was 'bashing' my head against the wall on this...  Ok, I apologize for the horrible pun.  Was up 'til 3am last night talking to an old friend and worked a bit more on this.  5 hours of sleep... I feel like a full fledged programmer!  

Now I'll need to figure out why Debian Squeeze has such an odd output.  Much like Ubuntu, it's switched to using dash as the shell, but a simple ls -l has changed it's format?  How odd.

leech

P.S. I figured out why it was doing it that way.  I had my .bashrc from Arch Linux from when I was dabbling with that.

---

### Post by dwhitney67 on 2010-08-07
Here's the version of bash I' running on Ubuntu 9.10:
```

bash -version
GNU bash, version 4.0.33(1)-release (i486-pc-linux-gnu)
...

```
Make sure you always specify "#!/bin/bash" in your scripts, because not all Linux distros link /bin/sh to /bin/bash.  Ubuntu is one of these distros.

You may also want to verify that you have Bash installed on your system; for all you know, /bin/bash may be linked to /bin/dash!

Also, verify your LANG environment variable setting.  I'm located in the US, so this is my setting:
```

env | grep LANG
LANG=en_US.UTF-8

```

P.S. On my system:
```

ls -l /etc/resolv.conf 
-rw-r--r-- 1 root root 78 2010-07-31 13:54 /etc/resolv.conf

```

---

### Post by leech on 2010-08-07
Interesting, they must have changed something.  I had previously verified, /bin/sh is a link to /bin/dash (so I was specifically using /bin/bash to cover the 'bashisms'), but even after copying my /etc/skel/.bashrc file into my home directory so now the date doesn't display as it was, it now displays as this;

```
-rw-r--r-- 1 root root 72 Aug  6 15:35 /etc/resolv.conf
```

I checked the LANG environment variable and it to is en_US.UTF-8.

Now if I put in a -x when running the script (sh -x test.sh)

I get the output of all the directories as ./AAA000000 (the A as letters and 0 as numbers) but then after the find command, it shows;

```
+ echo ./CBR061610
+ awk -F[A-Z] {print $3}
+ date=
+ [  ==  ]
[: 1: unexpected operator
+ echo
+ cut -c 1-2
+ MM=
+ echo
+ cut -c 3-4
+ DD=
+ echo
+ cut -c 5-6
+ YY=
+ echo Changing date for ./CBR061610 to --... 
Changing date for ./CBR061610 to --... 
+ touch -d ./CBR061610
touch: invalid date format `./CBR061610'
```

The different bash versions are 4.1.5 (doesn't work), 3.2.39 (Does work) and 3.1.17 (Old SLES 10 box which I'm replacing soon, works great).

Did they change something in Bash 4.1.x?

Time to do some more digging, I guess.  touch -d YYMMDD still works fine, but it's the part in the script where we use awk to make $date that is broken.

I just fixed it...  apparently in bash 4.1.x they changed the == to only need =.  Once I removed that second =, it worked perfectly.

Reminds me of Asterisk where 1.4.29 supported DB_del just fine, then Asterisk 1.4.32 complains that DB_del is deprecated and I should use Del_DB (well that's an example, I can't recall the actual syntax right now.)

Thanks a million again.  I can't believe it was something so simple.  So much for assuming Bash doesn't change all too often....

leech

---


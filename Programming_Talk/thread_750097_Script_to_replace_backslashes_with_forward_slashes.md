---
title: "Script to replace backslashes with forward slashes"
date: 2008-04-09
forum: Programming Talk
---

### Post by apoth on 2008-04-09
I need to recurse through some folders and replace any backslashes with forward slashes (Windows path names to Unix) in file contents.

It should just be a one liner but I'm useless with sed/awk and regexps in general. Can anyone offer a solution? Thanks.

---

### Post by ghostdog74 on 2008-04-09
show a listing of how your directory and files look like

---

### Post by apoth on 2008-04-09
```
$ find . -type f -name "*.html"
./spacer.html
./subscriptionprofile/subscriptionprofile_associations.html
./subscriptionprofile/subscriptionprofile_01.html
./subscriptionprofile/subscriptionprofile_costassociation_cod.html
./subscriptionprofile/subscriptionprofile_costassociation_btv.html
./subscriptionprofile/subscriptionprofile_costassociation.html
./broadcast/channel_01.html
./broadcast/broadcast_associations.html
./broadcast/package_01.html
./broadcast/event_01.html
./broadcast/program_01.html
./broadcast/category_01.html
./Banner.html
./ondemand/catalogue_01.html
./ondemand/schedule_01.html
./ondemand/catalogue_schedule_scenario_01.html
./ondemand/asset_01.html
./ondemand/assetgroup_01.html
./ondemand/ondemand_associations.html
./[TUT-003] - QSP Overview Presentation.html
./rating/rating_01.html
./rating/rating_associations.html
./acl/acquiredcontentlist_01.html
./acl/acquiredcontentlist_02.html
./acl/acquiredcontentlist_03.html
./acl/acl_associations.html
./devices/feature_01.html
./devices/deviceprofile_01.html
./devices/applicationserver_01.html
./devices/devicegroup_01.html
./devices/deviceclassifier_01.html
./devices/settopbox_01.html
./devices/devices_associations.html
./devices/streamingserver_01.html
./general/acquireable_01.html
./general/chargeability_01.html
./general/subscribeable_01.html
./general/chargeability_associations.html
./general/audiovariants.html
./general/overview.html
./general/content_children_01.html
./general/languagevariants.html
./general/commonattributes.html
./general/content_parents_01.html
./Framework.html
./policygroup/policygroup_01.html
./policygroup/policyoftypebaseprice_01.html
./policygroup/policygroup_associations.html
./policygroup/policyoftypeother_01.html
./policygroup/policygroup_scenario_01.html
./policygroup/interval_01.html
./LinksTable.html
./blank.html
./accesspoint/accesspoint_associations.html
./accesspoint/accesspoint_01.html
./account/account_01.html
./account/account_associations.html
./account/user_01.html
```

---

### Post by ghostdog74 on 2008-04-09
it pays to describe what you want to do properly, right.
```

# find . -name "*.jpg" | awk '{gsub("/","\\")}1'

```

---

### Post by apoth on 2008-04-09
> **ghostdog74 said:**
> it pays to describe what you want to do properly, right.

Not sure what you mean.

> **ghostdog74 said:**
> 
```

# find . -name "*.jpg" | awk '{gsub("/","\\")}1'

```

I couldn't get that working when I tested it, although this works:

```
echo "test\test" | awk '{ gsub(/\\/, "/"); print }'
```

I just need to get it to read in the contents of each of those files, run this against the contents and then spit it out to the same file now.

---

### Post by ghostdog74 on 2008-04-09
how did you get the windows slash ?? are you running the command on windows?? why don't you show what's not working?

---

### Post by apoth on 2008-04-09
These are existing documents created on a Windows machine using Windows file paths for the links. Not that I'm sure that how the slashes got there is of any relevance.

No, I'm running the command on linux.

What do you mean by what's not working? I'm asking for a script to be created for this purpose, I don't have an existing script for the job that doesn't work?

---

### Post by ghostdog74 on 2008-04-09
> **apoth said:**
> These are existing documents created on a Windows machine using Windows file paths for the links. Not that I'm sure that how the slashes got there is of any relevance.

No, I'm running the command on linux.

What do you mean by what's not working? I'm asking for a script to be created for this purpose, I don't have an existing script for the job that doesn't work?


first you said you need to recurse a directory and subdirectories in linux and replace "\" with "/" , correct ?
In *nix, the paths are all "/", as shown by your own "find" results a few posts back. so i ask you again, where is the windows file path with "\" you got from?describe your problem and what you want to do properly.

---

### Post by WW on 2008-04-09
ghostdog74: In the first line of the original post, apoth says he wants to change backslashes to slashes in the *contents* of the files.

apoth:  This will change *every* occurrence of \ to / in all the .html files in the current directory and all subdirectories.  It will also make backups of the originals with a tilde (~) added to the original file name.
> 
$ find . -name "*.html" -type f -exec sed 's/\\/\//g'  '{}'  -i~ \;

It is similar to the find command that you used above, but it uses the **-exec** option to execute a command on each file found.  The command is sed. The first argument of the sed command is 's/\\/\//g', which will substitute all occurrences of \ with /.  The -i~ option tells sed to make the substitution "in place", and make a backup with the extension ~.

---

### Post by murphlaw on 2008-04-09
**"an awk way"**

```

find -name "*.html" -type f | while read file
do 
  awk '{ gsub( /\\/, "/" ); print }' $file > $file.$$
  mv $file.$$ $file
done

```

---

### Post by apoth on 2008-04-09
Both great solutions, thanks guys.

---

### Post by subverted on 2008-07-11
> **murphlaw said:**
> **"an awk way"**

```

find -name "*.html" -type f | while read file
do 
  awk '{ gsub( /\\/, "/" ); print }' $file > $file.$$
  mv $file.$$ $file
done

```

How about something completely different? 

I'm using Vim to edit websites and like to test them in various browsers with:

:!firefox %

But using ies4linux it doesn't work because there are backslashes that vim can't interpret, so I need a script to reverse the forward slashes to backslashes as the file is called. Something like:
```

#!/bin/sh

for i in "$@"
do
  a="$a 'echo "$i"|sed -e 's#/#\\#g<CR>'"
done

eval ie6 $a 
```

Ha! Is that even remotely possible? or is there some regular expression for Vim that I am unaware of that would do the trick?

---

### Post by silentrebel on 2009-10-09
When I use this method:
```

$> hello="dkfafd\dklfafd\kdfasdfa"
$> goodbye=`echo $hello | awk '{ gsub( /\\/, "/" ); print }'`
```

I get:
```

awk: { gsub( /\/, "/" ); print }
awk:                ^ unterminated string

```

I cannot figure out why!


------------------------------------------------------------
I was also wondering if this expression would equally work...:
```
awk '{ gsub( "\\", "/" ); print }'
```
Thanks

---

### Post by ghostdog74 on 2009-10-09
> **silentrebel said:**
> When I use this method:
```

$> hello="dkfafd\dklfafd\kdfasdfa"
$> goodbye=`echo $hello | awk '{ gsub( /\\/, "/" ); print }'`
```

I get:
```

awk: { gsub( /\/, "/" ); print }
awk:                ^ unterminated string

```

I cannot figure out why!


------------------------------------------------------------
I was also wondering if this expression would equally work...:
```
awk '{ gsub( "\\", "/" ); print }'
```
Thanks

change your backticks to $() syntax.
```
g=$(echo $hello | awk '{ gsub( /\\/, "/" ); print }')


```

---

### Post by diesch on 2009-10-09
```
find -type f -exec perl -i -pe's:\\:/:g' {} \;
```

---

### Post by silentrebel on 2009-10-09
This advice worked perfectly:
> **ghostdog74 said:**
> change your backticks to $() syntax.
```
g=$(echo $hello | awk '{ gsub( /\\/, "/" ); print }')

```

For the record, 
```
goodbye=`echo $hello | awk '{ gsub("\\", "/"); print }'`
```
does not work, as I thought it might...

Could anyone tell me why the backticks do not work here?:
```
goodbye=`echo $hello | awk '{ gsub(/\\/, "/"); print }'`
```

---


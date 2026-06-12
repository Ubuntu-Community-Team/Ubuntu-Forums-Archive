---
title: "Better way ? md5sum on a dir with sub-dirs and files..."
date: 2009-12-26
forum: Programming Talk
---

### Post by iMisspell on 2009-12-26
I would like to run a md5 check on a dir which has many sub-dirs and files inside to find out if any file has been changed, renamed, deleted or added (and ive found this is not possible ;) ).

This script is being used to back-up files, the script is being run nightly as a cron-job.

So, here is what im currently doing (in a bash script) and im wondering if there is a better way. 

Creating a "md5sum" log file with...
```
find "$wiki_path/$extensions_path/${extension[${i}]}" -type f | xargs -i md5sum "{}" > "$currentDir/md5/current/${extension[${i}]}.log";
```
That log is saved to **md5/current/*.log**
Then i run md5sum on that file which was just created...
Run a md5sum on **md5/last/*.log** which is the same log as above but copied over to a different dir (at the end of the script, a day before)...
Compare the two, if different then "do the work needed".

Heres a snippet of the code...
```

	find "$wiki_path/$extensions_path/${extension[${i}]}" -type f | xargs -i md5sum "{}" > "$currentDir/md5/current/${extension[${i}]}.log";
	
	test1=`md5sum "$currentDir/md5/current/${extension[${i}]}.log" | awk '{print $1}'`;
	
	test2='';
	if [[ -e "$currentDir/md5/last/${extension[${i}]}.log" ]] ; then
		test2=`md5sum "$currentDir/md5/last/${extension[${i}]}.log" | awk '{print $1}'`;
	fi
	
	if [ "$test1" != "$test2" ]; then
	   
# do the work needed because they are different
		
	fi
	
	cp "$currentDir/md5/current/${extension[${i}]}.log" "$currentDir/md5/last/${extension[${i}]}.log"
	

```

Ive just been testing this out and its seams to be working well, just wondering if there is a better way.

Thanks for any advice.
--------------------------------

Here is the full story if you fell like reading and maybe offering any insight...

First; im new to linux, been a "day-to-day" desktop user for only a few months and have been running a ubuntu server for alittle over a year, but it was only being used as a MySQL, Apache and File server - so i have a lot to learn.

I have a few Mediawiki Extensions which ive developed and a couple more in the works, each extension has a number of files. A few months back i start to create back-ups of each extension, the back-up script runs nightly via cron-job. As of now im just creating a '.tar.bz2' for each extension - *extention_name-ver-yyyy-mm-dd.tar.bz2*. At the first of every month another cron-job runs, takes all the *extention_name-ver-yyyy-mm-dd.tar.bz2* and saves them as a single, */yyyy/mm/extention_name.tar.bz2* and then goes back and deletes all the old months tarballs.

There can be days, weeks or even months which i will not touch a particular extension, but with the current method im using to back up stuff, the untouched extensions are still being backed up which does not make sence to me.

So the above idea popped into my head, and here i am :)


_
_

---

### Post by monkeyking on 2009-12-26
I don't know if I understand correctly,
but do you know you can run md5sum -c .log.

This will calculate the md5sum for all entries and compare them?

---

### Post by iMisspell on 2009-12-26
> **monkeyking said:**
> I don't know if I understand correctly
In short, i would like to make a copy of a dir only if something has changed (file has been edited, deleted, checked, added, etc.) with the dir from the last time it was checked.

So i thought if i run a md5 on the dir, save the check-sum, i can use that saved check-sum next time the dir is checked, if the checksums are different then copy the dir, if they are the same no file has been changed so no work needs to be done.

Looking into md5sum -c (thanks) now, dont know anything about it.
I did try this but returned an error:
```
	test1=`md5sum -c "$wiki_path/$extensions_path/${extension[${i}]}/" | awk '{print $1}'`;
	
	echo "$test1";
```> md5sum: /var/www/mw/extensions/said_dir_name: read error


_

---

### Post by monkeyking on 2009-12-26
The paths in the md5sum.log
should match to the files.
So if you want to use that approach,
you need to change the entries in the .log file.
There is daemon somewhere, that there has to be 2spaces atleast between the file and the md5sum.
Or something like that.

On the otherhand
If you just want copy the changed files.

I would just use rsync,
which will only update the changed files

good luck

---

### Post by iMisspell on 2009-12-26
Thanks alot for the '*md5sum -c*' tip.
As of now, it does not change the current method of my back-up (for the lack of words) but does add to it, which is good.

I do not want to use rsync (i dont think anyway, will look into it farther though) because i dont want to keep "updating" a saved back-up, i want to create a completely new back-up if something has changed in the original dir which holds the "working" files.

But now with 'md5sum -c' i can run the code below and have a simple log file of what has changed and i can save that log with extension's back-up as an easy way to tell what files have been changed if i ever needs to.
```
md5sum -c "$currentDir/md5/current/${extension[${i}]}.log" | grep FAILED$ > "$currentDir/${extension[${i}]}.changed";
```

Now with that - something else just popped into my head...
While im comparing the md5sum's of **md5/current/*.log** and **md5/last/*.log** do a check on these two logs for any new files or any files which have been deleted and add that info to the "md5sum -c changed.log".

Thanks alot for your input.

_

---

### Post by monkeyking on 2009-12-26
There are many different ways to do that,
I think I would use the command 'diff' which will tell you the difference betweeen 2 files.
But this can be tedious parsing.

The way to go would be setting up cvs or similar, but thats in the long run.
I might be overkill for this.

---

### Post by iMisspell on 2009-12-26
I have a perl script ive been working on for when i release updates of the extensions to include a log file of the changes from version to version using 'diff', but like said above, im new to all of these linux luxuries :)  and have not found a nice format using 'diff'.

> **monkeyking said:**
> The way to go would be setting up cvs or similar, but thats in the long run.
I might be overkill for this.
You are right about this, ive just been lazy about it :(
Maybe now is time to do that.

The biggest extension (and the one im the most concerned about) has roughly 75 files not counting images and .sql update files.
The other extensions have between 5-30. So a versioning system would make most sence.

_

---

### Post by Arndt on 2009-12-27
> **iMisspell said:**
> 

I do not want to use rsync (i dont think anyway, will look into it farther though) because i dont want to keep "updating" a saved back-up, i want to create a completely new back-up if something has changed in the original dir which holds the "working" files.



You can use rsync to tell you whether something has changed; then you can use your own methods to actually make the backup.

---

### Post by ghostdog74 on 2009-12-27
Get a snapshot of your current directory

```

#!/bin/bash 
# bash 4.0
shopt -s globstar
for file in /path/**; do 
  [ -f "$file" ] && md5sum "$file" >> md5sum.base
done

```

To check with the snapshot
```

md5sum -c md5sum.base | awk '!/OK^/'

```

---

### Post by iMisspell on 2009-12-27
> **Arndt said:**
> You can use rsync to tell you whether something has changed; then you can use your own methods to actually make the backup.
Good to know (thanks), when i get more free time, will look into rsync more.



> **ghostdog74 said:**
> Get a snapshot of your current directory

```

#!/bin/bash 
# bash 4.0
shopt -s globstar
for file in /path/**; do 
  [ -f "$file" ] && md5sum "$file" >> md5sum.base
done

```
Scripts are running on 8.04 server, cant find bash 4 in repos (shopt -s globstar errors out).

Is what you posted any faster or better then:
```
find "/path/to" -type f | xargs -i md5sum "{}" > "out.log";
```
Right now the most files and subdirs are about 75 files total, 5-7 subdirs and 2 or 3 sub-sub-dirs.


_

---

### Post by geirha on 2009-12-27
Using find's -exec should be more efficient.
```
find /path -type f -exec md5sum {} + > out.log
```

The better way of backing up your source code though, is by putting it in a version control system (svn is fairly easy to use), and back up the vcs's database. That means you'll back up all changes done, and the accompanying metadata, like why each change was done (commit messages).

---

### Post by iMisspell on 2009-12-27
> **geirha said:**
> The better way of backing up your source code though, is by putting it in a version control system (svn is fairly easy to use), and back up the vcs's database. That means you'll back up all changes done, and the accompanying metadata, like why each change was done (commit messages).
Thanks for the -exec tip.

Installed and configured subversion last night and in the mist of learning some things now.
I know this would be the best way to go about it, but the whole 'svn add/delete/copy/move' is a real pain when you have not been doing it for years.

When i wrote php scripts in windows i would was using phpED, now with ubuntu im using phpEclipse - so i need to figure out how to get that working with Subversion which will hopefully make my life a little easier :)

It seams as if - if i move all my scripts (bash, perl, php, etc) to subversion ill have three sets of "files" after a back up is performed; the working files, the subversion files and the nightly-up files, correct ? The only problem i might have with that is the dbase back up will not be the source files will they ? Thoses back-up will only be usible via subversion, correct ? Just something new to get used to i guess.



_

---

### Post by geirha on 2009-12-28
A backup of the repository would be something like this. The dumpfile is a text file, so you can technically get all files from it, but the proper way would be to use the svn tools to put it back into an svn repository.
```

svnadmin dump /path/to/repos | gzip > "$(date +%Y%m%d)_svndump.gz"
zcat 20091228_svndump.gz | svnadmin load /path/to/repos

```

If you also want a backup of the current tree, do an export.
```
svn export file:///path/to/repos "$(date +%Y%m%d)_svnexport"
tar zcf ...

```
The difference between an export and checkout, is that the export will not contain the svn metadata (the hidden .svn-directories)

---

### Post by iMisspell on 2009-12-31
ok, have svn set up and working, but i would still like to back-up files (for now) simular to what ive been trying in this thread.

Ive ditched md5 and started to use 'rsync' (seams to be alot more consistent).

I would like to create a log file - for file changes which rsync has detected.

Is there a better way, heres what im using now (which is working).
```
rsync -azv --delete $org $save | egrep -v "^building file list|^sent |^total " > rsync.log
```
I would like the rsync.log to be clean and only have the changed, delete or added files to be listed.


_

---


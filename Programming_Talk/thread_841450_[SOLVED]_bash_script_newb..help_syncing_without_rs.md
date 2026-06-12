---
title: "[SOLVED] bash script newb..help syncing without rsync"
date: 2008-06-26
forum: Programming Talk
---

### Post by kevin1162 on 2008-06-26
hi,

let me start by saying my programming and linux knowledge/skill is VERY limited. I don't have much experience with either because it's not a large part of my job. I tinker here and there but nothing to write home about.

But due to recent events at my job i've been told i need to come up with a solution to sync a folder on one NAS to another NAS. The script has to be executed locally on each linux server because the directory setup and file access is unique to each.

I started off simple enough with my limited knowledge. I just made a BASH script that contains this then would as a cron job

```
cp -rup /nas1/dir1/* /nas2/dir2/
```

BUT then it dawned on me... If i delete a file or folder in /nas1/dir1 the old file will remain in /nas2/dir2. This is not acceptable, and this process has to be completley automated.

I can't for the life of me figure out how to do a comparison of the two directories and delete old files from /nas2/dir2... I tried looking at using diff but can't wrap my head around figuring that out.

Something like rsync isn't an option because the servers this script will be executed on 1) don't have it installed and 2) i'm not allowed to install any other software on them. So i'm stuck using a bash script or perl, and i know Zero about perl.

Normally i wouldn't ask for help in this manner but i'm under the gun and have a VERY short deadline that stops me from actually learning this. If someone could guide me i'd appreciate it.

---

### Post by geirha on 2008-06-26
Right, they want you to reinvent the wheel...

You'll need to be a bit more specific though.

1. Have you tried asking the community of the linux distribution you are working on? (What distribution is it btw?)

2. Are there any other basic unix programs missing?

3. Is the sync one way or two way?

The find command might be used to figure out which files/directories have been deleted.

---

### Post by kevin1162 on 2008-06-26
1. The servers are running Caldera OpenLinux 3.1 I couldn't google anything up on that distro other than wikipedia articles, etc.

2. Wouldn't know unless i was told what to look for.

3. the Sync is just one way, All the files from NAS1 need to be mirrored onto NAS2. The files on NAS2 will never be touched, but if something is changed on NAS1 it needs to be reflected on NAS2.

---

### Post by geirha on 2008-06-26
Syncing one way makes it a bit easier. This should list all files and directories in NAS2 that is not in NAS1. Piping it further to xargs and rm, then run your recursive copy might just do the trick. If copying everything each time the script is run is acceptable.
[php]
dir1="/nas1/"
dir2="/nas2/"

cd "$dir2"
find . -print0 | while read -d $'\0' file; do
  [ -e "$dir1/$file" ] || echo "$file"
done
[/php]

---

### Post by kevin1162 on 2008-06-26
awesome... You're my hero i appreciate your help

Can you explain the code though? like i said, i'm a novice at best and don't understand exactly what this does and i'd like to. I'm not at work so i can't play with it until the morning.

Also, you have it wrapped with php tags... Doesn't look like php to me but i could be wrong (it's happened before ;))

To be clear this can be inserted in a bash script?

---

### Post by ghostdog74 on 2008-06-26
since its only 1 way sync, 2 possible ways
1) bring everything over from NAS1 to NAS2 everytime you make a change
2) use tar. See [here ]("http://herbert.the-little-red-haired-girl.org/html/tar/tar_toc.html#TOC28")for more information.
eg
```

tar cf - ./NAS1 | (cd /NAS2; tar xvBpf - )

```

---

### Post by geirha on 2008-06-27
> **kevin1162 said:**
> 
Can you explain the code though? like i said, i'm a novice at best and don't understand exactly what this does and i'd like to. I'm not at work so i can't play with it until the morning.

If you cd into a directory and run "find ." You'll see it recursively searches for all files and directories in the "." directory (which is a special directory pointing to whatever directory you're currently in) and prints them one at each line.

If you then pipe it to a while loop that reads each line,
```
find . | while read line; do
```
each line of output from the find-command will be read into the variable "line" for each iteration. The "-print0" to find and "-d $'\0'" to read just makes it also handle pathnames with odd characters, like spaces and newlines. (On unix file systems, files can generally have any character in them, except / and \0)

[ -e PATH ] will return true if PATH exists, and false otherwise. By using the logical operators && and || you can do tasks depending on whether a command returns true or false. Try pasting these two in the shell.
```
[ -e /tmp ] && echo path exists || echo path does not exist
[ -e /fdajhfdk ] && echo path exists || echo path does not exist
```
It's basically just a shorthand for if/else.

> **kevin1162 said:**
> 
Also, you have it wrapped with php tags... Doesn't look like php to me but i could be wrong (it's happened before ;))

To be clear this can be inserted in a bash script?
The php-tags on this forum just happens to syntax highlight code, whether it be php, bash, c or otherwise. The code in my previous post is bash, not php :)

Read the bash guide for beginners [http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

---

### Post by kevin1162 on 2008-06-27
AWESOME!

serisouly... you've saved my bacon.

After playing around with your code this morning i've come up with this & appears to be working thus far.

```
#!/bin/bash

dir1="/directory_1/"
dir2="/directory_2/"

cd "$dir1"
find . -print0 | while read -d $'\0' file; do
  [ -e "$dir2/$file" ] || echo "$file" | xargs rm -rfv
done

cp -rupv /directory_2/* /directory_1/


```

I haven't tested this on my real application since i'm waiting for the other NAS to be shipped but it's worked on my ubuntu server i have setup.

again, many thanks =D>

---

### Post by geirha on 2008-06-27
With the "xargs rm", I kindof meant to put it on the entire loop
```
find . -print0 | while read -d $'\0' file; do
  [ -e "$dir2/$file" ] || echo "$file" 
done | xargs rm -rfv
```
That way you delete all files in one rm-command, but you might as well delete file by file. Not sure what is best.
```
  [ -e "$dir2/$file" ] || rm -rfv "$dir1/$file"
```
This is equivalent with your version above, just without the redundant echo and xargs.

Anyway, let me know how it works out on the real thing :)

---

### Post by kevin1162 on 2008-06-27
> With the "xargs rm", I kindof meant to put it on the entire loop

```
find . -print0 | while read -d $'\0' file; do
  [ -e "$dir2/$file" ] || echo "$file" 
done | xargs rm -rfv
```

Yeah, i changed this shortly after while i was looking at the code.

Also realized that if the network path to the main NAS was lost then it would erase everything that was backed up. So added an if statement.

```
#!/bin/bash

dir1="/directory_1/"
dir2="/directory_2/"

if [ -d $dir2 ]; then
 cd "$dir1"
 find . -print0 | while read -d $'\0' file; do
   [ -e "$dir2/$file" ] || echo "$file"
 done | xargs rm -rfv

 cp -rupv $dir2* $dir1
else
 echo Path Not found.. Check network status
fi

```

Seems to work fairly well thus far... Can you see any other potential problems?

---

### Post by geirha on 2008-06-27
That's probably a good idea, but does the directory disappear when it loses connection with the NAS? (it most likely does not) It's probably a good idea to check if there are any tools along with the NASs that will tell you if everything is OK. There's also the off chance of changes occuring while the script is running, which may or may not have consequences. If there is a way to lock the NASs while you operate on them, that would be a good thing to add to the script.

BTW, I'd add a / on the copy line, so it won't break if you change the dir2-variable to something not ending in a /. 
```
cp -rupv $dir2/* $dir1
```
consecutive slashes are treated as one slash in paths.

---

### Post by kevin1162 on 2008-06-27
> but does the directory disappear when it loses connection with the NAS?

Yeah they do, this is part of the reason that this need for backups came around... One day the NAS failed lol. Some of it's operational files are stored on the NAS and mounted where they need to be.

There is no network activity after a certain time of the day so i'm not worried about content changing since this script will run early morning.

> I'd add a / on the copy line, so it won't break if you change the dir2-variable to something not ending in a /. 

Good call, thanks!

---

### Post by kevin1162 on 2008-07-09
ok now i'm confused...

This was working, at least with the 2 directory thing...

this morning i was adding more directories and now i'm getting this error output.

> read: unknown option: -d
read: usage: read [-r] [name ...]


wtf?

This was working fine, now i don't understand how if i didn't change the syntax that all of a sudden this problem shows up.

Any ideas?

---

### Post by geirha on 2008-07-23
Sorry for the late reply, been away on vacation. This is a typical gotcha, where you have probably assumed that /bin/sh is /bin/bash. bash's builtin read command will accept the -d argument, but sh's builtin read is a bit more primitive. Make sure the sh-bang is #!/bin/bash.

---

### Post by kevin1162 on 2008-08-20
sorry i didn't reply, but just before you posted it started working.

The opening shbang is #!/bin/bash. and always was... but now all of a sudden it's giving me that error every time, i'm lost.

Oh and if it's relevant when i type 'man read' @ the CLI it brings up the man pages for read(2) - read from a file descriptor... That seems odd.

---

### Post by mssever on 2008-08-21
> **kevin1162 said:**
> Oh and if it's relevant when i type 'man read' @ the CLI it brings up the man pages for read(2) - read from a file descriptor... That seems odd.
Unfortunately, man doesn't help you with bash builtins. Use the help builtin for that: [FONT=Courier New]help read[/FONT]. I'm not quite sure what your problem is, but it looks like you're using a multi-character delimiter, though read ignores all characters in the delimiter but the first.

---

### Post by kevin1162 on 2008-08-21
But i never changed anything from the original code...

```

find . -print0 | while read -d $'\0' file; do
   [ -e "$content/$file" ] || echo "$file"
 done | xargs rm -rfv

cp -rupv $content/* $contentbak

```

I don't know what's happening

---

### Post by mssever on 2008-08-21
Works for me. You aren't calling it with ```
sh yourscript
```, are you? That would defeat the purpose of your shebang line.

---

### Post by kevin1162 on 2008-08-21
nope.

./script is how i'm executing it.

*edit*

if i type 'read --help' i get this output
read: --help: invalid option
read: usage: read [-r] [name...]

It's saying the only option is -r

---


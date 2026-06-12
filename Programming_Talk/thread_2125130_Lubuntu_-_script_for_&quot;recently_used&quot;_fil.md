---
title: "Lubuntu - script for &quot;recently used&quot; files"
date: 2013-03-13
forum: Programming Talk
---

### Post by Kevin McCready on 2013-03-13
Hoping someone might be able to write a little script which I can run from the console.

It would display the latest 15-20 files I've used. It would let me open the file by typing in the number of the file in the list generated.

Because I run LXDE in lubuntu, it doesn't have a separate "recently used" files option and the file manager consistently misses files I've opened lately.

---

### Post by schragge on 2013-03-13
This will find all files under your home directory accessed less than 24 hours ago
```
find ~ -atime 0
``` And this will do the same to all files accessed in the last 5 minutes ```
find ~ -amin -5
```

---

### Post by Kevin McCready on 2013-03-13
That was fun but I'm afraid not useful. The command lists all files accessed by the system, not by me. 

For example, I haven't opened some of those files for years. But the system accesses them when I or file manager opens a directory they live in.

---

### Post by sudodus on 2013-03-13
You can also try this alias, that you can tweak to get it as you like, and then add to your ***.bashrc*** file.

For example you can use atime or amin as suggested by schragge.

'ell24' looks in the current directory for normal files touched during the last 24 hours (not looking into the hidden directories). I use sudo so that it will find also system files or files created by other users (files your user might not have access to). You need not use sudo.

```
alias l24='sudo find * -ctime -1 -type f'
```

I find it useful and use it quite often. I have other aliases for the last week and last month.

---

### Post by schragge on 2013-03-13
Then you have to restrict the search terms. E.g. this will find only regular files in folders *~/Desktop*, *~/Documents* and *~/Downloads* accessed in the last three days
```
find -L ~/D{esktop,ocuments,ownloads} -type f -atime -3
```

---

### Post by Kevin McCready on 2013-03-13
I ran
sudo find * -ctime -1 -type f
nothing happened

I ran
find -L ~/Documents -type f -atime -3
and again it lists ALL the files in the directory that the SYSTEM has seen, not the files that I personally have accessed with an ap.

---

### Post by sudodus on 2013-03-13
> **Kevin McCready said:**
> I ran
sudo find * -ctime -1 -type f
nothing happened

Did you create any file in this directory or its subdirectories during the last 24 hours? Maybe not.


Did you create any file in this directory or its subdirectories during the last week? Probably, at least if your current directory is your home directory ~, check with

```
sudo find * -ctime -7 -type f
```

---

### Post by Kevin McCready on 2013-03-13
Did you create any file in this directory or its subdirectories during the last 24 hours? Maybe not.

yes I have created files in the directory today and in the last seven days. Both commands 

sudo find * -ctime -7 -type f
sudo find * -ctime -1 -type f
return nothing.

---

### Post by Kevin McCready on 2013-03-13
I discovered
-mtime is a measure of 24-hour periods, so ...
find -mtime 0
Finds all files that were modified in the last 24 hours.
find -mtime -2 
Find all files that are 2 days old or newer.
find -mtime +30
Find all files that were modified more than 30 days ago.

---

### Post by sudodus on 2013-03-13
> **Kevin McCready said:**
> Did you create any file in this directory or its subdirectories during the last 24 hours? Maybe not.

yes I have created files in the directory today and in the last seven days. Both commands 

sudo find * -ctime -7 -type f
sudo find * -ctime -1 -type f
return nothing.
Strange. These commands work for me now, and they have worked for years. Can you list your current directory (to show file names, ownerships and permissions)? Please post the output of the following commands. Select a directory with at least one recent file. It need not be your home directory, if you don't want to show that.

```
ls -l
```
```
ls -la
```

---

### Post by schragge on 2013-03-13
@**Kevin McCready**
I suppose the filesystem of your /home is ext4? Because I'm not sure how mtime/ctime/atime would work say on an NTFS volume. The following command should show the filesystem type:
```
sudo blkid -o list
```

---

### Post by Kevin McCready on 2013-03-13
I took out the 
*  
and it worked fine.
Now the task is to make a script to print each file with a number in front and to open the one I chose my entering the number.

---

### Post by Kevin McCready on 2013-03-13
yes ext4

---

### Post by sudodus on 2013-03-13
Double-click on it and it will be marked! Middle-click and it will be pasted! This is straight-forward and allows you to type the command you want to perform (or open it with).

---

### Post by schragge on 2013-03-13
Would this do the trick?
```
find -ctime -1 -type f -exec bash -c 'select f;do [[ -n $f ]]&&xdg-open "$f"||exit;done' _ {} +
```

---

### Post by sudodus on 2013-03-13
> **schragge said:**
> Would this do the trick?
```
find -ctime -1 -type f -exec bash -c 'select f;do [[ -n $f ]]&&xdg-open "$f"||exit;done' _ '{}' +
```

Great script :KS

---

### Post by Bucky Ball on 2013-03-13
*Thread moved to** Programming Talk***

---

### Post by Kevin McCready on 2013-03-13
thanks heaps, it certainly does the trick!!
Can you tell me how it works from the word "bash" onwards?
And how can I make it into a file name I can run? When I tried to make it into an alias it gave me an error.

---

### Post by schragge on 2013-03-13
> **Kevin McCready said:**
> Can you tell me how it works from the word "bash" onwards?

[LIST=1]
[*]find's action *-exec* executes *bash -c '[COLOR=blue]command string[/COLOR]'* and passes to it the found file names as parameters ( {} is the placeholder for file name and + shows that there're could be many of them on one line) 
[*]*bash -c '[COLOR=blue]command string[/COLOR]' $0 $1 $2 ...* executes everything in the '[COLOR=blue]command string[/COLOR]' as bash script and passes to it all words after that as shell parameters starting from $0. 
[*]*select* is a bash builtin that displays $1, $2, $3 and so on as a menu (I need to specify _ to consume $0 that gets discarded) 
[*]*f* either contains the file name selected from menu or is empty (wrong number/non-number selected). 
[*]*[[ -n $f ]]&&xdg-open "$f"||exit* tests for f: if it's not empty then *xdg-open "$f"* gets executed, otherwise *exit* ends the script. 
[*]*xdg-open* opens $f in the user's preferred application for its file type. 
[/LIST]

> **Kevin McCready said:**
> And how can I make it into a file name I can run? When I tried to make it into an alias it gave me an error.Pay attention to proper quoting when making an alias:
```

alias recent="find -ctime -1 -type f -exec bash -c 'select f;do [[ -n \$f ]]&&xdg-open \"\$f\"||exit;done' _ {} +"

```

---

### Post by Kevin McCready on 2013-03-13
Cool. You've been awesome. Thanks so much!

---

### Post by vasa1 on 2013-03-13
> **Kevin McCready said:**
> I ran
**sudo** find * -ctime -1 -type f
...What was your reasoning behind including **sudo**? My feeling is that one shouldn't **sudo** unless it is really needed.

Anyway, nice to see you got what you wanted :)

---

### Post by sudodus on 2013-03-14
> **vasa1 said:**
> What was your reasoning behind including **sudo**? My feeling is that one shouldn't **sudo** unless it is really needed.

Anyway, nice to see you got what you wanted :)

It was my suggestion, explained in post #4. I use it to be able to find files and directories, where the normal user account has no permission. (I don't think find will do any harm with root permissions.)

---

### Post by vasa1 on 2013-03-14
> **sudodus said:**
> It was my suggestion, explained in post #4. I use it to be able to find files and directories, where the normal user account has no permission. (I don't think find will do any harm with root permissions.)

Okay, got it. I don't have another user set up and wouldn't know about find accessing those files but I haven't needed sudo to find system files. And my comment was just about being more cautious because sudo persists for a while and not about sudo find, *per se*.

---

### Post by vasa1 on 2013-03-18
> **schragge said:**
> Would this do the trick?
```
find -ctime -1 -type f -exec bash -c 'select f;do [[ -n $f ]]&&xdg-open "$f"||exit;done' _ '{}' +
```
Nice!

I combined it with your earlier code
```
find -L ~/D{esktop,ocuments,ownloads} -type f -atime -3
```
to get
```
find ~/{Documents,Desktop,Downloads,Music} -ctime -1 -type f -exec bash -c 'select f;do [[ -n $f ]]&&xdg-open "$f"||exit;done' _ '{}' +
```

---

### Post by ofnuts on 2013-03-18
> **Kevin McCready said:**
> Hoping someone might be able to write a little script which I can run from the console.

It would display the latest 15-20 files I've used. It would let me open the file by typing in the number of the file in the list generated.

Because I run LXDE in lubuntu, it doesn't have a separate "recently used" files option and the file manager consistently misses files I've opened lately.

Define "latest 15-20 files I've used" first. Even with "heavier" desktop environments, this only concerns files explicitly opened by the environment's own apps, and duly noted (in ~/.kde/share/apps/RecentDocuments/, for instance). And these environments are somewhat heavier for a reason...

---


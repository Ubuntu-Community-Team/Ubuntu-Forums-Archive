---
title: "Help with beginning programming"
date: 2012-09-14
forum: Programming Talk
---

### Post by Mohan1289 on 2012-09-14
Hi guys i am newly joined in Ubuntu forums and i am very beginner of  programming. I wish to have strong programming skills in shell scripting  and to gain profound knowledge on Ubuntu Operating system and languages.
Please  suggest me some programs/projects which may help to improve my knowledge.
I am  practical person i learn things by work rather than reading so can you  guys please suggest me what to do.... 

Thank you :guitar:

---

### Post by blade4 on 2012-09-14
I suggest you start out with google search on how to speed up ubuntu . its a good way to learn about the nitty gritties of linux and it speeds up your system too . I would also recommend learning about custom compiling your own kernels - its actually very easy to do and again very educational . Fiddle around as much as you can .... but remember to back up your data beforehand so that you're safe if something goes wrong

As for Core programming stuff , I'm afraid you'll have to learn from books - no way around it really . I recommend python , C++ and  Java to start out . 

Cheers

---

### Post by lordievader on 2012-09-14
Practice, practice, practice. To learn a language you need to use a language. What I usually do when I want to learn a (programming) language is think of a project that can be done with the language. That way you are motivated to use it, instead of following examples from a text book or something.

What you could try to do is automating things. If there is something you do very frequently you can put it in a script and call that script with a hotkey.

With script, I mean bash scripts: [http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)
Is more about cli, but bash simply is a series of cli commands.

---

### Post by shreepads on 2012-09-14
Assignment: 

Build and deploy shell scripts to perform automated backup of /home to an external USB drive using rsync
- Daily at 02:00 hrs: Incremental backup
- Except every Sunday 02:00 hrs: Full backup

:-)

---

### Post by Mohan1289 on 2012-09-14
Thanks Guys

---

### Post by Mohan1289 on 2012-09-14
> **shreepads said:**
> Assignment: 

Build and deploy shell scripts to perform automated backup of /home to an external USB drive using rsync
- Daily at 02:00 hrs: Incremental backup
- Except every Sunday 02:00 hrs: Full backup

:-)


I will try to write a Shell script as you guided Shreepad

Thanks for your guidance i hope you will give your guidance in the future too

Thank you

---

### Post by Mohan1289 on 2012-09-14
> **shreepads said:**
> Assignment: 

Build and deploy shell scripts to perform automated backup of /home to an external USB drive using rsync
- Daily at 02:00 hrs: Incremental backup
- Except every Sunday 02:00 hrs: Full backup

:-)

I think the Script should be like this

#!/bin/bash
$day=(date +%a)
$date=(date)
&#8203;bfile=“/home   /var/www/  /etc /root /boot /opt”
dest=&#8203;"/mnt/myusb/Removable disk"
filename=$date.tgz

if($day=Sunday) then
echo "Full Backup Starts"

sudo tar -cvpzf $bfile  $dest/$filename

echo "Full Backup Finished"

else
echo "Daily Incremental Backup Starts"
rsync -avz $bfile $dest/$filename

echo "Daily Incremental Backup Finished"
fi

(sudo contrab 00 02 * * * bash /home/backup.sh)


Is this correct correct me if i am wrong.. 

Thank you

---

### Post by Vinton90 on 2012-09-14
Did Mohan1289 really just do that in four hours? Or am I seriously over thinking how hard it is to program or write shell scripts?

---

### Post by Vaphell on 2012-09-14
> Did Mohan1289 really just do that in four hours? Or am I seriously over thinking how hard it is to program or write shell scripts?
yes, you are overthinking it, it's not rocket science. There are few caveats but nothing to write home about ;-)

> Is this correct correct me if i am wrong..

not going into details i must say not bad, though i see few syntax errors

```
$day=(date +%a)
$date=(date)
```
$ should be on the other side of = ;-), you never see $ on the left
```
day=$(date +%a)
date=$(date)
```
think $ means 'get value of', so in english it would be day='get value of date command', just like x=$var means x='get value of var variable' and echo $var is print 'get value of var'


```
if($day=Sunday) then
```
this is wrong, if conditions are [ ] not ( ), also ; is missing
```
if [ $day = Sunday ]; then
```
i avoid ; if possible so i write my ifs this way
```
if [ ... ];
then
  cmd1;
  cmd2;
else
  cmd3;
fi
```
in this form no ; is required (newline fills its role), but if you wanted to write if in more condensed form spanning fewer lines, these are the places where you would have to put them.
same thing with while and for
```
while/for <stuff>;
do
  cmd1;
  cmd2;
done
```
also note that inside [ a = b ] you need to put spaces between all things. That is because it's nothing more than a *command param1 param2 param3 ...* .
[ is the command , the rest is its params :)


```
dest=&#8203;"/mnt/myusb/Removable[COLOR="Blue"]_[/COLOR]disk"
...
sudo tar -cvpzf $bfile [COLOR="Blue"]$dest[/COLOR]/$filename
...
rsync -avz $bfile [COLOR="Blue"]$dest[/COLOR]/$filename
```
protect your variables against spaces. Here $dest will be substituted with its value and shell will see this
```
sudo tar '-cvpzf' <bfiles> '/mnt/myusb/Removable' 'disk/<date>.tgz'
```
space inside dest will break the final value in 2 pieces. If your variables can hold any whitespace char and you want them in 1 piece, always use double quotes to protect against it.
```
"$dest/$filename"
```

---

### Post by BrianBlaze on 2012-09-14
> **Vinton90 said:**
> Did Mohan1289 really just do that in four hours? Or am I seriously over thinking how hard it is to program or write shell scripts?

I have been playing with Linux for a while and am still not even close to this guys skill in a few hours lol although I am all over the place and not just programming! :guitar: ROCK ON DUDE!

---

### Post by Mohan1289 on 2012-09-15
> **Vaphell said:**
> 

yes, you are overthinking it, it's not rocket science. There are few caveats but nothing to write home about ;-)

not going into details i must say not bad, though i see few syntax errors

```
$day=(date +%a)
$date=(date)
```$ should be on the other side of = ;-), you never see $ on the left
```
day=$(date +%a)
date=$(date)
```think $ means 'get value of', so in english it would be day='get value of date command', just like x=$var means x='get value of var variable' and echo $var is print 'get value of var'


```
if($day=Sunday) then
```this is wrong, if conditions are [ ] not ( ), also ; is missing
```
if [ $day = Sunday ]; then
```i avoid ; if possible so i write my ifs this way
```
if [ ... ];
then
  cmd1;
  cmd2;
else
  cmd3;
fi
```in this form no ; is required (newline fills its role), but if you wanted to write if in more condensed form spanning fewer lines, these are the places where you would have to put them.
same thing with while and for
```
while/for <stuff>;
do
  cmd1;
  cmd2;
done
```also note that inside [ a = b ] you need to put spaces between all things. That is because it's nothing more than a *command param1 param2 param3 ...* .
[ is the command , the rest is its params :)


```
dest=&#8203;"/mnt/myusb/Removable[COLOR=Blue]_[/COLOR]disk"
...
sudo tar -cvpzf $bfile [COLOR=Blue]$dest[/COLOR]/$filename
...
rsync -avz $bfile [COLOR=Blue]$dest[/COLOR]/$filename
```protect your variables against spaces. Here $dest will be substituted with its value and shell will see this
```
sudo tar '-cvpzf' <bfiles> '/mnt/myusb/Removable' 'disk/<date>.tgz'
```space inside dest will break the final value in 2 pieces. If your variables can hold any whitespace char and you want them in 1 piece, always use double quotes to protect against it.
```
"$dest/$filename"
```



Thanks for your suggestions and Corrections Vaphell
I will correct myself now...

The Code should be like this right??

#!/bin/bash

day=$(date +%a)

date=$(date)
&#8203;
bfile=“/home   /var/www/  /etc /root /boot /opt”

dest=&#8203;"/mnt/myusb/Removable_disk"

filename=$date.tgz

if[$day=Sunday];

then

echo "Full Backup Starts"

sudo tar -cvpzf  $bfile   $dest/$filename

echo "Full Backup Finished"

else

echo "Daily Incremental Backup Starts"

rsync -avz $bfile  $dest/$filename

echo "Daily Incremental Backup Finished"
fi

(sudo contrab 00 02 * * * bash /home/backup.sh)


is this correct now??

and the person who gave me asked some Question can you please answer them for me since i don't know the Answers too

The Questions are
- The incremental backup via rsync is creating a new folder every day,  so not incremental. And you're using option 'z' is that needed?
- Can tar and rsync work together like this?

I think we are creating a file not a Folder right?? :confused::confused:

---

### Post by Mohan1289 on 2012-09-15
And Somebody please give me Another assignment please... 
A simple one yet challenging one.. 
I wish to learn Shell Scripting as well as Linux.
I would appreciate assignments regarding Commands though like what will be the output of certain command and what's the use of certain command/parameter. 
Anything will be appreciated

Thank you  :):):)

---

### Post by cyb3r_sn4k3 on 2012-09-15
Linux is a great place to learn. When you do start programming try using geany. I absolutely love it! its great and supports almost anything!

---

### Post by Mohan1289 on 2012-09-15
Geany???

---

### Post by Elfy on 2012-09-15
*Thread moved to **Programming Talk**.*

---

### Post by Habitual on 2012-09-15
> **cyb3r_sn4k3 said:**
> ...When you do  start programming try using geany. 
I have to disagree with this recommendation based on...
What if X breaks and you have to modify your backup.sh script to include, or exclude certain directories?  Yeah, geany will be really "handy" then. You'll wish you paid more  attention to c-li skills and not some GUI with buttons and pretty little  "features".

"using geany" is NOT programming.

Don't get me wrong, geany is a pretty slick Text Editor for those new to programming  and/or shell scripting, but the techniques and lessons learned using it  should be transferable to the shell of the user.
</my_opinion>

Here's some resources to help get you started:
[CommandLineResources]("https://help.ubuntu.com/community/CommandLineResources")

HTH.

---

### Post by MG&amp;TL on 2012-09-16
> **Mohan1289 said:**
> And Somebody please give me Another assignment please... 
A simple one yet challenging one.. 
I wish to learn Shell Scripting as well as Linux.
I would appreciate assignments regarding Commands though like what will be the output of certain command and what's the use of certain command/parameter. 
Anything will be appreciated

Thank you  :):):)

Okay, I'll do one. I actually use this one all the time.

Find a pattern (search term) in a tree of files (if you don't have these, just download some random source code or something). When you find it in a file, print the matching line and the file it came from.

Hints:

1. Helpful commands might be "find" and "grep".

2. Bash has a for-loop feature that is very handy for iterating files and things.

> **Mohan1289 said:**
> Geany???

It's a text editor. Most people have a preference as regards which one to use. Stick with what you know until you feel you either need a feature to get things done faster, or you're just bored with your current one.

---

### Post by Mohan1289 on 2012-09-17
Hi Shreepad i tried for creating the script which should generates Incremental Backup Daily and Full Backup on Sunday at 02.00.

Can you please tell me where i'm wrong and send me the Correct script so that i can rectify my faults.

I thought my error lies in Filename right??? 
Instead of date.gz name for the backup i should give it as certain "name.gz" right??

If i append the file daily(Incremental Backup)then it'll be incremental backup you wanted???

and can we use rsync for Full Backup??

I google for that too but all i got is we can do incremental backup through rsync...

and why can't both rsync and tar don't work together??

I tried if else condition 

the script should follow just the commands right??

Is there any relation b/w them why they don't work together??

I am really Confused.

I am trying to solve it for 3 days and i don't get one possible alternative idea than the script i already wrote.

Thank you

---

### Post by shreepads on 2012-09-17
> **Mohan1289 said:**
> Hi Shreepad i tried for creating the script which should generates Incremental Backup Daily and Full Backup on Sunday at 02.00.

Can you please tell me where i'm wrong and send me the Correct script so that i can rectify my faults.

I thought my error lies in Filename right??? 
Instead of date.gz name for the backup i should give it as certain "name.gz" right??

If i append the file daily(Incremental Backup)then it'll be incremental backup you wanted???

and can we use rsync for Full Backup??

I google for that too but all i got is we can do incremental backup through rsync...

and why can't both rsync and tar don't work together??

I tried if else condition 

the script should follow just the commands right??

Is there any relation b/w them why they don't work together??

I am really Confused.

I am trying to solve it for 3 days and i don't get one possible alternative idea than the script i already wrote.

Thank you

By rsyncing to a new folder each day (without using hard links '-H' option), you are creating a new full backup each day. If you rsync to the same folder again that creates an incremental backup.

Rsync (used with 'a' option) creates a one-to-one backup from source to target, it doesn't compress the source to a single archive file on the destination (the 'z' option is only useful for compressing while transmitting to a remote rsync server). So in that sense it would be incompatible with the single archive file created by tar.

The brief was to only backup /home but you have backed up multiple paths.

Also, how can you ensure that the USB drive is always available on that mount point: mnt/myusb/Removable_disk

Can you run this on script on your install and see what works/ doesn't?

---

### Post by shreepads on 2012-09-17
> **Mohan1289 said:**
> And Somebody please give me Another assignment please... 
A simple one yet challenging one.. 
I wish to learn Shell Scripting as well as Linux.
I would appreciate assignments regarding Commands though like what will be the output of certain command and what's the use of certain command/parameter. 
Anything will be appreciated

Thank you  :):):)

Input: A folder name (e.g. /home/user/Music)

Processing: For each .mp3 file in the given folder and its subfolders:
a. Check if the ID3 tags for Album and Track Name are populated
b. If the Album name is blank, fill with the name of the folder in which the file is located
c. If the Track Name is blank, fill with the filename of the .mp3 file (without the .mp3 extension)

Output: List of .mp3 files whose ID3 contents have been changed. When these are opened by the user in Banshee/ Rhythmbox the Album and Track names should be corrected displayed.

---

### Post by Mohan1289 on 2012-09-17
> 
Also, how can you ensure that the USB drive is always available on that mount point: mnt/myusb/Removable_disk

Can you run this on script on your install and see what works/ doesn't?

well Removabke Disk is not actually Folder name i used that to represent i am storing data in Removable Disk That's all

---

### Post by Mohan1289 on 2012-09-22
> **MG&TL said:**
> Okay, I'll do one. I actually use this one all the time.

Find a pattern (search term) in a tree of files (if you don't have these, just download some random source code or something). When you find it in a file, print the matching line and the file it came from.

Hints:

1. Helpful commands might be "find" and "grep".

2. Bash has a for-loop feature that is very handy for iterating files and things.
  


Hi MG&TL

is MG&TL means(Mangaer and Team Leader??)

Because i have heavy work in my office i am unable to pay attention and learn shell scripting..

Even though i am still thinking about the task you gave but i still can't find the solution.

[COLOR=Red][COLOR=Black]grep command searches for the patterns in a tree of files or files.

find command searches for the files instead of patterns.

I  Understand this much, while i am trying to solve this one of my friend  mentioned about the PIPE( | ) which receives the out put the previous  command as input to the current command etc...

Based on that i thought an algorithm. 

1. We use "grep" command to search for the patterns in a tree of files.
2. we have to use find command to search for the file which contains that data.

but what i still can't understand is how???

If i give the out put of "grep" command to "find" to search for the file in which the grep command find the given patterns.

I still can't find the link.. 

How can i use for-loop in this script??

Do i have to search for a particular file repeatedly until the "grep" command found those patterns??

I think "grep" finds the patterns without using for loop doesn't it?

Or do i have to use for-loop to search the [/COLOR][/COLOR]file which contains the patterns the grep command found using find command...

Correct me if i am wrong

---

### Post by Vaphell on 2012-09-22
> Find a pattern (search term) in a tree of files (if you don't have these, just download some random source code or something). When you find it in a file, print the matching line and the file it came from.

Hints:

1. Helpful commands might be "find" and "grep".

2. Bash has a [COLOR="Red"]for-loop[/COLOR] feature that is very handy for iterating files and things.
more like while-loop, for-loop is not suited for that, it's better used with fixed lists/arrays.

too bad the exercise can be done with a single recursive grep (*grep -r*) ;-)
That being said, doing it with a while loop using find+grep would be the best learning experience, because one familiarizes oneself with the concept of loops over command output/file content line by line and doing something with it, which is a scenario that happens all the time.

General idea would be:
- produce list of files with find
- iterate over the list and do 'search for the pattern in a file with the path exactly like the text i am currently looking at'

---

### Post by Mohan1289 on 2012-09-22
But i don't get it Vaphell.
How can i use while loop??
i mean there is no i have to repeat all the files in the directory. Or is it okay if i just mentioned the directory name..

How can i write while loop without variables. 
Some Example please

---

### Post by lordievader on 2012-09-22
[http://www.cyberciti.biz/faq/bash-while-loop/](http://www.cyberciti.biz/faq/bash-while-loop/)

Cyberciti has a lot of bash examples. I go there often for the correct syntax.

---

### Post by MG&amp;TL on 2012-09-22
> **Vaphell said:**
> 
too bad the exercise can be done with a single recursive grep (*grep -r*) ;-)


Gah, and I tried so hard. :P

Oh well, my most-used 'script' is now shorter.

---

### Post by Vaphell on 2012-09-23
> How can i write while loop without variables.
Some Example please

your loop will have a variable holding the contents of the current line.

```
while read myvariable
do
  echo do something with $myvariable
done <source of data>
```
where <source of data> can be:
done **< file**
done **< <( command )**
done **<<< "string"**

---


---
title: "programming horror stories"
date: 2007-02-02
forum: Programming Talk
---

### Post by Hendrixski on 2007-02-02
We don't have a thread where people share programming horror stories do we?  I'll start one by sharing my week of hell:

A customer of mine had an interesting problem.  Their enterprise Business Intelligence system needed row level security based on an org chart that was only maintained in Active Directory, and they didn't want to maintain a separate security table in their SQL Server database.  I heard that VBScript can connect to AD and SQLServer "seamlessly" so I started to write the ETL process in VBScript on tuesday night.

I had never programmed in VB or VBScript before, nor have I ever done any OS Scripting, but I figured this would be a good time to learn.  I fancy myself as a good programmer after 6 years in C++, Java and SQL, but the kinds of errors I was making in VBScript were completely amateur!  It's a horribly hacked together language, has really crappy data structures and cryptic system settings that if you don't have declared make everything blow up.  The Error messages make no sense and the documentation sucks!  And "seamless" is not the word I would use for it.

It's friday and I'm just finishing up the project now, after I put in three 12-hour days this week.  I think I'm going to stay away from computers for a week now, see if maybe I can't fill up next week with meetings and crap.

---

### Post by g3k0 on 2007-02-02
oh oh  I've got one.

Once I was writing a program and it didn't compile the first time!

---

### Post by Lux Perpetua on 2007-02-02
My most horrifying story: once upon a time, I was working on a fairly complicated C++ program as part of a research project. At the time of this story, a typical run of my program would fail an assertion and produce a core dump. After a while, my directory accrued a large number of files named "core.2865090" or similar, so I issued the Unix command to remove all files with names beginning with "core": > rm core *See it? The space between the "core" and the "*"? It set me back about five weeks. From then on, I've always aliased rm to rm -i on all my Unix accounts.

---

### Post by Wybiral on 2007-02-02
> **Lux Perpetua said:**
> My most horrifying story: once upon a time, I was working on a fairly complicated C++ program as part of a research project. At the time of this story, a typical run of my program would fail an assertion and produce a core dump. After a while, my directory accrued a large number of files named "core.2865090" or similar, so I issued the Unix command to remove all files with names beginning with "core": See it? The space between the "core" and the "*"? It set me back about five weeks. From then on, I've always aliased rm to rm -i on all my Unix accounts.

lol... OMG, that sucks!

---

### Post by Hendrixski on 2007-02-02
> **Lux Perpetua said:**
> My most horrifying story: once upon a time, I was working on a fairly complicated C++ program as part of a research project. At the time of this story, a typical run of my program would fail an assertion and produce a core dump. After a while, my directory accrued a large number of files named "core.2865090" or similar, so I issued the Unix command to remove all files with names beginning with "core": See it? The space between the "core" and the "*"? It set me back about five weeks. From then on, I've always aliased rm to rm -i on all my Unix accounts.

oh man, you probably take the prize on this one.  What was the research project? Not your thesis project I hope!

What I would give to be working on UNIX again.  At least there everything makes sense.

---

### Post by yabbadabbadont on 2007-02-02
> **Lux Perpetua said:**
> My most horrifying story: once upon a time, I was working on a fairly complicated C++ program as part of a research project. At the time of this story, a typical run of my program would fail an assertion and produce a core dump. After a while, my directory accrued a large number of files named "core.2865090" or similar, so I issued the Unix command to remove all files with names beginning with "core": See it? The space between the "core" and the "*"? It set me back about five weeks. From then on, I've always aliased rm to rm -i on all my Unix accounts.

I was on my first programming job.  They used Unix and I had been there about three or four months.  To make things worse, they didn't do regular backups of the Unix system since very few of us actually used it in that office.  I did the good old "rm -rf *" in the temp directory where I had been messing with something late one Friday afternoon.  It seemed to take a little longer than usual.  So after it finished I ran "pwd"...

# pwd
/u4/sites
#

OH SH*T!  I had just destroyed all of the custom source code for more than 100 banks. :shock:   I went to the programmer who was mentoring me at the time and casually asked about backups.

"Hey Joe, do we have any backups of /u4?"
Very suspiciously, "Whyyyyy?"
"Ummm, I accidentally deleted a few files."
Even more suspiciously, "What did you do!?!"
"Uhhhhh, I completely deleted everthing in /u4/sites..."  (I wait for the yelling to start)

He started laughing himself silly.  That really started to piss me off so I demanded to know what was so funny.  Turns out that, just on a whim, he had done a manual full backup of the entire system that morning to a spare drive.  :D  My next task was to research, install, and configure some backup software.  We had full backups to tape every night starting the next week.  :lol:

---

### Post by Henry Rayker on 2007-02-02
While it wasn't a user error, I was working on an end of course project for one of my courses (a compiler, assembler and simulator for a simplified machine [when I say simplified, it still has branches, typical arithmetic, multiple addressing modes, interrupts, etc...it just lacked the more specialized instructions]) and I accidentally did the ```
rm *
``` meaning to do a ```
rm *.out
```. I didn't recall doing it, but I apparently backed up all of my project to the laptop's harddrive just that morning...

LUCKY!

---

### Post by lloyd mcclendon on 2007-02-02
source control owns you guys.  setup a SVN repository and learn how to use it, then rm -rf * is not a big deal.

i had to miss a deadline by a few weeks to make sure that this project was stable.  when i finally deemed that it was, i had to demo it infront of every important person in our company.  talk about a trainwreck...

the machine i used for the demo somehow had ie7 on it.  if your webapp looks great in firefox and ie6 it will NOT look anything like that in ie7.  also, if your users are all running 1024x768, make sure it looks right on that. 1600x1200 is pretty different.  so after brushing off the astetic issues, i navigate through a few pages explaining what they are as we go.  

then when we get to the good part of the app, the part that everyone has been DYING to see for the past few months .... i click submit ..... stacktrace.  ****!!!  i immediately broke out in a sweat, red face, nuts tried to go up in, etc.

it was a pretty bad scene, but in the end it allowed me to convince some people that we needed more time budgeted for FULL integration testing.  i demoed the app again the week after that and it was very well recieved.  pretty much everyone had a sense of humor about it then so it was all good, but man talk about a total confidence killer

---

### Post by rekahsoft on 2007-02-02
Once i wrote myself an ant script to build a project i was working on and had not comitted to subversion for 2 weeks and i accidentaly cleaned my src dir :'(

---

### Post by jblebrun on 2007-02-03
These rm * nightmares really bring to light one of the most glaring omissions of Linux... a filesystem API that allows "removals" to go to a temporary remove directory by default! I've redefined rm to mv parameters to a temporary "Trash" directory, that I can delete for real, later. 

Of course, the problem with this is that I'm getting comfortable with rm, which could be a bad thing when I'm at another computer!

I started doing it on my own machine ever since the day that I was playing with a chrooted environment. I accidentally exited from the chroot before type "rm /usr"

It was a pain rebuilding an entire /usr directory, let me tell you ;-) Lucky that's such an easy-to-restore directory (no custom data).

---

### Post by rko618 on 2007-02-03
jblebrun- I was so moved by your story and others that I have no declared the temporary alias of 'rm=rm -i' until I can write a mv setup similar to what you have done.

I'm pretty sure my future self is thanking you right now.

---

### Post by 3rdalbum on 2007-02-03
Maybe Ubuntu should automatically set up that alias by default?

(maybe my distro Copland should be the first that does that by default?)

---

### Post by Note360 on 2007-02-03
I already wrote one trash app in python called waste. Would it be appreciated if I made a more advanced version in C?

---

### Post by yabbadabbadont on 2007-02-03
Actually, all it takes is one major screwup involving rm or mv and you will **never** do it again.  :D

Oh, about source control, that was the next major project after we implemented backups.  PVCS in our case.  (our choices at the time were, rcs, sccs, and pvcs)

---

### Post by Ramses de Norre on 2007-02-03
I made /usr/bin/del which contains: ```
#!/bin/sh
mv ./$1 ~/.Trash


```
and it works flawlessly.

---

### Post by jblebrun on 2007-02-03
> **Ramses de Norre said:**
> I made /usr/bin/del which contains: ```
#!/bin/sh
mv ./$1 ~/.Trash


```
and it works flawlessly.

This is probably a better plan than aliasing rm. Then you get used to using your own "safe" command. Typing it on another system will just give you an error, and then you'll remember that you need to use "dangerous" rm. 

The problem with "rm -i" for me is that I just got in the habit of doing rm -rf. LOL.

---

### Post by g3k0 on 2007-02-03
Wow I didnt realize how dangerous rm was lol.  I know in windows you can get programs like undelete.  Is there anything like that for linux?

---

### Post by yabbadabbadont on 2007-02-04
> **g3k0 said:**
> Wow I didnt realize how dangerous rm was lol.  I know in windows you can get programs like undelete.  Is there anything like that for linux?

Probably, but I've never heard of any that work very well.  Everyone seems to learn the hard way that the *nix OSes won't hold your hand.  If you tell it to do something, it will do it.  Once people learn that mindset, most seem to like it.

---

### Post by g3k0 on 2007-02-04
Thats it fred flinstone.  Lets go write an undelete for linux that works!

---

### Post by joeilynn on 2007-02-04
Spam...

---

### Post by LordHunter317 on 2007-02-04
The design of ext3 makes it mostly impossible.  It's difficult on NTFS too, in certain situations, for lots of reasons.

---

### Post by Null Reference Exception on 2007-02-04
A manager insisted once I create a relational database schema for hierarchical (XML like) data. It was completely unnecessary, and after twisting my brain, the schema was so complicated! It was the biggest waste of time.

---

### Post by Hendrixski on 2007-02-04
> **g3k0 said:**
> Wow I didnt realize how dangerous rm was lol.  I know in windows you can get programs like undelete.  Is there anything like that for linux?

Yes.  There are forensics tools that allow you to look at where on your hard-drive those files were and can recover whatever hadn't been written over at that point.  However when you permanently delete something it's not supposed to be undo-able.  If you remove something to the trash bin THAT is supposed to be undo-able.  once it's deleted from trash though, that's a final delete as well.

It's really the same analogy as throwing something away to the trash bin in your house where you can still pull it out and salvage it, or actually  having it picked up by the garbage truck (that's when it's really gone, or "deleted").

---

### Post by g3k0 on 2007-02-04
I do realize that files are supposed to be gone.  But it is quite beneficial to those who make silly mistakes.  Continuing the analogy, if I dropped a 30 million dollar diamond in the trash and the garbage truck picked it up.  I would hunt that garbage truck down and get that diamond.  Even if I do stink of homeless man afterward.

---

### Post by phossal on 2007-02-04
> **Ramses de Norre said:**
> I made /usr/bin/del which contains: ```
#!/bin/sh
mv ./$1 ~/.Trash


```
and it works flawlessly.
Finally! I've found something *useful!* Thank you, and cheers!


> **rko618 said:**
> jblebrun- I was so moved by your story and others that I have no declared the temporary alias of 'rm=rm -i' until I can write a mv setup similar to what you have done. **I'm pretty sure my future self is thanking you right now.**
lol Quality.

---

### Post by raul_ on 2007-02-04
> **Ramses de Norre said:**
> I made /usr/bin/del which contains: ```
#!/bin/sh
mv ./$1 ~/.Trash


```
and it works flawlessly.

It seems it doensn't handle names with spaces very well:

```

raul@osiris:~/Desktop$ del new\ file 
mv: não é possível executar stat `./new': Arquivo ou diretório inexistente
mv: não é possível executar stat `file': Arquivo ou diretório inexistente
raul@osiris:~/Desktop$ del newfile 
raul@osiris:~/Desktop$ rm new\ file 
rm: apagar ficheiro regular vazio `new file'? y
raul@osiris:~/Desktop$ del new\ file.txt 
mv: não é possível executar stat `./new': Arquivo ou diretório inexistente
mv: não é possível executar stat `file.txt': Arquivo ou diretório inexistente

```

---

### Post by phossal on 2007-02-04
> **raul_ said:**
> It seems it doensn't handle names with spaces very well:


You know better. You can wrap the $1 in quotes to handle names with spaces. You know that though, which makes me wonder why you posted.

---

### Post by yabbadabbadont on 2007-02-04
> **phossal said:**
> You know better. You can wrap the $1 in quotes to handle names with spaces. You know that though, which makes me wonder why you posted.

Probably to just provide a common example of what wouldn't work so that others who read the thread will know about the issue.

---

### Post by raul_ on 2007-02-04
> **phossal said:**
> You know better. You can wrap the $1 in quotes to handle names with spaces. You know that though, which makes me wonder why you posted.

Actually i didn't remember that :D shame on me

---

### Post by Lux Perpetua on 2007-02-04
> **Ramses de Norre said:**
> I made /usr/bin/del which contains: ```
#!/bin/sh
mv ./$1 ~/.Trash


```
and it works flawlessly.May I suggest an alteration? ```
#!/bin/sh
mv ./$* ~/.Trash
```With that you can delete multiple files in a single command, similar to our old friend rm. The other one simply ignores all but the first command-line argument.

---

### Post by phossal on 2007-02-04
> **Lux Perpetua said:**
> May I suggest an alteration? ```
#!/bin/sh
mv ./$* ~/.Trash
```With that you can delete multiple files in a single command, similar to our old friend rm. The other one simply ignores all but the first command-line argument.
May I make a suggestion?
```

#!/bin/bash
mv ./"$@" ~/.Trash

```
The difference between $* and $@ is subtle, but *real*.

---

### Post by Lux Perpetua on 2007-02-04
> **phossal said:**
> May I make a suggestion?
```

#!/bin/bash
mv ./"$@" ~/.Trash

```
The difference between $* and $@ is subtle, but *real*.Thanks. I didn't know.

---

### Post by Ramses de Norre on 2007-02-05
> **phossal said:**
> May I make a suggestion?
```

#!/bin/bash
mv ./"$@" ~/.Trash

```
The difference between $* and $@ is subtle, but *real*.

There is still a problem I've noticed, this doesn't work with an absolute path.
del /home/user gets resolved to mv .//home/user ~/.Trash which gives an error.

---

### Post by phossal on 2007-02-05
> **Ramses de Norre said:**
> There is still a problem I've noticed, this doesn't work with an absolute path.
del /home/user gets resolved to mv .//home/user ~/.Trash which gives an error.

Remove the ./  

So it becomes:
```
#!/bin/bash
mv "$@" ~/.Trash
```

---

### Post by Hendrixski on 2007-02-05
> **g3k0 said:**
> I do realize that files are supposed to be gone.  But it is quite beneficial to those who make silly mistakes.  Continuing the analogy, if I dropped a 30 million dollar diamond in the trash and the garbage truck picked it up.  I would hunt that garbage truck down and get that diamond.  Even if I do stink of homeless man afterward.

Oh no, you're definitely correct.  That's why forensics tools exist, and as long as you don't save anything between the time you delete the files chances are you'll be able to recover them safely.  Then you don't smell like a homeless person afterwards because your bag of diamonds was on top of the garbage pile.

However if those files get written over, then it's a lot of work to possibly salvage the file.  Then it's the equivalent of smelling like a homeless person.  Not to mention you'd probably stay up for a few nights, not shower and get the same effect literally. 


So... we have 4 horror stories so far?  Anyone else?

---

### Post by Lux Perpetua on 2007-02-05
> **phossal said:**
> Remove the ./  

So it becomes:
```
#!/bin/bash
mv "$@" ~/.Trash
```Yeah, I guess that was a gimme. Any more last touches to our "move to trash" script, or is it ready for the Ubuntu repositories? ;-)

---

### Post by amohanty on 2007-02-06
> **phossal said:**
> Remove the ./  

So it becomes:
```
#!/bin/bash
mv "$@" ~/.Trash
```

'real' men actually handle corner conditions too :D 

alias rm to whatever this is called. And oh for extra large arg lists dont forget xargs :)

EDIT: ANd oh yeah - standard disclaimers apply - I am not responsible for anything.

```

#! /bin/bash

delete() {
  OFS=$IFS
  IFS='
'
  if [ $# -gt 0 ]
  then
    for f in $@
    do
      if [[ -f $f || -h $f ]]
      then
        mv --backup=numbered -f $f ~/.Trash
      elif [ -d $f ]
      then
        local tmp
        tmp=$(echo $f | sed -e 's/\///g')
        mv -f $f ~/.Trash/$tmp.$(date +%m%d%y.%H%M%S)
      else 
        echo $f not found.
      fi      
    done
  fi
  IFS=$OFS
}

rm_all_in_dir() {
  OFS=$IFS
  IFS='
'
  count=0
  for f in $(/bin/ls -1a $1)
  do
    if [[ $f != '.' && $f != '..' ]]
    then
      /bin/rm -rf $1/$f
      let count=count+1
    fi
  done
  echo $count files and dirs deleted.
  IFS=$OFS
}

purge() {
  OFS=$IFS
  IFS='
'
  local -a del_array
  idx=0
  echo Select file\(s\) to delete or type a to delete all:
  for f in $(/bin/ls -1A ~/.Trash)
  do
    echo $(( $idx+1 )). $f
    del_array[idx]=$(echo ~/.Trash/$f)
    let idx=idx+1
  done
  read reply
  if [[ $reply != '' && $reply = 'a' ]]
  then
    rm_all_in_dir ~/.Trash
  else
    multi=$(echo $reply | grep ,)
    if [ ! -z $multi ]
    then
      del_file_idxs=$(echo $multi | sed 's/,/\n/g')
      cnt=0
      for i in $del_file_idxs
      do
        /bin/rm -rf ${del_array[$(( $i-1 ))]}
        let cnt=cnt+1
      done
      echo $cnt files and dirs purged.
    fi
  fi
  IFS=$OFS
}

while getopts p name
do
    case $name in
    p) 
      purge
      exit 0
      ;;
    esac
done

delete $@
exit 0

```


AM

---


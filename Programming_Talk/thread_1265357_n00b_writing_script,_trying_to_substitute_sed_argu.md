---
title: "n00b writing script, trying to substitute sed argument into a file; how to approach?"
date: 2009-09-13
forum: Programming Talk
---

### Post by mailman1175 on 2009-09-13
Hello all!

I'm new down here (though I did read the FAQs before posting, and I know, sort of, what a blub is!), and I can tell you right off the bat that I may have jumped in over my head. But, that's how we learn, right? I'll try to be as clear and succinct as I can.

Here's the basic deal: I'm trying to write a bash script that will simplify the process I have to go through to optimize my AspireOne's Hardy install every time I break something and have to re-install (I'm an inveterate tinkerer and a Linux n00bie, so this happens frequently). I'm using sed pretty heavily, testing each piece as I go with dummy files. This is my first script, so it's entirely likely that I'm going about it the hard way.

At any rate, I've hit a wall, and I'm not sure that sed is the right tool. If it is the right tool, I'm not sure how to use it properly. If it's not, my limited google foo isn't leading me to the right choices. From the Ubuntu wiki, I'm trying to find this in /etc/init.d/sysklogd:

```
fix_log_ownership()
        for l in `syslogd-listfiles -a`
        do
                chown ${USER}:adm $l
        done
}
```

and replace it with this:

```
fix_log_ownership()
{
        for l in `syslogd-listfiles -a --news`
        do
                # Create directory for logfile if required
                ldir=$(echo ${l} | sed  's/[^\/]*$//g')
                if [ ! -e $ldir ] ; then
                        mkdir -p $ldir
                fi
                # Touch logfile and chown
                touch $l && chown ${USER}:adm $l
        done
}
```

You can see that the replacement code has a sed argument in it, and you probably already see what my problem is: I don't know how to quote or except those arguments, or turn them off, so that they're read and substituted merely as text, rather than as code. Does that make sense?

I understand, I think, that you can use backslash to quote single characters, but that seems... well, inelegant at best. I've tried nesting quotes and using curly braces, but that doesn't seem to do what I need done. Is there another protocol I should be using besides sed for this task? Is there an option I can use to turn off those arguments?

I hope I've explained well enough what I'm trying to do, and that I'm open to changing my approach. Thanks in advance for your help!

---

### Post by falconindy on 2009-09-13
Assigning the results of a command execution to a variable is easy. You need to enclose the command in backticks. That is...
```
ldir=$(echo ${l} | sed  's/[^\/]*$//g')
```should be rewritten as this:
```
ldir=`echo ${l} | sed  's/[^\/]*$//g'`
```No need to escape anything unless it needs to be escaped normally. Also, just to nitpick, you'd be fine using $1 in place of ${1}.

edit: I'm reading more through your code, and if I'm understanding it correctly (i hate sed), you just want to make a new directory for each log file based on the name of the log? Check out `basename` and see if that fits your needs. Essentially, it takes a path (e.g. path/to/log/file.log) and returns the last bit of it (e.g. file.log).

---

### Post by shel-hall on 2009-09-13
You might look into the 'basename' command; in most Unices it has options to return various parts of a file name.  If an appropriate option exists in the Ubuntu version, it might be easier and more reliable than using 'sed' to pick out the path part of the name.

Also, once you get the directory name, you don't actually need to see if it exists before using 'mkdir'; just ...

mkdir $dirname > /dev/null 2&>1

... so the shell doesn't get upset about the error that will occur if the directory already exists. 

-Shel

---

### Post by mailman1175 on 2009-09-13
> **falconindy said:**
> Assigning the results of a command execution to a variable is easy. You need to enclose the command in backticks. That is...
```
ldir=$(echo ${l} | sed  's/[^\/]*$//g')
```should be rewritten as this:
```
ldir=`echo ${l} | sed  's/[^\/]*$//g'`
```No need to escape anything unless it needs to be escaped normally. Also, just to nitpick, you'd be fine using $1 in place of ${1}.

Ok, just to keep things *really* simple here, if I escape only that argument with backticks, sed will read/substitute the rest of that as text, not as code? or are there other commands below that I need to give the same treatment?

ie:
```
sed '70,76 {[INDENT]s/fix_log_ownership()
{
        for l in `syslogd-listfiles -a --news`
        do
                # Create directory for logfile if required
                ldir=`$(echo $l | sed  's/[^\/]*$//g')`
                if [ ! -e $ldir ] ; then
                        mkdir -p $ldir
                fi
                # Touch logfile and chown
                touch $l && chown ${USER}:adm $l
        done
}[/INDENT]
```@shel: Huh? :D  Sorry, man, you did a total fly-by. Are you talking about replacing

```
mkdir -p $ldir
```with

```
mkdir $dirname > /dev/null 2&>1
```You kind of lost me after "basename". I'll google it though, and see if it looks like something I can be using to make this beast a little prettier... 

Thanks again!

---

### Post by falconindy on 2009-09-13
> **mailman1175 said:**
> @shel: Huh? :D  Sorry, man, you did a total fly-by. Are you talking about replacing

```
mkdir -p $ldir
```with

```
mkdir $dirname > /dev/null 2&>1
```You kind of lost me after "basename". I'll google it though, and see if it looks like something I can be using to make this beast a little prettier... 

Thanks again!
He's suggesting that you don't need to check for the existence of a directory before you go and create it -- instead, just make it and pipe any error output (in case it does exist) to /dev/null. 
```
mkdir -p $dirname > /dev/null 2&>1
```This will quietly fail if the directory already exists and the script moves on. You're saving yourself the need for the 'if' block.

Don't worry about sed. I don't think you need it; instead use `basename`. In short, it parses a path and returns the juicy bits after the final '/'. It's a lot easier than dealing with manual parsing of the path via sed and I believe it's what you're looking for.

edit: Your variable declaration is still a bit funky...
```
ldir=`$(echo $l | sed  's/[^\/]*$//g')`
```
You don't need to use the $( ) format for this. Try the following:
```
ldir=`basename $l`
```

---

### Post by mailman1175 on 2009-09-13
> **falconindy said:**
> He's suggesting that you don't need to check for the existence of a directory before you go and create it -- instead, just make it and pipe any error output (in case it does exist) to /dev/null. 
```
mkdir -p $dirname > /dev/null 2&>1
```This will quietly fail if the directory already exists and the script moves on. You're saving yourself the need for the 'if' block.

Don't worry about sed. I don't think you need it; instead use `basename`. In short, it parses a path and returns the juicy bits after the final '/'. It's a lot easier than dealing with manual parsing of the path via sed and I believe it's what you're looking for.

edit: Your variable declaration is still a bit funky...
```
ldir=`$(echo $l | sed  's/[^\/]*$//g')`
```You don't need to use the $( ) format for this. Try the following:
```
ldir=`basename $l`
```

Ok. I'm getting it, I think. I wasn't really concerning myself with what was between the curly braces, as I just copied/pasted that from the wiki. Really all I'm putting in, in this case, is
```
sed '70,76 {copy/paste}'
```But I can see this simplifying matters somewhat.

The whole thing should look like this, then?
```
sed '70,76 {
s/fix_log_ownership()\
{\
        for l in `syslogd-listfiles -a --news`\
        do\
                # Create directory for logfile if required\
                ldir=`basename=$1`\
                        mkdir -p $dirname > /dev/null 2&>1\
                fi\
                # Touch logfile and chown\
                touch $l && chown ${USER}:adm $l\
        done\
}
}'
```Tells me I definitely need to pay a bit more attention to what's going on under the surface, if I want to write elegant code. More to learn, more to learn. Thanks!

---

### Post by falconindy on 2009-09-13
Oh, wow... I've misunderstood your intentions. You're replacing code with other code in sysklogd... It makes sense to me now. Since sysklogd is a system file and doesn't change, why not just include a copy of the modified file with your setup script and replace it? Your new sysklogd can keep the original code (commented out) and drop in your own code after it. Then your setup script just does something like this:
```
mv /etc/init.d/sysklogd{,.bak}
cp /path/to/my/sysklogd /etc/init.d/sysklogd
```And then make sure the permissions and owner are correct.

---

### Post by mailman1175 on 2009-09-13
> **falconindy said:**
> Oh, wow... I've misunderstood your intentions. You're replacing code with other code in sysklogd... It makes sense to me now. Since sysklogd is a system file and doesn't change, why not just include a copy of the modified file with your setup script and replace it? Your new sysklogd can keep the original code (commented out) and drop in your own code after it. Then your setup script just does something like this:
```
mv /etc/init.d/sysklogd{,.bak}
cp /path/to/my/sysklogd /etc/init.d/sysklogd
```And then make sure the permissions and owner are correct.

Ok, so I need to create a directory, something like /aspireone-setup-scripts, including the file, sysklogd.new (with the old code commented out, new code appended thereafter). When I create that file, it needs to be owned by root, read/write permissions for root, read-only for others, then, right? ```
chown root /file
chmod u+rwx /file
```We'll save the script to /usr/bin, and can leave the rest of the directory in, for example, the Desktop directory. Then you're talking about using my script to back up the original sysklogd file (just in case), then swap my new file in its place.

Am I tracking?

---

### Post by mailman1175 on 2009-09-13
On second thought, it'd be better to copy that directory in under /tmp or something like that, so I don't have to worry about /home/{your username here}/Desktop, huh?

---

### Post by falconindy on 2009-09-13
> Then you're talking about using my script to back up the original sysklogd file (just in case), then swap my new file in its place.

Am I tracking?
Yep, that's it. Although, I'm not sure why you need to copy the script to /usr/bin/. Isn't this just a one time setup? Run it once from wherever and you shouldn't need it again, correct? If you want to keep it on the desktop, its no problem... `id -un` resolves the name of the current user so you can use a path like /home/`id -un`/Desktop or even just $HOME/Desktop.

Also, careful... sysklogd needs read/execute permissions across the board. `chmod 755` matches the permissions I have on my own sysklogd.

---

### Post by mailman1175 on 2009-09-13
> **falconindy said:**
> Yep, that's it. Although, I'm not sure why you need to copy the script to /usr/bin/. Isn't this just a one time setup? Run it once from wherever and you shouldn't need it again, correct? If you want to keep it on the desktop, its no problem... `id -un` resolves the name of the current user so you can use a path like /home/`id -un`/Desktop or even just $HOME/Desktop.

Also, careful... sysklogd needs read/execute permissions across the board. `chmod 755` matches the permissions I have on my own sysklogd.

Right on, man. Thanks.

---


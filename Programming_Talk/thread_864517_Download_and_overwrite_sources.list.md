---
title: "Download and overwrite sources.list"
date: 2008-07-19
forum: Programming Talk
---

### Post by kwaanens on 2008-07-19
I'm growing tired of maintaining two sources.list, and will be cron-ing an upload from one computer, and have a download&overwrite on the second.

The first one is done, but I'm not sure what's the smartest move for the latter.

The file that needs dl-ing is [http://home.no.net/kwaanens/linux/hardy/sources.list](http://home.no.net/kwaanens/linux/hardy/sources.list)

It needs superuser rights, of course.

I need to make sure that no changes are done if the file is not present, I do not want to end up with sources.list being overwritten by an empty file.
Another thing is that I'd like to make a backup of the overwritten file.

Any ideas on how this script would look like?

Thanks!

-- Ketil

---

### Post by mssever on 2008-07-19
> **kwaanens said:**
> I'm growing tired of maintaining two sources.list, and will be cron-ing an upload from one computer, and have a download&overwrite on the second.

The first one is done, but I'm not sure what's the smartest move for the latter.

The file that needs dl-ing is [http://home.no.net/kwaanens/linux/hardy/sources.list](http://home.no.net/kwaanens/linux/hardy/sources.list)

It needs superuser rights, of course.

I need to make sure that no changes are done if the file is not present, I do not want to end up with sources.list being overwritten by an empty file.
Another thing is that I'd like to make a backup of the overwritten file.

Any ideas on how this script would look like?

Thanks!

-- Ketil
Basic algorithm:

[LIST=1]
[*]Download the file to a temporary location, such as /tmp.
[*]Do appropriate error checking. Decide how to handle network errors and determine what type of validation is appropriate.
[*]Copy the existing file to your backup location.
[*]Overwrite the existing file with your replacement.
[/LIST]

---

### Post by kwaanens on 2008-07-20
Thanks for that, but that is basically word for word what I stated in my post.
I was kinda looking for the commands to use.

I guess something like this:

cd /tmp
wget [http://home.no.net/kwaanens/linux/hardy/sources.list](http://home.no.net/kwaanens/linux/hardy/sources.list)
[error checking]
cp /etc/apt/sources.list /etc/apt/sources.list.[date]
mv /tmp/sources.list /etc/apt/sources.list

---

### Post by ghostdog74 on 2008-07-20
> **kwaanens said:**
> 
[error checking]

error checking would be to see if its [zero size file](http://tldp.org/LDP/abs/html/fto.html) among others

---

### Post by mssever on 2008-07-20
> **kwaanens said:**
> I was kinda looking for the commands to use.
You didn't say which language you're using, though from your recent post it appears that you're using bash. I can't give you code if I don't know what language.

After running wget, be sure to check its exit status:
```
wget whatever
if [ $? -eq 0 ]; then
    #handle errors here
    exit 1
fi
# further checking, such as for a zero-length file
```Note that $? refers to the exit status of the last command. So you have to check it immediately after the command you're interested in. If you need to do something else first, store it in a variable: ```
status=$?
```Properly-written CLI programs will exit with a 0 exit status on success and nonzero otherwise. Consult the program's manual for an explanation of exit statuses. You might want to check for specific statuses in addition to 0.

---

### Post by kwaanens on 2008-07-20
Nice! Thanks a bunch!
I'll try this when I get the time

(I was not using a language at all when writing my first post, I was just wondering what was the best way to do this.)

Appreciate your help! As always, ubuntuforums is a great way to get help!

---


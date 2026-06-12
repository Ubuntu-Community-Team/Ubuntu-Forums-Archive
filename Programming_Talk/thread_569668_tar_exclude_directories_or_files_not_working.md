---
title: "tar: exclude directories or files not working"
date: 2007-10-07
forum: Programming Talk
---

### Post by .evan on 2007-10-07
I've tried many variations on ways of excluding directories in a tar command
and would appreciate any thoughts on this issue.

none work.

tar -cvfpj --exclude=~/My_Music tarFile.bz2 /home/evan/
tar -cvfpj tarFile.bz2  --exclude=~/My_Music /home/evan/
tar -cvfpj tarFile.bz2  --exclude=~/My_Music /home/evan/
tar -cvf --exclude=~/My_Music tarFile.tar /home/evan/

# quoting the exclude paths:
tar -cvfpj --exclude="~/My_Music" tarFile.bz2 /home/evan/
tar -cvfpj tarFile.bz2  --exclude="~/My_Music" /home/evan/
tar -cvfpj tarFile.bz2  --exclude="~/My_Music" /home/evan/
tar -cvf --exclude="~/My_Music" tarFile.tar /home/evan/

# not using ~ character in exclude paths:
tar -cvfpj --exclude="/My_Music" tarFile.bz2 /home/evan/
tar -cvfpj tarFile.bz2  --exclude="/My_Music" /home/evan/
tar -cvfpj tarFile.bz2  --exclude="/My_Music" /home/evan/
tar -cvf --exclude="/My_Music" tarFile.tar /home/evan/

# not using ~ character and not quoting the exclude paths:
tar -cvfpj --exclude=/My_Music tarFile.bz2 /home/evan/
tar -cvfpj tarFile.bz2  --exclude=/My_Music /home/evan/
tar -cvfpj tarFile.bz2  --exclude=/My_Music /home/evan/
tar -cvf --exclude=/My_Music tarFile.tar /home/evan/

#creating an exclude list file and referencing that
tar -cvfX ~/scripts/EXCLUDE_list tarFile.tar /home/evan/
tar -cvf --exclude-from ~/scripts/EXCLUDE_list tarFile.tar /home/evan/
tar -cvf --exclude-from=~/scripts/EXCLUDE_list tarFile.tar /home/evan/
tar -cvf --exclude-from="~/scripts/EXCLUDE_list" tarFile.tar /home/evan/
tar -cvf --exclude-from=$HOME/scripts/EXCLUDE_list tarFile.tar /home/evan/

#contents of the EXCLUDE_list file have taken many forms -
#  none have appeared to have any effect.

# version 1
/My_Music/

# version 2
/My_Music

# version 3
My_Music

# version 4 - trying to isolate file types
*.mpg 
*.mp3
*.m4a

Thanks.
[http://www.hobbylobby.wordpress.com/](http://www.hobbylobby.wordpress.com/)

---

### Post by qpieus on 2007-10-07
according to the man page, the exclude option requires two "dashes"```
--exclude=
```

---

### Post by bashologist on 2007-10-08
None of your examples should work. I'm not gonna go through them all and say why tho. This might work, idk.
```
tar --exclude=/home/evan/My_Music -cvfpj tarFile.bz2 /home/evan/
```

---

### Post by gnusci on 2007-10-08
Here I go:
[PHP]
> tar --exclude='My_Music' -cvjf tarFile.bz2 /home/evan/  [/PHP]

---

### Post by bashologist on 2007-10-08
> **gnusci said:**
> Here I go:
```
tar --exclude='My_Music' -cvjf tarFile.bz2 /home/evan/
```

That's exactly the same except it would exclude "/home/evan/blah/My_Music" if it exists, which may or may not be what he wants. You couldn't explain the difference for him?

---

### Post by .evan on 2007-10-08
I'm running my script with this line:

```
tar --exclude=/home/evan/My_Music --exclude=/home/evan/SCHOOL -cvpzf home_bup.tgz /home/evan

```

and it all seems to be working properly !!!

I've seen many examples and can't recall anyone putting --exclude before the switches.  that wasn't obvious at all.

thanks for the advice.

oh - I was using 2 dashes... it just didn't look like it with this font.

and I finally figured out another less than obvious thing about tar - the "-f" switch has to be the last one listed.

That caused me all kinds of grief :)

.evan
[http://www.hobbylobby.wordpress.com/](http://www.hobbylobby.wordpress.com/)

---

### Post by aceqbaceq on 2009-03-13
i had the same problem. man tar describes option exclude very badly. 

common style using "tar+exclude" suggested in internet sources is like:


tar \
- -exclude&#8230; \
- -exclude&#8230; \
- -exclude&#8230; \
&#8230;
- -exclude&#8230; \
-cvpzf home_bup.tgz /home/username

but i think it is a very annoying method.

I suggest next:

for fedora core

tar cvpzPf /tmp/backup.tar.gz &#8211;exclude={/proc/*,/sys/*,/tmp/*,/dev/*} /

for Debian

tar cvfpP /tmp/debian2.tar &#8211;exclude={&#8221;/proc/*&#8221;,&#8221;/sys*&#8221;,&#8221;/tmp/*&#8221;,&#8221;/home/user/*&#8221;} /

and more common if i need backup using ssh (ssh+nice+tar)

ssh root@192.168.0.1 &#8220;cd /;nice -n 10 tar cvpP &#8211;exclude={&#8221;/proc/*&#8221;,&#8221;/sys*&#8221;,&#8221;/tmp/*&#8221;,&#8221;/home/user/*&#8221;} /&#8221;>backup.tar.gz



and before "exclude" we have two "-" not one.

---


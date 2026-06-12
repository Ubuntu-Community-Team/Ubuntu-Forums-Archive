---
title: "how to awk?"
date: 2009-03-12
forum: Programming Talk
---

### Post by KhaaL on 2009-03-12
I'm trying to make my life easier with a backup script, right now I've incorporated the OpenPGP keys of repositories into my sources.list. To get them, I use the command:

less sources.list |grep apt-key

The idea is to make it put every command without the commenting dash, ready to be massprocessed :twisted: So I need to turn this output:

## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABF3B2646E619416
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1024R/43CBFCC0


Into this:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABF3B2646E619416 && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1024R/43CBFCC0

(or similiar). Anyone who can help me in this? 

Thanks in advance!

---

### Post by kaibob on 2009-03-12
I just began learning awk a few days ago and decided to give this a try. I came up with the following, which does appear to work:

```
awk 'BEGIN {ORS=" && "} {gsub(/## /,"")} {print}' oldfile > newfile
```

You need to change oldfile to the actual name of your file.

---

### Post by ghostdog74 on 2009-03-12
if one is using awk, there is no need to use extra awks. Just like if one is using Perl, i would find it strange if I see code like this
```

perl -e "blah ... " | perl -e "sfsdfs"

```

anyway, here's one solution out of many.
```

# awk '/##/{s=s sprintf("%s %s", $0,/##/?"&&":"");}END{print s}' file
## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com ABF3B2646E619416 &&## sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1024R/43CBFCC0 &&


```
there are still "##" left, so i leave it to OP to give it a try if he's interested.

---

### Post by myrtle1908 on 2009-03-12
or in Perl ...

```
perl -n -w -e'/^##\s*(.*)$/ && print $1.((eof)?"":" && ")' input.txt
```

---


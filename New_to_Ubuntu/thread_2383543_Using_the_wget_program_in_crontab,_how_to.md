---
title: "Using the wget program in crontab, how to?"
date: 2018-01-26
forum: New to Ubuntu
---

### Post by nandi.debian on 2018-01-26
My wish is the following, download website index file once every hours.

This is how I write in crontab file: 0 * * * * * wget [www.example.com](www.example.com) /home/<user>/

---

### Post by steeldriver on 2018-01-26
I don't think wget takes a target path after the URL in the way you have written it - did you actually test the command in an interactive terminal?

You will probably need to either cd to the target directory first, or use the -P (--directory-prefix) option:

```

       -P prefix
       --directory-prefix=prefix
           Set directory prefix to prefix.  The directory prefix is the
           directory where all other files and subdirectories will be saved
           to, i.e. the top of the retrieval tree.  The default is . (the
           current directory).

```

e.g.

```

0 * * * * /usr/bin/wget -P /home/<user>/ www.example.com

```

or

```

0 * * * * cd /home/<user>/ && /usr/bin/wget www.example.com

```

(You also appear to have one too many time fields.)

---

### Post by nandi.debian on 2018-01-26
> 0 * * * * cd /home/<user>/ && /usr/bin/wget [www.example.com](www.example.com)




thanks, lovely script. Downloads the file on schedule and renames it 1 2 3 4.

---


---
title: "A simple RM question?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by sjaxso on 2008-10-13
Hi there,

I have a bunch of directories on /media/disk/pics that I share on my home network. I used some crappy backup software that zipped every image, so now in every folder I have duplicate files with a .zip extension.

How do I remove the .zip files in one go? I tried rm -rf *.zip from the /pics directory, but it didn't have the desired effect of going into the folders below and removing the zip files.

I could do it all manually in each directory, it would be suitable penance for using a windows backup tool in the first place :(

---

### Post by ibuclaw on 2008-10-13
The unix "find" command should be substantial enough for you to achieve this:

```
find /path/to/dir -type f -iname "*.zip" -exec rm -f {} \;
```

To read more on find:
**man find**

Regards
Iain

---

### Post by bodhi.zazen on 2008-10-13
rm -rf should be just the ticket.

Perhaps specify a directory :

rm -rf ./*.zip

If that fails you can use find

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

[http://www.linux.com/articles/55377](http://www.linux.com/articles/55377)

---

### Post by dhughes on 2008-10-13
I'm not sure, I thought maybe the R switch had to be a capital R since Linux commands and filenames are case sensitive, But no I just checked the man file for 'rm' and it states: "* -r, -R, --recursive remove directories and their contents recursively*"

 

  It should not be hard but I'm not sure right now, if it isn't as simple as what you wrote plus the capital R maybe a script would do it, but I'm not so good at scripts.

 edit: there you go bodhi.zazen should know more than I would :P

---

### Post by gnudoc on 2008-10-13
Try ```
find /media/disc/pics -name "*.zip" | while read line; do rm "$line"; done
```


works for me.

Edit: Heh. Multiple solutions. :) Linux is a great thing. My bash-foo isn't as great as tinivole - I'd forgotten about -exec. Anyway, be careful of -f - you may get what you wish for ;)

---

### Post by aeiah on 2008-10-13
i guess im late with mine :(

```

cd /media/disc/
find pics -true | grep .zip | sed 's/ /\\ /g'| xargs rm

```

---

### Post by sjaxso on 2008-10-13
Crikey, six different ways to do it.

I've copied them all into my wiki. Thanks all, you guys(n gals) rock.

---


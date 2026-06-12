---
title: "what's wrong with this 'case' stmnt? (Bourne Shell)"
date: 2013-11-30
forum: Programming Talk
---

### Post by DanPerecky on 2013-11-30
I am messing around in Bourne Shell, in Ubuntu 12.04

In the script, the following is the code so far:

 ptt="01CEDB198782E190"

           case "$ptt" in
             "$line" )                                               

            ...do stuff... never gets here.

              ;;
             *) echo line: "$line" does not contain ptt: "$ptt" 
              ;;
           esac

----------------------------------------------
Typical $line is:  ./01CEDB198782E190/dir/dir

I've tried ptt (the blkid of a mounted partition) with and without quotes around. There is no difference. 

I must be missing something.

---

### Post by steeldriver on 2013-11-30
AFAIK the case test is an *equality *test i.e. $ptt will only match a string exactly equal to "01CEDB198782E190" (not a superstring *containing *"01CEDB198782E190")

**In bash**, you could do a regex match using the =~ operator, but I don't think case...esac supports that, you'd need to do a regular 'if' statement i.e.

```

if [[ $line =~ $ptt ]]; then 
  do stuff
else
  do other stuff
fi

```

---

### Post by Vaphell on 2013-11-30
you can use wildcards in cases so it's not really an equality test. I think glob rules apply.

OP, you have it backwards - your variables need to switch places. You should check if $line matches *$ppt*

```
$ ptt=01CEDB198782E190
$ line=./01CEDB198782E190/dir/dir
$ case $line in *$ptt*) echo true;; *) echo false;; esac
true
```

---

### Post by DanPerecky on 2013-12-02
> **Vaphell said:**
> you can use wildcards in cases so it's not really an equality test. I think glob rules apply.

OP, you have it backwards - your variables need to switch places. You should check if $line matches *$ppt*

```
$ ptt=01CEDB198782E190
$ line=./01CEDB198782E190/dir/dir
$ case $line in *$ptt*) echo true;; *) echo false;; esac
true
```

The syntax you shared:
           case "$line" in
              *$ptt* )

  ..worked great. Thanks!

---


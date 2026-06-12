---
title: "String compare in BASH"
date: 2016-04-02
forum: Programming Talk
---

### Post by guilly on 2016-04-02
Hello,

I wrote a small script in order for my users to get a unified desktop with some predefined shortcuts which are copied from /etc/skel. One of the conditions in the script is to only apply this if a user is logging in with an LDAP account and not local. I validate this by doing the following:

user=`whoami`

if [ -e $user == "tcu*" ]; then
blah
fi

problem is my string compare never seems to be true. my user objects all start with tcu and then a random 6 digit (tcu569430). What exactly am I doing wrong with my comparison ? Is it because my user object has a combination of alpha and numeric BASH doesn't treat it as a string ? 

Any help is appreciated!

---

### Post by steeldriver on 2016-04-02
The -e is for file tests, AFAIK

For pattern matching, you probably need to use bash's extended test [[ ... ]] in place of the older [ ... ] e.g.

```

$ user=tcu569430
$ if [[ $user = tcu* ]]; then echo "match"; fi
match

```

This is also one of the rare occasions where the argument should not be quoted - see [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

---

### Post by sudodus on 2016-04-02
You want to check if the three first characters match. Try

```
if [ "${USER:0:3}" == "tcu" ]
then
 echo "success"
fi
```

Tip 1: Use double-quotes for the variable too, when comparing the strings.

Tip 2: Do you need whoami or can you use the pre-defined variable with capitals, "$USER"?

---

### Post by guilly on 2016-04-05
> **steeldriver said:**
> The -e is for file tests, AFAIK

For pattern matching, you probably need to use bash's extended test [[ ... ]] in place of the older [ ... ] e.g.

```

$ user=tcu569430
$ if [[ $user = tcu* ]]; then echo "match"; fi
match

```

This is also one of the rare occasions where the argument should not be quoted - see [http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

Thanks, yes you're correct the -e is for file tests. I was writing from memory and got confused. The code I was using was if [ $user == "tcu*" ]. I tried your solution and it worked, so I think where I went wrong was the quotes around my test condition (tcu*) ?? Or was it the double square brackets.

---

### Post by guilly on 2016-04-05
> **sudodus said:**
> You want to check if the three first characters match. Try

```
if [ "${USER:0:3}" == "tcu" ]
then
 echo "success"
fi
```

Tip 1: Use double-quotes for the variable too, when comparing the strings.

Tip 2: Do you need whoami or can you use the pre-defined variable with capitals, "$USER"?

Thanks, I ended up going with your solution as I thought it was more elegant... Plus I like python so I like the use of ${USER:0:3} :)... I didn't test the pre-defined variable $USER however. I just stuck with whoami.

---

### Post by sudodus on 2016-04-06
You are welcome, and thanks for marking this thread as SOLVED :-)

---


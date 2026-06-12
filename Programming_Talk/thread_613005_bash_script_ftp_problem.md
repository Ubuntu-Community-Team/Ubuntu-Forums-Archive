---
title: "bash script ftp problem"
date: 2007-11-14
forum: Programming Talk
---

### Post by pylon42 on 2007-11-14
There's something odd going on here.

This works fine:

 ```
  
  1 #!/bin/bash 
  2 
  3 if []; then
  4         echo "anything"
  5 else
  6         echo "anything"
  7 fi
  8 
  9 ftp -in <<EOF
 10 open random.site.com 
 11 user $username $password 
 12 bin
 13 put $localFile $remoteFile
 14 close 
 15 bye
 16 EOF

```


This gives me an unexpected end of file error.  
```

  1 #!/bin/bash 
  2 
  3 if []; then
  4         echo "anything"
  5 else if
  6         echo "anything"
  7 fi
  8 
  9 ftp -in <<EOF
 10 open random.site.com 
 11 user $username $password 
 12 bin
 13 put $localFile $remoteFile
 14 close 
 15 bye
 16 EOF
```

... all I want to do is put an "else if" statement in the first part.

---

### Post by Siph0n on 2007-11-14
I dont know anything about bash, but with an else if u have to give a condition usually? Could that be the problem here? Like:

if x==1:
    print 'hey'
else if x == 2:
    print 'hey hey'
else
    print 'elseeeeeee'

Maybe?

---

### Post by pylon42 on 2007-11-14
Naw, the original has conditions in it. I just deleted most of the code because it contained a lot of usernames and passwords and such. I added a condition to the else if in the example above and the problem persists.

---

### Post by pylon42 on 2007-11-14
A more complete example with the problem:


```

  1 #!/bin/bash 
  2 
  3 if [ "$site" = "kjkjk" ]; then
  4         echo "anything"
  5 else if [ $blah = "toast"]; then
  6         echo "anything else"
  7 fi
  8 
  9 ftp -in <<EOF
 10 open blah.com 
 11 user $username $password 
 12 bin
 13 put $localFile $remoteFile
 14 close 
 15 bye
 16 EOF
```

---

### Post by Fire_Chief on 2007-11-14
> **Siph0n said:**
> I dont know anything about bash, but with an else if u have to give a condition usually? Could that be the problem here? Like:

**if** x==1:
    print 'hey'
**else**_ if_ x == 2:
    print 'hey hey'
_else_
    print 'elseeeeeee'

Maybe?

Siph0n is on the right track though...you are missing the else statement after your else if. Look at it this way...for every if (whether it's just if or else it) you have to have an else. So for the working example, you have an if and an else to match it. The non-working one has the first if, the matching else (else if), but no else match for the second if (else if). Hope that's not too confusing. I've highlighted and underlined the matches above to help clarify.

---

### Post by pylon42 on 2007-11-14
Thank you both for your help. I've been Googling this as well... I found a site that said to use "elif" instead of "else if". I gave it a shot and everything just started working.

I appreciate the tip about the lack of an else, i'll fix that up as well.

---


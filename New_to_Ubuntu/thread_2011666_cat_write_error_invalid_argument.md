---
title: "cat write error invalid argument"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by ihsankocak on 2012-06-27
hi, i am trying to:
abc@abc-linux:~/Desktop$ cat "sample.au"  > /dev/snd/seq

but it says:cat write error invalid argument

do you see what the problem is?

---

### Post by drmrgd on 2012-06-27
Do you have write permissions for that file?  Try running the command with sudo.

---

### Post by ihsankocak on 2012-06-27
> **drmrgd said:**
> Do you have write permissions for that file?  Try running the command with sudo.

yes i tried it with sudo but same error occured.

---

### Post by Miljet on 2012-06-27
I don't think "cat" is the command you need here. Try using "echo" instead. And use double redirector if you want to add to existing file instead of replacing all information.
```
abc@abc-linux:~/Desktop$ sudo echo "sample.au" >> /dev/snd/seq
```

---

### Post by ihsankocak on 2012-06-28
> **Miljet said:**
> I don't think "cat" is the command you need here. Try using "echo" instead. And use double redirector if you want to add to existing file instead of replacing all information.
```
abc@abc-linux:~/Desktop$ sudo echo "sample.au" >> /dev/snd/seq
```

i tried echo but the error is same:echo: write error: Invalid argument

---

### Post by steeldriver on 2012-06-28
/dev/snd/seq is a character special file - I think this is more likely why you're getting the error (and why it's 'invalid argument' not 'permission denied')

What exactly are you trying to do? I don't really know anything about sound but afaik there are some alsa utilities for this kind of thing at a higher level (amidi? aplaymidi?)

[btw if it was a permissions issue then 'sudo cat' wouldn't help because it's the redirect  of stdout that needs elevated write permissions - you could use a 'sudo tee'  instead of the '>' or wrap the whole command in a sudo sh 'cat ...' however iirc the default is for /etc/snd/seq  to be rw for members of the audio group so provided user is a member of  'audio' there should be no permission issue]

---

### Post by ihsankocak on 2012-06-28
> **steeldriver said:**
> /dev/snd/seq is a character special file - I think this is more likely why you're getting the error (and why it's 'invalid argument' not 'permission denied')

What exactly are you trying to do? I don't really know anything about sound but afaik there are some alsa utilities for this kind of thing at a higher level (amidi? aplaymidi?)

[btw if it was a permissions issue then 'sudo cat' wouldn't help because it's the redirect  of stdout that needs elevated write permissions - you could use a 'sudo tee'  instead of the '>' or wrap the whole command in a sudo sh 'cat ...' however iirc the default is for /etc/snd/seq  to be rw for members of the audio group so provided user is a member of  'audio' there should be no permission issue]

 this is an example of accessing devices in a pdf document.it should play the file but it didnt via this codes: ```
sudo cat  sample.au  >  /dev/snd/seq
```

---


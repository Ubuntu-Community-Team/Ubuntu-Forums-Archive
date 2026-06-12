---
title: "Make echo text appear to be typed"
date: 2008-07-30
forum: Programming Talk
---

### Post by Sub101 on 2008-07-30
I know this is a silly request and has no real need but i would like to have my echo text type out. That is to type each letter at a time. Is there a way to do this at all?

Thanks for your help

---

### Post by LaRoza on 2008-07-30
What language?

---

### Post by OutOfReach on 2008-07-30
I know very little to no bash (if I am correct this is the language you are talking about), but from past experiences (from other languages) I think you need to set a timer, or something along the lines of that.

---

### Post by Sub101 on 2008-07-30
Sorry, I completely forgot to say, using bash. Yeh i thought about maybe using 

> 
echo H
sleep 1
echo E
sleep 1
echo L
sleep 1
echo L
sleep 1
echo O 

or something similar. I was just curious as to whether there was perhaps a similar method to making echo bold and that sort of thing. Thanks for the quick replies.

---

### Post by WW on 2008-07-30
**slowecho**
```

#!/bin/bash
#
# slowecho -- a bash script that echoes its argument one character
#             per second.
#
arg=${@}
for (( i=0; i < ${#arg}; i+=1 )) ; do
    echo -n "${arg:$i:1}"
    sleep 1
done
echo

```
E.g.
```

$ ./slowecho 'Hello, world!'
Hello, world!
$ 

```
See how the characters in the output were printed one per second? :)

---

### Post by LaRoza on 2008-07-30
> **WW said:**
> **slowecho**
```

#!/bin/bash
#
# slowecho -- a bash script that echoes its argument one character
#             per second.
#
arg=${@}
for (( i=0; i < ${#arg}; i+=1 )) ; do
    echo -n "${arg:$i:1}"
    sleep 1
done
echo

```
See how the characters in the output were printed one per second? :)
That won't work in Ubuntu, which uses Dash as the default shell. Change it to #!/bin/bash.

---

### Post by ghostdog74 on 2008-07-30
its already #!/bin/bash?

---

### Post by LaRoza on 2008-07-30
> **ghostdog74 said:**
> its already #!/bin/bash?

I see it is. I pasted the code over an old script I had, and it may have had the sh and I must have retained that.

Sorry. Carry on people :-)

---

### Post by Sub101 on 2008-08-03
Thanks worked brilliantly.

---


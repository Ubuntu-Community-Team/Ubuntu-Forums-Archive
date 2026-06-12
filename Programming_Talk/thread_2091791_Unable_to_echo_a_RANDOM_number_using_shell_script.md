---
title: "Unable to echo a RANDOM number using shell script"
date: 2012-12-06
forum: Programming Talk
---

### Post by ask_ on 2012-12-06
Hello,
I was just trying to learn the use of the variable $RANDOM in shell. 

When I use the command 
```
echo $RANDOM
``` 
directly from the terminal it gives a random number alright.

But when I try to run a simple shell script containing the above line , all I get at the output is a blank line.

Where are things going wrong ?

I have created a shell file with following contents :- 
```
#!/bin/bash
echo $RANDOM;
```

Output I get at terminal prompt is a blank line.

Is the terminal treating it as a special character or something ?

Even the following code,(which I intend to use in another code) is not working , 
```
#!/bin/bash
number=$RANDOM;
echo $number;
```

Instead of $RANDOM if , I say number=1 , echo is echoing 1 alright.


Thanks.

---

### Post by ask_ on 2012-12-06
I searched on google for the problem. And found a solution on a unix forum website. Sorry for troubling, friends, I should have searched more before posting.

[http://www.unix.com/302437792-post9.html](http://www.unix.com/302437792-post9.html)

I was using sh command to run the script , while my shell version is bash. The site advises to use bash command instead , it worked. 


:D

---

### Post by SlugSlug on 2012-12-06
You can just

```
chmod +x script.file
```

then ```
./script.file
```

You defined bash in top line

---

### Post by ask_ on 2012-12-06
> **SlugSlug said:**
> You can just

```
chmod +x script.file
```

then ```
./script.file
```

You defined bash in top line

Ya. Will try this code out too. 
Thanks for replying. :cool:   :)

---

### Post by codemaniac on 2012-12-06
you do not need the ';'  unless you are placing multiple commands in a single line.

---


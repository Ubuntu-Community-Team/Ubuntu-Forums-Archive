---
title: "[SOLVED] Shell Command that asks for path"
date: 2007-11-06
forum: Programming Talk
---

### Post by mdpalow on 2007-11-06
Hey Everyone,

I'm trying to write a script (first time) and it's really coming out nicely. However, I want to 'kick it up a notch' and make it a little better:

I have  a simple function that runs a simple command. But, in order to make it really nice, I want some input from the user.

I simply want them to tell me where a certain file is located (full path) and then based on that answer, I want the simple command that I'm running to have that path the user entered:

Example:

some command '/their inputed path would then get placed here'

does that make any sense?

Thanks in advance to all that reply...

---

### Post by LaRoza on 2007-11-06
[http://www.shelldorado.com/goodcoding/cmdargs.html](http://www.shelldorado.com/goodcoding/cmdargs.html)
A command line argument?

Use $1, $2, $3, etc

---

### Post by mdpalow on 2007-11-06
k, didn't understand anything you just wrote there. :)  I was hoping for an example, but I'll look at your link. I have read something about that already, but I'll read this link as well.

If anyone can post with an example, I would be grateful as this is my FIRST script as mentioned in my original post.

Thanks in advance again,

---

### Post by LaRoza on 2007-11-06
> **mdpalow said:**
> k, didn't understand anything you just wrote there. :)  I was hoping for an example, but I'll look at your link. I have read something about that already, but I'll read this link as well.

If anyone can post with an example, I would be grateful as this is my FIRST script as mentioned in my original post.

Thanks in advance again,

For example, take this script named "hw.sh":

```

#! /bin/bash

echo $1

```

Make it executable, and run it. Any word typed after the scripts name will be echoed. Only the first word though. $2 will be the second, $3 the third, etc. ($0 is the script's name). So, ```
./hw.sh Hello
``` will print "Hello" to the terminal.

"$#" is the number of arguments. This script will print any number of arguments.
```

while [ $# -gt 0 ]
do
    echo "$1"
    shift
done

```

I don't know bash that well, and generally use Python for scripting. This was all taken from other sources.

---

### Post by mdpalow on 2007-11-06
I think I can work with this.

However, I'm having a little problem with this file as I've had with other example scripts I've been downloading and trying to run.

They don't run..

I created a file and put in:

#! /bin/bash

echo $1

I saved it and right clicked on it for properties, then permissions, and selected ' Allow Executing file as program '

Then I click on file and click Run In Terminal and Run and neither work.

If I go to terminal and type bsh filename, I get an error.

What am I doing wrong?

Thanks again...

---

### Post by LaRoza on 2007-11-06
You must type "./" before the file name. Your directory will not be in your PATH, and will need to be specified. "." is your cwd.

Your path is $PATH to the shell, so you can "echo $PATH", to see what it is.

You shouldn't mess with it.

---

### Post by mdpalow on 2007-11-06
thanks LaRosa,

I got your example to work, but I don't think this is what I'm looking for based on my initial request though.

I'm gonna keep looking at it to see if I'm missing something..

I'm looking to ask the user a question like:

Where is your file located?

and then I want them to input a path and have that path run inside a tar command

Here's what I have so far:

function option_7
{
tar -xpvzf /home_backup.tgz -C /home
}   # end option_7

This works fine, but I want the script to ask them where is the 'home_backup.tgz' file?

Then I want the code to do this:

tar -xpvzf /thepath_they_entered_goes_here -C /home

---

### Post by dwhitney67 on 2007-11-06
mdpalow, forgive me for writing this, but it seems what you need are better communication skills; both your OP and your follow ups are unclear.

If what you need is to read input from a user, whether it be a path or any other bit of information, then use the "read" statement.  For example,

```
#!/bin/bash
echo -n "What is the full path of the file? "
read FilePath

if [ -f $FilePath ]
then
    tar xvf $FilePath
else
    echo "The file '$FilePath' does not exist."
fi
```

---

### Post by mdpalow on 2007-11-06
dwhitney67,

My communication skills are fine - thanks. 

It's 3:30 am and I'm tired and frustrated. However, my communication skills must be OK, since you were obviously able to provide me with exactly what I was asking for based on my post(s).

Didn't need your smart *** remark...

By the way, don't preface a comment with 'forgive me' and then proceed to talk down to someone as if NOW it's OK to do it.

That's like saying "No disrespect" and then calling someone an idiot.

Would appear based on your comment - YOU might need some better communication skills (i.e. Learn how to phrase things without sounding like a pompous a**) ...

---

### Post by LaRoza on 2007-11-06
> **mdpalow said:**
> dwhitney67,

My communication skills are fine - thanks. 

It's 3:30 am and I'm tired and frustrated. However, my communication skills must be OK, since you were obviously able to provide me with exactly what I was asking for based on my post(s).

Didn't need your smart *** remark...

By the way, don't preface a comment with 'forgive me' and then proceed to talk down to someone as if NOW it's OK to do it.

That's like saying "No disrespect" and then calling someone an idiot.


Not really, the poster was not sure of what you want, and I wasn't sure myself. Vague posts are not bad, and are common in the wee hours of the morning. Your posts were not really clear about what you want, because it looked like you wanted to use command line arguments, but you said that wasn't so. The other poster chimed in with the "read" command, which, if I were more skilled in bash, I would have done. 

The poster wasn't talking down to you, just pointing out that that what you were asking wasn't entirely clear.

In communication, there exists a receiver, and a sender. Communication requires both faculties to work for successful communication. You didn't send a entirely clear message, and you misinterpreted anothers, not a symbol of good communication. Also, accepting feedback is a very good skill to learn.

Now, don't take *this* post as an offense.

---

### Post by mdpalow on 2007-11-06
Thanks LaRoza,

I can accept feedback without problem. Maybe in the early AM I was more 'trigger-happy' because I was really tired and looking for a solution and nothing else.

However, you must admit - your post is different from 'dwhitney's' in that you said:

"what you were asking wasn't entirely clear."

That was a much better way of putting it rather than accusing me of NEEDING better communication skills right off the bat.

Had it been stated like you put it, I wouldn't have reacted the way I did. 

I think in order to communicate effectively, you need to be able to speak the language, right? Shell scripting is a whole 'nother language to me that I don't understand. :) lol 

Anyway - thanks for your posting and I hope we can all now move on and away from the drama.

I concede. I might have been overly touchy last night, but I simply think the reply didn't have to start out the way it did.

I have another post to make about all this coding stuff and I'll try to be more clear.

thanks again...

---

### Post by LaRoza on 2007-11-06
> **mdpalow said:**
> 
I concede. I might have been overly touchy last night, but I simply think the reply didn't have to start out the way it did.


No problem! I have had bigger miscommunications in the past. Saying you needed better communication skills was blunt, but I think you'll find that most programmers are blunt. They accept criticism, and do not bandy words. It is easy to talk to computers than humans. Treating people as we would computers leads to trouble.

Coding early in the morning causes interesting scenerios, one of which is code you don't understand.

I once woke up after a night/morning of coding, and wondered what the code was supposed to do and what moron wrote it, then I remembered...

---


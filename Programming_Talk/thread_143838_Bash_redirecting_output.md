---
title: "Bash redirecting output"
date: 2006-03-13
forum: Programming Talk
---

### Post by draenor on 2006-03-13
Hi, I'm having some problem redirecting output. I was about to make a simple bash script of "safe remove" for some standard types. 

The idea is to do a tmp=`rm -i --preserve-root -v PATTERN`
Then I can compare the tmp output with standard strings and create my own error printings instead the one rm by default prints. However, rm hi.txt where hi .txt is a non-existant file causes error output. Now I want to catch that output and put it in my tmp variable, and NOT print it to stdout. 

My idea then was tmp=`rm -i --preserve-root -v PATTEN 2>&1` 2> /dev/null. 
This causes tmp to contain the error msg printed by rm without printing it to stdout. However, now I can't remove files who actually exist by some strange reason. 

If you know a way to walk around this I'd be glad to know. 

Secondly, I know this isn't the right forum but since I was making a post already .. Somehow some of my default laptop shortcuts doesn't work anymore, such as Fn+F11 for decreasing volume etc. I can't remember any action that may have caused this. Any idea of get them back ? (and yeah, in system->settings->keyboardshortcuts they are still assigned). 

Thanks in advance for the help.

---

### Post by hod139 on 2006-03-13
Can't you just check if the file exists before calling the rm command?

```

if [ -e ${PATTERN} ] #  See if PATTERN exists in the current directory
then
        rm -i --preserve-root -v ${PATTERN}
else
        echo "The file" ${PATTERN} "does not exists!"
        tmp="Anything you want"
fi

```

Not sure about your second problem.

---

### Post by draenor on 2006-03-13
That's a solution to it. However it only works for that kind of error. But on the other hand, I guess it's pretty rare to encounter other errors. I had something in mind similar to what you described as backup plan. Good thinking that I could use -e to check for existing files. Thanks for the help hod139.

---

### Post by hod139 on 2006-03-13
You can always check the return value of the rm command too.  If rm failed, it will exit with a value > 0. 

```

rm -i --preserve-root -v ${PATTERN} 
# Check if the rm command worked
if [ $? -gt 0 ]; then
        echo "Something went wrong!"
fi

```

---


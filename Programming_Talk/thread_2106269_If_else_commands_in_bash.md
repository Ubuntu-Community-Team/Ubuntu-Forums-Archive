---
title: "If else commands in bash"
date: 2013-01-18
forum: Programming Talk
---

### Post by raziel09 on 2013-01-18
I am trying to create a simple bash script which i can run after installing a fresh ubuntu install.

As part of this i want to be given the choice of performing a action or skipping it using the if/else statements; i checked some of the bash guides on the sticky \google and youtube but don't seem to be able to get them to work.

Here's a example of the script that i have; after this part runs there will be another two similar statements.

```
#!/bin/bash

S1="y" 

echo "Do you want to copy the Firefox\Thunderbird Profiles? (y/n)"
read option

if [ $option-eq $S1 ];

then 

sudo cp -ar /media/user/Drive/Mozilla/.thunderbird /user/

sudo cp -ar /media/user/Drive/Mozilla/.mozilla /user/
 
else

fi

```However if i enter y the terminal shuts down. I also tried having two variables (y and n) but was still unable to get it to run.

The commands themselves run fine when i copy and paste them into a terminal.

Can anyone advise where i'm going wrong?

---

### Post by mcduck on 2013-01-18
the -eq operator is used for comparing integers. To compare strings in the if statement you need to do something like this:

```
if [ "$option" = "$S1" ]
```

Also, the else statement will cause a syntax error unless you actually have some command in it. (and at least the code you atatched here is missing a space between the $option and -eq operator in the if statement ;))

I hope this helps you, and good luck with your project. :)

---

### Post by raziel09 on 2013-01-18
Thank you very much for the help

After amending the script the y command now works and runs the commands successfully; i tested this using the verbose option on the commands.

Would you be able to advise how i can add a no option onto the script?

after the commands i tried adding 

```


if [ "$option" = "$S2" ]

then fi



```However this  again causes the terminal to close down.

---

### Post by steeldriver on 2013-01-18
you don't need the 'else' if you're not actually doing anything else - it's


```
if [ condition ]
then
  something
fi
```OR
```
if [ condition ]
then
  something
else
  something else
fi
```

---

### Post by mcduck on 2013-01-18
> **raziel09 said:**
> Thank you very much for the help

After amending the script the y command now works and runs the commands successfully; i tested this using the verbose option on the commands.

Would you be able to advise how i can add a no option onto the script?

after the commands i tried adding 

```


if [ "$option" = "$S2" ]

then fi



```However this  again causes the terminal to close down.
Well, since you probably wan the "no" option to apply unless the user specifically chooses "yes", you can just use the "else" statament like you had it in your original post. Just add something for the script to actually *do* in that situation, and it will be fine.

```
#!/bin/bash

S1="y" 

echo "Do you want to copy the Firefox\Thunderbird Profiles? (y/n)"
read option

if [ "$option" = $S1 ], then
sudo cp -ar /media/user/Drive/Mozilla/.thunderbird /user/
sudo cp -ar /media/user/Drive/Mozilla/.mozilla /user/
 
else
echo "Do nothing"

fi
```

If you specifically want to test for the "no" option, you'd use *elif*. But in this case it would only make sense if you then add the option to repeat the question in case the user typed something else than yes or no. (I suppose the best way to do that would be to change the code from if statement into a while loop which repeats until the user has selected either "y" or "n"). Anyway, here's the elif:


```
#!/bin/bash

S1="y"
S2="n"
 
echo "Do you want to copy the Firefox\Thunderbird Profiles? (y/n)"
read option

if [ "$option" = $S1 ]; then
sudo cp -ar /media/user/Drive/Mozilla/.thunderbird /user/
sudo cp -ar /media/user/Drive/Mozilla/.mozilla /user/
 
elif [ "$option" = $S2 ]; then
echo "Do nothing"

fi
```

---

### Post by raziel09 on 2013-01-18
Thank you both for your help with this. The script now runs through without errors :D

Still have to tidy it up a bit and might consider compressing the thunderbird and firefox folders to make it quicker moving from source to destination but the basics are there.

---


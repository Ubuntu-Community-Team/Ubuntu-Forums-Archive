---
title: "[SOLVED] How can I make my AND operator check exit statuses?"
date: 2008-07-08
forum: Programming Talk
---

### Post by jingo811 on 2008-07-08
> linux$ **./operators.sh** 
[COLOR="Red"]./operators.sh: line 11: [: too many arguments[/COLOR]
You're missing some important stuff.  The script will now try and install 
the header files from the Internet!


**operators.sh** 
[PHP]#!/bin/bash

# chmod 744 operators.sh 


cd /lib/modules/`uname -r`/build

BRUCE="`ls -la | grep include`"
BANNER="`ls -la | grep .config`"

if [ $BRUCE ] && [ $BANNER ]; then ##### Line 11 too many arguments?
	echo "include folder and .config file both exists"
else
	cat<<EOF
You're missing some important stuff.  The script will now try and install 
the header files from the Internet!
EOF
fi[/PHP]

---

### Post by unutbu on 2008-07-08
```
if [ -e include ] && [ -e .config ]; then 
```

---

### Post by ghostdog74 on 2008-07-08
look at the [manual](http://tldp.org/LDP/abs/html/comparison-ops.html)before posting next time. you should know it by now.

---

### Post by mssever on 2008-07-09
Also, [[ is more flexible than [. It also is prone to fewer errors. If you get in the habit of using [[, there's no need for [ unless you have to be compatible with some shell other than bash.

---

### Post by jingo811 on 2008-07-09
Tnx for the help people my wings are still not ready to fly by their own engine yet.  I discovered today that I have a bad habit of stubbornly approach problems the _CLI way_ and not the _programmers way_.  So I have a tendency to overcomplicate the simplest of solutions, sorry it's a curse I've been living with since eternity :)

I decided to strive for Shell portability so I didn't use the Bash specific [[.  But could you guys explain this Bashism text to me?  English is not my native language so I don't quite follow what they are trying to say in that lengthy mass of text.
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Are they trying to say that all future Ubuntu releases starting from Hardy 8.04 and forward will be phasing out Bash and completely replace it with Dash instead?  Meaning that all of my old Bashism scripts will be useless on Hardy 8.04 + future Ubuntu releases?

[PHP]
#!/bin/bash

FILE="/lib/modules/`uname -r`/build/.config"
FOLDER="/lib/modules/`uname -r`/build/include"

#if [ -e /lib/modules/`uname -r`/build/.config ]; then echo "This file exists.";fi
#if [ -d /lib/modules/`uname -r`/build/include ]; then echo "This folder exists.";fi
#...........................................................................................


#if [ -e /lib/modules/`uname -r`/build/.config ] && [ -d /lib/modules/`uname -r`/build/include ]; then
if [ -e $FILE ] && [ -d $FOLDER ]; then
#if [[ -e $FILE && -d $FOLDER ]]; then
	cat<<EOF


	The file and folder:

		/lib/modules/`uname -r`/build/.config
		/lib/modules/`uname -r`/build/include

	already exists, you don't need to install any kernel headers.


EOF
else
	cat<<EOF


	You need to install kernel headers!


EOF
fi
[/PHP]

---

### Post by unutbu on 2008-07-09
(1) Even if Ubuntu developers decide that all their system scripts will use dash, it does not mean they will not ship bash along with the system. You are free to continue using bashisms, as long as you start your script file with

```
#!/bin/bash
```

and not 

```
#!/bin/sh
```

(2) Unless you need to read other peoples' shell scripts, I don't think there is great value in learning dash or bash. For the same amount of effort, you will gain a lot more power and be able to do a lot more things easily in perl or python. On the other hand, it appears you are reading other peoples' shell scripts, so feel free to ignore this comment!

(3) Everything between 'cat<<EOF' and 'EOF' is treated as a multi-line string.
```

cat<<EOF
...
Pure text
You can write whatever you want
and it is piped to cat, which
displays it on the screen
...
EOF
```


```
if [ -e $FILE ] && [ -d $FOLDER ]; then 
```

tests if .config file exists and include directory exist in /lib/modules/`uname -r`/build.
If they exist (are present), then the message 
> 
    The file and folder:

        /lib/modules/`uname -r`/build/.config
        /lib/modules/`uname -r`/build/include

    already exists, you don't need to install any kernel headers.

is printed on the screen.
If one or both of them isn't present then the message
> 

    You need to install kernel headers!

is printed on the screen.

---

### Post by mssever on 2008-07-09
> **jingo811 said:**
> I decided to strive for Shell portability so I didn't use the Bash specific [[.  But could you guys explain this Bashism text to me?  English is not my native language so I don't quite follow what they are trying to say in that lengthy mass of text.
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Are they trying to say that all future Ubuntu releases starting from Hardy 8.04 and forward will be phasing out Bash and completely replace it with Dash instead?  Meaning that all of my old Bashism scripts will be useless on Hardy 8.04 + future Ubuntu releases?
When you start a script with #!/bin/sh, Ubuntu used to start bash; now it uses dash. This is only relevant if you start scripts that way. And there aren't very many reasons to do so. Certain boot scripts are required to be sh scripts, because at that stage of the boot process, another interpreter might not be available. But aside from that, the portability issue is moot nowadays. If you start your scripts with #!/bin/bash, you're guaranteed to get bash. And virtually every UNIX-like system has bash these days, so portability really isn't an issue.

If you can use bashisms to imporove your code, there are very few reasons not to do so. So, go ahead and use them. Just don't begin your scripts with #!/bin/sh unless you know that writing a full bash script won't work. 99% of the time, you should go ahead an use bash.

---

### Post by jingo811 on 2008-07-09
> **mssever said:**
> Also, [[ is more flexible than [. It also is prone to fewer errors. If you get in the habit of using [[, there's no need for [ unless you have to be compatible with some shell other than bash.

It seems like I couldn't get away with [ in the end after all.  The script worked when tested directly but when I sourced it from another file **Mother.sh** then everything broke.  So your valuable [[ advice saved me later on this evening. THANKS!! 

[SIZE="4"]Good mojo[/SIZE] for . sourcing scripts.
> if [[ -e $FILE && -d $FOLDER ]]; then

[SIZE="4"]Bad mojo[/SIZE] for . sourcing scripts.
> if [ -e $FILE ] && [ -d $FOLDER ]; then

> **unutbu said:**
> 
...
...

(3) Everything between 'cat<<EOF' and 'EOF' is treated as a multi-line string.

...
...
...


Haha unutbu you explained every line of code that I wrote myself :) I just posted that code to show you guys that you helped me along with solving my problem.  But thanks for explaining it all to me especially (1) and (2).

---

### Post by unutbu on 2008-07-09
Oops! Haha! Sorry! :oops:
:lolflag:

---

### Post by mssever on 2008-07-09
> **jingo811 said:**
>   [SIZE=4]Good mojo[/SIZE] for . sourcing scripts.


[SIZE=4]Bad mojo[/SIZE] for . sourcing scripts.
Actually, that's just coincidence. The difference is that [ is a regular command, and the option -e requires an argument. When you sourced the script, apparently $FILE wasn't set, so the shell expansion rules translated your code to ```
[ -e ]
```, which is a syntax error. [[ is a special bash construct and is smart enough to handle these types of situations and realize that you're testing ```
[[ -e "" ]]
``` which is syntactically valid.

Another point. *Make it a habit to always surround variable references in double quotes!* E.g., write "$FILE", not $FILE. Shell expansion will trip you up in very creative ways otherwise. There are some situations where you can get away with breaking this rule, but there few that are harmed by following it.

---

### Post by jingo811 on 2008-07-09
```
THANKS="will do\!"

echo "Roger, "$THANKS""
```

---

### Post by ghostdog74 on 2008-07-09
> **unutbu said:**
> 

(2) Unless you need to read other peoples' shell scripts, I don't think there is great value in learning dash or bash. 

i suggest you keep this comment to yourself, because this is definitely bull.

---

### Post by unutbu on 2008-07-09
Sorry, ghostdog74, I really did not mean to say anything offensive. I know I am prejudiced by my lack of understanding of shell scripting. But mainly I just meant to say that I've been able to accomplish a lot more stuff using perl than I have using bash.

Besides the naturally good intellectual challenge, what do you see as the advantages of learning bash?

---

### Post by ghostdog74 on 2008-07-09
> **unutbu said:**
> 
Besides the naturally good intellectual challenge, what do you see as the advantages of learning bash?
I am not going to go into this. you have to do research and read / practice more on shell to find out. [Here's](http://groups.google.com.sg/group/comp.unix.shell/browse_frm/thread/25a282733558257e/758ef8b0e8848428?hl=en&lnk=gst&q=why+shell+scripting#758ef8b0e8848428) for your reading pleasure

---

### Post by unutbu on 2008-07-09
Thanks for the link; I liked Alan Gutierrez's comments quite a lot!

---

### Post by unutbu on 2008-07-09
Speaking of scripting, I've sometimes been mystified why scripts work from the command line but not when called from a udev rule 
([http://ubuntuforums.org/showthread.php?t=818960&highlight=udev](http://ubuntuforums.org/showthread.php?t=818960&highlight=udev))
or from a cron job ([http://ubuntuforums.org/showthread.php?t=854628](http://ubuntuforums.org/showthread.php?t=854628))

Do you have any advice on how to solve these problems?

---

### Post by ghostdog74 on 2008-07-09
cron will usually work. some things to check
1) environment: make sure environment is set up properly
2) make sure users who can run job have their permissions granted
3) make sure the cron daemon is running
4) in some systems there might be cron.deny, cron.allow. Make sure they are properly set up
5) in the script, make sure you have the shebang, else you must indicate the interpreter in the cron entry.
6) make sure the crontab entries are correct, ie their syntaxes
7) if the path to the script contain spaces, make sure you quote them
8) and so on
i have not worked with Ubuntu's cron and it may or may not have some peculiarities, so that's all i have to say. you may look at [this](https://help.ubuntu.com/community/CronHowto) if you have not.

---

### Post by jingo811 on 2008-07-10
> **unutbu said:**
> Sorry, ghostdog74, I really did not mean to say anything offensive. I know I am prejudiced by my lack of understanding of shell scripting. But mainly I just meant to say that I've been able to accomplish a lot more stuff using perl than I have using bash.

Besides the naturally good intellectual challenge, what do you see as the advantages of learning bash?

The advantage for me is learning to automate system admin tasks if you don't admin much then bash probably won't look as sexy as some other languages. :)

The second advantage I've found for myself is automating my long boring Linux tutorials so I don't have to explain so much to newbies when I try to help them.  It's a win-win situation I learn some programming and newbies end up not having to learn anything at all :) ( most of them like it that way, supply and demand. )

---


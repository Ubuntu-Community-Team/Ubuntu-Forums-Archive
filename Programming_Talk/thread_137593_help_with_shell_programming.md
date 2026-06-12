---
title: "help with shell programming"
date: 2006-02-28
forum: Programming Talk
---

### Post by squelchwelly on 2006-02-28
Hello,
I just started working through "Beginning lInux Programming" by Matthew and Stones and am having difficulty getting one of their sample scripts to run. Using vi and bash, I typed this in from page 36, and called it tryifthree. It is supposed to demonstrate the elif construct:

#!/bin/sh

echo "Is it morning? Please answer yes or no"
read timeofday

if [$timeofday = "yes" ]
then
        echo "Good morning"
elif [$timeofday = "no" ]; then
        echo "Good afternoon"
else
        echo "Sorry, $timeofday not recognized. Enter yes or no"
        exit 1
fi

exit 0

and when I run it I get

rodmac@cherry:~/practiceprogs$ ./tryifthree
Is it morning? Please answer yes or no
yes
./tryifthree: line 6: [yes: command not found
./tryifthree: line 9: [yes: command not found
Sorry, yes not recognized. Enter yes or no

If I type in "no" I get a similar error message saying, no: command not found.
I looked over it lots of times and cannot see why it should not run so I downloaded the source code from wrox.com.  They call it elif1 and when I run that I get a different error:

bash: ./elif1: /bin/sh^M: bad interpreter: No such file or directory

Then I copied and pasted it into gedit, saved it and ran it. I got the same error about a bad interpreter.
I am a beginner to shell programming and  would be grateful for any help because I am completely flummoxed. I started out full of optimism because it looked like this book would explain lots of things about Linux programming that I wanted to know about. My impression of Ubuntu so far is that it is brilliant; everything has worked so far! I had hoped to scale the heights of programming but I cannot even tie my bootlaces.
Thanks.

---

### Post by ubuntumaneh on 2006-02-28
Instead of:
if [$timeofday = "yes" ]

you should use:
if [$timeofday == "yes" ]

The same for:
Use:
elif [$timeofday == "no" ];


Now, I believe you are not in a POSIX enviroment, so this little mistake will raise that exception. Try it.

---

### Post by LordHunter317 on 2006-02-28
You need a space between the '[' and the command.  As for the other error, it looks like your newlines are something other than what the shell expects, you didn't save this as like a mac file, did you?

---

### Post by heimo on 2006-02-28
Put space after [ in if statements:
```

#!/bin/sh

echo "Is it morning? Please answer yes or no"
read timeofday

if [ $timeofday = "yes" ]
then
        echo "Good morning"
elif [ $timeofday = "no" ]; then
        echo "Good afternoon"
else
        echo "Sorry, $timeofday not recognized. Enter yes or no"
        exit 1
fi

exit 0

```

---

### Post by LordHunter317 on 2006-02-28
[QUOTE=ubuntumaneh]Now, I believe you are not in a POSIX enviroment, so this little mistake will raise that exception. Try it.[/QUOTE]No, what he wrote won't do that.

---

### Post by jrib on 2006-02-28
[QUOTE=squelchwelly]
if [$timeofday = "yes" ]

elif [$timeofday = "no" ]; then
[/QUOTE]

change that to:

```

if [ $timeofday = "yes" ]

elif [ $timeofday = "no" ]; then

```

notice the space after the [, as for your second question, seems there are stray ^M chars in your file, the command ```
sed -i 's/^M//g' /path/to/script.sh
``` should take care of them
and you enter the '^M' by hitting ctrl-v and then ctrl-m

[edit] too slow :)

---

### Post by jrib on 2006-02-28
after reading what lordhunter said, you may need to use 's/^M/\n/g' in the sed command above insteadm since mac files use new lines like that instead of using \n

try both and let us know what works, or if both fail :)

---

### Post by lcg on 2006-02-28
[QUOTE=squelchwelly]Hello,
I just started working through "Beginning lInux Programming" by Matthew and Stones and am having difficulty getting one of their sample scripts to run.
...
I am a beginner to shell programming and  would be grateful for any help because I am completely flummoxed.[/QUOTE]
Try this one
```
#!/bin/sh

echo "Is it morning? Please answer yes or no"
read timeofday

if [[ $timeofday == "yes" ]]; then
    echo "Good morning";
elif [[ $timeofday == "no" ]]; then
    echo "Good afternoon";
else
    echo "Sorry, $timeofday not recognized. Enter yes or no";
    exit 1;
fi

exit 0
```

Your problem came from the fact that [ is a builtin command for bash. You didn't have a space between [ and your variable, so after bash substituted the value for the variable, there was a new word which bash didn't know how to interpret ([yes).
There were several ; missing, I used [[ ]] instead of [ ] (read 'man bash' for the reasons) and == for string comparison (which is not really necessary, I just like to be able to distinguish comparison from assigning a value to a variable).

HTH,
Lars

---

### Post by squelchwelly on 2006-02-28
Aaaargh - poke me in the eye! I knew about the space after [ because Matthew and Stones do mention it. I might have spotted the mistake if the version I downloaded had run. I don't know anything about sed yet but I tried
 sed -i 's/^M//g' /path/to/script.sh
 by doing this in the directory containing the script:
 sed -i 's/^M//g' ./elif1
 Nothing much seemed to happen, which I gather can be a good sign - no error messages. However running the script still gives the error message
  bash: ./elif1: /bin/sh^M: bad interpreter: No such file or directory
  So I tried the other version
   sed -i 's/^M/\n/g' ./elif1
but with the same (lack of) results.
I didn't get the file from a mac. Using vi to look at the download version I see "(dos)" in the status bar after the file name but I don't see any instances of ^M. However when I use vi to look at the version I made by copying and pasting the downloaded version I see ^M at the end of each line but no "(dos)" in the status bar. The sed commands you guys showed me seem to have no effect on it.
But the version I typed in by hand works so thanks for the help. I can hardly believe how quickly I got a response. It sure would be handy to be able to make these downloaded files work so any advice on this would be gratefully accepted.
Thanks
Roddy

---

### Post by jrib on 2006-02-28
did you make sure to enter '^M' by pressing ctrl-v and then ctrl-m and not ^ followed by M?  I think you can also use '\r' instead of '^M', so you may want to try that too

If these don't work it might be helpful to attach the file that is giving you problems

---

### Post by jerome bettis on 2006-03-01
[quote=lcg]I used [[ ]] instead of [ ] (read 'man bash' for the reasons)[/quote] 
i've never seen [[ ]] before, and i'm too lazy to sift through that (giant!) manual ... could you briefly explain the advantage of using double instead of single brackets?

---

### Post by squelchwelly on 2006-03-01
Mea culpa! I thought I would get away with copying and pasting these arcane looking sed commands. Now I have tried them by typing ctrl v and ctrl m like jason suggested and they both work! Thanks a bundle- there are hundreds of programs in the download file so the sed commands will be really useful.
On another point about using "==" instead of "="  I tried this and the script worked without giving any error messages. So I think I'll adopt this to distinguish comparison form assignment.
My optimism is restored
Thanks
Roddy

---

### Post by lcg on 2006-03-01
[QUOTE=jerome bettis]i've never seen [[ ]] before, and i'm too lazy to sift through that (giant!) manual ... could you briefly explain the advantage of using double instead of single brackets?[/QUOTE]
From 'man bash':
```
[[ expression ]]
   Return  a  status  of  0 or 1 depending on the evaluation of the
   conditional expression expression.
```

I have always used [[ ]] for comparison and never really questioned it. I googled a bit (ever tried to make Google accept [[ as search term?) and found [this page]("http://www.medife.com.ar/LDP/LDP/abs/html/testconstructs.html"). Very far down the page, it says: "*The [[ ]] construct is the more versatile Bash version of [ ]. This is the extended test command, adopted from ksh88.*" and "*Using the [[ ... ]] test construct, rather than [ ... ] can prevent many logic errors in scripts. For example, the &&, ||, <, and >  operators work within a [[ ]] test, despite giving an error within a [ ] construct.*"

HTH,
Lars

---

### Post by lcg on 2006-03-01
[QUOTE=squelchwelly]On another point about using "==" instead of "="  I tried this and the script worked without giving any error messages. So I think I'll adopt this to distinguish comparison form assignment.[/QUOTE]
I've always been fond of languages which made that distinction. It makes code much easier to read and maintain, which IMO is really important. However, for POSIX compliance bash also accepts = as comparison, AFAIK.

Actually, I've always liked programming languages where the syntax is clean, the compiler can actually give helpful error messages and a very strict type and range checking is done at compile time. For these reasons I really love Ada (or VHDL for designing hardware).

Lars

---


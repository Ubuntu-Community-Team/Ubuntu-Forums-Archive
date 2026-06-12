---
title: "assign the exit status of a command to a variable"
date: 2007-03-01
forum: Programming Talk
---

### Post by foormea on 2007-03-01
hi all
first, i'm sorry for this newbie question. i'm learning bash programming and i'm now somewhat confused... :(

i'm trying to assign the exit status of the following command _directly_ to a variable:

synclient -l | grep TouchpadOff | grep -q 1

i thought that (( ...... )) would work but it doesn't

---

### Post by duff on 2007-03-01
like this?
```
# $(exit 1)

# echo $?
1

# $(exit 4)

# echo $?
4

```

---

### Post by foormea on 2007-03-01
thanks for the suggestion but this is not what i'm trying to do :)

i could do:
synclient -l | grep TouchpadOff | grep -q 1
TOUCHPAD_STATUS=$?

but i'm trying to have the exit status of the "synclient -l | grep TouchpadOff | grep -q 1" expression directly assigned to TOUCHPAD_STATUS

---

### Post by duff on 2007-03-01
$? gives you exit status, do you want the program's output?

---

### Post by foormea on 2007-03-01
what i'm trying to get is the exit status without supplying the command on the line before assigning it to the variable. i don't think i'm being exactly clear :D

basically, i'm trying to do something like:
TOUCHPAD_STATUS=exit_status_of_"synclient -l | grep TouchpadOff | grep -q 1"

without using a function

pretty much like variable=`uname -r` would assign the output of uname -r to variable
but what i want is the exit status

OR
if it's impossible to get the exit status this way, it seems that (( ... )) returns 1 if the expression inside returns a non-null result (or something like that). but i can't figure out how that works.

---

### Post by duff on 2007-03-01
are you just trying to avoid the output?  how about piping to dev null?

synclient -l | grep TouchpadOff | grep -q 1 &>/dev/null
TOUCHPAD_STATUS=$?

---

### Post by foormea on 2007-03-01
lol, not trying to avoid the output, grep -q does it :)

trying to get TOUCHPAD_STATUS=............              WITHOUT executing the command before

---

### Post by LotsOfPhil on 2007-03-01
So duff's 2 line solution is inacceptable?

---

### Post by Mr. C. on 2007-03-01
If you are using bash, you can use PIPESTATUS:


# echo Hello | (grep goo  )         
# echo ${PIPESTATUS[0]} ${PIPESTATUS[1]}
0 1

Otherwise, $? is always the exit status of the last command in a pipeline.

---

### Post by s1ightcrazed on 2007-03-01
To do it on a single line, you can use:

TEST=$(ls -l > /dev/null)$?

Put whatever command you want in the () and the variable will get assigned to the exit status of that command. I do this all the time for compatibility checks (when doing cross platform stuff). You can even do:

if [[ $(synclient -l | grep TouchpadOff | grep -q 1 )$? == 0 ]]; then echo "true"; fi

Basically using the exit status to determine if the system that the command is run on can actually handle the command first. Mind you I don't have to resort to this trick often, but it does come in handy from time to time. 

Enjoy!

---

### Post by Mr. C. on 2007-03-01
That's a good trick s1ightcrazed.

It might be more accurate to say "will get assigned the exit status of the last command" rather than "will get assigned to the exit status of that command".

Very nice.

---

### Post by foormea on 2007-03-02
s1ightcrazed, this is EXACTLY what i needed. thanks a lot!!!

---

### Post by foormea on 2007-03-03
got a problem, i really can't understand...

(synclient -l returns the total list of options of the touchpad. i wanna know if the touchpad is on or off)

this works fine, first executing the set of commands then reading $?
> 
#!/bin/sh
synclient -l | grep TouchpadOff | grep -q 1
case "$?" in
0 )
   echo "off";;
1 )
   echo "on";;
esac
exit 0


however i'd like to assign the exit status directly. i know it's useless since the previous script works fine, but still... :)

typing this directly at the shell prompt works fine:
> 
echo `synclient -l | grep TouchpadOff | grep -q 1`$?

returning 0 when it's off, and 1 when on

but why the hell won't this script work???:
> 
#!/bin/sh
case "`synclient -l | grep TouchpadOff | grep -q 1`$?" in
0 )
   echo "off";;
1 )
   echo "on";;
esac
exit 0

in order to try to understand why it doesn't work, i also tried doing:
> 
test=`synclient -l | grep TouchpadOff | grep -q 1`$?
echo $test

works perfectly at command prompt
but doesn't work in a script........................................... :((((( :((((((((

---

### Post by Mr. C. on 2007-03-03
Too many new programmers want to jump in without reading and learning from the documentation.  Let me suggest when things aren't working, you try to digest the sometimes challenging documentation.  From man bash, the syntax of a case statement is:

       case word in [ [(] pattern [ | pattern ] ... ) list ;; ] ... esac

So, what is a "word".  Again, man bash tells us:

       word   A  sequence  of  characters  considered  as a single unit by the
              shell.  Also known as a token.

So, can you now see why your attempt doesn't work?

MrC

---

### Post by foormea on 2007-03-03
hey Mr. C.
i appreciate your help and i promise i'll rely more on doc from now on :)

word: A token that is not an operator.

token: A sequence of characters considered a single unit by the shell. It is either a word or an operator.

operator: A control operator or a redirection operator. See section 3.6 Redirections, for a list of redirection operators.

control operator: A word that performs a control function. It is a newline or one of the following: `||', `&&', `&', `;', `;;', `|', `(', or `)'.

----> my command uses the | operator and therefore can't work in a case construct.
ok, understood and thanks for telling me to check the doc :)

however, i still can't understand why
> test=`synclient -l | grep TouchpadOff | grep -q 1`$?
echo $test 
works, but why
> #!/bin/sh
test=`synclient -l | grep TouchpadOff | grep -q 1`$?
echo $test 
won't work.

-------------> okay just found out that /bin/sh is a symlink to /bin/dash. it works fine when using #!/bin/bash instead of #!/bin/sh. i'll read doc about what dash is

okay, thanks master Mr. C. !

---

### Post by po0f on 2007-03-03
foormea,

Dash is a gimped Bash, change it:

```
$ sudo dpkg-reconfigure dash
```

Answer "No".

---

### Post by Mr. C. on 2007-03-03
Yes, I was just replying when I saw the other posters comment too.

Always know what interpreter (#! line at the top of your scripts) you are using.

sh != bash != ksh
csh != tcsh

MrC

---

### Post by foormea on 2007-03-03
mmhhhh, since it's said that dash is faster than bash, shouldn't i keep dash as default /bin/sh shell, and just use #!/bin/bash instead of #!/bin/sh in my scripts?

---

### Post by Mr. C. on 2007-03-03
You should NOT reconfigure /bin/sh unless you are certain of the ramifications.   The shell is critical to early boot up - mess with this inappropriately, and you won't boot.

There is nothing your system does with the shell that is time critical in this manner.

---

### Post by po0f on 2007-03-03
Mr. C.,

I've been using Bash as the default shell interpreter since Dapper and have yet to see *any* side effect, besides my scripts automatically being run through Bash instead of Dash.

---

### Post by foormea on 2007-03-03
ok :)
thanks guys for your help!

---

### Post by Mr. C. on 2007-03-03
> **po0f said:**
> Mr. C.,

I've been using Bash as the default shell interpreter since Dapper and have yet to see *any* side effect, besides my scripts automatically being run through Bash instead of Dash.

I didn't say it can't or shouldn't be done; I said to be sure to understand.

If something goes terribly wrong with someone's system who took up your advice, are you going to go over and fix it for that person?  :-)

MrC

---

### Post by po0f on 2007-03-03
Mr. C.,

I have given this advice on several occasions, and AFAIK the results have only been positive.

Now, if something were to go wrong because of any advice I had given, I would certainly go out of my to help the user repair the situation.  I don't do house calls though.  ;)

---

### Post by Mr. C. on 2007-03-03
This reminds of a guy named Timothy Treadwell.  For over a dozen years he believed in his position.  I don't think he's a believer anymore.

---


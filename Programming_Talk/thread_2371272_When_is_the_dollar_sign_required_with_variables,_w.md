---
title: "When is the dollar sign required with variables, when is it not?"
date: 2017-09-12
forum: Programming Talk
---

### Post by John_Patrick_Mason on 2017-09-12
I have a few question mostly relating to script 1. Here are the questions I have:

First, why is the if statement missing at line 14. This is the first time (at least in the book) that I've encountered a test without an if statement. Is that even allowed? Presumably so, or else the script wouldn't run, but then what does line 14 mean?
Second, still at line 14, why is the $REPLY variable not quoted? Shouldn't the $REPLY variable be quoted in case if the $REPLY variable returns an empty value? Wouldn't that cause the operator to interpreted as a non-null string instead of an operator?
Third, again, why isn't the variable $REPLY at line 20 quoted, again for the same reasons?
Fourth, how come I can't omit the dollar sign after doing file validation at line 22? If I take a quick look at script #2, I was able to omit the dollar sign at line 12 after making sure the variable wasn't an empty variable. How is the variable $REPLY different from any other variable that I've used?
Lastly, at the first dollar sign at line 17, is that a command substitution within a (( )) compound command?


Script #1:

```

     1    #!/bin/bash
     2    
     3    # read-validate: validate input
     4    
     5    
     6    invalid_input () {
     7        echo "Invalid input '$REPLY'" >&2
     8        exit 1
     9    }
    10    
    11    read -p "Enter a single item > "
    12    
    13    # input is empty (invalid)
    14    [[ -z $REPLY ]] && invalid_input
    15    
    16    # input is multiple items (invalid)
    17    (( $(echo $REPLY | wc -w) > 1 )) && invalid_input
    18    
    19    # is input a valid filename?
    20    if [[ $REPLY =~ ^[-[:alnum:]\._]+$ ]]; then
    21        echo "'$REPLY' is a valid filename."
    22        if [[ -e $REPLY ]]; then
    23            echo "And file '$REPLY' exists."
    24        else
    25            echo "However, file '$REPLY' does not exist."
    26        fi
    27    
    28        # is input a floating point number?
    29        if [[ $REPLY =~ ^-?[[:digit:]]*\.[[:digit:]]+$ ]]; then
    30            echo "'$REPLY' is a floating point number."
    31        else
    32            echo "'$REPLY' is not a floating point number."
    33        fi
    34    
    35        # is input an integer?
    36        if [[ $REPLY =~ ^-?[[:digit:]]+$ ]]; then
    37            echo "'$REPLY' is an integer."
    38        else
    39            echo "'$REPLY' is not an integer."
    40        fi
    41    else
    42        echo "The string '$REPLY' is not a valid filename."
    43    fi

```

Script #2:

```

     1    #!/bin/bash
     2    
     3    # test-integer3: determine if an integer is within a
     4    # specified range of values.
     5    
     6    MIN_VAL=1
     7    MAX_VAL=100
     8    
     9    INT=50
    10    
    11    if [[ "$INT" =~ ^-?[0-9]+$ ]]; then
    12        if [[ INT -ge MIN_VAL && INT -le MAX_VAL ]]; then
    13            echo "$INT is within $MIN_VAL to $MAX_VAL."
    14        else
    15            echo "$INT is out of range."
    16        fi
    17    else
    18        echo "INT is not an integer." >&2
    19        exit 1
    20    fi

```

---

### Post by &amp;KyT$0P# on 2017-09-13
> **John_Patrick_Mason said:**
> This is the first time (at least in the book) that I've encountered a test without an if statement. Is that even allowed?
Think of a test like basically a special kind of program.  Where you can run programs, you can run tests.  Where you can run tests, you can run programs.

> what does line 14 mean?
[FONT=Courier New]program1 && program2[/FONT] means 'run program2 only if program1 succeeded'.  So your line 14 is equivalent to this -
```
if [[ -z $REPLY ]];then
  invalid_input
fi
```

> Second, still at line 14, why is the $REPLY variable not quoted? Shouldn't the $REPLY variable be quoted in case if the $REPLY variable returns an empty value? Wouldn't that cause the operator to interpreted as a non-null string instead of an operator?
Third, again, why isn't the variable $REPLY at line 20 quoted, again for the same reasons?
I agree, I think it should be quoted.  Good catch.

---

### Post by Rocket2DMn on 2017-09-13
I agree that the REPLY variable should be quoted everywhere here.

The dollar sign is always required, except when being dereferenced as an arithmetic variable.  This works for counters inside double parentheses (()).  It's still need outside though, like when echoing:
```

#!/bin/bash
for ((i=0; i<10; i++)); do
  echo "$i"
done

```
Apparently (as I just had to look up now), the $ is also not needed for the integer value in your script #2, line 12, since the variable is being dereferenced inside double brackets [[]] while using comparison operators like -eq, -lt, -gt, etc.  It's still required in line 11 though.

---

### Post by Rocket2DMn on 2017-09-13
I'd also like to add that I've become a big fan of shellcheck - a lint tool for shell scripts.  You can install [shellcheck]("apt:shellcheck") from the Universe repository, or even use the online interface at [https://www.shellcheck.net/](https://www.shellcheck.net/) which links you to the documentation on warnings/errors.  It won't solve all of your problems, but it's a big help.

---

### Post by sisco311 on 2017-09-13
> **John_Patrick_Mason said:**
> 
First, why is the if statement missing at line 14. This is the first time (at least in the book) that I've encountered a test without an if statement. Is that even allowed? 

Check out:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)

[[ is a compound **command** it has nothing to do with the syntax of the if statement. 

> **John_Patrick_Mason said:**
> Presumably so, or else the script wouldn't run, but then what does line 14 mean?


If, and only if, the exit code of the [[ command is 0 then *invalid_input* is executed.

---

### Post by John_Patrick_Mason on 2017-09-13
[QUOTE=Rocket2DMn]
The dollar sign is always required, except when being dereferenced as an arithmetic variable.
[/QUOTE]

Can you define the word "dereferenced" without getting too technical? I think I know what you mean, but I just want to be sure.

Also by "arithmetic variable" you mean any variable equal to a real number, correct?

---

### Post by Rocket2DMn on 2017-09-14
In short, the $ symbol indicates to the shell that the text that follows is the name of a variable (which has some value, even if that value is empty, i.e., '').  In certain situations though, the shell knows that it's looking at a variable even without you having to say so explicitly by putting a $ in front of the name.  The counter inside the double parentheses is one such example.

Dereference simply means the shell is going to substitute the value of a variable where you and I (human beings reading the shell script) see a variable name.  E.g., if we set

```

i=10

```
Then later when we refer to it:
```

echo "$i"

```
the bash interpreter knows to substitute "10" for "$i", so the actual command it executes is:
```

echo "10"

```
which prints "10" to the console (without quotes).

---

### Post by John_Patrick_Mason on 2017-09-14
> **Rocket2DMn said:**
> In short, the $ symbol indicates to the shell that the text that follows is the name of a variable (which has some value, even if that value is empty, i.e., '').  In certain situations though, the shell knows that it's looking at a variable even without you having to say so explicitly by putting a $ in front of the name.  The counter inside the double parentheses is one such example.

Dereference simply means the shell is going to substitute the value of a variable where you and I (human beings reading the shell script) see a variable name.  E.g., if we set

```

i=10

```
Then later when we refer to it:
```

echo "$i"

```
the bash interpreter knows to substitute "10" for "$i", so the actual command it executes is:
```

echo "10"

```
which prints "10" to the console (without quotes).

OK, so if I understand correctly, the dollar sign can be omitted after making sure the respective variable has been properly introduced beforehand, when using the compound commands (( )) and
[[ ]], does that make sense?

---

### Post by Rocket2DMn on 2017-09-14
> **John_Patrick_Mason said:**
> OK, so if I understand correctly, the dollar sign can be omitted after making sure the respective variable has been properly introduced beforehand, when using the compound commands (( )) and
[[ ]], does that make sense?

You still typically need the $ with [[ ]].  The fact that there are two brackets on each end is to support compound if statements joined with && in the earlier examples.  It was only when using the integer comparison operators like -eq, -gt, -lt, etc. inside [[ ]] that the $ wasn't necessary.  Interestingly, it appears that the $ IS required when you only use single [ ] for a single (non-compound) comparison using -eq, -gt, -lt, etc.  Bash is just weird like that.

If in doubt, just use the $ sign when you need to get the value from a variable.  Also check your script with shellcheck - it might give you some information about when you're using the $ sign when it's not actually needed, but this is just an optimization.

---

### Post by John_Patrick_Mason on 2017-09-14
> **Rocket2DMn said:**
> You still typically need the $ with [[ ]].  The fact that there are two brackets on each end is to support compound if statements joined with && in the earlier examples.  It was only when using the integer comparison operators like -eq, -gt, -lt, etc. inside [[ ]] that the $ wasn't necessary.  Interestingly, it appears that the $ IS required when you only use single [ ] for a single (non-compound) comparison using -eq, -gt, -lt, etc.  Bash is just weird like that.

If in doubt, just use the $ sign when you need to get the value from a variable.  Also check your script with shellcheck - it might give you some information about when you're using the $ sign when it's not actually needed, but this is just an optimization.

I reread your first comment after learning what the world "dereferencing" meant, and now I think I get it. I also found [this]("https://unix.stackexchange.com/questions/68694/when-is-double-quoting-necessary") useful link from Stack Exchange on double-quoting. I can't say I understood everything, but it does say that double quotes are optional within double brackets, which would explain why the author decided not to include them in the first script on line 14. I'm less sure though about lines 20, 29, and 36. The answer from the link I provided says that double-quotes are needed within double brackets on the right side of the following operators =, ==, !=, =~, but it doesn't say anything about the left side, about the variable itself.

---

### Post by John_Patrick_Mason on 2017-09-15
Anyone care to comment on using double quotes inside double brackets based on the information contained in the link I provided?

---

### Post by Rocket2DMn on 2017-09-15
There is a bullet point in the post about exactly that.
> 
[y]ou can omit double quotes ... [w]ithin double brackets. Double brackets are shell special syntax.
...
Except that you do need double quotes where a pattern or regular expression is expected: on the right-hand side of = or == or != or =~.

Don't worry about patterns and regular expressions until you find that you need them.

As I mentioned earlier, and the responder said in the page you linked:
> 
Second, it is far easier to use double quotes all the time than to remember when they are needed. They are needed most of the time, so you'll need to learn when they aren't needed, not when they are needed.

I'd recommend that you don't get hung up on these bash quirks too much, and get on with achieving what it is that your scripting is meant for.  In time, you'll learn the ins and outs of programming/scripting languages as you use them.  Very few people in the world can say they truly understand every last detail of even a single one of the seemingly innumerable languages out there.

---

### Post by John_Patrick_Mason on 2017-09-19
I'd like to thank all of you for responding. I'm now marking this thread as solved.

---


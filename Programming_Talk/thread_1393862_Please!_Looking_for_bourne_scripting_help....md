---
title: "Please! Looking for bourne scripting help..."
date: 2010-01-29
forum: Programming Talk
---

### Post by geektanic on 2010-01-29
I didn't know where else to post it as all other forum categories were specific to ubuntu but I was hoping for the genuine enthusiasm and help of a community like this one here...

In short I cannot get this script to work: [http://www.intuitive.com/wicked/showscript.cgi?005-validint.sh]("http://www.intuitive.com/wicked/showscript.cgi?005-validint.sh")

I am trying to get back into coding and help buffer my linux certification by getting my scripting more fluid. I have both typed and copied and pasted this script to ensure it is not error on my part but it still refuses to detect a negative integer as stated.

What drives me the most crazy is that the following two code blocks provide different results. I have typed them side by side in the terminal to prove that the only difference is variable name.

```
geektanic@monolith:~/scripts$ testvalue="-24"
geektanic@monolith:~/scripts$ echo $testvalue
-24
geektanic@monolith:~/scripts$ number="-24"
geektanic@monolith:~/scripts$ echo $number
-24
geektanic@monolith:~/scripts$ if [ "${testval%${testval#?}}" = "-" ] ; then
> testval2="${testval#?}"
> else
> testval2="$testval"
> fi
geektanic@monolith:~/scripts$ if [ "${number%${number#?}}" = "-" ] ; then
> testvalue="${number#?}"
> else
> testvalue="$number"
> fi
geektanic@monolith:~/scripts$ echo $testvalue
24
geektanic@monolith:~/scripts$ echo $number
-24

```

Now I have considered the possibility of reserved names (despite the fact that I have used $number in previous scripts) and replaced all instances with a random string and **still** gotten the same result.

Can someone please tell me what I've done wrong.

---

### Post by falconindy on 2010-01-29
I'm actually having no issues with the script that you've posted. Are you sure you're not using Dash instead of Bash? BTW, the link in your post looks insanely suspicious. I didn't and I won't click on it. If you want to post code, use any of the hundreds of pastebin clones out there or just use code tags here.

---

### Post by cariboo on 2010-01-29
You'll probably get better help here, than in the Cafe.

---

### Post by geektanic on 2010-01-29
> **falconindy said:**
> I'm actually having no issues with the script that you've posted. Are you sure you're not using Dash instead of Bash? BTW, the link in your post looks insanely suspicious. I didn't and I won't click on it. If you want to post code, use any of the hundreds of pastebin clones out there or just use code tags here.

The link is to the publisher forum for the book 'Wicked Cool Shell Scripts' as linked to the main page here: [http://www.intuitive.com/wicked/index.shtml]("http://www.intuitive.com/wicked/index.shtml")

The script specifically posted on the site I linked is as follows...
```
#!/bin/sh
# validint - validate integer input, allow negative ints too

validint()
{
  # validate first field. Optionally test against min value $2 and/or 
  # max value $3: if you'd rather skip these tests, send "" as values.
  # returns 1 for error, 0 for success.

  number="$1";	    min="$2";	   max="$3"

  if [ -z $number ] ; then
    echo "You didn't enter anything. Unacceptable." >&2 ; return 1
  fi
  
  if [ "${number%${number#?}}" = "-" ] ; then	# first char '-' ?
    testvalue="${number#?}" 	# all but first character
  else
    testvalue="$number"
  fi
  
  nodigits="$(echo $testvalue | sed 's/[[:digit:]]//g')"
  
  if [ ! -z $nodigits ] ; then
    echo "Invalid number format! Only digits, no commas, spaces, etc." >&2
    return 1
  fi
  
  if [ ! -z $min ] ; then
    if [ "$number" -lt "$min" ] ; then
       echo "Your value is too small: smallest acceptable value is $min" >&2
       return 1
    fi
  fi
  if [ ! -z $max ] ; then
     if [ "$number" -gt "$max" ] ; then
       echo "Your value is too big: largest acceptable value is $max" >&2
       return 1
     fi
  fi
  return 0
}

# uncomment these lines to test, but beware that it'll break Hack #6
# because Hack #6 wants to source this file to get the validint()
# function. :-)

# if validint "$1" "$2" "$3" ; then
#   echo "That input is a valid integer value within your constraints"
# fi
```

When you say you have no issues with the script I posted, you mean the code I pulled from my terminal? I'm totally clueless to what is wrong then. I've unset and re-created the variables multiple times. At this point I'm sure it's me doing something stupid I'm just too close to it to see what.

---

### Post by saulgoode on 2010-01-30
> **geektanic said:**
> In short I cannot get this script to work: [http://www.intuitive.com/wicked/showscript.cgi?005-validint.sh]("http://www.intuitive.com/wicked/showscript.cgi?005-validint.sh")

... it still refuses to detect a negative integer as stated.

Perhaps you linked to the wrong script? The validint function shown doesn't "detect a negative number", it appears to detect whether the absolute value of a number falls within a range.

---

### Post by geektanic on 2010-01-30
```
  if [ "${number%${number#?}}" = "-" ] ; then	# first char '-' ?
    testvalue="${number#?}" 	# all but first character
  else
    testvalue="$number"
  fi
  
```

This block here should be stripping the "-" sign off the beginning of the variable $number.

Which is exactly what baffles me because it works outside the script under my test variables and yet it fails immediately after injecting it into the script.

---

### Post by Reiger on 2010-01-30
Well it would: /bin/sh is symlinked to the faster, non-interactive and more basic-POSIX shell called dash.

OTOH what you use in your terminal is the heavier, more feature rich shell called bash.

So the hunt for bashisms (shell code that is specific to bash) is on!

This PDF should be a good start: [http://princessleia.com/plug/2008-JP_bash_vs_dash.pdf](http://princessleia.com/plug/2008-JP_bash_vs_dash.pdf)

---

### Post by Vox754 on 2010-01-30
> **geektanic said:**
> 
What drives me the most crazy is that the following **two code blocks provide different results**. I have typed them side by side in the terminal to prove that the only difference is variable name.

```
geektanic@monolith:~/scripts$ **testvalue**="-24"
geektanic@monolith:~/scripts$ echo $testvalue
-24
geektanic@monolith:~/scripts$ number="-24"
geektanic@monolith:~/scripts$ echo $number
-24
geektanic@monolith:~/scripts$ if [ "${**testval**%${testval#?}}" = "-" ] ; then
> **testval2**="${**testval**#?}"
> else
> testval2="$testval"
> fi
geektanic@monolith:~/scripts$ if [ "${**number**%${number#?}}" = "-" ] ; then
> **testvalue**="${**number**#?}"
> else
> testvalue="$number"
> fi
geektanic@monolith:~/scripts$ echo **$testvalue**
24
geektanic@monolith:~/scripts$ echo **$number**
-24

```


Look closely at your interactive session.

At the beginning, you declare **"testvalue"**, but in the in the first if-statement you test **"$testval"**. Then you assign "${testval#?}" to **"testval2"**, but you never echo "$testval2".

You probably defined "testval" somewhere before, so its value remains unchanged.

In the second if-statement you test **"number"**, then you assign "${number#?}" to **"testvalue"**.

You echo both **"$testvalue"** and **"$number"**, which demonstrate the result of the second if-statement, not the first one.

Look at this
```

geektanic@monolith:~/scripts$ testvalue="-24"
geektanic@monolith:~/scripts$ echo $testvalue
-24
geektanic@monolith:~/scripts$ number="-24"
geektanic@monolith:~/scripts$ echo $number
-24
geektanic@monolith:~/scripts$ if [ "${testvalue%${testvalue#?}}" = "-" ] ; then
> testvalue_new="${testvalue#?}"
> else
> testvalue_new="$testvalue"
> fi
geektanic@monolith:~/scripts$ if [ "${number%${number#?}}" = "-" ] ; then
> number_new="${number#?}"
> else
> number_new="$number"
> fi
geektanic@monolith:~/scripts$ echo $testvalue ; echo $testvalue_new
-24
24 
geektanic@monolith:~/scripts$ echo $number ; echo $number_new
-24
24

```

---

### Post by Vox754 on 2010-01-30
> **geektanic said:**
> 
```
#!/bin/sh
# validint - validate integer input, allow negative ints too

validint()
{
  # validate first field. Optionally test against min value $2 and/or 
  # max value $3: if you'd rather skip these tests, send "" as values.
  # returns 1 for error, 0 for success.

  **number**="$1";	    **min**="$2";	   **max**="$3"

  if [ -z $number ] ; then
    echo "You didn't enter anything. Unacceptable." >&2 ; return 1
  fi
  
  if [ "${number%${number#?}}" = "-" ] ; then	# first char '-' ?
    **testvalue**="${number#?}" 	# all but first character
  else
    testvalue="$number"
  fi
  
  nodigits="$(echo **$testvalue** | sed 's/[[:digit:]]//g')"
  
  if [ ! -z $nodigits ] ; then
    echo "Invalid number format! Only digits, no commas, spaces, etc." >&2
    return 1
  fi
  
  if [ ! -z $min ] ; then
    if [ "**$number**" -lt "**$min**" ] ; then
       echo "Your value is too small: smallest acceptable value is $min" >&2
       return 1
    fi
  fi
  ...
}
...
```


Look at the code.

The if-statement only removes the minus sign from "$number", if it is present. Then it uses the resulting "testvalue" as input to "sed" to test for the presence of non-digits.

Perhaps this test can be done all by "sed".
```

...
  **number**="$1";	    min="$2";	   max="$3"

  if [ -z $number ] ; then
    echo "You didn't enter anything. Unacceptable." >&2 ; return 1
  fi
  
  nodigits="$(echo **$number** | sed 's/-*[[:digit:]]*//g')"
...

```

The values actually compared are the original "$number" with the original "$min" and "$max" which, by the way, are not tested for non-digits.

---

### Post by geektanic on 2010-01-30
On that note, Vox, your post above perfectly resolves the issue and fixes the script. Thanks a lot, it's been very helpful!

---

### Post by Vox754 on 2010-01-30
> **geektanic said:**
> On that note, Vox, your post above perfectly resolves the issue and fixes the script. Thanks a lot, it's been very helpful!

It's unclear to me if you actually understood what's going on, or you just decided to use the "sed" solution I used.

Use the original script but print the variables
```

validint()
{
...
  echo "testvalue=$testvalue"
      
  nodigits="$(echo $testvalue | sed 's/[[:digit:]]//g')"

  echo "nodigits=$nodigits"
...
}

if validint "-24" "-30" "+30" ; then
  echo "That input is a valid integer value within your constraints"
fi

```

Then run it with "bash" and "dash"
```

geektanic@monolith:~/scripts$ **bash** 005-validint.sh
testvalue=24
nodigits=
That input is a valid integer value within your constraints

geektanic@monolith:~/scripts$ **dash** 005-validint.sh
testvalue=-24
nodigits=-
Invalid number format! Only digits, no commas, spaces, etc.

```

There is a difference, who knew!

As said, dash is a minimal shell and lacks complicated constructs like substitutions.

---

### Post by geektanic on 2010-01-30
> **Vox754 said:**
> It's unclear to me if you actually understood what's going on, or you just decided to use the "sed" solution I used.


I had taken note that Reiger had earlier pointed out the difference between Dash and Bourne. (Not Bash because as I understand it bash would be #!/bin/bash and I'm running #!/bin/sh)

That said I was already expecting troubles with the script as I had early on run into a road block in that the printed book that I'm going through actually starts:

```
#!/bin/sh
# validint - Validates integer input, allowing negative ints too.

**function** validint
{
```

function being invalid in Bourne (so I exchanged for validint()) - The site I linked for the book's publisher actually has this corrected already but even if I copy his shell script directly instead of using the one that I've written my modifications to, it still failed during said if/else clause. (All other portions worked flawlessly, only identification of negative values failed)

So, yes, I used your code because it works and seemingly more efficiently since it removes an unnecessary if clause. Especially since the if clause apparently does not work in bourne.

---

### Post by Vox754 on 2010-01-30
> **geektanic said:**
> I had taken note that Reiger had earlier pointed out the difference between Dash and Bourne. (Not Bash because as I understand it bash would be #!/bin/bash and I'm running #!/bin/sh)
...
Especially since the if clause apparently does not work in bourne.

You are still a little confused there.

The original "Bourne" shell is not used any more in reality. The default shell in most Linux distributions is Bash, and /bin/sh is just a symbolic link to /bin/bash.
```

user@PC:~$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2009-01-08 08:03 /bin/sh -> bash

```

In 2006, Ubuntu decided to change the symlink to /bin/dash, a smaller shell.
```

user@PC:~$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2009-01-08 08:03 /bin/sh -> dash

```

That means that when you use #!/bin/sh, in reality you are using /bin/dash not the original Bourne shell.

That's why I pointed that the difference in reality is between Bash and Dash.

```

**sh** 005-validint.sh    is the same as    **dash** 005-validint.sh

but different to

**bash** 005-validint.sh

```

All that you read in that book, I believe, is supposed to be compatible with Bash, not Dash, that's why you may get errors.

---

### Post by geektanic on 2010-01-30
Ahh, yes I see now, thanks for clearing that up for me. I'm trying I promise :(

---


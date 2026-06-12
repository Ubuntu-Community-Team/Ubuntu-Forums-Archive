---
title: "bash printf command formating arguments"
date: 2007-01-17
forum: Programming Talk
---

### Post by newsman on 2007-01-17
I h ave already defined Filename as follows: FILENAME="stty.png"


After: printf "%\n" "$FILENAME"

the output i get:

bash: printf: `\': invalid format character


what is going on?
----------------------------------------------------------
According to "Linux Shell Scripting with Bash" i should get a normal output?? (txt in book copied below)

The value of variables can be printed using the printf command. printf has two arguments: a formatting code, and the variable to display. For simple variables, the formatting code is “%s\n” and the variable name should appear in double quotes with a dollar sign in front of the name

---

### Post by Ragazzo on 2007-01-17
You forgot the s in %s

---

### Post by newsman on 2007-01-17
see i am so quick at thinking of solutions.. i forget the problem...lolsssss

---

### Post by osx on 2009-08-11
I'm trying to do something similar where I am grabbing hex values from a file and trying to convert them to decimal.

Example:

```
cut -b 7-10 file.txt | od -t x4 | cut -s -d " " -f 2 | printf "%d\n" $1
```

But all I get back is 0 (i.e., a zero) when I know the proper answer is 11850013.

I know part of the problem is that printf expects either a "0x" or a "\x" to proceed the value in order specify hex as the value to convert. So, I have two questions.

First, how do do get "0x" on the front of the value so that printf knows it is in hexadecimal?

Second, how to I pass the results from cut to printf?

Further explanation. If I do this:

```

cut -b 7-10 file.txt | od -t x4 | cut -s -d " " -f 2
```

I get back this: b4d11d

When I do this to the result of the above command:

```

printf '%d\n' 0xb4d11d
```

I get this result: 11850013

How can I make this all happen in a single command line instead of two?

Thanks.

---

### Post by stylishpants on 2009-08-11
You can't use $1 as in your first example, because nothing is setting $1 to anything.

Neither bash's built-in printf nor /usr/bin/printf appear to have an option to read from stdin.

You could do it with xargs:

```

# use sed to prepend 0x, then xargs to get the output into printf
echo b4d11d | sed 's/^/0x/' | xargs printf "%d"

```

You could also use perl or ruby for this:
```

Here are a few ways to do it in ruby:

bob@box:~$ echo b4d11d | ruby -ne 'puts $_.hex'
11850013

bob@box:~$ echo b4d11d | ruby -ne 'printf "%d\n" % $_.hex'
11850013

bob@box:~$ echo b4d11d | ruby -ne 'printf "%d\n" % "0x#{$_}"'
11850013


```

---

### Post by osx on 2009-08-11
> **stylishpants said:**
> You can't use $1 as in your first example, because nothing is setting $1 to anything.

Neither bash's built-in printf nor /usr/bin/printf appear to have an option to read from stdin.

You could do it with xargs:

```

# use sed to prepend 0x, then xargs to get the output into printf
echo b4d11d | sed 's/^/0x/' | xargs printf "%d"

```

You could also use perl or ruby for this:
```

Here are a few ways to do it in ruby:

bob@box:~$ echo b4d11d | ruby -ne 'puts $_.hex'
11850013

bob@box:~$ echo b4d11d | ruby -ne 'printf "%d\n" % $_.hex'
11850013

bob@box:~$ echo b4d11d | ruby -ne 'printf "%d\n" % "0x#{$_}"'
11850013


```

Thanks. I never used xargs before, but your suggestion worked great.

I may need to create a larger script that does more and will work on Linux, Mac, and Windows. Of ruby and perl, would ruby be the better way to go for cross platform use?

---

### Post by stylishpants on 2009-08-12
> **osx said:**
> Thanks. I never used xargs before, but your suggestion worked great.

I may need to create a larger script that does more and will work on Linux, Mac, and Windows. Of ruby and perl, would ruby be the better way to go for cross platform use?

You can do fine either way, this question comes down to preference.  IMHO, use whichever language you are more comfortable with.  If that leaves you with a tie, brush up on your ruby and go that way.  Ruby has a brighter future and provides a cleaner and clearer type system.

Python would be fine too, for that matter.

I've had success with cross platform development (on Linux and Windows) using both ruby and perl.  Things get a little funny when you interact with the more advanced Windows APIs, but that's not exactly cross-platform anyway.
I've never programmed on the mac with those languages, so no comment there.

---


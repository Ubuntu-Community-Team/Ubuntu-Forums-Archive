---
title: "Bash string equal to retun value of executable?"
date: 2007-08-12
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-08-12
I'm trying to make a cronjob in OpenBSD where I call sysctl to get the temperature of the CPUs.  Now I have very little experience in bash, but a fair amount in many other programming languages.  So here's what I'm trying to do:

call sysctl hw.sensors.lm0.temp.0 
This prints out three temperatures.  The first one I'm assuming is the chipset, usually sitting at around 45'C (although it's hotter than either of the processors, which I would assume it not to be).  The other two I assume are the two processors, sitting at around 33-35'C each.  (There are two dual-core xeon processors, and I would assume each core would monitor it's own temperature, but I guess not).

What I want to do is take these printed outputs and only take out the numbered temperatures, the best I can get is '45.00 degC', although I'm not sure how to take a substring of a printed output.  I tried redirecting the output to a string as 'sysctl .... > $temp1', but that didn't work, as I expected.  Any ideas?

---

### Post by slavik on 2007-08-12
maybe sysctl prints to stderr? try redirecting stderr ( prog 2> err.log)

---

### Post by nitro_n2o on 2007-08-12
I'm not sure about sysctl but for finding a number in your output sounds like grep's job... so instead of directing the output pipe it to grep with the appropriate pattern to match... you can even go advanced and use awk and sid to have a nice formatted output :) but i'm not sure how to do that :(

---

### Post by ssam on 2007-08-12
```

sysctl .... > $temp1

```

would try to write the output to a file with a file name of the contents of the string $temp1

```

temp1=`sysctl hw.sensors.lm0.temp.0`

```
will put the output into the string temp1. note that the quote mark is a GRAVE ACCENT (ascii 0x60) (the forum software may mangle it).

then you can use the string

```

echo $temp1

```
note that you only use the $ to get stuff out ot the string

you could then pipe the string through sed to manipulate it with regular expresions.
```

echo $temp1 | sed 's/[^0-9 ]//g'

```
would remove all chars apart from numbers and space. (those are just normal single quotes)

and i imagine you are wanting to log this to a file
```

echo $temp1 | sed 's/[^0-9 ]//g' >> filename

```

the >> means append to file.

then you could do it all as a one liner

```

sysctl hw.sensors.lm0.temp.0 | sed 's/[^0-9 ]//g' >> filename

```

bash can be very awkward to use when you are used to other programming languages. things like escaping become very important. i strongly recomend a read of [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) it is comprehensive rather than advanced.

---

### Post by bigboy_pdb on 2007-08-12
You mentioned that there's a command that returns '45.00 degC' (I will refer to that command as **temp_command**) and I'm guessing that you want to get the '45.00' part. I would recommend doing the following to extract the tempurature:

temp=$(echo $(**temp_command**) | grep -o '[[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]]')

The following is an explanation of the command (and bear in mind that when standard output is not redirected then it is printed to the screen).

$(**command_to_execute**) executes the command **command_to_execute** and returns the text that is printed (to standard output) by **command_to_execute** where all newlines are replaced by spaces (for proof of this you can run the commands 'ls -l', 'echo $(ls -l) | od -c', and 'ls -l | od -c' and compare the output).

If for some reason you want to read some text that would normally be outputted to the screen line by line, I would recommend using the following code:
```

# current_line is the variable that each line is read into
while read current_line; do
	**command_list**
done < <(**command_that_prints_multiple_lines**)

```

The pipe character '|' sends the standard output of one command into the standard input of another command.

'grep -o reg_exp' prints only the portion of the text it reads that matches the regular expression reg_exp to standard output.

The regular expression '[[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]]' matches any text that is a digit followed by a digit followed by a decimal/period followed by two more digits. If for some reason this regular expression doesn't work, you can use '[0123456789][0123456789]\.[0123456789][0123456789]' which matches a character that is also a digit (0 or 1 or 2 or ... or 9) followed by a digit (0 or 1 or 2 or ... or 9) followed by a decimal/period followed by two more digits (0 or 1 or 2 or ... or 9 followed by 0 or 1 or 2 or ... or 9).

**[EDIT]**
The following command returns the tempurature (remember that $(command) returns the output of the command):

$(echo $(temp_command) | grep -o '[[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]]')

and 

temp=$(echo $(**temp_command**) | grep -o '[[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]]')

stores it in the variable called temp
**[/EDIT]**

So in other words one of the following commands should store the temperature in the variable temp.

temp=$(echo $(**temp_command**) | grep -o '[[:digit:]][[:digit:]]\.[[:digit:]][[:digit:]]')

temp=$(echo $(**temp_command**) | grep -o '[0123456789][0123456789]\.[0123456789][0123456789]')

If you want to print it to the screen, you can use 'echo $temp' to do this.

---

### Post by mrpeenut24 on 2007-08-12
> **ssam said:**
> 
```

temp1=`sysctl hw.sensors.lm0.temp.0`

``````

echo $temp1 | sed 's/[^0-9 ]//g'

```

Awesome thanks ssam!  I just didn't know how to store it into a variable, because I'm eventually going to have to send it to gnuplot.  Also I hadn't thought of using sed, instead I was going to use substring, but this will help me if the temperature is over 99.  Thanks everyone for the help!

---


---
title: "Psensor: is it possible to save its output to a file?"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by vasa1 on 2012-06-06
I have installed Psensor from the Ubuntu Software Center and like it very much.

However, I would like to know if it is possible to somehow capture (pipe? stream?) the data it outputs graphically _also_ to a file for a longer period than what appears to be the default of ten minutes.

"It can monitor: the temperature of the motherboard and CPU sensors (using lm-sensors)." (excerpted from its page at USC.)

I'm enclosing a typical image with both temperature and CPU usage ticked.

I have looked for a log file in /var/log but didn't find anything related to Psensor.

There _is_ ~/.psensor/log but it's always empty.

The reason I'm asking is that I want to compare different environments (Unity 2D versus Xfce 4.10) to see which runs cooler and takes less CPU usage. And, rather than taking screenshots ever so often, if I could log the values to a file, I could later play with them in LibreOffice Calc's charts.

(Just in case it isn't clear ... I don't know programming)

---

### Post by 3rdalbum on 2012-06-06
You may be able to use the command-line "sensors" program (which should be installed already for you, since you've already got lm-sensors), piped to a text file.

```
sensors > sensor-test1.txt
```

Unfortunately 'sensors' only runs once, then exits. You may be able to use the 'watch' command to keep running it:

```
watch sensors > sensor-test1.txt
```

But it doesn't seem to work properly for me.

---

### Post by Vaphell on 2012-06-06
yes, command line tools are best suited for dumping output to readable files

```
while true; do sensors | grep 'CPU Temperature' >> log.txt; sleep 15; done
```
infinite loop with 15 second interval dumping CPU temp line to given file.
>> appends data to output file, > overwrites output file

---

### Post by vasa1 on 2012-06-06
Vaphell's suggestion is what I'm using right now. (I had to change CPU Temperature to temp1).

I'm wondering if it is possible to time-stamp each line. I didn't see any switch or option for that with the sensors command.

Otherwise, I can just take the time the file was created and go from there.

---

### Post by Vaphell on 2012-06-06
you need 2 things:
```
date '+%F %H:%M:%S'
```
date --help if you need other format

```
sensors | grep 'temp1' | sed -r 's/^.*: +(.*) +[(].*$/\1/'
```
sed should get rid of the sensor name and thresholds, leaving only temp - though it depends on the actual output format you get

mashing it together:
```
echo $( date '+%F %H:%M:%S' ): $( sensors | grep 'temp1' | sed -r 's/^.*: +(.*) +[(].*$/\1/' ) >> log.file

-- output
2012-06-07 02:22:45: +37.0°C

```

---

### Post by vasa1 on 2012-06-06
> **Vaphell said:**
> you need 2 things:
```
date '+%F %H:%M:%S'
```
date --help if you need other format

```
sensors | grep 'temp1' | sed -r 's/^.*: +(.*) +[(].*$/\1/'
```
sed should get rid of the sensor name and thresholds, leaving only temp - though it depends on the actual output format you get

mashing it together:
```
echo **$**( date '+%F %H:%M:%S' ): **$**( sensors | grep 'temp1' | sed -r 's/^.*: +(.*) +[(].*$/\1/' ) >> log.file

-- output
2012-06-07 02:22:45: +37.0°C

```
Thanks for that, Vaphell. I spent quite some time last night pushing things along but ended up with something quite long. I will look at your code a little later on today which seems to have things I don't know about like the use of **$**.

---

### Post by vasa1 on 2012-06-07
Re. the **$** after **echo**, is [http://www.askdavetaylor.com/backtick_notation_mean_bash_shell_script.html](http://www.askdavetaylor.com/backtick_notation_mean_bash_shell_script.html) the appropriate explanation?

---

### Post by vasa1 on 2012-06-07
Getting the regex for sed took me quite a while ;)
I had to make quite a few guesses about things but now```
echo $( date '+%H:%M:%S' ): $( sensors | grep 'temp1' | sed -r 's/^.*:        +(.*)  +[(].*$/\1/' ) >> templog.txt
```works for me.
I'll take a break and get to the *while true ... done* bit a little later but it seems like it's going to be perfect.

---

### Post by vasa1 on 2012-06-07
> **vasa1 said:**
> Re. the **$** after **echo**, is [http://www.askdavetaylor.com/backtick_notation_mean_bash_shell_script.html](http://www.askdavetaylor.com/backtick_notation_mean_bash_shell_script.html) the appropriate explanation?In other words, $() is used instead of backticks.

---

### Post by Vaphell on 2012-06-07
yes, backticks are deprecated and $() should be used instead. In case of multiple layers of commands $() don't require escaping of stuff, while backtics do. It's obvious where $() begins and where it ends when there are many of these lumped together while backticks lack that readability plus they can be mistaken for ' ' by tired eyes.

```
sed -r 's/^.*:        +(.*)  +[(].*$/\1/'
```

these multiple spaces should not be required, + = 1-or-more (* = 0-or-more, ? = 0-or-1) so ' +' should be enough. If you are sure the number of spaces is fixed you can put as many spaces as required (which is what you probably did) or use ' {4}' (whatever the number is) and drop + entirely. What does the line of interest look like exactly?

crude example
```
$ echo "xxx:    +44.4C  (..." | sed -r 's/^.+: +(.+) +[(].+$/\1/'
+44.4C 
$ echo "xxx:    +44.4C  (..." | sed -r 's/^.+: {4}(.+) {2}[(].+$/\1/'
+44.4C
```

---

### Post by vasa1 on 2012-06-07
> **Vaphell said:**
> ...
these multiple spaces should not be required, + = 1-or-more (* = 0-or-more, ? = 0-or-1) so ' +' should be enough. If you are sure the number of spaces is fixed you can put as many spaces as required (which is what you probably did) or use ' {4}' (whatever the number is) and drop + entirely. What does the line of interest look like exactly?
...
Here's the line:
```
temp1:        +46.5°C  (crit = +93.0°C)
```
Yes, I counted the spaces and added them into the expression.
BTW, I've marked this as **solved** even though there's a lot more for me to learn about the intricacies of sed ;)

Once again, thanks for your help!

---

### Post by vasa1 on 2012-06-08
This is what I have now:
```
while true; do echo $( date '+%H:%M:%S' ), $( sensors | grep 'temp1' | sed -r 's/^.* {8}\+(.*)°C  .*$/\1/' ) >> zzz.txt; sleep 15; done
```keeping in mind that the **sensors** line being processed is ```
temp1:        +44.5°C  (crit = +93.0°C)
```
The minor changes are to have a cleaner output (like a .csv file which doesn't need cleaning up in LibreOffice Calc) and the odd filename is to get to it in the folder by just typing 'z'. (I don't have any other files starting with 'z'.)

I was wondering a bit about the "°C" and how it would behave in the regex but there wasn't an issue.

---

### Post by jeanfi on 2012-07-06
Psensor is logging temperatures when the debug mode is enabled (option '-d 3'). 
psensor-server has the same feature/option.

You will have this kind of log output:

[1335777734] [DEBUG] Measure: CPU 34.00
[1335777734] [DEBUG] Measure: Core 0 34.00
[1335777734] [DEBUG] Measure: Core 1 34.00
[1335777734] [DEBUG] Measure: CPU Fan 763.00
[1335777734] [DEBUG] Measure: Case Fan2 0.00
[1335777734] [DEBUG] Measure: Case Fan 526.00
[1335777734] [DEBUG] Measure: temp1 35.00
[1335777734] [DEBUG] Measure: temp2 42.00
[1335777734] [DEBUG] Measure: temp3 34.00
[1335777734] [DEBUG] Measure: HDD 32.00
[1335777734] [DEBUG] Measure: GPU NVidia 37.00

First field is the date of the measure (number of senconds since the Epoch), last field is the temperature using Celcius unit.

This feature has been added only few months ago in the development branch. You can give it a try by compiling psensor directly from the source repository or by using ppa:jfi/psensor-daily-trunk PPA. It will be in the future v0.7.0 release.

Anyway, Psensor is not the most efficient way to log temperatures (log output is not compact and psensor or even psensor-server will require more cpu/memory resources than a simple script based on 'sensors'). I think that previous reponses are more approriate to your need. Maybe you should also take a look at: [http://www.lm-sensors.org/wiki/man/sensord](http://www.lm-sensors.org/wiki/man/sensord)

> for a longer period than what appears to be the default of ten minutes.Yes, 10mn is the default, you can change it using menu>psensor>preferences>graph>monitoring duration

---

### Post by vasa1 on 2012-07-06
I'm sorry I didn't see this post earlier! Thanks for replying. I do hope you'll visit more often :)

---

### Post by jeanfi on 2012-07-06
> **vasa1 said:**
> I do hope you'll visit more often :)
Please, don't hope too much:) 
I never monitor this forum nor plan to do it in the future, I just discovered your bunch of psensor questions by chance.
If you need some help from me, the best way is to send an email to [email]jeanfi@gmail.com[/email] with a subject starting with '[psensor]'.

---

### Post by vasa1 on 2012-07-06
> **jeanfi said:**
> Please, don't hope too much:) 
I never monitor this forum nor plan to do it in the future, I just discovered your bunch of psensor questions by chance.
If you need some help from me, the best way is to send an email to [email]jeanfi@gmail.com[/email] with a subject starting with '[psensor]'.

Okay, no problem :)

---


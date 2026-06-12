---
title: "Math function with sed or awk"
date: 2012-03-06
forum: Programming Talk
---

### Post by mastermindg on 2012-03-06
I have a file that has a sequence of repeating data that looks like this:


```
height=42
align=left><a
href="download.php/myfile.zip><img

align="right"><b><a
align=center>
align=center><nobr>2011-09-25<br
align=center>175.17<br>MB</td>
align=center>469<br>times</td>
align=center><b><a
align=center>0</td>
align=left><a
```

How do I print the previous five lines of the file if a line containing MB has a value less than 200?

Thanks!

---

### Post by emiller12345 on 2012-03-06
this is not exactly what you asked but I think it might be useful for what your doing. For me its not easy to use sed to match new lines, so i'd alter the output to only have newlines where i'd need them
```
$ cat filename | tr '\n' '~' | sed 's/href\="/\nhref\=/g' | sed 's/MB<\/td>/MB<\/td>\n/g' | grep "MB<\/td>" | tr '~' ' '
```from here you'd get an output like
```

href=download2.php/myfile.zip><img  align="right"><b><a align=center> align=center><nobr>1911-09-25<br align=center>175.17<br>MB</td>
href=download3.php/myfile.zip><img  align="right"><b><a align=center> align=center><nobr>2010-09-25<br align=center>999.22<br>MB</td>
href=download4.php/myfile.zip><img  align="right"><b><a align=center> align=center><nobr>2011-09-25<br align=center>67.32<br>MB</td>

```where all the important data is now on one line, making it easier to filter

Edit:
dropping it into a loop with a bc comparison, you can see if it's less then 200 MB
```
$ for i in $(cat filename | tr '\n' '~' | sed 's/href\="/\nhref\=/g' | sed 's/MB<\/td>/MB<\/td>\n/g' | grep "MB<\/td>"); do megabyte="$(echo $i | tr '~' ' ' | grep -o ">\([^<]*\)<br>MB" | cut -d\> -f2 | cut -d\< -f 1)"; if [ "$(echo "$megabyte < 200" | bc)" = "1" ]; then echo $i | tr '~' ' '; fi; done
```this yields
```

href=download2.php/myfile.zip><img  align="right"><b><a align=center> align=center><nobr>1911-09-25<br align=center>175.17<br>MB</td>
href=download4.php/myfile.zip><img  align="right"><b><a align=center> align=center><nobr>2011-09-25<br align=center>67.32<br>MB</td>

```

---

### Post by mastermindg on 2012-03-06
Thanks emiller for the response! It's not exactly what I wanted but it's definitely getting me on the right track. Unfortunately when I run the the inital output thru a loop I'm getting syntax errors:
```
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
align=center>175.17<br>MB</td>
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
(standard_in) 1: syntax error
align=center>67.32<br>MB</td>
```

I'm not sure why, though. I copied the output from the box 2nd from the top just in case. If you could have a look that would be great. Thanks.

---

### Post by emiller12345 on 2012-03-06
I think i might have seen this before.  bash for loops dont iterate line by line, they iterate by line or space. you might need to add a another couple tr's in the loop to remove the spaces, then add them back in once your inside a single iteration.

Update:
try running using a copy of your original format to do the processing, not what I had already formatted

---

### Post by mastermindg on 2012-03-06
Thanks for the help! I really appreciate your time and patience!

My solution was kind of sneaky but nevertheless works. I ended up scrapping the suggestions(no offense) and stuck with my original data. Used grep to grab the line numbers and then awk to filter and pick the line number back up:

lineno=$(cat filename | grep -n MB | sed 's/>/:/' | awk -F":" ' $3 < 200 ' | awk -F":" '{print $1}')
link=$(echo $(($lineno-6)))
sed -n '$linkp'

Fortunately the data is generated in php and the formatting is always the same so I know that the link that I'm trying to get is always going to be 6 lines up from the size.

---

### Post by Khayyam on 2012-03-06
Edit ... gahhh, I really need to read the problem **before** providing a solution ... sorry.

Anyhow, I get the sense that actually you don't want "the previous 5 lines" because why would you want '<align'?

So the line before the match ...

```
awk -v n=1 '/MB/ && NR>n {print i[(NR-n)%n]}{i[NR%n]=$0}' input.txt
```

The fifth line before the match ...

```
awk -v n=5 '/MB/ && NR>n {print i[(NR-n)%n]}{i[NR%n]=$0}' input.txt
```

... and yes I know it doesn't match '< 200' ... you are going about this all the wrong way. Strip the data **then** parse. If you look at my previous post you will see tabulated data and the method of printing and evaluating it.

best ... khay

---

### Post by Khayyam on 2012-03-06
> **mastermindg said:**
> lineno=$(cat filename | grep -n MB | sed 's/>/:/' | awk -F":" ' $3 < 200 ' | awk -F":" '{print $1}')

My name's x and I'm a pipeaholic ... hehe

best ... khay

---


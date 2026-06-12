---
title: "alternative to clear"
date: 2012-02-22
forum: Programming Talk
---

### Post by bigrockcrasher on 2012-02-22
I am currently write a bash script that will periodicity output some data. I am using command clear only show the newest data. but the problem is clear only moves the last output above the top of the terminal which means you can scroll to see the old data. it never permanently the other outputs. how do I clear the previous output. i know you can clear the history cache that is not what i want. i want just the permanently clear the output of the current executing bash script

---

### Post by cortman on 2012-02-22
> **bigrockcrasher said:**
> I am currently write a bash script that will periodicity output some data. I am using command clear only show the newest data. but the problem is clear only moves the last output above the top of the terminal which means you can scroll to see the old data. it never permanently the other outputs. how do I clear the previous output. i know you can clear the history cache that is not what i want. i want just the permanently clear the output of the current executing bash script

Redirect STDOUT to /dev/null?

---

### Post by bigrockcrasher on 2012-02-22
this just prevent anything to outputting to the screen. I want to view only the newest data

---

### Post by t1497f35 on 2012-02-22
tput reset

---

### Post by sudodus on 2012-02-22
If you write only one line, you can overwrite that line, which is fairly simple using ANSI escape code
[[COLOR="Red"]_http://en.wikipedia.org/wiki/ANSI_escape_code_[/COLOR]]("http://en.wikipedia.org/wiki/ANSI_escape_code")

If you write several lines it is also possible to overwrite using ANSI escape code, but a little more tricky.

Use the escape codes to move the cursor and to clear lines or part of lines.

---

### Post by bigrockcrasher on 2012-02-22
> **t1497f35 said:**
> tput reset
That just clears all output from previous command line calls. I am looking for something like the command "top". where the output of the command is cleared first before outputting again but not clearing any of the previous command outputs

---

### Post by WasMeHere on 2012-02-22
> **sudodus said:**
> If you write only one line, you can overwrite that line, which is fairly simple using ANSI escape code
[[COLOR="Red"]_http://en.wikipedia.org/wiki/ANSI_escape_code_[/COLOR]]("http://en.wikipedia.org/wiki/ANSI_escape_code")

If you write several lines it is also possible to overwrite using ANSI escape code, but a little more tricky.

Use the escape codes to move the cursor and to clear lines or part of lines.
+1

Here is an example how to implement ANSI escape code. I do not erase lines.
```
#!/bin/bash
#
# init
typeset key=
typeset      dow=+$'\E[37m'$'\E[1;2H'"%A"
typeset      day=$'\E[2;4H'"%e"
typeset      month=$'\E[3;3H'"%b"$'\E[0m'

typeset      time=+$'\E[37m\E[2;2H'"%_H.%M.%S"$'\E[0m'$'\E[1;1H'
typeset      year=+$'\E[37m\E[2;3H'"%Y"$'\E[0m'$'\E[1;1H'
typeset      cls=+$'\E[2J'

while [ "$key" != q ]

do

# date

 echo "$cls"
 echo -n `/bin/date "$dow$day$month"`
 read -sn 1 -t 3 key

 if [ "$key" != q ]
 then
  echo "$cls"
  echo -n `/bin/date "$year"`
  read -sn 1 -t 3 key
 fi

# time

 if [ "$key" != q ]
  then
  echo "$cls"
  echo -n `/bin/date "$time"`
  read -sn 1 -t 4 key
 fi
 echo "$cls"
done

```
In order to erase lines (instead of 'clear screen') you should use
> CSI n K 	***EL - Erase in Line*** 	Erases part of the line. If n is zero (or missing), clear from cursor to the end of the line. If n is one, clear from cursor to beginning of the line. If n is two, clear entire line. Cursor position does not change.
which is ***'escape [ 2 K'*** or [FONT="Courier New"]**[SIZE="3"]'\E[2K'[/SIZE]**[/FONT] in a linux terminal window.

---


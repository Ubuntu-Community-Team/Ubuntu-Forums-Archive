---
title: "Regular Expression"
date: 2008-11-20
forum: Programming Talk
---

### Post by Mbengi Bongi on 2008-11-20
Can someone tell me what the regular expression for an exact match in a Bash shell script is?

e.g. A user inputs data and the script searches for an exact match to what the user inputs.


Many thanks

---

### Post by fredscripts on 2008-11-20
I think you may read: [http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_04.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/chap_04.html)

---

### Post by Mbengi Bongi on 2008-11-20
How do I get the script to check if the input is an exact match of a string in a text file?

I'm guessing **if** and **grep** are involved, I just can't seem to combine the two. :confused:

---

### Post by raf_kig on 2008-11-20
```

if grep -q "$string" "$filename";
    then echo found something
fi;

```

There  you go, but you should really read up some basic shell scripting stuff.

And btw. if the input contains user could still use regex in $string.

Regards,

raf

---

### Post by Mbengi Bongi on 2008-11-21
Thanks very much Raf_Kig,

Just before I read your post I was doing exactly just that and i did:

```
if (grep -siq $input data1.csv); then

SNN=$(grep -siw $input data1.csv | cut -d, -f2)
echo -e "Station Name:" '\E[37m'$SNN  ; tput sgr0 
else
echo "Station Not found"
```

So my script is (mainly) working now

Do you know (anybody?) how I can get the script to look for a certain word (the word will always be at a certain position in each row in data1.csv) and if that word is present the script echoes

**Depot Name:**

instead of

**Station Name:**

I've tried:
```

if grep -q "DEPOT" "data1.csv"; then
echo -e "Depot Name:" '\E[37m'$SNN  ; tput sgr0 
else
echo -e "Station Name:" '\E[37m'$SNN  ; tput sgr0 
fi

```

but this doesn't work - I've tried with single/double quotes etc

I was just wondering whether my ANSI escape codes are interfering at all or am I doing something wrong? :(

---

### Post by ghostdog74 on 2008-11-21
> **Mbengi Bongi said:**
> Can someone tell me what the regular expression for an exact match in a Bash shell script is?

e.g. A user inputs data and the script searches for an exact match to what the user inputs.


Many thanks

to look for exact match, you use the == operator, not necessary regular expression. I do not understand your requirement, however, to search for exact match of a word in a certain column, eg 3rd column
```

awk '$3=="someword"' file

```

---

### Post by Mbengi Bongi on 2008-11-23
My script is basically an enquiry tool for UK railway stations.

A user inputs a code and the details for that station are retrieved from the csv file.

Some data refers to Depots rather than stations, what I need is

**Depot Name:**

to be echoed instead of

**Station Name:**

I though by having the word 'DEPOT' in the csv file at the end of each row the script would detect this and change the heading accordingly.

---


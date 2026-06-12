---
title: "Count occurence of a character per line in a HUGE file"
date: 2006-11-17
forum: Programming Talk
---

### Post by tenjin on 2006-11-17
Hi,

I have a csv file with 4 million rows...

I need to be able to count how many delimeter characters there ar on each line (semi-colon) as I'm getting import failures describing "too many fields" errors.

As the file has 4 million lines in it it's basically crashing everything I try to open it in, or at best, it renders the application unusable.

Can anyone give me some Perl / bash / AWK etc. that will give me a report of the occurences of ';' per line in my file?

Thanks

D.

---

### Post by hod139 on 2006-11-17
Here's some bash
```

cat "HUGE_FILE" | tr -cd  ";" | wc -c

```For a nice script version of this see [here]("http://tldp.org/LDP/abs/html/extmisc.html#LETTERCOUNT").

**Edit:** I misread your first post.  The above command will give the total count in the file.  It will take a little more work to get a number per line:

```

while read line; do echo "$line" | tr -cd  ";" | wc -c; done <HUGE_FILE 1>OUTFILE

```Note, you probably won't want to echo the count to the screen anymore, but output it to a file which is why I am redirecting the output to OUTFILE

**Edit 2:** last edit.  I decided to make the output prettier: it now prints the line number and the count
```

n=0; while read line; do echo -n "$((n=$((n + 1)))) -> "; echo "$line" | tr -cd  ";" | wc -c; done <HUGE_FILE 1>OUT_FILE

```

---

### Post by ghostdog74 on 2006-11-17
A Python alternative:

```

count = 0 	
for lines in open("file4million.txt"):
 	c = lines.count(";")
 	count = count + c
print "Total delimiter count: " , count

```

---

### Post by tenjin on 2006-11-17
Hi,

Fantastic, thanks!

Trying it now...

D.

---

### Post by shawnhcorey on 2006-11-17
> **tenjin said:**
> Hi,

I have a csv file with 4 million rows...

I need to be able to count how many delimeter characters there ar on each line (semi-colon) as I'm getting import failures describing "too many fields" errors.

As the file has 4 million lines in it it's basically crashing everything I try to open it in, or at best, it renders the application unusable.

Can anyone give me some Perl / bash / AWK etc. that will give me a report of the occurences of ';' per line in my file?

Thanks

D.

Have you tried making a copy of the file and delete all but the first 10 rows of it? Sometimes when an application says, "Too many fields," it means too much data; the file is too big.

Have you inspected the first few rows of the data? Many applications have a limit of 255 fields per row. You can usually tell this by examining the first few rows.

---

### Post by almostlinux on 2008-07-31
I stumbled across this through a google search.

The read followed by cat | tr | wc method is incredibly slow. 

Doubt if the original author would read this but,

awk 'BEGIN { FS = ";" } ; { print NF-1 }' <million_lines.csv>

---

### Post by tenjin on 2008-08-02
Hi,

I'm still here!  8-)

Thanks for the code, I appreciate you taking the time to post it for me. I'll try it out now.

Cheers

D.

---


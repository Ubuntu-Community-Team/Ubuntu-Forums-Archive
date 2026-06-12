---
title: "Bash newbie help -"
date: 2013-04-22
forum: Programming Talk
---

### Post by Rush2112 on 2013-04-22
Hello - I'm a bash newbie and would be very grateful for your help.

I need to run a bash script via cron to update a file.
The file is a .DAT (similar to csv) and contains pipe separated values.
I need to insert a header row at the top.

I would like to:

1) Make a backup of the file
2) Insert a header row **if not already present**
3) Save the file (replacing the old one)
4) add a success or failure message (perhaps appended to the cron email).
5) Exit

1) run via cron on my server for a specific user account

Here's what I have so far:

```


#!/bin/bash
# Grab the file, make a backup and insert the new line
sed -i.bak 1i"red|blue|green|orange|yellow" thefilename.dat

Exit


```

How can I prevent sed adding the header if it already exists?

---

### Post by BlinkinCat on 2013-04-22
Hi,

Until you get a specific answer to your problem, I would just like to let you know that there are 10 links to "bash" in the Links page of NewDocs - See link in my signature.

[https://help.ubuntu.com/community/Links](https://help.ubuntu.com/community/Links)

I trust you will receive an answer to your problem.

Cheers - :)

---

### Post by mo.reina on 2013-04-22
I think ```
grep
``` returns true if it finds what it's looking for no?

If that's the case you can do something like:

```
if grep <header>
             do something
          else
             insert header
```

---

### Post by matt_symes on 2013-04-22
Hi

> How can I prevent sed adding the header if it already exists?

You can use sed :smile:

```
sed -i  '1 s/^$/red|blue|green|orange|yellow/' filename
```

**^$** will ensure the line only gets added if the first line is empty

Kind regards

---

### Post by prodigy_ on 2013-04-22
> **matt_symes said:**
> **^$** will ensure the line only gets added if the first line is empty
I'd expect it to be not empty in a CSV file.

And there's a possible problem with grep solution suggested above: it will search the entire file, not just the first line. To be sure you need something like:
```
head -1 /path/to/file_name | grep pattern || sed ...
```

For success/failure monitoring check **set -e** and **set -x** from bash manpage. -e makes the script to stop on any untested command that exits with nonzero status. Then you can simply check the script exit status. -x makes every command to be echoed in STDERR so you can redirect 2>/path/to/log_file and get a complete trace log.

---

### Post by schragge on 2013-04-22
> **prodigy_ said:**
> And there's a possible problem with grep solution suggested above: it will search the entire file, not just the first line.No, it won't. The [COLOR=#ff0000]1[/COLOR] there restricts it to the first line:
```
sed -i  '[COLOR=#ff0000]1[/COLOR] s/^$/red|blue|green|orange|yellow/' filename
```
I'd suggest
```
sed -i.bak '1{/^red|/!s/^/red|blue|green|orange|yellow\n/}' filename
```
or
```
sed -i.bak $'1{/^red|/!ired|blue|green|orange|yellow\n}' filename
```
Any error messages from *sed* would be emailed to you by *cron* anyway. If you also want to be notified when the file has the header (either inserted by *sed* or already present before) then probably just grepping for it would be enough:
```
grep -nm1 '^red|' filename
```

---


---
title: "Simple CSV script - plug into template"
date: 2007-04-05
forum: Programming Talk
---

### Post by jaykup on 2007-04-05
I'm looking to take a CSV file and plug each CSV value into a template per line.  I have some examples to better understand..

This is the CSV file.  It is much longer, these are the first few lines.  You can see the pattern.

```
CPP-R2223-1,"COLORANT, WARM RED (UV)",PolyPropylene, Virgin, Regrind,Weight:,Verified By:,Date Verified:
9202,"COLORANT, WHITE",N\A, Virgin, Regrind,Weight:,Verified By:,Date Verified:
W06105,"COLORANT, WHITE",N\A, Virgin, Regrind,Weight:,Verified By:,Date Verified:
CST-W 1034-1,"COLORANT, WHITE",N\A, Virgin, Regrind,Weight:,Verified By:,Date Verified:
W04938,"COLORANT, WHITE",N\A, Virgin, Regrind,Weight:,Verified By:,Date Verified:
PC-004,"COLORANT, WHITE",N\A, Virgin, Regrind,Weight:,Verified By:,Date Verified:
```

This is the template that I would like to plug these values into --


```
<html>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=7 STYLE="font-size: 60pt">[COLOR="Red"]**VAR1**[/COLOR]</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=7 STYLE="font-size: 36pt">[COLOR="Red"]**VAR2**[/COLOR]</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=7 STYLE="font-size: 36pt">[COLOR="Red"]**VAR3**[/COLOR]</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=6 STYLE="font-size: 28pt">[COLOR="Red"]**VAR4**[/COLOR]</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=6 STYLE="font-size: 28pt">**[COLOR="Red"]VAR5[/COLOR]**</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=6 STYLE="font-size: 28pt">**[COLOR="Red"]VAR6[/COLOR]**</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=6 STYLE="font-size: 28pt">**[COLOR="Red"]VAR7[/COLOR]**</FONT></P>
<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">
<FONT SIZE=6 STYLE="font-size: 28pt">**[COLOR="Red"]VAR8[/COLOR]**</FONT></P>
</html>
```

You can see the CSV file has many symbols and extra commas.  Each of the VAR1 VAR2 would be replaced with its respective CSV.  One line of the CSV file would populate that entire template, and the next line would populate a new template.

Lastly, I want to create separate files for each line with file names based on the first value of each line.

Can someone point me in the right direction?

---

### Post by WW on 2007-04-05
Python, perl, awk, etc... take your pick!

Here is a Python program to do it:
```

#!/usr/bin/env python

#
# process_csv.py
#

import sys
import csv

def line2(field,fs1, fs2):
    return '<FONT SIZE=' + str(fs1) + ' STYLE="font-size: ' + str(fs2) + 'pt">' + field + '</FONT></P>\n'


if len(sys.argv) != 2:
    print "use: process_csv csv_file"
    sys.exit(-1)

try:
    csvfile = open(sys.argv[1],"rb")
except IOError:
    sys.exit('Unable to open %s' % sys.argv[1])

line1 = '<P CLASS="western" ALIGN=CENTER STYLE="margin-top: 0.08in; margin-bottom: 0.25in">\n'
reader = csv.reader(csvfile)
for row in reader:
    filename = row[0].strip() + ".html"
    filename = filename.replace(" ","_")  # Delete this line if spaces in file names are OK.
    try:
        outfile = open(filename,"w")
    except IOError:
        print 'Unable to create the file %s; skipping.' % filename
        continue
    outfile.write('<html>\n')
    outfile.write(line1)
    outfile.write(line2(row[0],7,60))
    outfile.write(line1)
    outfile.write(line2(row[1],7,36))
    outfile.write(line1)
    outfile.write(line2(row[2],7,36))
    outfile.write(line1)
    outfile.write(line2(row[3],6,28))
    outfile.write(line1)
    outfile.write(line2(row[4],6,28))
    outfile.write(line1)
    outfile.write(line2(row[5],6,28))
    outfile.write(line1)
    outfile.write(line2(row[6],6,28))
    outfile.write('</html>\n')
    outfile.close()

```
Suppose your data file is data.csv.  Run this program in a terminal like this
```

$ python process_csv.py data.csv

```
Note that the program replaces any spaces in the file names with underscores. You can delete the line that makes this change if you don't mind spaces in the file names.

---

### Post by jaykup on 2007-04-05
Perfect!  I had to remove an extra > to make it work right, but thanks!

return '<FONT SIZE=' + str(fs1) + '> STYLE="font-size: 

to

return '<FONT SIZE=' + str(fs1) + ' STYLE="font-size: 

The power of python always amazes me!

---

### Post by WW on 2007-04-05
Whoops.  I took the extra > out of the code above.

Yeah, the "batteries included" approach that python takes is nice. I hadn't use the CSV module before, but csv is such a fundamental format that I figured something like it had to exist.  A google for "python csv" leads right to the docs.

---

### Post by jaykup on 2007-04-05
Yup!  It's time to read some books on python it's self.  It may be a little slower than perl, but it sure is easier to read and seems more powerful

---

### Post by jaykup on 2008-09-16
I just wanted to say thanks again (WW) for the program you created, and wanted to show you how I used it in the real world.

It has made everyones lives easier over the past year.

This is what the folder structure looks like.  Each file is easy to find by simply typing in the window, and easily modified by Word (easy for users who aren't very computer savvy).

[[IMG]http://img176.imageshack.us/img176/753/zresinsheetsresin200809vm0.th.png[/IMG]](http://img176.imageshack.us/my.php?image=zresinsheetsresin200809vm0.png)

What it looks like in word:

[[IMG]http://img176.imageshack.us/img176/5126/709natpolyacdocmicrosofak3.th.png[/IMG]](http://img176.imageshack.us/my.php?image=709natpolyacdocmicrosofak3.png)

And what it looks like out in the warehouse:

[[IMG]http://img176.imageshack.us/img176/3706/IMG_1735Custom.th.jpg[/IMG]](http://img176.imageshack.us/my.php?image=IMG_1735Custom.jpg)

[[IMG]http://img176.imageshack.us/img176/3010/IMG_1736Custom.th.jpg[/IMG]](http://img176.imageshack.us/my.php?image=IMG_1736Custom.jpg)

Up close:

[[IMG]http://img176.imageshack.us/img176/4343/IMG_1737Custom.th.jpg[/IMG]](http://img176.imageshack.us/my.php?image=IMG_1737Custom.jpg)

Before we had these identification sheets, our technicians had to try and find resin by looking at 3.5" labels, and some were on high shelves, or just didn't have labels at all.  We got a lot of different resins from the same suppliers, so the large print like "Ashland" on the outside didn't help either.  It is still a work in progress, but now they can easily identify resins.  When they are put away, new labels can be looked up easily and printed instantly.

The script only took a few seconds to run through over 500 different labels and create 500 files.

---


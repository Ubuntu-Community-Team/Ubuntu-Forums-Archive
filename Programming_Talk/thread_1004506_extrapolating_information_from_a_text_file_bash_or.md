---
title: "extrapolating information from a text file bash or perl"
date: 2008-12-07
forum: Programming Talk
---

### Post by dunryc on 2008-12-07
Hi guys heres hoping some one can help I have alrge text file with details of people who have applied or bee granted/ declined a consumer credit license in the UK the format is below :-

> Consumer Credit Bulletin
Period From:   01/12/2008   To:   06/12/2008
Standard Licences Issued
Region:   All
	
Licensee	The Harley Gallery
Categories	Credit brokerage
Right To Canvass Off Trade Premises	No
Licence No	0543037
Commencement Date	05-Nov-2003		

	
Licensee	Andrew Jones
Also Trading As	Clover Financial Services
Categories	Consumer credit
Consumer hire
Credit brokerage
Credit reference agency
Debt adjusting/counselling
Debt collecting
Right To Canvass Off Trade Premises	No
Licence No	0590185
Commencement Date	29-Sep-2006		

	
Licensee	Satvision UK Limited
Also Trading As	Sarvision Uk Ltd
Satvision Uk
Categories	Consumer hire
Credit brokerage
Right To Canvass Off Trade Premises	No
Licence No	0607685
Commencement Date	31-Oct-2007		

	
Licensee	Warren Davies Ltd
Also Trading As	Llwynhendy Dental Surgery
Warren Davies Dental Care
Warren Davies Dental Care (Dental Practice).
Categories	Consumer credit
Consumer hire
Credit brokerage
Right To Canvass Off Trade Premises	No
Licence No	0616616
Commencement Date	01-Dec-2008

what i want to do is use the text file as input and convert to csv i only need to grab details on the company's that include credit brokerage as one of there catergoires Does any one know if this type of program is possbiel or even feasible ?

> Licensee,Also Trading As 1,Also Trading As 2,Also Trading As 3,Also Trading As 4, License Number , Commencment Date 

Thanks Dunryc

---

### Post by WW on 2008-12-07
Here's a python script you could experiment with:

get_licence_data.py
```

import sys

if len(sys.argv) < 2:
    print "use: get_licence_data licence_file > data.csv"
    sys.exit(0)

f = open(sys.argv[1],'r')
# This loop assumes that the block of lines associated with a licensee
# always begins with "Licensee <name>", and always ends with
# "Commencement Date <date>".  It also assumes that the list of "Also Trading
# As" names is always terminated by the line that begins with "Categories".
# It also assumes that the items to be printed are always in the order shown
# in the example: Licensee, Also Trading As (if any), Categories, ..., Licence No,
# Commencement Date. With a bit more code, different orders could be handled.
# For example, it could collect the data in a dictionary, and then call
# a method to print the data in any format desired.
try:
    while True:
        line = f.next().strip()
        if line.startswith("Licensee"):
            licensee = line.split(' ',1)[1]
            licence_data = [licensee]
        if line.startswith("Also Trading As"):
            ata = line.split(' ',3)[3]
            licence_data.append(ata)
            line = f.next().strip()
            while not line.startswith("Categories"):
                licence_data.append(line)
                line = f.next().strip()
        if line.startswith("Licence No"):
            licence_no = line.split(' ',2)[2]
            licence_data.append(licence_no)
        if line.startswith("Commencement Date"):
            comm_date = line.split(' ',2)[2]
            licence_data.append(comm_date)
            print ','.join(licence_data)
except StopIteration:
    f.close()

```

Run with the given sample:
```

$ python get_licence_data.py licence_data.txt 
The Harley Gallery,0543037,05-Nov-2003
Andrew Jones,Clover Financial Services,0590185,29-Sep-2006
Satvision UK Limited,Sarvision Uk Ltd,Satvision Uk,0607685,31-Oct-2007
Warren Davies Ltd,Llwynhendy Dental Surgery,Warren Davies Dental Care,Warren Davies Dental Care (Dental Practice).,0616616,01-Dec-2008
$ 

```

---

### Post by dunryc on 2008-12-07
Thanks for that WW ive just given it a try but get errors 

> Traceback (most recent call last):
  File "get_licence_data.py", line 31, in <module>
    licence_no = line.split(' ',2)[2]
IndexError: list index out of range


any idea on what im doing wrong thanks dunryc

---

### Post by WW on 2008-12-07
Is there a line in your data file that begins with "Licence No", but does not look like "Licence No some_text_here"?  E.g. "Licence No1234", or just "Licence No" (with no number after "No")?  Either case will cause that error.

---

### Post by WW on 2008-12-07
I just reread your post; my code doesn't limit the output to credit brokerages.  I'll give that a shot.

---

### Post by WW on 2008-12-07
New version-this should only print the data for entries that have "Credit brokerage" in their list of Categories:

```


import sys

if len(sys.argv) < 2:
    print "use: getdata licence_data_file > data.csv"
    sys.exit(0)

f = open(sys.argv[1],'r')
# This loop assumes that the block of lines associated with a licensee
# always begins with "Licensee <name>", and always ends with
# "Commencement Date <date>".  It also assumes:
# o  the list of "Also Trading As" names is always terminated by the line that
#    begins with "Categories",
# o  the items to be printed are always in the order shown in the example:
#    Licensee, Also Trading As (if any), Categories, ..., Licence No, Commencement Date.
#    In particular, the list of Categories is assumed to end when a line beginning
#    with "Right To Canvass" is reached.
# With a bit more code, different orders could be handled.
try:
    while True:
        line = f.next().strip()
        if line.startswith("Licensee"):
            licensee = line.split(' ',1)[1]
            licence_data = [licensee]
            brokerage = False
        if line.startswith("Also Trading As"):
            ata = line.split(' ',3)[3]
            licence_data.append(ata)
            line = f.next().strip()
            while not line.startswith("Categories"):
                licence_data.append(line)
                line = f.next().strip()
        if line.startswith("Categories"):
            cat = line.split(' ',1)[1].strip()
            if cat == "Credit brokerage":
                brokerage = True
            line = f.next().strip()
            while not line.startswith("Right To Canvass"):
                if line == "Credit brokerage":
                    brokerage = True
                line = f.next().strip()
        if line.startswith("Licence No"):
            licence_no = line.split(' ',2)[2]
            licence_data.append(licence_no)
        if line.startswith("Commencement Date"):
            comm_date = line.split(' ',2)[2]
            licence_data.append(comm_date)
            if brokerage:
                print ','.join(licence_data)
            brokerage = False
except StopIteration:
    f.close()

```

---

### Post by ghostdog74 on 2008-12-07
awk
```

#!/bin/bash
awk 'BEGIN{RS="\n\n";FS="\n"}
/Categories Credit brokerage/{
 for(i=1;i<=NF;i++){
    if( $i ~ /Licensee/ || $i ~ /Also Trading As/ || $i ~ /Licence No/ || $i ~ /Commencement Date/){
        printf "%s,", $i
    }
 }
 print ""
}' file

```

---


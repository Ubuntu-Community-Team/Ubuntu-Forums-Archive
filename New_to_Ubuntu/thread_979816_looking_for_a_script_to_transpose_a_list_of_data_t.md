---
title: "looking for a script to transpose a list of data to CSV format"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by c7borg on 2008-11-12
Hi guys, could anyone point me in the right direction I have a list of addresses I want to sort into a tabular format below is a sample of the list

I'm looking into how to sort through a list, and print each element into a line under the right category  heading (using comma's as a separator) then using a blank as a prompt for the script to move onto the next bunch of data in the list (in this case contact details) putting that on a new line

Thanks in advance

bob smith
43 canarvon road
worcester
WD2 4 XY
Tel:0800 000 000
Email:get@me.co.uk

john doe
56 victoria street
little hampton
hamtonshire
Email:the@there.com

lilly allen
94 Dames close
Simsville
Essex
Phone:0909811811

I would like to sort it as follows(csv format):
name, address1, address2, address3, address4, email, phone
bob smith, 43 canarvon road, worcester, WD2 4 XY, , Email:get@me.co.uk, Tel:0800 000 000 
john doe, 56 victoria street, little hampton, hamtonshire, ,the@there.com, ,
lilly allen, 94 Dames close, Simsville, Essex,,, Phone:0909811811

---

### Post by jamesrl on 2008-11-12
Well you ask a semi-difficult task.
Say you wanted to just say add have a comma replace the new line that ends every line with text; and go to a new line every time there's a non-blank line.  You could do this fairly simply with sed (man sed) I believe.

What you want to do is more than that, however, as you want to recognize certain elements as "email addresses", "telephone numbers" and place them in the approrpiate column for a CSV format.  
You probably could do what you are asking with some combination of sed and gawk, but personally I'd just write a quick python script.

---

### Post by rrashkin on 2008-11-12
I like Python so I'm happy to suggest a Python implementation.
I assume that while telephone numbers can be preceeded by "Tel:" or "Phone:", email addresses are always preceeded by "Email:".  Also, even though you want 4 address fields, your list will always only have 3 (as in your sample).
```
#sort list into csv
infile = 'z:/python/smpl.txt'
outfile = 'z:/python/smpl.csv'
try: f = open(infile)
except: exit()
recs = []
rec = []
for l in f:
    if l.strip() != "": rec.append(l.rstrip('\n'))
    else: recs.append(rec); rec=[]
f.close()
f=open(outfile,'w')
for r in recs:
  if len(r)==4: r.append('')
  if len(r)==5:
       if r[-1][0:5]=="Email": r.append('')
       else: r.insert(4,'')
  r.insert(4,'')
  f.write(','.join(r)+'\n')
f.close()
raw_input('done')
```

---

### Post by jamesrl on 2008-11-12
So save your data file to "sample.dat", and save this code to a python file (say open gedit), call it say "data_to_csv.py".  Then from the terminal go the directory you put everything in, and run "python data_to_csv.py".  If all goes well you'll have a csv file.
```

#!/usr/bin/python2.5

readfile = open("sample.dat", "r")
# open file for reading
datafilelines = readfile.readlines()
# reads file

writefile = open("sample.csv", "w")
# opens file for writing 

temp_data_list = ["",]*7
# generates a list to store each persons info in
td_index = 0
# index for the list 

for line_with_return in datafilelines:
    line = line_with_return.replace('\n','') 
    # this removes the \n from each line ending
    if not line == '':
        if not (line.startswith("Tel:") or 
                line.startswith("Email:") or 
                line.startswith("Phone:") ):
            ## if the line doesn't begin with a special marker
            ## put it in the next available slot
            temp_data_list[td_index] = line
            td_index += 1
        if (line.startswith("Tel:") or line.startswith("Phone:")):
            ## if its a telephone number put in 6th slot (counting from 0)
            temp_data_list[6] = line
        if (line.startswith("Email:") or line.find("@") > 0):
            temp_data_list[5] = line
    if line == '':
        # convert the list to a string seperated by commas
        temp_data_str = ""
        for temp_data in temp_data_list:
            temp_data_str += temp_data + ","
        temp_data_str = temp_data_str[0:-1] + "\n"
        # get rid of last comma, and add a new line character
        writefile.write(temp_data_str)
        ## write it to a file

        ## reset temp_data to blank
        temp_data_list = ["",]*7 
        td_index = 0

if temp_data_list[0]:
## make sure last line gets written
    temp_data_str = ""
    for temp_data in temp_data_list:
        temp_data_str += temp_data + ","
    temp_data_str = temp_data_str[0:-1] + "\n"
    writefile.write(temp_data_str)
readfile.close()
writefile.close()

```

---


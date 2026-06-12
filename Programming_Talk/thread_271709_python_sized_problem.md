---
title: "python sized problem"
date: 2006-10-05
forum: Programming Talk
---

### Post by uk_sphinx on 2006-10-05
```

   1:import csv # This will help us reading csv formated files
   2:
   3:cars_file = open('2006_FE_Guide_14-Nov-2005_download.csv', 'rb')
   4:
   5:# The reader method will put each line
   6:# of the csv file into a list of columns.
   7:reader = csv.reader(cars_file)
   8:
   9:i = 0    # line counter
  10:print
  11:
  12:reader.next() # skip the header line
  13:for line in reader:
  14:
  15:    i = i + 1
  16:
  17:    print line[1],    # manufacturer
  18:    print line[2],    # model
  19:    print line[3],    # displacement in liters
  20:    print line[5],    # transmission type
  21:    print "average mpg is", line[9]
  22:
  23:    if i == 10:
  24:
  25:        i = 0
  26:        print
  27:        raw_input("Hit Enter to continue")
  28:        print
  29:
  30:print
  31:cars_file.close()
  32:
 
```

hello people. that short script is off a tutorial im ploughing through for python. its supposed to list collumns off a csv they told me to download.
thats the exact thing they told me to code as i copied that straight from there tutorial.
below is what its displaying....
im pretty sure its not supposed to display like this althought i dont know coz they didnt show a pic of what the results are supposed to be like...........

 ***sphinx*** python cars
W O   W O   W O   W O   W O   W O   W O   W O   W O   W O
hit enter
W O   W O   W O   W O   W O   W O   W O   W O   W O   W O
hit enter
W O   W O   W O   W O   W O   W O   W O   W O   W O   W O
hit enter
W O   W O   W O   W O   W O   W O   W O   W O   W O   W O
hit enter
W O   W O   I N I I N I I N I I N I I N I I N I I N I I N I
hit enter
I N I I N I I N I I N I I N I I N I I N I I N I I N I I N I
hit enter
I N I I N I I N I I N I I N I I N I I N I I N I I N I I N I
hit enter
I N I I N I I N I I N I I N I I N I I N I I N I I N I I N I
hit enter
I N I I N I I N I I N I I N I U B C U B C U B C U B C U B C
hit enter
U B C U B C U B C U B C U B C U B C U B C U B C U B C U B C
hit enter
U B C U B C U B C U B C U B C U B C U B C U B C U B C U B C
hit enter
U B C U B C U B C U B C U B C U B C U B C U B C U B C U B C
hit enter
U B C U B C U B C U B C U B C U B C U B C U B C U B C U B C
hit enter
U B C U B C U B C U B C U B C U B C U B C U B C U B C U B C
hit enter

anyone got any idea what the hells up???

also its, supposed to ask you to hit enter after every 10 lines of info.
looks like 10 attempts at words???

---

### Post by maubp on 2006-10-05
The code you showed us should print the data from ten lines, then wait for the user to press enter, then print the next ten lines' data, etc.

The fact that your example output says "hit enter" rather than "Hit Enter to continue" tells me that the code you are running and the code you showed us are different.

Maybe you made an error copying the code...

Also, what does the input file look like if you open it in a text editor?

---

### Post by etank on 2006-10-05
I just tried the code and it seems to work fine for me. I just created a test csv file and ran it against that. Here is the code, data file and the output.

Data```

Manufacturer,Model,DIL,Transmission,,,,,,MPG
11,12,13,14,15,16,17,18,19,10
21,22,23,24,25,26,27,28,29,20
31,32,33,34,35,36,37,38,39,30
41,42,43,44,45,46,47,48,49,40
51,52,53,54,55,56,57,58,59,50
61,62,63,64,65,66,67,68,69,60
71,72,73,74,75,76,77,78,79,70
81,82,83,84,85,86,87,88,89,80
91,92,93,94,95,96,97,98,99,90
101,102,103,104,105,106,107,108,109,100
111,112,113,114,115,116,117,118,119,110
```

Code```

import csv

data_file = open('data.csv', 'rb')
reader = csv.reader(data_file)

i = 0
print

reader.next()
for line in reader:
    i = i + 1
    
    print line[1],
    print line[2],
    print line[3],
    print line[4],
    print line[5],
    print 'avg mpg is', line[9]
    
    if i == 10:
        i = 0
        print 
        raw_input('Hit enter to continue')
        print
        
print
data_file.close()
```

Output```

D:\>python data_file.py

12 13 14 15 16 avg mpg is 10
22 23 24 25 26 avg mpg is 20
32 33 34 35 36 avg mpg is 30
42 43 44 45 46 avg mpg is 40
52 53 54 55 56 avg mpg is 50
62 63 64 65 66 avg mpg is 60
72 73 74 75 76 avg mpg is 70
82 83 84 85 86 avg mpg is 80
92 93 94 95 96 avg mpg is 90
102 103 104 105 106 avg mpg is 100

Hit enter to continue

112 113 114 115 116 avg mpg is 110
```

---

### Post by uk_sphinx on 2006-10-05
yeah i did change the hit enter to continue.
i didnt think it would matter as the input was only used as a pause.its not a command is it?
the file i downloaded wasnt displayed in a text file it was displayed in one of the office progs.
when i clicked on it it had a few options and a code like box that you had to scroll manually.
said unicode above the writing and you could change it to other formats.

guess i must have messed it up by accident or something???

---


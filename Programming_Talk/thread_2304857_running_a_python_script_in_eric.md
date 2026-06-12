---
title: "running a python script in eric"
date: 2015-11-30
forum: Programming Talk
---

### Post by tim141 on 2015-11-30
Hey All

total newbie question here...;)

I have been trying to run a few python scripts - just simple ones to import a csv and then create a graph.

such as:

import csv
data_file = "/media/sf_shared/income_dist.csv"
with open(data_file, 'r') as csvfile:
    reader  = csv.DictReader(csvfile)
    data = list(reader)

I have been running it in the terminal window through the python interpreter - but found it hard to not make a mistake sometimes in the longer scripts - and had to keep going back to the start of the script (if there is a way to undo a missed indent etc please tell me! )

thought it would be easier to do in an IDE such as eric but when I copy the script like that into eric, and press run it comes up with an error - terminated with exit status 0. 

Obviously I have no idea what im doing. If anyone could steer me in roughly the right direction, would be much appreciated.

cheers
Tim

---

### Post by tim141 on 2015-11-30
ok so im learning that you can do this, just by running this and it appears in the shell window. much easier than just editing in the shell itself

import csv
data_file = "/media/sf_shared/income_dist.csv"
with open(data_file, 'r') as csvfile:
    reader = csv.DictReader(csvfile)
    data = list(reader)
    
    print len(data)
    
    print reader.fieldnames

---

### Post by oldfred on 2015-11-30
I have not used eric recently, but do use geany. I had to change a few settings to convert tabs to spaces (3 different places) and then it works pretty well. I just copy some code from Internet, save as .py and run it. Terminal shows errors or if error is 0 then it ran correctly, but not necessarily with the results expected.

---


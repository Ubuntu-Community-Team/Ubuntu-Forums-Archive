---
title: "Python nested for loop problem"
date: 2011-04-07
forum: Programming Talk
---

### Post by melissawong on 2011-04-07
Hi, I always have a problem with a for loop with if conditions in a for  loop. Sometimes it work and sometimes it don't What I'm trying to do is something like this: I have a list and a  file with lines. For each item in my list, I wanna check the whole file  for lines with column1 matching the item and do something.

List1 = ['mango','orange','apple']
file1:
mango\tMon\t12
orange\tTues\t5
apple\tSat\t6
orange\tWed\t1

for item in list1:
    for line in file1:
        fruit = line.split()[0]
        Date = line.split()[1]
        Number = line.split()[2]
        if fruit == item:
            [Do something]

The problem is only the first item in the list will be screened. I can't  figure out why the loop was not repeated for the rest in the list. 

Appreciate any help! 
Thanks, 
Melissa

---

### Post by simeon87 on 2011-04-07
If I understand correctly your code looks like this:
```

List1 = ['mango','orange','apple']
for item in list1:
    for line in file1:
        fruit = line.split()[0]
        Date = line.split()[1]
        Number = line.split()[2]
        if fruit == item:
            [Do something]
```

and your file looks like (with tabs):

```
mango\tMon\t12
orange\tTues\t5
apple\tSat\t6
orange\tWed\t1
```

Does [Do something] contain a break statement? In that case the for loop will be terminated and you won't see much happening for the remaining items of the list.

Also note that you have List1 and list1 in your code, you should make sure they both start with the same letters.

Other than that I currently don't see a reason why it wouldn't continue with the rest of the list / file.

---

### Post by DaithiF on 2011-04-07
Hi, I think the problem is that having read through all the lines in the file for the first item, theres nothing left to read from the file for the second and subsequent items.

instead it would be better to read the file once, populating a list of lines from that.
alternatively you could do file1.seek(0) at the start of each outer loop, but better to just read the file once. 

so something like:

```
file_lines = file1.readlines()
for item in list1:
    for line in files_lines:
        fruit,date,number = line.split()
        if fruit == item:
            # do stuff

```

---

### Post by melissawong on 2011-04-07
> **DaithiF said:**
> Hi, I think the problem is that having read through all the lines in the file for the first item, theres nothing left to read from the file for the second and subsequent items.

instead it would be better to read the file once, populating a list of lines from that.
alternatively you could do file1.seek(0) at the start of each outer loop, but better to just read the file once. 

so something like:

```
file_lines = file1.readlines()
for item in list1:
    for line in files_lines:
        fruit,date,number = line.split()
        if fruit == item:
            # do stuff

```

It worked! Thanks a lot :D

---

### Post by melissawong on 2011-04-08
I have one more problem. I wrote a function but I can't use .write() to output values if I use that function. This function is supposed to allow me to check if the value I enter is wrong. Here's part of the code:

```

out = open('output.txt','w')
def errormsg(value1, dictionary):
    if value1 in dictionary.keys():
        value2 = value1
    else:
        print "Wrong value!"
        value2 = raw_input ("Enter value again: ")
    return value2

for x in listx:
    mdict2 = mdict[x] #nested dictionary
    pdict2 = pdict[x] #nested dictionary
    list1 = []
    if len(mdict2)==1 and len(pdict2)== 1:
        list1 = mdict2.keys() + mdict2.values() + pdict2.keys() + pdict2.values()
        y = "\t".join(list1)
        out.write ("%s\t%s"%(x, y))
        #print '{0}\t{1}\t'.format(x, y)
    else:
        input1 = raw_input ("Enter Mvalue: ")
        new_input1 = errormsg(input1, mdict2)
        input2 = raw_input ("Enter Pvalue: ")
        new_input2 = errormsg(input2, pdict2)
        out.write("%s\t%s\t%s\t%s\t%s\n"% (x, new_input1, mdict2[new_input1],new_input2, pdict2[new_input2]))
        #print '{0}\t{1}\t{2}\t{3}\t'.format(x, new_input1, mdict2[new_input1], new_input2, pdict2[new_input2])

```If I use print statement (shown as comments above), the correct values are printed on the screen. However, "print >> out" doesn't work. Any idea how I can fix this?

Thanks
Melissa

---

### Post by DaithiF on 2011-04-08
Hi, I'm not sure I understand.  Are you saying that the lines like:
```
out.write('stuff goes here')

```do not actually write to the file?

that seems odd, but bear in mind that output will be buffered before being physically written to disk.  Either calling out.close() (when finished with the file), or out.flush() (if you still have more to write) will force whatever you have written to be physically written to disk from the buffer.

---

### Post by melissawong on 2011-04-08
yup. It's not writing text to the output file.

Anyway, I change the function to the following and it works.
```

def select(dictionary) :
    while 1:
        value1 = raw_input ("Enter value: ")
        if value1 in dictionary.keys():
            return value1
            break
        else:
            pass

```

---


---
title: "How do I compare 2 csv files and pull out the same in both"
date: 2019-07-08
forum: Programming Talk
---

### Post by lance bermudez on 2019-07-08
I ran the below script on some usb harddrives that I have .

I want to see if the file1.csv has repeats of the sha256 file hash in it. I also want to compare file1csv and file2.csv and pull out from the both of them the file hashes that are in both of them. 

I used this python 3 program to make the csv files
```

#!/usr/bin/env python3
import os
import hashlib
import sys

start_path = input('Start path for file sha256sum\n')
files_dir = []
for path,dirs,files in os.walk(start_path):
    for filename in files:
        files_dir.append(os.path.join(path,filename))

# BUF_SIZE is totally arbitrary, change for your app!
BUF_SIZE = 65536  # lets read stuff in 64kb chunks!                

def pwalk():
    for x in files_dir:
        try:
            hasher = hashlib.sha256()
            with open(x, 'rb') as openfile:
                content = openfile.read(BUF_SIZE)
                hasher.update(content)
                with open('data.csv', 'a') as f:
                    print(hasher.hexdigest(), x, sep=",")#, file=f)
                    f.write(hasher.hexdigest()+','+str(x)+'\n')
        except PermissionError as permission_error:
            print(permission_error)
            with open('errors.txt', 'a') as e:
                e.write(str(permission_error)+'\n')
            pass
        except FileNotFoundError as filenotfounderror:
            pass
            print(filenotfounderror)
            with open('errors.txt', 'a') as e:
                e.write(str(filenotfounderror)+'\n')
        except OSError as oserror:
            pass
            with open('errors.txt', 'a') as e:
                e.write(str(oserror)+'\n')
            print(oserror)
    #input('Enter to close...')

pwalk()

```

---

### Post by SeijiSensei on 2019-07-08
You can use the command-line program diff.  

```
diff file1.csv file2.csv | diff - file1.csv
```

The first diff generates a file with the differences between file1.csv and file2.csv.  The second diff takes that output (represented as "-") and compares it to file1.csv. The result will be lines in file1.csv that match those in file2.csv.

I looked at the [man page]("https://linux.die.net/man/1/diff") to see if diff had a switch that would reverse its operation, returning matching rather than unmatching lines, but didn't see that option.

---

### Post by dmnur on 2019-07-09
[SIZE=3]**If you need to compare whole lines**[/SIZE]

Use **comm**. By default **comm** outputs three columns: (1) lines unique to FILE1, (2) lines unique to FILE2, (3) lines common to both files.
To suppress specific columns, use one of the options: **-1**, **-2**, **-3**.

In your case you need lines common to both files, so you need to suppress columns 1 and 2:
```
comm -12 file1.csv file2.csv
```

But **comm** expects that lines in your files are sorted, so make sure they are. A quick way to do this if you use Bash:
```
comm -12 <(sort file1.csv) <(sort file2.csv)
```

For example:
```

$ cat file1.csv
hash1,f1.txt
hash2,f2.txt
hash3,f3.txt

$ cat file2.csv
hash5,f5.txt
hash4,f4.txt
hash3,f3.txt

$ comm -12 <(sort file1.csv) <(sort file2.csv)
hash3,f3.txt

```

[HR][/HR]

[SIZE=3]**If you need to compare only hashes**[/SIZE]

**join** will do in your case, I guess. It joins lines of two files on their common fields.
The **-t** option specifies the character to use as a field separator. The **-j** option specifies which field to join on.
Again, lines of the files need to be sorted.

For your case:
```
join -t ',' -j 1 <(sort file1.csv) <(sort file2.csv)
```

As I can see, your CSV files have two fields: (1) hash, (2) filename.
So the above command will give you three fields in the end: (1) common hash, (2) filename from FILE1, (2) filename from FILE2.

For example:
```

$ cat file1.csv
hash1,f1.txt
hash2,f2.txt
hash3,f3.txt

$ cat file2.csv
hash3,f4.txt
hash4,f5.txt
hash5,f6.txt
hash1,f7.txt
hash3,f8.txt

$ join -t ',' -j 1 <(sort file1.csv) <(sort file2.csv)
hash1,f1.txt,f7.txt
hash3,f3.txt,f4.txt
hash3,f3.txt,f8.txt

```

If you want to get only hashes in your output and get rid of duplicates, use the following:
```

$ join -t ',' -j 1 -o 0 <(sort file1.csv) <(sort file2.csv) | uniq
hash1
hash3

```

[hr][/hr]

Read **man** and **info** pages of the above commands for more details.

---

### Post by lance bermudez on 2019-07-13
my windows work computer does not have the linux subsystem IT admin will not install it. Using the examples you have given me I came up with this.

I open both files in notepad/gedit and put this as the first line
hash,file path

I can use this python 3 script to give the same in both files but it does not have the file path
I could not figure out how to do that.
```

import pandas as pd
import os

# current user home directory
print(os.getcwd())

# list files in current directory
for name in sorted(os.listdir('.')):
      print(name, end='\n')

# get files to compare to find the same in them
oneCSV = input('1 file to compare to find the same\n')
twoCSV = input('2 file to compare to find the same\n')

# pandas read file.csv
p1 = pd.read_csv(oneCSV, delimiter=',')
p2 = pd.read_csv(twoCSV, delimiter=',')

# pandas get only hash column in 1 file
print('Getting output from file 1')
with open('fileone.txt', 'w') as outfile:
    for index, row in p1.iterrows():
        fileone = row['hash']
        print(row['hash'])
        print(fileone, file=outfile)

# pandas get only hash column in 2 file
print('\nGetting output from file 2')
with open('filetwo.txt', 'w') as outFile:
    for index, row in p2.iterrows():
        filetwo = row['hash']
        print(row['hash'])
        print(filetwo, file=outFile)

# files made by pandas read for sorting out the same in both
with open('fileone.txt', 'r') as t1, open('filetwo.txt', 'r') as t2:
    fileone = t1.readlines()
    filetwo = t2.readlines()

# work if line == match
print('\nIn Both files')
with open('same.csv', 'w') as OutFile:
    for line in filetwo:
        if line in fileone:
            print(line.rstrip())
# put the same files hashes in file NO file path with it
            OutFile.write(line)
#cleanup tmp hash 1 file & 2 file
    os.remove('fileone.txt')
    os.remove('filetwo.txt')

```

---

### Post by The Cog on 2019-07-13
Try this untested bit of code. 
It reads the files into a dict mapping hashes to lists of paths. Then prints any duplicate hashes found within each file.
Then it compares the two dicts looking for duplicate hashes between files and prints all the paths of any duplicates.
```
#!/usr/bin/python3

import os

# Read a file and make a dict of hash to list of paths
def readFile(fname):
    hashdict = {}
    for line in open(fname).read().splitlines():
        k, v = line.split(",", 1)
        vlist = hashdict.get(k, [])
        vlist.append(k)
    return hashdict


# Print all the hashes with multiple paths 
def printFileDups(hashdict):
    for k, vlist in hashdict.items():
        if len(vlist) > 1:
            print("Duplicate: " + k)
            for v in vlist:
                print("    " + v)

    
# current user home directory
print(os.getcwd())

# list files in current directory
for name in sorted(os.listdir('.')):
      print(name, end='\n')

# get files to compare to find the same in them
oneCSV = input('1 file to compare to find the same\n')
twoCSV = input('2 file to compare to find the same\n')

print("\nREADING " + oneCSV)
hd1 = readFile(oneCSV)
printFileDups(hd1)
print("\nREADING " + oneCSV)
hd2 = readFile(twoCSV)
printFileDups(hd2)
print("\nCOMPARING FILES...")
for k in hd1:
    if k in hd2:
        print("Duplicate:  + k")
        print("    "+oneCSV)
        for v in hd1[k]:
            print("        " + v)
        print("    "+twoCSV)
        for v in hd2[k]:
            print("        " + v)

```

---

### Post by lance bermudez on 2019-07-15
I do not know for sure what is going on but I think that the hashdict is blank that the data being read from the file is not going in to the dictionary.

---

### Post by The Cog on 2019-07-15
OK, I'll knock up a couple of test files tonight and give it a try.

---

### Post by lance bermudez on 2019-07-15
The Cog  Woof thank you so much for giving me the dictionary example it was a great starting point I know that you could make the code better then I did but following your example I came up with this.

```

import os
import csv # to read files into dict

# dictionaries from files
hashdict1 ={}
hashdict2 ={}

def MakeHasdict(oneCSV, twoCSV):#oneCSV):
    with open(oneCSV, 'r') as t1:
        reader = csv.reader(t1)
        for line in reader:
            k, v = line
            hashdict1.update([line])

#def MakeHasdict2():#twoCSV):
    with open(twoCSV, 'r') as t2:
        reader = csv.reader(t2)
        for row in reader:
            k, v = row
            hashdict2.update([row])

def CompareFiles(oneCSV, twoCSV):
    print('\nfile one is ', oneCSV)
    print('file two is ', twoCSV)
    print('\nSame in both')
    with open('Same.csv', 'w') as Outfile:
        Outfile.write('file one is ')
        Outfile.write(oneCSV)
        Outfile.write('\n')
        Outfile.write('file two is ')
        Outfile.write(twoCSV)
        Outfile.write('\n')
        Outfile.write('\nSame in both\n')
        writer = csv.writer(Outfile)
        for key, value in hashdict1.items():
            if key in hashdict2:
                print(key, value)
                writer.writerow([key, value])

    
        print('\nNot in file1')
        print('hash file path')
        Outfile.write('\nIN File1 Only\n')
        for key, value in hashdict2.items():
            if key not in hashdict1:
                print(key, value)
                writer.writerow([key, value])

        print('\nNot in file2')
        print('hash file path')
        Outfile.write('\nIN File2 Only\n')
        for key, value in hashdict1.items():
            if key not in hashdict2:
                print(key, value)
                writer.writerow([key, value])

# current user home directory
print(os.getcwd())

# list files in current directory
for name in sorted(os.listdir('.')):
      print(name, end='\n')
  
# get files to compare to find the same in them
oneCSV = input('1 file to compare to find the same\n')
twoCSV = input('2 file to compare to find the same\n')

# making dictionaries from csv files
MakeHasdict(oneCSV, twoCSV)

#Getting same and diff
CompareFiles(oneCSV, twoCSV)

```

---

### Post by The Cog on 2019-07-15
Yes, I made a pig's ear of reading the files. Sorry. Here's a tested version:
```
#!/usr/bin/python3

import os

# Read a file and make a dict of hash to list of paths
def readFile(fname):
    hashdict = {}
    for line in open(fname).read().splitlines():
        k, v = line.split(",", 1)
        vlist = hashdict.get(k, [])
        vlist.append(v)
        hashdict[k] = vlist
    return hashdict


# Print all the hashes with multiple paths 
def printFileDups(hashdict):
    for k, vlist in hashdict.items():
        if len(vlist) > 1:
            print("Duplicate: " + k)
            for v in vlist:
                print("    " + v)

    
# current user home directory
print(os.getcwd())

# list files in current directory
for name in sorted(os.listdir('.')):
      print(name, end='\n')

# get files to compare to find the same in them
oneCSV = input('1 file to compare to find the same\n')
twoCSV = input('2 file to compare to find the same\n')

print("\nREADING " + oneCSV)
hd1 = readFile(oneCSV)
print("hd1 =", hd1)
printFileDups(hd1)
print("\nREADING " + twoCSV)
hd2 = readFile(twoCSV)
print("hd2 =", hd2)
printFileDups(hd2)
print("\nCOMPARING FILES...")
for k in hd1:
    if k in hd2:
        print("Duplicate: " + k)
        print("    "+oneCSV)
        for v in hd1[k]:
            print("        " + v)
        print("    "+twoCSV)
        for v in hd2[k]:
            print("        " + v)
```

---


---
title: "python script help"
date: 2011-07-08
forum: Programming Talk
---

### Post by flyingsliverfin on 2011-07-08
I was trying to make a script that would replace the spaces in text files (when they were created to look like columns) with tabs, so that excel on macs could convert that into a spreadsheet. I know there's a way to do it, but i couldn't be bothered and it could save some time.
So an example input would be:
```
 1927  1  1 1927.002686      8.30    21.10     0.00    14.70     0.00     0.00
 1927  1  2 1927.005493      7.20    18.90     0.00    13.05     0.00     0.00
 1927  1  3 1927.008179      4.40    17.80     0.00    11.10     0.00     0.00
```
except the columns are seperated by spaces...

heres the script i wrote to convert the extra spaces into single tabs:

```
for z in infile: #gives a string (also the row)
	rowList = list(z)[:-1] #turn into list of chars
	counter = 0
	for x in range(0,len(rowList)):
		if x + counter == len(rowList)-1:
			break
		if rowList[x].isalnum() == False and rowList[x+1].isalnum() == False:
			rowList.pop(x+1)
			counter += 1
	for x in range(0,len(rowList)):
		if rowList[x] == ' ':
			rowList[x] = '\t'
	out = ''.join(rowList)
	outfile.write(out+'\n')
outfile.close()
```

however this doesnt work well...
the second attempt i did was similar:
```
for z in infile:
	rowList = list(z)[:-1]
	counter = 0
	for x in range(0,len(rowList)):
		x = x+counter
		if x == len(rowList):
			break
		if rowList[x].isspace() == True and rowList[x+1].isspace() == True:
			while rowList[x+1].isspace() == True:
				rowList.pop(x+1)
				counter +=1
	for x in range(0,len(rowList)):
		if rowList[x] == ' ':
			rowList[x] = '\t'
	out = ''.join(rowList)
	outfile.write(out+'\n')
```
 and works much better, but it sometimes a single space... and i haven't been able to isolate why.

---

### Post by Bachstelze on 2011-07-08
```
firas@aoba ~ % cat test.txt 
 1927  1  1 1927.002686      8.30    21.10     0.00    14.70     0.00     0.00
 1927  1  2 1927.005493      7.20    18.90     0.00    13.05     0.00     0.00
 1927  1  3 1927.008179      4.40    17.80     0.00    11.10     0.00     0.00
firas@aoba ~ % echo "%s/\ \ */\t/g\nw" | ed test.txt
237
162
firas@aoba ~ % cat test.txt                         
	1927	1	1	1927.002686	8.30	21.10	0.00	14.70	0.00	0.00
	1927	1	2	1927.005493	7.20	18.90	0.00	13.05	0.00	0.00
	1927	1	3	1927.008179	4.40	17.80	0.00	11.10	0.00	0.00

```

:)

---

### Post by flyingsliverfin on 2011-07-08
wut?

---

### Post by Bachstelze on 2011-07-08
> **flyingsliverfin said:**
> wut?

Isn't that what you want to do?

---

### Post by flyingsliverfin on 2011-07-08
yea... im just confused by what its doing...

---

### Post by Bachstelze on 2011-07-08
It opens the file in ed and run the following commands:

%s/\ \ */\t/g and w

% means run the command on every line of the input file
s// means substitute
\ \ * means one or more space
\t means tab
so s/\ \ */\t/ means substitute \ \ * with \t
g means substitute all occurrences of \ \ * on a line

\n means new line, to separate ed commands

w means write (i.e. apply the changes to the file and quit)

If you want you can do the same thing interactively:

```
firas@aoba ~ % cat test.txt 
 1927  1  1 1927.002686      8.30    21.10     0.00    14.70     0.00     0.00
 1927  1  2 1927.005493      7.20    18.90     0.00    13.05     0.00     0.00
 1927  1  3 1927.008179      4.40    17.80     0.00    11.10     0.00     0.00
firas@aoba ~ % ed test.txt 
237
%s/\ \ */	/g
w
162
q
firas@aoba ~ % cat test.txt 
	1927	1	1	1927.002686	8.30	21.10	0.00	14.70	0.00	0.00
	1927	1	2	1927.005493	7.20	18.90	0.00	13.05	0.00	0.00
	1927	1	3	1927.008179	4.40	17.80	0.00	11.10	0.00	0.00

```

But as you can see, ed's interface is very dry, so it's not a good editor to use interactively.

---

### Post by pafoo on 2011-07-08
Nice ed command. I didnt know about the \nw after you said global. Then piping to ed, brilliant. That means I can edit text files via ssh -q !!!!! YAY!!!! 

As a side note, you can test that command without editing the file by using "sed"

sed '[FONT=&quot]%s/ \ \ */\t/g' test.txt

It will output the results to STOUT w/o opening/editing the file
[/FONT]

---


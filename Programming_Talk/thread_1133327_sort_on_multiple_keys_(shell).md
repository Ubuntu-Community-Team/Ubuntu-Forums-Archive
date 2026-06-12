---
title: "sort on multiple keys (shell)"
date: 2009-04-22
forum: Programming Talk
---

### Post by monkeyking on 2009-04-22
Hey I've got an interesting problem.
I need to sort lines of a file given 2 keys,
this could be a small snippet of a file.

[PHP]
1   chr9      1  6
2   chr2      2  4
3   chr2      3  3
4   chr7      4  6
5   chr8      5  6
6   chr9      6  3
7   chr6      7  9
8   chr6      8  9
9  chr10      9  4
10  chr4     10  6
11  chr2     11  6
12  chr8     12 10
13 chr10     13  7
14 chr10     14  7
15  chr7     15  7
[/PHP]

I need to sort by 2nd column and 4 column.
Such that the second column is ascending, and the 4th column is ascending within each grouping of column2.

This could be done with perl or whatever programming language,
but I think it is possible to use std unix 'sort'.

I've tried 'sort -k1 -k3' but I can't nail it.

thanks in advance

edit: this would be the output
[PHP]
      V1 V2 V3
16  chr1 16  1
9  chr10  9  4
13 chr10 13  7
14 chr10 14  7
3   chr2  3  3
2   chr2  2  4
11  chr2 11  6
19  chr4 19  3
10  chr4 10  6
17  chr5 17  7
7   chr6  7  9
8   chr6  8  9
18  chr7 18  3
4   chr7  4  6
15  chr7 15  7
5   chr8  5  6
12  chr8 12 10
6   chr9  6  3
1   chr9  1  6
20  chr9 20  7

[/PHP]

---

### Post by ghostdog74 on 2009-04-22
using your sample input, show your output.

---

### Post by monkeyking on 2009-04-22
Sure!

sorry should have though about that.

[PHP]
      V1 V2 V3
16  chr1 16  1
9  chr10  9  4
13 chr10 13  7
14 chr10 14  7
3   chr2  3  3
2   chr2  2  4
11  chr2 11  6
19  chr4 19  3
10  chr4 10  6
17  chr5 17  7
7   chr6  7  9
8   chr6  8  9
18  chr7 18  3
4   chr7  4  6
15  chr7 15  7
5   chr8  5  6
12  chr8 12 10
6   chr9  6  3
1   chr9  1  6
20  chr9 20  7
[/PHP]

---

### Post by kaibob on 2009-04-23
I am not knowledgeable about the sort command but had a look at the man page and came up with the following. I tried it out, and it sorted the data as shown in your output. 

```
sort -b -k 2.4,2.5 -k 4n file
```

For a general numeric sort, you can add an -n or -g option:

```
sort -n -b -k 2.4,2.5 -k 4 file
```

BTW, your output had more lines than the input file. Did I miss something?

---

### Post by monkeyking on 2009-04-23
Thanks kaibob!

Indeed your command seems to do the trick on this small example.

But I need some clarification on this magic command,
the man page is not really clear for me. 
[PHP]-k2.4,2.5[/PHP]
This tells to use the 4th and 5th char in column2 to sort, right?
so
```

chr111
chr112

```
Would be assumed to be the same for this sorting command?

while the
[PHP]-k 4[/PHP]
tells to use the entire 4th column, rigth?

I dont see why I shouldn't be able to use

[PHP]sort -k 2 -k 4 file.txt[/PHP]
If I didn't care about the numeric order of the second column,
but just wanted it grouped by same values.

Thanks

---

### Post by kaibob on 2009-04-24
> **monkeyking said:**
> ...I dont see why I shouldn't be able to use

[PHP]sort -k 2 -k 4 file.txt[/PHP]
If I didn't care about the numeric order of the second column,
but just wanted it grouped by same values.

Thanks
As I mentioned in my earlier post, I'm a novice with the sort command. But, I'll answer what I can and hopefully a forum member with more knowledge will correct what I get wrong. 

The numbers 2.4 and 2.5 do refer to characters 4 and 5 of column 2. Apparently, you can also specify a range of characters (e.g. -k 2.4,2.9). 

The option "-k 2.4,2.5" would ignore the sixth character in column 2 and thus chr111 and chr112 would be the same for sorting purposes. I ran a test and confirmed that this is the case. 

The option "-k 4" does use the entire fourth column. Both of the following commands work for me:

```
sort -k 4 file

sort -n -k 4 file
```

I don't entirely understand the portion of your post quoted above. Your command does sort on column 2. Even with the -b option, the command does not sort on column 4. I don't know why. 

As noted in my earlier post, the following command correctly sorts column 2 and subsorts column 4 in numerical order. You do need to change 2.5 to reflect the maximum number of digits in the second column:

```
sort -b -n -k 2.4,2.5 -k 4 file
```

Anyways, that's the extent of my knowledge, which isn't much. As noted, hopefully a more knowledgeable forum member will explain more.

---

### Post by monkeyking on 2009-04-25
Hi thanks for your reply,
I endede up writing my own cpp program for doing this.


But for anyone reading this,
I am quite interested in a solution.

---

### Post by Arndt on 2009-04-25
> **monkeyking said:**
> Hi thanks for your reply,
I endede up writing my own cpp program for doing this.


But for anyone reading this,
I am quite interested in a solution.

This seems to work (only you seem to have more lines in your expected output than in the input).

```
$ sort -k 2b,2b -k 4n,4 file
```

I haven't used 'sort' much except for using the whole line as a key, so this took a while to get working. Spaces are very important to 'sort'.

---

### Post by kaibob on 2009-04-25
> **Arndt said:**
> This seems to work (only you seem to have more lines in your expected output than in the input).

```
$ sort -k 2b,2b -k 4n,4 file
```

I haven't used 'sort' much except for using the whole line as a key, so this took a while to get working. Spaces are very important to 'sort'.

I tried the above command line and it sorted column 2 but not column 4. Locale can affect the sort order; perhaps that's why things that work for me do not work for the OP.

The following gets rid of extra spaces and does seem to work:

```
cat file | tr -s ' ' | sort -k2,2 -k4,4
```

---

### Post by Arndt on 2009-04-25
> **kaibob said:**
> I tried the above command line and it sorted column 2 but not column 4. Locale can affect the sort order; perhaps that's why things that work for me do not work for the OP.

As an aside, spaces do make a difference with a dictionary sort, but I piped the whole thing through the tr -s command to get rid of the extra spaces and that didn't make a difference.

Locale can affect the sort order, but it should only affect non-ASCII characters, I think. Here is what I have:

```
$ cat sort.in
1   chr9      1  6
2   chr2      2  4
3   chr2      3  3
4   chr7      4  6
5   chr8      5  6
6   chr9      6  3
7   chr6      7  9
8   chr6      8  9
9  chr10      9  4
10  chr4     10  6
11  chr2     11  6
12  chr8     12 10
13 chr10     13  7
14 chr10     14  7
15  chr7     15  7
$ LC_ALL=C sort -k 2b,2b -k 4n,4 sort.in
9  chr10      9  4
13 chr10     13  7
14 chr10     14  7
3   chr2      3  3
2   chr2      2  4
11  chr2     11  6
10  chr4     10  6
7   chr6      7  9
8   chr6      8  9
4   chr7      4  6
15  chr7     15  7
5   chr8      5  6
12  chr8     12 10
6   chr9      6  3
1   chr9      1  6

```

What do you get?

---

### Post by kaibob on 2009-04-25
> **Arndt said:**
> ...What do you get?
I created the file, sort.in, and then ran the command from your post. Our results are different. For example, look at column 4 of lines 1, 2, and 3 of the sorted data. The order is 7 7 4 rather than 4 7 7. 

```
$ cat sort.in
1   chr9      1  6
2   chr2      2  4
3   chr2      3  3
4   chr7      4  6
5   chr8      5  6
6   chr9      6  3
7   chr6      7  9
8   chr6      8  9
9  chr10      9  4
10  chr4     10  6
11  chr2     11  6
12  chr8     12 10
13 chr10     13  7
14 chr10     14  7
15  chr7     15  7

$ LC_ALL=C ; sort -k 2b,2b -k 4n,4 sort.in
13 chr10     13  7
14 chr10     14  7
9  chr10      9  4
11  chr2     11  6
3   chr2      3  3
2   chr2      2  4
10  chr4     10  6
7   chr6      7  9
8   chr6      8  9
15  chr7     15  7
4   chr7      4  6
12  chr8     12 10
5   chr8      5  6
6   chr9      6  3
1   chr9      1  6
```

---

### Post by kaibob on 2009-04-25
The following is the output with the same file and command but piped through tr:

```
$ LC_ALL=C ; cat sort.in | tr -s ' ' |  sort -k 2b,2b -k 4n,4
9 chr10 9 4
13 chr10 13 7
14 chr10 14 7
3 chr2 3 3
2 chr2 2 4
11 chr2 11 6
10 chr4 10 6
7 chr6 7 9
8 chr6 8 9
4 chr7 4 6
15 chr7 15 7
5 chr8 5 6
12 chr8 12 10
6 chr9 6 3
1 chr9 1 6
```

---

### Post by Arndt on 2009-04-26
> **kaibob said:**
> The following is the output with the same file and command but piped through tr:

```
$ LC_ALL=C ; cat sort.in | tr -s ' ' |  sort -k 2b,2b -k 4n,4
9 chr10 9 4
13 chr10 13 7
14 chr10 14 7
3 chr2 3 3
2 chr2 2 4
11 chr2 11 6
10 chr4 10 6
7 chr6 7 9
8 chr6 8 9
4 chr7 4 6
15 chr7 15 7
5 chr8 5 6
12 chr8 12 10
6 chr9 6 3
1 chr9 1 6
```

But the ';' shouldn't be there. Look:

```
$ TEST=hej perl -e 'printf "x %s x\n", $ENV{"TEST"}'
x hej x
$ TEST=hej ; perl -e 'printf "x %s x\n", $ENV{"TEST"}'
x  x
```

If you use ';', you have to export the variable too, or the called programs won't see it.

---

### Post by kaibob on 2009-04-26
> **Arndt said:**
> But the ';' shouldn't be there....

Sorry! I know little about setting environmental variables on the command line, so I first ran the commands with and then without the semi-colon to see if it would made a difference. It didn't.

To make sure, I just recreated sort.in and reran all commands without the semi-colon.

```
$ cat sort.in
1   chr9      1  6
2   chr2      2  4
3   chr2      3  3
4   chr7      4  6
5   chr8      5  6
6   chr9      6  3
7   chr6      7  9
8   chr6      8  9
9  chr10      9  4
10  chr4     10  6
11  chr2     11  6
12  chr8     12 10
13 chr10     13  7
14 chr10     14  7
15  chr7     15  7
$ LC_ALL=C sort -k 2b,2b -k 4n,4 sort.in
13 chr10     13  7
14 chr10     14  7
9  chr10      9  4
11  chr2     11  6
3   chr2      3  3
2   chr2      2  4
10  chr4     10  6
7   chr6      7  9
8   chr6      8  9
15  chr7     15  7
4   chr7      4  6
12  chr8     12 10
5   chr8      5  6
6   chr9      6  3
1   chr9      1  6
$ LC_ALL=C cat sort.in | tr -s ' ' |  sort -k 2b,2b -k 4n,4
9 chr10 9 4
13 chr10 13 7
14 chr10 14 7
3 chr2 3 3
2 chr2 2 4
11 chr2 11 6
10 chr4 10 6
7 chr6 7 9
8 chr6 8 9
4 chr7 4 6
15 chr7 15 7
5 chr8 5 6
12 chr8 12 10
6 chr9 6 3
1 chr9 1 6
```

It's interesting to note that every column-4 number that is out of sequence has a column-2 number that is preceded by fewer spaces. Thus, compare lines 1, 2, and 3 of the sorted data without tr. Also, compare lines 4, 5, and 6 of the sorted data without tr. In both instances, lines with column-2 numbers preceded by fewer spaces are sorted higher. I assume (but don't know) that this is correct behavior if the option to ignore leading blank spaces (i.e. -b) is omitted.

An alternative to your command that does work:

```
$ LC_ALL=C sort -k 2b,2 -k 4,4n sort.in
9  chr10      9  4
13 chr10     13  7
14 chr10     14  7
3   chr2      3  3
2   chr2      2  4
11  chr2     11  6
10  chr4     10  6
7   chr6      7  9
8   chr6      8  9
4   chr7      4  6
15  chr7     15  7
5   chr8      5  6
12  chr8     12 10
6   chr9      6  3
1   chr9      1  6
```

---

### Post by Arndt on 2009-04-26
> **kaibob said:**
> Sorry! I know little about setting environmental variables on the command line, so I first ran the commands with and then without the semi-colon to see if it would made a difference. It didn't.

To make sure, I just recreated sort.in and reran all commands without the semi-colon.

```
$ cat sort.in
1   chr9      1  6
2   chr2      2  4
3   chr2      3  3
4   chr7      4  6
5   chr8      5  6
6   chr9      6  3
7   chr6      7  9
8   chr6      8  9
9  chr10      9  4
10  chr4     10  6
11  chr2     11  6
12  chr8     12 10
13 chr10     13  7
14 chr10     14  7
15  chr7     15  7
$ LC_ALL=C sort -k 2b,2b -k 4n,4 sort.in
13 chr10     13  7
14 chr10     14  7
9  chr10      9  4
11  chr2     11  6
3   chr2      3  3
2   chr2      2  4
10  chr4     10  6
7   chr6      7  9
8   chr6      8  9
15  chr7     15  7
4   chr7      4  6
12  chr8     12 10
5   chr8      5  6
6   chr9      6  3
1   chr9      1  6
$ LC_ALL=C cat sort.in | tr -s ' ' |  sort -k 2b,2b -k 4n,4
9 chr10 9 4
13 chr10 13 7
14 chr10 14 7
3 chr2 3 3
2 chr2 2 4
11 chr2 11 6
10 chr4 10 6
7 chr6 7 9
8 chr6 8 9
4 chr7 4 6
15 chr7 15 7
5 chr8 5 6
12 chr8 12 10
6 chr9 6 3
1 chr9 1 6
```

It's interesting to note that every column-4 number that is out of sequence has a column-2 number that is preceded by fewer spaces. Thus, compare lines 1, 2, and 3 of the sorted data without tr. Also, compare lines 4, 5, and 6 of the sorted data without tr. In both instances, lines with column-2 numbers preceded by fewer spaces are sorted higher. I assume (but don't know) that this is correct behavior if the option to ignore leading blank spaces (i.e. -b) is omitted.

An alternative to your command that does work:

```
$ LC_ALL=C sort -k 2b,2 -k 4,4n sort.in
9  chr10      9  4
13 chr10     13  7
14 chr10     14  7
3   chr2      3  3
2   chr2      2  4
11  chr2     11  6
10  chr4     10  6
7   chr6      7  9
8   chr6      8  9
4   chr7      4  6
15  chr7     15  7
5   chr8      5  6
12  chr8     12 10
6   chr9      6  3
1   chr9      1  6
```

Very confusing. I think I'll return to 'sort' the day I really need it.

---

### Post by kaibob on 2009-04-26
> **Arndt said:**
> Very confusing. I think I'll return to 'sort' the day I really need it.
I agree. :)

BTW, out of curiosity, I converted sort.in into a csv file and then opened and sorted it in OpenOffice Calc. It took about 2 minutes and everything worked exactly how you would expect.

---


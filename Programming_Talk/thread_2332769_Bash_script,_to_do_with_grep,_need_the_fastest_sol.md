---
title: "Bash script, to do with grep, need the fastest solution possible"
date: 2016-08-03
forum: Programming Talk
---

### Post by vikler on 2016-08-03
Hi everyone, need the fastest possible solution which involves
1) grepping through a lot of large files
2) using a list of strings to grep, a list rather large

So basically in details, I have several 46 very large files. Each of them contains the following lines
id:hash where
id is digital string, hash is sha1/md5I 

need to process file with only ids and find id:hash pair for each of them in those large txt files. 
Also I need to find exact pair. For example for 1234 simple grep would return 5**1234**:, 523**1234**: etc

What's the fastest way to do it? The list with ids only contains about 30k rows, and the id:hash files each contain about 400k rows. I do use parallel which does increase performance, but since I need to find a very large set of ids, it's all very slow.

Any help would be greatly appreciated!

---

### Post by papibe on 2016-08-03
Hi vikler.

Take a look at the command 'join', which is one of the preisntalled Gnu tools. A combination of 'sort' and 'join' should solve the problem.

Hope it helps. Let as know how it goes.
Regards.

---

### Post by vikler on 2016-08-03
Hi papibe,
thanks for replying
So you suggest doing the following:
join <(sort 1.txt) <(sort 2.txt) [etc for all 46 files]
And then performing grep on one big file for each of the lines I need to find (listed in ids file), correct?

Would it really increase the performance (grep a very big single file rather than several smaller [though still large] files)?

---

### Post by papibe on 2016-08-03
I believe you got the idea on how to use join, and sort. However, I don't understand the final format.

For instance
keys:
```
5:comment4
4:comment3
3:comment2
2:comment1
1:comment0

```
hashes:
```
2:26ab0db90d72e28ad0ba1e22ee510510
3:6d7fce9fee471194aa8b5b6e47267f03
4:48a24b70a0b376535542b996af517398
5:1dcca23355272056f04fe8bf20edfce0
1:b026324c6904b2a9cb4b88d6d61c81d1

```
then:
```
$ join -t: <(sort -n keys) <(sort -n hashes) 

1:comment0:b026324c6904b2a9cb4b88d6d61c81d1
2:comment1:26ab0db90d72e28ad0ba1e22ee510510
3:comment2:6d7fce9fee471194aa8b5b6e47267f03
4:comment3:48a24b70a0b376535542b996af517398
5:comment4:1dcca23355272056f04fe8bf20edfce0

```
Once you join the files, what else do you need to do?

Regards.

P.S.: you may need to use 'sort -n' if the keys are numbers.

---

### Post by vikler on 2016-08-03
thanks for reply. Yes, keys just has numbers, no comments.
here is what I have:
keys:
```

1
2
3
4
5
6
7

```
hashes1:
```

num1:hash1
num2:hash2
num3:hash3
...

```
..
hashes46 [overall 46 large files]
```

numXYZ:hashXYZ
numZXYZZ:hashZXYZZ
...

```

What I do right now:
```

time for i in `cat ../hashes`; 
do 
echo $i; 
find . -type f | parallel -k -j150% -n 10000 -m grep -H -n -m 1 '^'$i':' {} >> ../result && break; 
done

```
Still it takes about 15 minutes to find 31 keys among all hashes files... Which is totally not solution for me, as I need to find about 20-30k keys....

Does join seem to be a solution in my case? Sorry, maybe I should've written a live example of what files look like in my first case.

Again, thanks so much for replying, I truly appreciate your help!

---

### Post by papibe on 2016-08-03
Assuming:
[LIST]
[*]'../hashes' contains the keys (I'll call it '../keys' instead), and
[*]the current directory contains only hashes files.
[/LIST]

Then this should work:
```
for file in ./*; do join -t: <(sort -n ../keys) <(sort -n "$file"); done
```
However, you would be sorting the keys every time. If you write the code to a script in the directory above, you could do:
```
 #!/bin/bash

sort ./keys -o sorted_keys

for file in ./hashes_dir/*; do
    join -t: ./sorted_keys <(sort -n "$file") >> ./results
done

```
To measure the time:
```
time ./script.sh
```
Let us know how that works.
Regards.

---

### Post by vikler on 2016-08-03
thanks!

looks like in files in hashes_dir I have a few fields that cannot be sorted (different hash for keys). I've to think how to deal with it....

---


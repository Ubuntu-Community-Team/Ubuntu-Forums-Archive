---
title: "Reading binary numbers to array from file  (C)"
date: 2011-01-22
forum: Programming Talk
---

### Post by lazyrussian on 2011-01-22
Hi,

I have an input file that has X bits per line, with X lines in total. 
I need to read each line into an element of an array; *arr[n] = n'th line from file *
I will not need to do any type of manipulation with these numbers, so reading in as a string will do me fine.

What's the best way to read this data into an array using C?

Thanks!

---

### Post by lazyrussian on 2011-01-22
I figure I should add some sample code - this throws a seg fault:

```

#define N 500

char fname[32];

  sprintf(fname, "file%d.txt", N);
  FILE *inputFile = fopen(fname, "r+");

    for(i=0;i<N;i++) {
      fscanf(inputFile, "%s", inputSource[i]);
      printf("%d, %s", i, inputSource[i]);
    }

  fclose(inputFile);

```

---

### Post by lazyrussian on 2011-01-22
Gah, I've gotten it to work partially, but now I've read elsewhere I need to build structures and what not to get it to scale and read properly.

Notable points: Use chars, fread(), and open the data with rb (e.g., fopen("file.txt", "rb")) 

Thanks anyway guys.

---

### Post by bouncingwilf on 2011-01-22
Sorry, I don't quite understand - you say you are reading binary numbers (in your title) but then refer to "bits" and finally use fscanf to read into an undeclared variable. Another area the raises confusion is the reference to lines of data in the file - usually (but not exclusively) binary files are contiguous streams of data. I  think maybe it would help if you could "re-define" what you are trying to achieve and we will try to assist.

Bouncingwilf

---

### Post by lazyrussian on 2011-01-22
> **bouncingwilf said:**
> Sorry, I don't quite understand - you say you are reading binary numbers (in your title) but then refer to "bits" and finally use fscanf to read into an undeclared variable. Another area the raises confusion is the reference to lines of data in the file - usually (but not exclusively) binary files are contiguous streams of data. I  think maybe it would help if you could "re-define" what you are trying to achieve and we will try to assist.

Bouncingwilf

Hah, sorry about that.

ok, so I have a data set that looks like this (as an example)
```

01001
01101
00000
11001
00001

```

I need to read each line in to a different element in an array.

---

### Post by talonmies on 2011-01-22
The C++ STL bitset container would be perfect for the string to binary conversion. Is there delimiting in the input file, and if so, what is it?

---

### Post by lazyrussian on 2011-01-22
> **talonmies said:**
> The C++ STL bitset container would be perfect for the string to binary conversion. Is there delimiting in the input file, and if so, what is it?

There's a '\n' delimiter at the end of every line. 
There are as many lines as there are bits in a line.
So, if I have a line with 500 0s and 1s, then the file has 500 lines, with 0s and 1s dispersed in a random sequence in each line.

---

### Post by lisati on 2011-01-22
One thing that can make a difference to how we approach this: is it (1) raw binary data, or (2) a text file with some kind of CR-based line break or other delimiter at the end of each line? 

If I understand you correctly, it's the second of these.

---

### Post by lazyrussian on 2011-01-22
> **lisati said:**
> One thing that can make a difference to how we approach this: is it (1) raw binary data, or (2) a text file with some kind of CR-based line break or other delimiter at the end of each line? 

If I understand you correctly, it's the second of these.

Yes, it's the latter.

---

### Post by lisati on 2011-01-22
I just had another look at post 2 in this thread. I think I see a clue. Here's my $0.02 towards a solution.

In C, one way of defining a string is as an array of characters, something like this, which sets aside an area of 20 bytes for your string:
```

char my_string[20];

```
When you refer to something like my_string[i], you are actually referring to the i'th character in the string.

If you want to have an array of strings, you will need to do something like this:
```

char my_array_of_strings[20][30];

```


(Mrs Lisati wants my attention, maybe others can expand on this a bit.)

---

### Post by lazyrussian on 2011-01-22
Alright,

so it stands, a snippet of my semi-working code looks like this:
```

#define N 5

char inputArray[N][N];

  sprintf(fname, "file%d.txt", N);

  FILE *inputFile = fopen(fname, "rb+");

    for(i=0;i<N;i++) {
      fread(&inputArray[i], sizeof(inputArray[i]), 1, inputFile);
      printf("%d: %s\n", i, inputArray[i]);
    }

  fclose(inputFile);


```

The output looks like this:
```

0: 01001
1: 
0110
2: 1
000
3: 00
11
4: 001
0


```

For reference, the input in file5.txt is:
```

01001
01101
00000
11001
00001

```

---

### Post by lazyrussian on 2011-01-22
ok, I think that's happening is that it's reading the first 5 characters, and then on the next line it reads '\n' + the next 4 characters, and so on. That's why it gets so messed up. Is there a way for it to skip the line break delimiter?

---

### Post by lazyrussian on 2011-01-22
First off, thank you Mr. Lisati for your clarification about 2d arrays and strings!

ok, almost got it working now, but I'm not sure why I have to 

[LIST=1]
[*]Read (N+2) instead of N chars
[*]Why a line break appears after each item si read in
[/LIST]

New Code:
```

#define N 5

char inputArray[N][N];

  sprintf(fname, "tweens%d.txt", N);
  FILE *inputFile = fopen(fname, "rb+");
    for(i=0;i<N;i++) {
      fgets(&inputArray[i][0], N+2, inputFile);
      printf("%d: %s\n", i, inputArray[i]);
    }

```

Output:
```

0: 01001

1: 01101

2: 00000

3: 11001

4: 00001


```

---

### Post by bouncingwilf on 2011-01-22
When you get that working to your satisfaction, you may want to try using fgets() and dynamically set the size of the arrays at runtime (assuming the arrays are always square).

fgets() will read up to n bytes (you can set the max) OR until the end of the line. It easy from there to determine the number of elements in each dimension of the array and the use malloc() to allocate the necessary space. ( use free when you've finished with the array). That way, if you inadvertently open a file of the wrong size, the program shouldn't crash.



Bouncingwilf

---

### Post by lazyrussian on 2011-01-22
> **bouncingwilf said:**
> When you get that working to your satisfaction, you may want to try using fgets() and dynamically set the size of the arrays at runtime (assuming the arrays are always square).

fgets() will read up to n bytes (you can set the max) OR until the end of the line. It easy from there to determine the number of elements in each dimension of the array and the use malloc() to allocate the necessary space. ( use free when you've finished with the array). That way, if you inadvertently open a file of the wrong size, the program shouldn't crash.



Bouncingwilf

Right, I am using fgets() (see my previous psot), but it is reading the end of line character for some reason.

---

### Post by lazyrussian on 2011-01-22
Never mind. I don't think it's actually reading the Newline character. There was just something screwing going on with the way I was outputting it.

Anywy,y my problem's solved! Thanks everyone! Square 'char' matrices solved the problem!

---


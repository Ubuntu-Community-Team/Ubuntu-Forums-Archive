---
title: "Reading doubles from a file in C"
date: 2014-02-10
forum: Programming Talk
---

### Post by bikewrecker on 2014-02-10
Hi guys. I'm writing a program for my cs class and I have to make it read doubles from a file. Its supposed to read one double per line. Then I'm supposed to use the doubles to find the standard deviation of the values in the file. Right now I'm just working on getting the values off of the file and storing them in an array. Here is my code so far:
```

  5 int
  6 main()
  7 {
  8         FILE* file = fopen ("file.dat", "r");
  9         int lines = 0, i = 0, c = 0;
 10         c = getc(file);
 11         while (c != EOF)
 12         {
 13                 if (c =='\n')
 14                 lines++;
 15                 c = getc(file);
 16         }
 17         printf("%d\n",lines);
 18         double x[lines];
 19         while(!feof(file))
 20         {
 21                 fscanf(file, "%lf", &x[i]);
 22                 printf ("%lf \n", x[i]);
 23                 i = i+1;
 24         }
 25         fclose(file);
 26 return 0;
 27 }
~               

```

The file i have made as file.dat has 11 lines in it. 

Here is the output 
```

[drmcb@pc30 ~/Homework4]$ ./sdev.out
11
[drmcb@pc30 ~/Homework4]$ 

```

If anyone could let me know what I'm doing wrong I would greatly appreciate it!

---

### Post by spjackson on 2014-02-10
What is the state of the file once the first loop completes? How many times will the second loop be executed if the file is in that state?

---

### Post by bikewrecker on 2014-02-10
> **spjackson said:**
> What is the state of the file once the first loop completes? How many times will the second loop be executed if the file is in that state?

I'm not sure what you're asking. The program runs the first loop correctly because in the first printf prints the right number of lines. This is my first time dealing with opening and reading files with C, so I'm kindof just stumbling around blindly trying to make something work.

---

### Post by spjackson on 2014-02-10
Your first loop reads until the end of file is reached. Then, when you get to your second loop, you are already at end of file, so it executes zero times. You don't want to be at end of file, you want to be at the start of the file.

---

### Post by bikewrecker on 2014-02-10
Oh, ok awesome! Thank you so much! I just added ```
  void rewind(FILE *f);
rewind(file);

``` before the second loop and now its working a lot better. Thank you so much for your help!

---

### Post by ofnuts on 2014-02-10
What spjackson is hinting at is that your first loop reads the file to the end, so there is nothing left to read for the second loop. So you have three choices:
[LIST=1]
[*]Close/reopen the file. Not a good idea (in a real app, some other program could open the file in the small tile window between the close and the open) 
[*]Reset the read pointer to the beginning with fseek() 
[*]Avoid reading the file twice altogether:
[LIST=|INDENT=1]
[*]allocate space a bit more dynamically (list, resizable array) so that it grows (steadily or by steps) as you read the data 
[*]start the file with a count of numbers to follow (which may be a god thing if you design evolves and this file starts holding several sequences of numbers) 
[/LIST]
   
[/LIST]

---


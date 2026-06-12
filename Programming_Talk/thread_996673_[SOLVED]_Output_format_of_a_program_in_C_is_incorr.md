---
title: "[SOLVED] Output format of a program in C is incorrect"
date: 2008-11-29
forum: Programming Talk
---

### Post by PmDematagoda on 2008-11-29
I made a program in C, the output it provides is correct, however the output format(which is specific) is incorrect. I will not post the entire program because it is unnecessary however I will post a smaller, to-the-point program that I made for the purposes of solving this minor headache:-
```
#include <stdio.h>
#include <string.h>

int main(){
  char testarray[10][17];
  int somenumber=7484,count;
  FILE *in;
  in = fopen("test.in","r");
  for(count=1;count<=5;count++){
    fgets(testarray[count],sizeof testarray,in);
  }

  for(count=1;count<=5;count++){
    printf("%s %d",testarray[count],somenumber);
  }
}
```
The file has some text line-by-line. The output format that should have been there(and is there in code without the two-dimensional array, however the output is incorrect):-
```
text number
text number
```
The resultant output format from the above code is:-
```
text
 number
text
 number
```
which leads me to believe that something in the array is incorrect, probably due to fgets since it seems to work fine with fscanf, but I can't put my finger as to what the exact problem is or how to solve it.

Thanks in advance for any help in this problem:).

---

### Post by slavik on 2008-11-29
each testarray element has a newline at the end

was your input file made in windows? that would explain it

---

### Post by Tony Flury on 2008-11-29
looks to me like fgets is reading to the end of the line - which of course includes a '\n'. that '\n' will be stored as part of your text string, and printed out when you print your string.

Also - I would be careful of your user of sizeof. I think that sizeof(testarray) will return 170, so your fgets will read up to 170 characters (rather than 10 that I think you are expecting). so if you get a very long line - your fgets will go wrong.

---

### Post by PmDematagoda on 2008-11-29
> **slavik said:**
> each testarray element has a newline at the end

was your input file made in windows? that would explain it

The program and input file were both made in Linux. However, I did use Gedit to create the input file, perhaps that is the problem?

> Also - I would be careful of your user of sizeof. I think that sizeof(testarray) will return 170, so your fgets will read up to 170 characters (rather than 10 that I think you are expecting). so if you get a very long line - your fgets will go wrong.
That is true, however I do this on the assumption that there will be no abnormalities as such. But I did not know the part about sizeof giving the size of the full array and not just one row, thanks for that:).

About the new line, I tried removing it by doing a strcmp and replacing the \n(if any) with a null value, however I get a segmentation fault with this.

---

### Post by slavik on 2008-11-29
nevermind my comment, the others were correct (I should've taken longer to read your code).

fgets will read upto and including the newline char, that's why it is there. you do not have to use strcmp to remove the newline, you can do the following:

char * str = "blah\n";
str[strlen(str)-1] = '\0';

---

### Post by PmDematagoda on 2008-11-29
Thanks for the help slavik, your code solved the problem.:)

---


---
title: "control characters in prinf()"
date: 2012-10-01
forum: Programming Talk
---

### Post by bouncingwilf on 2012-10-01
Now I know I'm going senile! I must have forgotten something from the deep distant past but for the life of me I'm perplexed!

I just want to generate a string to pass a formatted date string to a system call but can't seem to get the closing quotes in place 

only two lines of code

    char datestring[40];
    snprintf(datestring,40,"date --date=\" %s \"  \n",argv[1]);

Where argv[1] is the string to insert

output from     printf("%s",datestring); is 

GMT+0date --date=" Wed Aug 29 00:45:26 GMT+0date --date=" Wed Aug 29 00:45:30 GMT+0date --date=" Wed Aug 29 00:45:34 GMT+0date --date=" Wed Aug 29 00:45:42 GMT+0date --date=" Wed Aug 29 00:45:46 GMT+0date --date=" Wed Aug 29 00:45:50 GMT+0date --date=" Wed Au.................    etc.

Can't seem to get the second \" or \n to function - what have I forgotten please.


Bouncingwilf


OK I've proved I'm an idiot - > 40 chars in the string!

---


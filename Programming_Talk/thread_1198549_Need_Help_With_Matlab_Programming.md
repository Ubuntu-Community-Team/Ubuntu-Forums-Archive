---
title: "Need Help With Matlab Programming"
date: 2009-06-27
forum: Programming Talk
---

### Post by RookieUbuntuUser58 on 2009-06-27
To start off I'm not really comfortable programming in Matlab (haven't used it in ages). I have the code below but I'm having trouble. Heres what the code is suppose to do and hopefully someone could help. The user inputs A0,A1, A2,A3 and matlab sorts it out into labeled values Amax, Amin, Aa, Ab (a and b are subscripts for the values that are not max nor min). Then from there I use a code to do things like Amax+Amin = Ab + Aa (I know how to do this part of the code). Im just having problems with the sorting and mathlab labeling the sorted values Amax, Amin, Aa, Ab to proceed. Thanks in advance for any help.

clear
A0=input('Please Input A0');
A1=input('Please Input A1');
A2=input('Please Input A2');
A3=input('Please Input A3');
userValues = [A0, A1, A2, A3];
sorted = sort(userValues);
min=userValues(1);
max=userValues(length(userValues));

CN:Suppose to be all one big program. User imputs the values, it gets sorted to Amin, Amax, Aa, and Ab; then program evaluates it using Amax + Amin = Aa +Ab and etc and draws a conclusion.

---

### Post by RookieUbuntuUser58 on 2009-06-27
Bump, anyone? I would really like to move onto the next steps of the program but not knowing how to do the sort and labeling the sorted values is holding me back.

---

### Post by PaulM1985 on 2009-06-27
Just a guess but should you not be using 

amin = sorted(1)
amax = sorted(length(sorted))

does sorted = sort(uservalues) not put the sorted version of uservalues into an array called sorted.

Just a guess. I havent used matlab in a long while either

Paul

---

### Post by RookieUbuntuUser58 on 2009-06-27
> **PaulM1985 said:**
> Just a guess but should you not be using 

amin = sorted(1)
amax = sorted(length(sorted))

does sorted = sort(uservalues) not put the sorted version of uservalues into an array called sorted.

Just a guess. I havent used matlab in a long while either

Paul

I changed it to amin and amax. But when I run the program (to test as it is not complete). It prompts for the A0, A1, A2, A3 but does nothing after that. Say I want to do Amax+Amin<=Aa+Ab; the other values Aa and Ab are not defined. So what does Matlab designate the values not Amax and Amin as. Or how do I let it know to designate those values to Aa and Ab (when it sorts it)?

---

### Post by PaulM1985 on 2009-06-27
This worked for me in Octave

clear
A0=input('Please Input A0');
A1=input('Please Input A1');
A2=input('Please Input A2');
A3=input('Please Input A3');
userValues = [A0, A1, A2, A3];
sorted = sort(userValues);
min=sorted(1);
max=sorted(length(userValues));
printf("%d\n", min)
printf("%d", max)

regarding Aa and Ab, you have not set these so far.

You would need to add lines:
Aa = sorted(2);
Ab = sorted(3);
(provided Aa is smaller than Ab and these are the array indices you wanted)
so that the variables are initialised.  Then the test should be ok to carry out

---

### Post by RookieUbuntuUser58 on 2009-06-27
> **PaulM1985 said:**
> This worked for me in Octave

clear
A0=input('Please Input A0');
A1=input('Please Input A1');
A2=input('Please Input A2');
A3=input('Please Input A3');
userValues = [A0, A1, A2, A3];
sorted = sort(userValues);
min=sorted(1);
max=sorted(length(userValues));
printf("%d\n", min)
printf("%d", max)

regarding Aa and Ab, you have not set these so far.

You would need to add lines:
Aa = sorted(2);
Ab = sorted(3);
(provided Aa is smaller than Ab and these are the array indices you wanted)
so that the variables are initialised.  Then the test should be ok to carry out

Thanks had to change it a bit to get it to work in Matlab
clear
A0=input('Please Input A0');
A1=input('Please Input A1');
A2=input('Please Input A2');
A3=input('Please Input A3');
userValues = [A0, A1, A2, A3];
sorted = sort(userValues);
Amin=sorted(1);
Amax=sorted(length(userValues));
fprintf('%d\n', Amin)
fprintf('%d', Amax)

for a test returned:
Please Input A0 3
Please Input A1 4
Please Input A2 5
Please Input A3 6
3
6>> 

But I have to use these sortings for inequality if then statements (which I know how to do). So what would the values not designated as Amax and Amin be called for the expressions or how would I designate them? Assuming the max and min values are called by Amax and Amin?

Edit: I see you beat me to the answer. Thanks will try it.

---

### Post by PaulM1985 on 2009-06-27
Just a tip.. if you are looking at sorting values, put the smallest and largest as the middle two values in the array to make sure the sorting worked.

In your test you had the first value as the smallest (3) and the last as the largest (6) so you didnt test if the sort necessarily worked.

---

### Post by RookieUbuntuUser58 on 2009-06-27
> **PaulM1985 said:**
> Just a tip.. if you are looking at sorting values, put the smallest and largest as the middle two values in the array to make sure the sorting worked.

In your test you had the first value as the smallest (3) and the last as the largest (6) so you didnt test if the sort necessarily worked.

Thanks again. Your tips worked perfectly. I'm working on completing the rest of the program. BTW I really gotta start learning to use Octave. Seems the codes are a bit different but not by much.:)

---

### Post by [h2o] on 2009-06-29
Is there a reason why you couldn't use the max() and min() functions that are already in MATLAB? These should be faster than a full sort as well.

---


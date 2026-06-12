---
title: "C/C++: Reset variable &quot;on the fly&quot; ?"
date: 2010-08-24
forum: Programming Talk
---

### Post by Repgahroll on 2010-08-24
Hello there.

I'm making a program that will receive from an external source some values every second. I'm using the command "tail" to get those values, and I need to set them dynamically into variables.

Is there a way to do this?

Thanks in advance.

---

### Post by Rany Albeg on 2010-08-24
Hello,

I'm not sure I understand you correctly , but it sounds like you need to use the 'new' operator or the 'malloc' function to dynamically allocate the memory and then make your program read these values into it.
If I'm getting you wrong please be more specific and try to describe what you mean when you say "on the fly".

---

### Post by Zugzwang on 2010-08-24
It appears to me as if you want a multi-threaded application in which one thread always looks for new values by executing the "tail" command in a shell (actually, the tail command itself doesn't really produce any data. Why don't you read it from the source where "tails" gets its data from?) every second and then updates a variable of your process according to the new value.

While this is certainly possible, it appears as it your proposed method for the problem you are having is over-complicated for whatever task you are trying to solve. Would you mind adding some details? Where does "tail" get its data from? What happens if there appeared multiple new data lines in the last second? Etc...

---

### Post by Repgahroll on 2010-08-24
Thanks for the answers.

In fact, I have a homemade (by me) musical keyboard here that sends (via Arduino) the keys states actually a lot of times every second.

I couldn't figure out how to use libserial or any other method to get the data I need. And tail is able to get the data correctly.

On the USB the computer keeps receiving the keys states as fast as Arduino can send. The format is binary, like this:

000011000000010
000010000100000

So It can detect whether the keys 'starts' when \n appears this way isn't necessary to add any kind of identifier, the program simply calculate the distance from \n to tell which key is pressed.

Now, my problem is that I need to be able to "read" it into a variable, then I can explode it and program which note the computer will play.

It's very basic, however, I don't know how to actually transform this data into a variable without calling tail various times (which is very slow) or using some other method to get the data that corrupts it.

Thanks.

EDIT: The actual keyboard has 200+keys

---

### Post by dwhitney67 on 2010-08-24
Open the USB (device) port and read the data.

If you do not know how to open a file and read data from it, then I would suggest that you learn how so that you understand the basics.  Opening the device for a USB port shouldn't be much different, nor harder.

As Zugswang was attempting to hint at, abandon your pursuit of using "tail".  There's no place for it in a C/C++ application.

By the way, C and C++ are different languages, with the latter sharing many features of the former, and yet at the same time supplanting many of its archaic and error-prone features.  Choose wisely as to which language to use.

---


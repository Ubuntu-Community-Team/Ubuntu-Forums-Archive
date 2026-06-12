---
title: "[SOLVED] Storing doubles in file"
date: 2007-12-09
forum: Programming Talk
---

### Post by roberto22085 on 2007-12-09
I am creating a c++ program. I am a little confused why if you store a number like 15.00, c++ removes the .00. But if you pull the 15 out of a file into a double variable, it won't add the .00. Is this confusing to anyone else? C++ takes the .00 off even when I type them in that way, but it doesn't add them back even if it's stored into a double variable.

My program doesn't work correctly unless the .00 is on the end of the double. If I go into the data file manually and add the .00, my program comes up with the correct totals.

Any way, my question is, how can I store a number as 15.00 if the user inputs 15 or 15.00??

Thanks in advance!!!

---

### Post by Moezzie on 2007-12-09
I dont really know why c++ does not display your .00. My guess would be that its just not nessesary because 15 is the same as 15.00.

I would probably just fix this though a simple if-statement. 
Could look something like this.

If (number has no decimals)
{
  print number and .00
}

---

### Post by engla on 2007-12-09
Well you have to use the format string to specify the number format if that is important; for example, the float format %f can be specified with two numbers "%X.Yf", where X is the field width and Y is the number of decimals. So try something like

```
fprintf(file, "%.2f", number);
```

Edit: Hm, sorry I'm such a C head. Perhaps[ this link can help you?]("http://www.cplusplus.com/reference/iostream/ios_base/precision.html"): You can set the output stream to "fixed" and then set the number of digits.

---

### Post by aks44 on 2007-12-09
> **roberto22085 said:**
> I am a little confused why if you store a number like 15.00, c++ removes the .00. But if you pull the 15 out of a file into a double variable, it won't add the .00. [...] C++ takes the .00 off even when I type them in that way, but it doesn't add them back even if it's stored into a double variable.The **double** type stores numbers, not a sequence of digits. 15 is the same as 15.00. It's just a display convention which doesn't change the value of the number. Do you also expect to input an integer 0001 and get anything else than 1 when you output it back?

> **roberto22085 said:**
> Is this confusing to anyone else?No. :)

> **roberto22085 said:**
> If I go into the data file manually and add the .00, my program comes up with the correct totals.If your program can't correctly do its job unless your numbers are stored in this specific format, then you have bigger problems than finding how to output numbers using that very format. You should focus on making your program work correctly instead of trying to work around an obvious bug in your code. Just my 0.02.

---

### Post by roberto22085 on 2007-12-09
Thanks engla for your help! I am researching your tip and it looks like it's going to work.

Aks44....I am really sorry!! I'll reprogram C++ ASAP so that it works correctly.

I guess my assumption is that if C++ removes the .00 off of 15, it should be able to re-add them when it read the number back in from the file OR not take them off in the first place. Programming is all logic and that sounds logical to me! I don't think it's my code.....I am reading in doubles the only way you can (as far as I know). I am not an expert, that's why I posted the question to see if someone could help me. So I guess if I'm that dumb, next time you can just ignore my post!

Thanks!

---

### Post by aks44 on 2007-12-09
> **roberto22085 said:**
> Aks44....I am really sorry!! I'll reprogram C++ ASAP so that it works correctly.

I guess my assumption is that if C++ removes the .00 off of 15, it should be able to re-add them when it read the number back in from the file OR not take them off in the first place. Programming is all logic and that sounds logical to me! I don't think it's my code.....I am reading in doubles the only way you can (as far as I know).

C++ doesn't "take off" anything. Again, a **double** stores a *number* not a character string so it is totally irrelevant whether the stream you read from actually contains the decimal part or not, std::istream (cin, ifstream, ...) understands both "15" and "15.00" the same way.


> **roberto22085 said:**
> I am not an expert, that's why I posted the question to see if someone could help me. So I guess if I'm that dumb, next time you can just ignore my post!

I just pointed out that the bug is not where you think it is. Your problem is not that C++ outputs 15 instead of 15.00, but that you *rely* on the .00 to be there in order for your program to give correct results. Noone called you dumb.

Again, your problem is not on the output side like you believe, but on the input side.

---

### Post by cwaldbieser on 2007-12-09
I think if you showed your relevant code, it would be easier for others to explain why you are having a problem.

Like aks44 mentioned, if you are storing the number to a file in its numeric representation (i.e. as binary data) rather than its ASCII representation, C++ is not actually storing or removing the decimal places.  It stores the numeric representation, and it is up to your program to represent that value in a way that makes sense to ther rest of your program.

---


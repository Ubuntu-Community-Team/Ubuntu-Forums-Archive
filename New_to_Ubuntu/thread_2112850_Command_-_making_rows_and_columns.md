---
title: "Command - making rows and columns"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by toad3000 on 2013-02-05
Is there any command I can use to make a text file that contains n number of columns and n number of rows? 

Thanks.

---

### Post by CaptainMark on 2013-02-06
as in just blank spaces or do you plan to make a chart for something?

---

### Post by tgalati4 on 2013-02-06
Open a terminal:

```
man nano
```

There is a line/column switch that places the cursor at a particular line and column.

Save the file and you might get what you want.

---

### Post by squakie on 2013-02-06
You can also put text in a spreadsheet - try the spreadsheet in LibreOffice and play with it.  Spreadsheets by default are columns and rows.  Don't worry about the default size of a column - you can change that as you need.

---

### Post by CaptainMark on 2013-02-06
> **tgalati4 said:**
> Open a terminal:

```
man nano
```

There is a line/column switch that places the cursor at a particular line and column.

Save the file and you might get what you want.

I don't believe this will create the extra space though, I think it can only be used to jump to existing lines/columns, perhaps if the op tells us more what you want to do we might be able to tell you the easiest way to do it

---

### Post by Frogs Hair on 2013-02-06
You can create a table with rows and columns in Libre Office Writer.

---

### Post by toad3000 on 2013-02-06
No, I'm sorry I was pretty unclear.
I mean to make rows and columns with the echo command? Is that possible? Also is it possible to tell echo how many spaces I want between each word without actually pressing space many times?

---

### Post by steeldriver on 2013-02-06
How about something using bash printf?

```
$ for i in {1..5}; do for j in {1..3}; do printf "xxx\t"; done; printf "\n"; done
xxx     xxx     xxx
xxx     xxx     xxx
xxx     xxx     xxx
xxx     xxx     xxx
xxx     xxx     xxx

```

---

### Post by papibe on 2013-02-06
Hi toad3000.

Yes and no. Let me explain.

Using 'echo' would create just text files.

However, in terms of usability, tools like 'awk', and 'cut' to name a few, would interpret those files as rows and columns.

For instance, you can create a file redirecting the output using '>', and then adding more lines by using '>>':
```
echo 1 Hello Hola > file.txt
echo 2 Yes Si >> file.txt
echo 3 No No >> file.txt
```
Then your file would be:
```

1 Hello Hola
2 Yes Si
3 No No
```
Then you can use awk to print column 2:
```
awk '{print $2}' file.txt
Hello
Yes
No
```
Does that help? 

Let us know how it goes.
Regards.

---

### Post by toad3000 on 2013-02-06
I see what you're saying there. 
But it just it seems pretty tedious to say right the name of one column and press many space bars to right the name of the second column? Is there a way of doing that in echo? I mean to specify spaces between columns or texts?

Thanks.

---

### Post by papibe on 2013-02-06
In terms of functionality, you only need one space, or one separator.

For example:
```
1,Hello,Hola
2,Yes,Si
3,No,No
```
And then:
```
$ awk -F, '{print $2}' file.txt
Hello
Yes
No
```
Is that what you are looking for?

May you are concern about format? like equi spaced columns? something like this:
```

1  Hello  Hola
2  Yes    Si
3  No     No
```
Tell us how it goes.
Regards.

---


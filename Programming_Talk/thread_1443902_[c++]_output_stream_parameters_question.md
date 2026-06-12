---
title: "[c++] output stream parameters question"
date: 2010-03-31
forum: Programming Talk
---

### Post by fasoulas on 2010-03-31
what is the difference between ? 

```
ofstream out("data.txt" , ios::out | ios::in);
```

AND

```
ofstream out("data.txt");
```

i was trying to do a piece of code to work for hours and when i wrote
**ios::out | ios::in** as a second parameter to this output file stream my code worked and the stream wrote the data to the file a wanted,whereas before it hasn't happening 

Why an output file stream needs ios::in and ios::out to write to a file? 

This is a striped down version of my code

```
	
        ifstream read ;
	ofstream writeout ; 

	read.open("data.txt") ;
	
	somefunction(num , ID , price , size , read );
	
	readF.close() ;
	
	do
	{
		readF.open("data.txt") ;
	
		writeout.open("out.txt" , ios::out | ios::in);
		
		//this function must write data to a file
		someotherfunction(writeout , num , ID);

		////////CODE//////////

		read.close();
		writeout.close();
	
	}while(...);

```

sorry for my bad english

---

### Post by MadCow108 on 2010-03-31
the difference is the way the file is opened. ios::out opens the file in write mode, ios::in opens it in read mode.
This changes where the filepointer is placed, how it behaves and what is done with previous content.

the difficulty is that ofstream opens the stream implicitly in ios::out | ios::trunc mode

to avoid truncation you need to open it in read/write mode: ios::out|ios::in
even if its an output stream, don't ask me why...
if you want to append you can use ios::app
(ios::ate will also truncate without an ios::in thrown in)

if you want to have a file in full input output mode, use the input/output classes fstream for files, or iostream for more general streams
here is an overview of the stream classes:
[http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

---

### Post by fasoulas on 2010-03-31
> **MadCow108 said:**
> the difference is the way the file is opened. ios::out opens the file in write mode, ios::in opens it in read mode.
This changes where the filepointer is placed, how it behaves and what is done with previous content.

the difficulty is that ofstream opens the stream implicitly in ios::out | ios::trunc mode

to avoid truncation you need to open it in read/write mode: ios::out|ios::in
even if its an output stream, don't ask me why...
if you want to append you can use ios::app
(ios::ate will also truncate without an ios::in thrown in)

if you want to have a file in full input output mode, use the input/output classes fstream for files, or iostream for more general streams
here is an overview of the stream classes:
[http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

thanks a lot for the help i think i got your point.

---


---
title: "C++: How do I open file and getLine() from the middle instead of the beginning?"
date: 2008-07-31
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-07-31
I have some very large text files, ~ 46 - 90 MB that I am parsing, but the data that I really care about is always at the end, around the last 200 kb.  I get this data by opening the file and then doing

ifstream textfile;
textfile = open("log.txt");

while(!textfile.fail())
{
    string nextline;
    getLine(nextline, textfile);
    //more code...
}

The above might have some errors, but you get the idea.  Instead of starting the getLine() routine at the beginning of the file, how can I start closer to the end?  Say 99% through the file.

---

### Post by LaRoza on 2008-07-31
I found this in the standard library: [http://www.cppreference.com/cppio/seekg.html](http://www.cppreference.com/cppio/seekg.html)

---

### Post by SNYP40A1 on 2008-07-31
> **LaRoza said:**
> I found this in the standard library: [http://www.cppreference.com/cppio/seekg.html](http://www.cppreference.com/cppio/seekg.html)

Hi LaRoza, I saw that function too, but it does not do me much good w/o knowing the position that I want to seek to.  How do I say, "seek to line number (#total lines * 0.99)"?

---

### Post by LaRoza on 2008-07-31
> **SNYP40A1 said:**
> Hi LaRoza, I saw that function too, but it does not do me much good w/o knowing the position that I want to seek to.  How do I say, "seek to line number (#total lines * 0.99)"?

[http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

See about 3/4 the way down. You can read files from the end.

---

### Post by SNYP40A1 on 2008-07-31
> **LaRoza said:**
> [http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

See about 3/4 the way down. You can read files from the end.

Thanks, that did the trick!  Here's the code I made based on your reference:

	ifstream datafile;
	datafile.open(filepath.c_str());
	int begin = datafile.tellg();
	datafile.seekg (0, ios::end);
	int end = datafile.tellg();
	int newpos = end - begin;
	newpos = 0.95*newpos;
	datafile.seekg(newpos, ios::beg);

---


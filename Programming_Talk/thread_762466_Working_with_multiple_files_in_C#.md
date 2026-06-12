---
title: "Working with multiple files in C#"
date: 2008-04-22
forum: Programming Talk
---

### Post by true_friend on 2008-04-22
Hi
I am absolute beginner of C#, trying to learn it for corpus programming and text processing. I want to build a small application  which will work as follows.
There is a list of words in text file. And there are two folders having text files say Corpus A and Corpus B. I want this application to get a word from wordlist txt file and search for its occurance in Corpus A's all files. An integer will count the number of files in which the search found the word. At the end it will return the number of files in the form of integer. Same is the case with Corpus B folder. The result will be then combined in a console line with word, Corpus A, Corpus B sequence. I am so much beginner that I couldn't find a way to handle multiple text files. I mean to process them in a loop. I have studied almost all file handling classes like StreamReader, StreamWriter, TextReader, DirectoryInfo, FileInfo etc. But I couldn't find a method to enlist the files in directory or putting in an array. Please indicate me how can I do this.
Regards

---

### Post by twistedtwig on 2008-04-22
Sounds very much like a school / college assignment to me.  Have a look at:

```

string folderPath = "c:\temp\";
string searchCriteria = "*.txt";

DirectoryInfo dir = new DirectoryInfo(folderPath);
FileInfo[] = dir.GetFiles(searchCriteria);

```

That returns an array of files.  I hope you can find your way from there.

---

### Post by true_friend on 2008-04-22
Thanks a lot. It should be ok for me.
Regards

---


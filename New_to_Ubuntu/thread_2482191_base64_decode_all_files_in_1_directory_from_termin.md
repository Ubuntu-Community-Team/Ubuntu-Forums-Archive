---
title: "base64 decode all files in 1 directory from terminal?"
date: 2022-12-23
forum: New to Ubuntu
---

### Post by nginmu on 2022-12-23
ok here's the command I've been using on individual files, kept in /me/c

```

me@skully:~/c$ sudo base64 --decode docx > docx.docx

```

.. where for example, docx is a plain text file containing a base64 encoding of an MS Word .docx document.

it spits out the decoded MS Word document as docx.docx which I can then open in a word processor.

I have a raft of text files in the directory, all with random placeholder names like rumple, tug, alvin, ffff, interesting, newts etc..

What I'd like to do is issue one terminal command to go through the directory and base64 decode each and every file, leaving the originals in place, and placing the decodes into their own subdirectory, each with the same filename as the original.

How would I accomplish that?

I guessed at 

```

me@skully:~/c$ sudo base64 --decode *  > ~/c/o/*

```

but it did not work

Could I modify something like this; [https://dev.to/equiman/base64-encode-decode-multiple-files-2ol1](https://dev.to/equiman/base64-encode-decode-multiple-files-2ol1)

[edit] - got the code at the above link working.

---

### Post by Impavidus on 2022-12-23
First: why sudo? It's only needed if you don't have read permission on the files you want to decode, but as they are in your home directory, you should have that permission.

I suggest you write a loop in bash that repeatedly calls base64 for each file you want to decode. A bash scripting guide should tell you how.

---

### Post by nginmu on 2022-12-23
Sorry, pure frustration. I couldn't get it to work so I went all brute force flailing in the dark, thinking maybe permissions were the issue. I should perhaps keep a bash scripting book on my desk. I always learn a bit about it, then forget..

---


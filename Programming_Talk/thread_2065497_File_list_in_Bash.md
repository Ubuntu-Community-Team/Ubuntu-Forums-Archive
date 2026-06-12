---
title: "File list in Bash"
date: 2012-10-02
forum: Programming Talk
---

### Post by angus1964 on 2012-10-02
I'm very new to Bash but im wondering if theres an easy way to do the following.
I have a folder which contains my Kindle books, inside the folders are folders for each author, then a folder for each book which contains the book and a jpg of the cover.
Is it possible to get bash to create a simple list of only the books?

---

### Post by Lars Noodén on 2012-10-02
find or ls should do the trick but can you first cut and paste an example of what the folders contain?

---

### Post by angus1964 on 2012-10-02
I have a main folder Kindle. In that folder for example there is a folder J K Rowling, inside that folder there is a folder for each harry potter book which contains the book and a jpg of the cover. This is repeated for quite a few authors and loads of books.
What i would like is to create a list of the books i.e.
Harry Potter & the sorcerors stone.mobi
Harry Potter & the deathly halllows.mobi
and so on.
Im assuming that bash has some way of working through the folders and producing the list?

---

### Post by Lars Noodén on 2012-10-02
Yes, you can walk through the folders with [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html)

```

find /home/angus1964/kindle/ -name '*.mobi' -print

# or
cd /home/angus1964/kindle/ 
find . -name '*.mobi' -print

```

See also
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

---

### Post by angus1964 on 2012-10-02
Meant to say the path to the books would be.
/kindle/jkrowling/harrypotterandthechamberofsecrets/harrypottterandthechamberofsecrets.mobi
/kindle/jkrowling/harrypotterandthedeathlyhallows/harrypotterandthedeathlyhallows.mobi

---

### Post by angus1964 on 2012-10-02
Thanks for quick reply find works a treat, totally noobie question can i make a file from the output?

---

### Post by angus1964 on 2012-10-02
Sorry to be a noob but is also possible for the list to just have the book name and not include the file path?

---

### Post by Lars Noodén on 2012-10-02
> **angus1964 said:**
> Thanks for quick reply find works a treat, totally noobie question can i make a file from the output?

Use a redirect.

```

find /home/angus1964/kindle/ -name '*.mobi' -print > my_books.txt

```

> **angus1964 said:**
> Sorry to be a noob but is also possible for the list to just have the book name and not include the file path?

printf has an option to just print the filename without the directory.

```

find /home/angus1964/kindle/ -name '*.mobi' -printf "%f\n" > my_books.txt

```

---

### Post by angus1964 on 2012-10-02
Thanks Lars for your quick replies, that was exactly what i needed. Having now seen the power of Bash at first hand im away to order some books on the subject.

Once again thanks very much.

Cheers

---

### Post by Lars Noodén on 2012-10-02
bash is pretty awesome.  There's nothing like making the computer do the work!

---


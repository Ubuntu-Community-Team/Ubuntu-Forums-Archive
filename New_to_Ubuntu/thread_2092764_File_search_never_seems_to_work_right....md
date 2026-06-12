---
title: "File search never seems to work right..."
date: 2012-12-08
forum: New to Ubuntu
---

### Post by diablo75 on 2012-12-08
This is something I've never been able to figure out in the last 4 or 5 years since I started using Ubuntu.

Within Nautilus, there is now a search box at the top you can type things into to try and find files within the location you're currently looking at.

I just decided, as a test, to type "*.jpg", since, well you know, in Windows if you type that it'll show you every single JPG file on your hard drive if you're searching against C:

This search was done against a hard drive out of another computer I just attached to my system and booted into Ubuntu.  Zero files come back in the search result.  What gives?  Is it because the drive needs to be indexed?  Is there a way for me to search for things on a drive that hasn't been indexed without going to a command line?  What am I *still* doing wrong?  Just curious; in the mean time, I'm just going to reboot into Windows search again.

---

### Post by Frogs Hair on 2012-12-08
I install the gnome desktop utilities and use the included search tool. I have no idea  why it works much better than the built in tool in Nautilus. 

I ran a search for .png and got over 15,000 results before stopping the search.

---

### Post by Bucky Ball on 2012-12-08
Are you sure there's are .jpg files on the hard drive???

---

### Post by erind on 2012-12-08
> **diablo75 said:**
> [...]

I just decided, as a test, to type "*.jpg", since, well you know, in Windows if you type that it'll show you every single JPG file on your hard drive if you're searching against C:

This search was done against a hard drive out of another computer I just attached to my system and booted into Ubuntu.  Zero files come back in the search result.  What gives?  Is it because the drive needs to be indexed? 

[...]
The search in Nautilus is literal, so "*" will be part of the search, and not a wildcard as you expected. Use *.jpg* instead.

From my experience these are some of the things to keep in mind when using the search function of Nautilus, ( *version 2.32.0 *) :


[LIST]
[*] There's no need to use wildcards - they are implicit.
[*] The search is NOT case sensitive.
[*] Separate the search key words with white space, to narrow the search down.
[*] The search is a logical "AND" of its search composing key words, but their order does NOT matter.
[/LIST]

  So a search for the file "**file_name**" can be done using the key words: 

 ```
1. "file"
2. "name"
3. "name FILE"
4. "file name _"  
5. "_ name file"
6. "NaMe _ file"
7. "file_   name"
 ...

 # Note the spaces between key words in the above examples.

```All of the above combinations of the search key words will find the file named "**file_name**" in Nautilus.

---


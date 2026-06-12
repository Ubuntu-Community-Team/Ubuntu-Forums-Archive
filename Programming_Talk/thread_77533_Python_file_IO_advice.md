---
title: "Python file I/O advice"
date: 2005-10-17
forum: Programming Talk
---

### Post by stateq2 on 2005-10-17
Hi,

I want search a text file for a specific string.  Once opening the file in read mode, I know that I can use 'file.seek(n).....'n' representing the number of bytes to go to in a file.  Is there a way to specify a string instead of an integer?...or am I missing something?  Thanks.

---

### Post by stateq2 on 2005-10-17
well....I think I need to use the 'fileinput' module...i'll do some more research

---

### Post by psychicdragon on 2005-10-17
re.search does pretty much what you're looking for.

---

### Post by jrbj on 2005-10-17
[QUOTE=stateq2]Hi,

I want search a text file for a specific string.  Once opening the file in read mode, I know that I can use 'file.seek(n).....'n' representing the number of bytes to go to in a file.  Is there a way to specify a string instead of an integer?...or am I missing something?  Thanks.[/QUOTE]

Are you just looking for the presence of the string, or will need to edit the text?

I'm not sure how familiar you are with Python, so please forgive me if this example seems very basic.  I just want it to be complete.

```

# This code snippet will open a text file, read in all the text.
# It then return the index position of the search string if it exists.
# If the search string doesn't exist, it returns -1

# Open the file in text mode
# (Replace "filepath\filename" with the full path to the file)
f = file("filepath\filename", "r")

# Read in the entire text of the file
filetext = f.read()

# Replace "searchstring" with the string you're search for
strpos = filetext.find("searchstring")

# If the search string is found, strpos will now contain the
# index number of the search string's location
# If it is not found, strpos will equal -1

```

---

### Post by stateq2 on 2005-10-19
[QUOTE=jrbj]Are you just looking for the presence of the string, or will need to edit the text?

I'm not sure how familiar you are with Python, so please forgive me if this example seems very basic.  I just want it to be complete.

```

# This code snippet will open a text file, read in all the text.
# It then return the index position of the search string if it exists.
# If the search string doesn't exist, it returns -1

# Open the file in text mode
# (Replace "filepath\filename" with the full path to the file)
f = file("filepath\filename", "r")

# Read in the entire text of the file
filetext = f.read()

# Replace "searchstring" with the string you're search for
strpos = filetext.find("searchstring")

# If the search string is found, strpos will now contain the
# index number of the search string's location
# If it is not found, strpos will equal -1

```[/QUOTE]
This is exactly what I needed.  Thanks :)

---


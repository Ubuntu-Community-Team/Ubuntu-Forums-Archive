---
title: "filenames starting with &quot;the&quot;"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by ZOOstation on 2008-11-20
I've been wondering, is there any way to set Ubuntu to sort files that begin with the word "the" under the first letter of the next word, instead of listing them all under T? Strictly in terms of the GUI, I don't care how it names and organizes the files themselves.

---

### Post by markjensen on 2008-11-20
Strange request.

I don't see any way that the file manager, or any listing would do this.

I think that what you may be after is some bash script or such to find those files starting with "the" and rename the file, so "the_xxxx" would be renamed to "xxxx,the"

---

### Post by LowSky on 2008-11-20
Its not really that strange if your thinking in terms of Band names, book titles, movie titles, and so on. The big issue comes from human language versus machine language. Words like The and el and la, and so on, are really place holders for important nouns that are not names, like, "the tree" 
Its use is for a person to know if a someone is talking about an object or an idea over a person,

"the tree is green" for an object
"Bob is green" for a person
if you said "the Bob is green" it would imply Bob is some type of object.

when it comes to file systems, don't include "the" as it computers see everything as simple letters not language.

And even if you did make a script it could effect names that shoud stay with the T's like There, Thermal, them, theif, and so on.

---

### Post by lisati on 2008-11-20
> **LowSky said:**
> And even if you did make a script it could effect names that shoud stay with the T's like There, Thermal, them, theif, and so on.

One possibility, which I've seen used in some BASIC programs for parsing textual input, adds a space after the word you're searching for, e.g. "THE " in preference to "THE"

---

### Post by unutbu on 2008-11-20
> I don't care how it names and organizes the files themselves.

ZOOstation, are you saying it would be okay to rename the files? If so, this command
```

rename 's/^the //i' *
```

will remove the string 'The ' or 'the ' from the beginning of all files. Obviously once that's done, the GUI will display the files in order you desire.

---

### Post by alphacrucis2 on 2008-11-20
I notice that what the OP is asking for is exactly what the Apple Itunes program does when listing songs by title or album name so it is obviously doable.

---

### Post by markjensen on 2008-11-20
> **unutbu said:**
> ZOOstation, are you saying it would be okay to rename the files? If so, this command
```

rename 's/^the //i' *
```

will remove the string 'The ' or 'the ' from the beginning of all files. Obviously once that's done, the GUI will display the files in order you desire.

It will also change a band name like They Might Be Giants

---

### Post by markjensen on 2008-11-20
> **alphacrucis2 said:**
> I notice that what the OP is asking for is exactly what the Apple Itunes program does when listing songs by title or album name so it is obviously doable.

Doable, yes.  Any app can re-arrange as they see fit.

The thread starter wanted the filesystem to sort differently.  Now, this would involve either renaming the files, or writing up your own sort in a program.

---

### Post by adaptr on 2008-11-20
> **markjensen said:**
> It will also change a band name like They Might Be Giants
No, it won't - notice the space after "the".

---

### Post by markjensen on 2008-11-20
> **adaptr said:**
> No, it won't - notice the space after "the".
Ahhh... I notice it.... Now

---

### Post by ZOOstation on 2008-11-21
No, I don't mean just renaming the files. And yes, I mean exactly like iTunes does. Though strangely enough my iPod sorts bands without regard for "the" but not songs or albums. Apple's got some 'splainin to do.

---


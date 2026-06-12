---
title: "Ogg files and python"
date: 2008-11-04
forum: Programming Talk
---

### Post by me_takis on 2008-11-04
Hi all

I am developing a music player with python and pygame. It worked fine until I tried opening an .ogg file located in the examples folder named "Experience ubuntu.ogg". The program froze trying to open the above file which is of course a video file with an .ogg extension.
So the question I have is: how can I tell, using python, if a file is .ogg audio or .ogg video? and furthermore do other music formats have same issues (pygame supports mp3, wav, ogg, xm, mid & cda files)?

Regards
Takis

---

### Post by Greyed on 2008-11-05
[http://ekyo.nerim.net/software/pyogg/](http://ekyo.nerim.net/software/pyogg/) ?  No personal experience, just Googled "ogg Python" and that was the top hit.

---

### Post by stweat on 2008-11-05
I have not a clue how to write code

Is there are any code writers out there
 
looking for a new name for a portable 
dist.. How about littlebit.

---

### Post by me_takis on 2008-11-06
I found it and it's quite easy too.

First the file must be opened for reading:
f=open('Experience ubuntu.ogg')

then the first line must be read:
a=f.readline()

If it's a video file then the word 'theora' is surely inside the first line and if not then it's an audio file:
if 'theora' in a:  print 'it's a video!!!'

Not so scientific method but it works.

When finished, the file must be closed:
f.close()

---

### Post by Greyed on 2008-11-06
Isn't crafting a test based on a known quantity to determine the validity of one's assumptions the very definition of scientific?  ;)

---


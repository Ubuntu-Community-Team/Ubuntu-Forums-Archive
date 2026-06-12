---
title: "Remove Error Sound"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Mr. Man on 2008-11-01
is there anny way that i can remove the sound the computer makes when an error occurs? like when you backspace too much and it makes that annoying sound. maybe it would be even better to put a little softer sound insteaad of the one i have now. and let it ring only one even if i keep holding in the button.

---

### Post by justchange on 2008-11-01
The sound is made by a .wav file.

You can alter the .wav file in a program like Audacity (lower the volume.)

Find the particular file using Places>Search for Files>Name contains: *.wav.

I'm not sure which sound you're referring to, but try "alert.wav".
Copy it to Audacity (or other audio editor) and modify it to your heart's content.
Change the extension of the original file to .old (in case you want to restore it.)
Save the altered file with the original file's name and location.
You're done.
[I]
Note: If you can't change anything in the folder because you don't have root permissions, open a terminal (Applications>Accessories>Terminal) and type ```
gksudo nautilus
```. This opens the Nautilus file manager as a Super User, allowing the file changes.[/I] 

As for making it sound only once... I think that would take a re-write of the program: not in my skillset.

Good luck.

---


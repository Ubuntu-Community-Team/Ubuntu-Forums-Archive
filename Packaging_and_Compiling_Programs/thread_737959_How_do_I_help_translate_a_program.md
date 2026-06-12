---
title: "How do I help translate a program?"
date: 2008-03-28
forum: Packaging and Compiling Programs
---

### Post by graabein on 2008-03-28
I might help out on translating a program but I don't know which form this usually takes. I'm not sure it's on [Rosetta]("https://launchpad.net/rosetta"). 

What are the standard ways of doing translations?

Can anyone post some links for me to read up on?

---

### Post by erginemr on 2008-03-28
I am not sure about the funcionality of this Launchpad site, but I had once got my hands dirty to correct some small translation errors for an application in my system. 

I had used the source code of the program, where there were several translation files *.po, all in text format, one for each language. There was a tool, **poedit** in the repositories, specifically developed to edit those files. I believe you can install it with:
```
sudo aptitude install poedit
```
Then, when you (or the actual developer) compile the project, those *.po files are converted into human-unreadable *.mo files as part of the Debian package. 

So, I believe that one of the ways to help the translation of an application is to get into contact with its developer and ask his/her permission to translate the application to your language, or to review and correct the translation if it has already been translated.

On a final note, I would like to thank you both for having donated to the forum and willingness to get involved in open-source project development. **Thank you!** :KS

---

### Post by graabein on 2008-03-28
No no, thank *you*.


I've already been in touch with the developer btw.

---


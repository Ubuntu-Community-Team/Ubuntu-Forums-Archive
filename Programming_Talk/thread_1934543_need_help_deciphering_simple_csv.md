---
title: "need help deciphering simple csv"
date: 2012-03-02
forum: Programming Talk
---

### Post by yelena on 2012-03-02
Is it possible to decipher a csv file with the ciphering code?
I have the cipher code and can someone help me deciphering with python! 
thank you!! 
 
# Ciphering code
GradingFile = open("c:\\temp\\grading.csv", "r")
GradingFileCiphered = open("c:\\temp\\gradingciph.csv", "w")
linenumber = 0
for line in GradingFile:
linenumber += 1
WriteThisLine = ""
for character in line:
if character != "\n":
character = chr(ord(character) + linenumber%10)
WriteThisLine += character
GradingFileCiphered.write(WriteThisLine)
GradingFile.close()
GradingFileCiphered.close()

---

### Post by diesch on 2012-03-02
You just have to change 
```
 character = chr(ord(character) + linenumber%10)
```to
```
 character = chr(ord(character) - linenumber%10)
```

```
#!/usr/bin/env python

GradingFile = open("gradingciph.csv", "r")
GradingFileCiphered = open("gradingdeciph.csv", "w")
linenumber = 0

for line in GradingFile:
    linenumber += 1
    WriteThisLine = ""
    for character in line:
        if character != "\n":
            character = chr(ord(character) - linenumber%10)
        WriteThisLine += character
    GradingFileCiphered.write(WriteThisLine)
GradingFile.close()
GradingFileCiphered.close()

```

---


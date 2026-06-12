---
title: "looking for text  documents"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by Jonatan Formentera on 2012-05-30
Hi, I have two questions. The first one is:I'm very forgetful and sometimes I forget the name of my text documnents. I have Ubuntu 11.10 and I have the possibility to search for a documnet introducing a word or phrase, but I've tried it several times and it doesn't work. Can anyone tell me how to do it.The second question is. I have livre-office and I'd like to do an effect with texts. If you look at articles in magazines or papers, at the beginning the first character is larger than the other characters, these ones surround it perfectly. Do anyone know if I can do it with livre-office
Thanks

---

### Post by irv on 2012-05-30
> **Jonatan Formentera said:**
> Hi, I have two questions. The first one is:I'm very forgetful and sometimes I forget the name of my text documnents. I have Ubuntu 11.10 and I have the possibility to search for a documnet introducing a word or phrase, but I've tried it several times and it doesn't work. Can anyone tell me how to do it.The second question is. I have livre-office and I'd like to do an effect with texts. If you look at articles in magazines or papers, at the beginning the first character is larger than the other characters, these ones surround it perfectly. Do anyone know if I can do it with livre-office
Thanks
First, do you keep your doc and text files in your Documents directory? If you do, do a search from there.
[ATTACH]218956[/ATTACH]
Next, when you are creating a document in the word processor in LibreOffice just highlight the first character and make it bigger then the rest of the text and bold it. You can make it a different font also. I do this all the time.

---

### Post by steeldriver on 2012-05-30
if you don't mind the command line, you can use the 'find' command for fine-grained searching - it can be quite tricky to get right, feel free to post back with an example and we can try to show you how

for the libreoffice question, I believe you are talking about 'drop caps' - the consistent way to do those is select Format -> Paragraph from the menu bar and then choose the 'Drop Caps' tab

---

### Post by Jonatan Formentera on 2012-05-30
Ok. For instance, I have a text document in Documents. Its name is *Manifest del 12 M.odt*. But I have forgotten this name. I remember the sentence *que els ciutadans de*. That is in it. How can I find this document?

---

### Post by irv on 2012-05-30
There is a program called Recoll. You can install it by this command in a terminal.
```
sudo apt-get install recoll
```
The first time you run it it will build an index of your computer files.
It will take awhile to do this depending on how many files you have on your computer. It took about 2 to 2 1/2 hours to do mine.
But once you have done this it only takes a few seconds to search your entire computer for anything that is within a file.
It works great for me.
I am sure this is what you are looking for.

---

### Post by traditionalist on 2012-05-30
> **irv said:**
> There is a program called Recoll. You can install it by this command in a terminal.
```
sudo apt-get install recoll
```The first time you run it it will build an index of your computer files.
It will take awhile to do this depending on how many files you have on your computer. It took about 2 to 2 1/2 hours to do mine.
But once you have done this it only takes a few seconds to search your entire computer for anything that is within a file.
It works great for me.
I am sure this is what you are looking for.

+1 For Recoll.  First class, very very fast and finds any text in any document file immediately. You can get it here;

[[IMG]http://img842.imageshack.us/img842/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img842.imageshack.us/i/ubuntusoftwarecenter001.png/")


Make sure you put the index somewhere you have enough space, and not in the /root

---


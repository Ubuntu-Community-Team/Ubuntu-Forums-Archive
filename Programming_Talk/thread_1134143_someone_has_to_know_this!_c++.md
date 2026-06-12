---
title: "someone has to know this! c++"
date: 2009-04-23
forum: Programming Talk
---

### Post by ayastona on 2009-04-23
hi. the title might be a little confusing.

c++

i am trying to set up variables that have multiple other variables within them..

so for instance i need to enter a persons name and then along with that name i need to specify the persons age and address and a few other demographic informations..

that information will then be written to a file. (which i know how to do... i think....) then i will move to the next person and enter their name and within that persons name i will repeat the process as before...

how do i go about doing this? do i need to create a class? please help!

---

### Post by ayastona on 2009-04-23
Currently i have been taking the information directly entered by a person using my program and having the information printed into a text file... i may have to make it so that i can search for the information later and so i was wondering what is the best way to handle all-text information so that if i do need to recall it i can easily find it..

right now it just seems to me that by simply placing text into the text file, i am setting myself up for disaster in the future when i have alot of information saved.. 
thanks!

---

### Post by michy99 on 2009-04-23
You will have a better chance of getting your questions answered in the programming forum.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by manuelb on 2009-04-23
You may want to take a read [here]("http://crasseux.com/books/ctutorial/Structure-declarations.html#Structure%20declarations").
You can go for a **class** or a **struct**, in fact a struct is a class with every member public by default, conversely a class is a struct with every member private by default: there are other differences, but for now you just want to know that the **class** keyword is available only in c++ and instead concentrate your start on the very basic concept of programming.. just my head up on the matter :)

---

### Post by 3Miro on 2009-04-23
As manuelb said, you need either a class or a struct. In programming (in a very general sense) you have data and functions that manipulate the data. struct creates a data type consisting of several already defined data types (i.e. int for someone's SSN and int for the same person's age). A class incorporates data and functions together in a structured way.

My advice is to learn the basics of structs first and then moving to classes should be easy.

---


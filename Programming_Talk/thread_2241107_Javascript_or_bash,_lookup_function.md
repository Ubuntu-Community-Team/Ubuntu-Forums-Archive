---
title: "Javascript or bash, lookup function"
date: 2014-08-24
forum: Programming Talk
---

### Post by Joshua_Harris on 2014-08-24
I am attempting to write a script to help me move things along at work. I work for a company that deals in bulk mailing with the US Postal sevice. A big part of my job is sorting mail. Well, sometime things get out of order and we have to look up where things are supposed to go using three digit scheme sheets, lets say the zip code is _005_63, that would go in a tray with the tag 117. It's a bit confuseing, and looking it up takes time. What I'm wanting to do is translate this scheme sheet into a script so I could input the first three digits of the zip code and get the proper scheme. I simply just don't know how to go about this, as I am fairly new to programming in general. Any help would be greatly appreciated. :)
EDIT: A way to impliment this in javascript or bash would be preferable.

---

### Post by Tristan_Williams on 2014-08-24
How exactly does each zip code match up with each scheme?

I don't understand how 005 = 117

---

### Post by Joshua_Harris on 2014-08-24
It's not so much as it 005 equaling 117, it's more of what each code  aligns with on a collumn. The full list of AADC schemes can be found here:  [http://pe.usps.com/text/LabelingLists/L801.htm](http://pe.usps.com/text/LabelingLists/L801.htm)
What I'm basically  trying to do is just be able to pull the proper sequence from this list  by inputting the first three digits of the zip code, rather than  checking every peice of male against the list manualy.

---

### Post by nerdtron on 2014-08-24
Post an example on what you want to do so that we can see the bigger picture. Something like I have these example file names file1, file2, file3 and then each one has a code, so file1 corresponds to code1 and put on this folder.
Something along those lines. It would be better if you give the exact filenames and folders you want them to move into. The key here is to have a pattern on filenames to generate a script.

---

### Post by ian-weisser on 2014-08-25
I would do it with a bash array.
See [http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html) for an example.

label[zip_digits]=label_digits
label[005]=117
label[006]=006
label[010]=160

zip=005
output=label[zip]
echo output

---

### Post by ofnuts on 2014-08-25
I would do it with two things:

1) a file where each line is your key and its value using some convenient format (key=value, for instance)
2) a script that runs grep on the file above to find the line with the key (grep "$key="), cutting the key out (cut -d = -f2)  and outputting the value.

---


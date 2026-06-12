---
title: "Archive vs. 7Zip Program"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by lisar915 on 2008-05-15
Hello again everyone,

I've managed to install 7Zip, which I would like to use to Zip and Unzip files.  However, the only compression program that comes up is the Archive program that is installed by default.  How do I make it so that 7Zip is the program used by default?

Thanks again!
lisar915

---

### Post by DarkSaga70 on 2008-05-15
I went into the repositories and searched 7 zip and it just added it to the default program as a part of it instead of having to install a seperate program. Not sure if thats what you wanted to hear though. sorry.

---

### Post by lisar915 on 2008-05-15
> I went into the repositories and searched 7 zip and it just added it to the default program as a part of it instead of having to install a seperate program. Not sure if thats what you wanted to hear though. sorry.

The way I did it was by going to "Add and Remove Programs."  From there I checked on 7Zip, and clicked "Apply" to have it installed.  Should I have done it instead through the Synaptic Manager?

Thanks.

---

### Post by Sukarn on 2008-05-15
Yeah, 7zip gets added as an option in the default program.

---

### Post by DarkSaga70 on 2008-05-15
not sure if that makes a difference or not but I used synaptic so it cant hurt to try it :)

---

### Post by Rhubarb on 2008-05-15
Installing p7zip and / or pzip-full gives full support for 7zip archives in the archive manager program.
This way you can open a 7zip archive, and you can also create 7zip archives easily with the same archive manager.

So p7zip and p7zip-full are just plugins to achive manager to allow it to deal with 7zip archives easily.

---

### Post by lisar915 on 2008-05-15
> Installing p7zip and / or pzip-full gives full support for 7zip archives in the archive manager program.
This way you can open a 7zip archive, and you can also create 7zip archives easily with the same archive manager.

So p7zip and p7zip-full are just plugins to achive manager to allow it to deal with 7zip archives easily.

So then does it matter that I installed 7zip without using the Synaptic Manager?

---

### Post by alexandremrj on 2008-05-15
Add/remove and synaptics are only tho different graphical interfaces for the management of software, so they can be called the same thing.

If you want to associate a kind of file with a particular program just go to the file, righ click and select "Properties"

Then press add and there will be a list of programs to choose. Just select the program you want and you're good to go.

P.S:With the right click and "Open with another application" you only change the program for this specific time, it doesn't become default.

---

### Post by Sukarn on 2008-05-15
> **alexandremrj said:**
> If you want to associate a kind of file with a particular program just go to the file, righ click and select "Properties"

Then press add and there will be a list of programs to choose. Just select the program you want and you're good to go.

P.S:With the right click and "Open with another application" you only change the program for this specific time, it doesn't become default.

That seems completely offtopic.



Anyway, back on topic, I think 7zip from Add/Remove installs p7zip-full.
Just right click the file(s) you compress with 7zip, click "Create Archive" and then select .7z from the drop down box.

---


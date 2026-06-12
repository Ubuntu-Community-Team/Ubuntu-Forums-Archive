---
title: "Python: Resources"
date: 2010-12-20
forum: Programming Talk
---

### Post by Sailor5 on 2010-12-20
Greetings!

So I'm making a PE executable file in Python destine for Windows. When finished the user of such will enter two short strings of data that we will need to store _inside_ of the executable file. Here is my method so far.

[http://d.imagehost.org/0928/Screenshot-6.png](http://d.imagehost.org/0928/Screenshot-6.png)

The file will already come with a text resource that we'll overwrite with the users entered data when given. As we can see from the picture this is the default text resource. When the users entered their two strings we'll open a handle to the executable file and replace the default string to incorporating the newly entered users details.
```
fp = open('Stuff/bin.exe','rb');info = fp.read();fp.close()
info = info.replace('<0161DATA1#DATA20161>','<0161'+str(input1)+'#'+str(input2)+'0161>')
nfp = open('Done.exe','wb');nfp.write(info);nfp.close()
```However here's the problem. There are 21 characters in the `<0161DATA1#DATA20161>` string. If we where to try and put the word 'www.ubuntuforums.org' into the DATA1 field here's the outcome.
```
<0161www.ubuntuforums
```Because we've breached the 21 character limit it no longer allows us to add more characters. So my question is how can we get past this dilemma or is there a better way to add/edit text resources in Python?

Thanks Bye!

---

### Post by DaithiF on 2010-12-20
> **Sailor5 said:**
> that we will need to store _inside_ of the executable file.
Why, why why?  

I hope you have a really good reason for needing to store something** inside **the binary??  Otherwise this is so wrong I don't know where to begin ... a python script containing code to perform on-the-fly modifications to the future binary .exe that its going to be py2exe'd into... sorry but thats kinda crazy.

---

### Post by Sailor5 on 2010-12-20
We can split this into two divisions. The Child executable which is the one where we store the text resource [when ran it will read the resource and perform actions accordingly] and the parent application which opens the Child to add the user defined data. 

It's imperative that everything needed for the Child is stored within itself so there is only one singular file to deploy for the user. Instead of having multiple files with different information stored in them. There's only two small strings that the user has to enter and the only way I can think of to store them is inside the Child file as a resource. Then we get the problem above. If there's anything else you want me to explain further do tell me.

---

### Post by Reiger on 2010-12-20
What's wrong with:
- here's an archive with executable & resources,
- you extract it somewhere,
- you run the executable
- the executable finds the resources relative to itself
- ??
- profit! :p

---

### Post by raydeen on 2010-12-23
Or have the executable check for the presence of the data file in the same folder when it loads up. If if finds it, it can read it in, the user can modify it, and then have it written back out to the disk. If it's not found, the program could simply create a new file object that could be written out when the user is done modifying it.

---


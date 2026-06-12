---
title: "Python Help! Add To File"
date: 2006-07-04
forum: Programming Talk
---

### Post by noob_Lance on 2006-07-04
Hey,

I need help with a program im working on. I need to append text to a file. The following is the code im using... but it dosnt want to seem to work for me.

```

def AddImage(name, image):
	myFile = open("/home/"+user+"/.vangogh/"+name+"/"+name, "a+")
	myFile.write(image+"\n")
	myFile.close()
	print "Image Added"

```

I get no errors when execute this code. Anyone please help. 

thanks
~Lance

---

### Post by thumper on 2006-07-04
How do you know that it isn't working?

Aside: look at os.path.join:
```

  filename = os.path.join('/home', user, '.vangogh', name, name)

```
Did you mean for name to be there twice?

Also, just open in append mode 'a', you don't need the + as you are not reading and writing.

---

### Post by noob_Lance on 2006-07-04
i know its not working because after i try to use the function... i get no print statement (so it causes an error but dosnt show it) and i check the file and it dosnt add the new image into the file.

ill try again with "a" not "a+"..

~Lance

oh and the os.path.join... it wont make a difference. i use the same structure to create and read from the file... but appending dosnt work.

---


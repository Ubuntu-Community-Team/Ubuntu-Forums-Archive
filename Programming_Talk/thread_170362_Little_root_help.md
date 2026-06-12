---
title: "Little root help"
date: 2006-05-04
forum: Programming Talk
---

### Post by Drakx on 2006-05-04
Hi

Im doing a little shell scripting and so far its all been good and fun till i wanted root access :confused: Ive googled around and must have asked the wrong question cause what i got back was not the answer ive been looking for, all i want is to get root access via the script so the end user can run say drakx.sh and the script asks the user for the root password so the script can do all it needs to :)

What ive done so far is some thing like this...

```
echo -n "Please enter your root password: "
read rootPass
sudo
```

Thats one way i've taken it and here is the other

```
sudo
echo -n "Please enter your root password: "
read rootPass

```

So any help at all would be great 

Thanks.

---

### Post by neouser99 on 2006-05-04
is this really necessary? just have the script check if root is running it, and if it is not root, output and error telling the user to run the script with
```
sudo script.sh
```

-neo

---

### Post by cgjones on 2006-05-04
```

sudo *command you want to run*

```

Put this in your script, by itself, and it should work.

---

### Post by Drakx on 2006-05-04
Yes the asking for root is required else i would not ask, also sudo command i wanna run defeats the whole point of the script, but thanks any way.

Any one else

---

### Post by neouser99 on 2006-05-04
im not trying to be mean here or anything, but what are you trying to do? you are being really vague and being vague when asking how to gain root access on a box is not something that people will jump at answering.

if some of your script needs root, nothing will break if all of it has root.

-neo

---

### Post by cgjones on 2006-05-04
Yeah, I was a little puzzled myself.  Putting sudo followed by the command directly into the script will prompt the user for the password. Isn't that what you wanted?

---

### Post by Drakx on 2006-05-04
[QUOTE=cgjones]Yeah, I was a little puzzled myself.  Putting sudo followed by the command directly into the script will prompt the user for the password. Isn't that what you wanted?[/QUOTE]


I did try that but for some strange reason would not ask  for the root password, guess im gonna go back and take another look, i know i can use gksudo but this script is for a server so thats outta the question :), i dont mean to be vauge but im gonna :). When its done and ive tested ill post it as its the first "real useful" shell script ive done im slightly consious about it :D

---


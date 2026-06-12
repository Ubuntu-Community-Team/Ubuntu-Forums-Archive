---
title: "Read/write permissions"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by cowabungabruce on 2008-05-21
I am trying to load a program with these directions:

  "For the server part, you'll need both "uinput" and "joydev" modules.
Make sure to have read/write access on "/dev/misc/uinput or /dev/input/uinput or /dev/uinput" devices."

so I edited modules on boot:
sudo gedit /etc/modules

and added "uinput" and "joydev" to the list.

Now I don't know how to change permissions on those three files.

On a completely different note; compiz-fusion and emerald work perfect for me if after I log in i type:

SKIP_CHECKS=yes compiz --replace

and

emerald --replace

in the terminal. I want this to happen automatically on boot. I put both of those commands in "Sessions Manager" but it just boots to metacity. Am I missing something?

Thanks in advance for the help. (I'm on 8.04 if that makes any difference)

---

### Post by neurostu on 2008-05-21
The standard way of editing permissions is as follows:

Make readable, wtitable, executable. This is only for yourself.
```

chomd +r filename
chmod +w filename
chmod +x filename

```
If you want to allow other people to read and write you have use another method:
```

chmod XYZ filename

```
where X Y & Z 
```

X = your own permissions
Y = your group's permissions
Z = anybody else's permissions

```
where:
```

4 - Read
2 - Write
1 - Execute

```
so if you do:
```

chmod 444 filename

```
You, your group, and everybody can read the file. 
To give read and write access you can add 4 and 2 for 6
```

chmod 666 filename

```
to make it so you can read, write, execut but others can only read and execute
```

chmod 755 filename

```

---

### Post by 50words on 2008-05-21
How do you change permissions for a specific group?

Say my username is jim, and I want to allow read/write/execute access to a file and its contents for group jerks. How would I use chmod to set permissions recursively?

---

### Post by neurostu on 2008-05-21
If you had a folder named foo and you wanted to give yourself and your group: Read, Write, Execute access to it all all subfiles and folders while prohibiting access from all others folders you would type:
```

chmod -R 770 foo

```
The manual entry does a good job explaining chmod
```

man chmod

``` 
or go here: [http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

---

### Post by 50words on 2008-05-21
I didn't realize that a file/folder can only be owned by one user and one group at a time.

---


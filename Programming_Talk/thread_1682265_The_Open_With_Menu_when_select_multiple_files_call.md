---
title: "The Open With Menu when select multiple files calls multiple times my program?"
date: 2011-02-05
forum: Programming Talk
---

### Post by hakermania on 2011-02-05
Ok, so, when I select a lot of my app's project files and I select Open With 'myapp' the system calls:
```

myapp path/to/the/project/file1
myapp path/to/the/project/file2
myapp path/to/the/project/file3

```You understand that this is a big problem, especially when you don't want multiple instants of your application, and I don't want either! So, when I do this, I get 'N' number of messages telling me that the process is already running, where 'N' is the number of project files I selected to open!
The thing is, that my program has the option to open multiple files very well and handle them with ease, but you have to use:
```

myapp path/to/the/project/file**1** path/to/the/project/file**2** path/to/the/project/file**3**

```and not multiple instants of 'myapp'.

How can I set this by default? Has it to do with the mime-type? Because it is a new mime-type that opens by default with 'myapp'.
I've coded the program in C++ (with QtCreator), so I don't know if I can handle this from there, I've tried when opening the program to write to a file if it has arguments (so you have selected a project file to open), then the second instance will see this file and send a Dbus message to the already running one with the path to the other project etc, but this doesn't work because all these instances are called concurrently with such a speed that you can't do anything!

So, any suggestion deeply appreciated!:popcorn:

---


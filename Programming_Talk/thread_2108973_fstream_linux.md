---
title: "fstream linux"
date: 2013-01-26
forum: Programming Talk
---

### Post by luckyisdog on 2013-01-26
Working in Eclipse and the program uses fstream to open file

[HTML]fstream filenames("server_drawing_filenames.txt", fstream::in);[/HTML]

Then it says "No such file or directory"

I tried running it using sudo, still wouldn't work. I put server_drawing_filenames.txt in /Debug/ or wherever the binary was located. Still doesn't work.

I've tried "\server_drawing_filenames.txt" and "/server_drawing_filenames.txt"

What could be the problem?

---

### Post by dwhitney67 on 2013-01-26
> **luckyisdog said:**
> 
What could be the problem?
The file you are attempting to open is not located on the same directory as the executable program that you are running.

Perhaps if you depended less on Eclipse, and more on your ability to run the program from a terminal (ie a console or command line), this solution to the issue will become more apparent.  An IDE will not make you are better programmer!

---

### Post by luckyisdog on 2013-01-26
Yeah that's true. Compiling from the terminal would be much better for the experience and understand what could be the problem.

I do see that the binary and "server_drawing_filenames.txt" are located in the same folder.

Here is a snapshot

[http://i.imgur.com/PW7354M.png](http://i.imgur.com/PW7354M.png)

---

### Post by dwhitney67 on 2013-01-26
Then check the file permissions on "server_drawing_filenames.txt" to ensure that you have, at a minimum, read permissions.

Btw, the following statement in your C++ program will not spit out any message indicating "No such file or directory".
```

fstream filenames("server_drawing_filenames.txt", fstream::in);

```
Perhaps you should also post the code following the fstream statement so that it can be verified that you are properly checking the results of that statement.

---

### Post by SledgeHammer_999 on 2013-01-26
1. Open a terminal
2. Use "cd" command to navigate to the binary folder
3. Run your binary with:
```
./<binary name>
```

Does it work now?

---

### Post by luckyisdog on 2013-01-26
Using cd to directory and using ./drawdown_server

now perror shows "Not a directory" instead of "No such file or directory"

I've checked the ls permissions of the txt file and it says -rw-r--r--

[HTML]fstream filename_opener("server_drawing_filenames.txt", fstream::in);

    if(filename_opener.is_open()){
      cout << "File is open << endl;
    }else{
        perror("file");
        cout << "Could not open server_drawing_filenames.txt!" << endl;
    }[/HTML]

---

### Post by luckyisdog on 2013-01-26
Ah! No need to scratch your heads anymore.

Instead of [HTML]fstream filenames("server_drawing_filenames.txt");[/HTML]

I should've declared and used open.

[HTML]fstream filenames;
filenames.open("server_drawing_filenames.txt");
[/HTML]

Did also require launching the binary using "./"

---

### Post by SledgeHammer_999 on 2013-01-26
FYI, it shouldn't make a difference either way.

---

### Post by dwhitney67 on 2013-01-26
> **luckyisdog said:**
> Ah! No need to scratch your heads anymore.

Instead of [HTML]fstream filenames("server_drawing_filenames.txt");[/HTML]

I should've declared and used open.

[HTML]fstream filenames;
filenames.open("server_drawing_filenames.txt");
[/HTML]


That shouldn't make a difference.

You could have also done...
```

fstream filenames("server_drawing_filenames.txt", fstream::in);

if (filenames)    // here the fstream object gets converted to a bool using the operator bool() method associated with fstream
                  // the bool() method returns the status of good()
{
    cout << "File is open." << endl;
}
else
{
    cerr << "Unable to open file." << endl;
}

```

---

### Post by luckyisdog on 2013-01-26
Yeah I found it strangely odd that that method worked while the other didn't!

---


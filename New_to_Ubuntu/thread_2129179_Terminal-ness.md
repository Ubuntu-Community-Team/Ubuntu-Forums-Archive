---
title: "Terminal-ness"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by emanmcdow on 2013-03-25
Soooooo, I really enjoy using terminal, but I feel I haven't learned everything there is to know about it. I know a lot of the basic stuff (ping, sudo apt-get install/update/upgrade , cd, ls, pwd, cowsay, etc) are there any other commands i should know to be fluent with in terminal? Also, is there something like Batch files but for terminal?

---

### Post by deadflowr on 2013-03-25
Did you look at the sticky

[http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

---

### Post by Lars Noodén on 2013-03-25
The link mentioned above goes to some good resources.  I would highly recommend figuring redirects and pipes into your self-study curriculum.  They really bring the power of the shell to the forefront  even if you can only recall a few programs off the top of your head.  sed and awk are useful, too.

---

### Post by Lars Noodén on 2013-03-25
If you want a print book to look at, here is a review of one that would be relevant:

[http://books.slashdot.org/story/13/03/25/1339229/book-review-a-practical-guide-to-linux-commands-editors-and-shell-programming](http://books.slashdot.org/story/13/03/25/1339229/book-review-a-practical-guide-to-linux-commands-editors-and-shell-programming)

---

### Post by Kopkins on 2013-03-25
One thing I find very useful is tab completion. When typing into a terminal it's important to be accurate. When typing for example a file name start with the path and then press tab to complete the path. For example ```

$ ls Doc <TAB>
      #changes to 
$ ls Documents/
      #or 
$ ls D <TAB>
      #nothing happens
     <TAB> #again lists possible completions
$ ls D <TAB> <TAB>
      Documents/ Downloads/ Desktop/

```

Using this , it improves your accuracy as you move from directory to directory helping to avoid typos. It can also help speed up changing directories or typing out long file paths. It also automatically escapes characters like '?,!' and whitespace, " " in filenames. 

```

$ ls
backlight  hdmi  openbox-pypanel.sh  update-git  document 1
# the contents of a directory

#the cat command can output the contents of a file.
#pretend you want to `cat' document 1

$ cat document 1
cat: document: No such file or directory
cat: 1: No such file or directory

# cat sees those as two files, so you have to tell it that its all one filename by escaping the space with the "\" character

$ cat document\ 1
 contents of document 1

#or 

$ cat doc <TAB>

#changes to 

$ cat document\ 1
contents of document 1

```

Like stated above, read the sticky post about it. 

Scripting is also nice to be able to do, it can help speed up more complicated processes that you do often. And it's fun!

Best of luck
Kopkins

---

### Post by NetworkNerd7 on 2013-03-25
The ubuntu/linux version of a windows batch file is a .sh (shell) script.

To run an sh file: [(sudo)] sh (filename).sh

For example:

sudo sh myscript.sh

---


---
title: "Home Folder"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Zotick on 2008-05-03
I moved my home folder into my desktop, then my trash, and it wont let me delete it from my trash. What can I do?

---

### Post by Rocket2DMn on 2008-05-03
What do you mean you moved your home folder to your desktop and now you're trying to delete it?  Are you trying to get rid of that username?  That folder should be under /home - you should move it back from the trash immediately otherwise you are going to break your system.

---

### Post by Zotick on 2008-05-03
No, I was trying to do something stupid. So I went to my application list then dragged the home folder section onto my desktop, then later I wanted to delete it, So I did then it went to my trash, then I try deleting it from my trash, and it wont allow me.

---

### Post by macaholic on 2008-05-03
Well you can delete it by typing```
sudo rm -r ~/.local/share/Trash/files/<name of directory or file>
```in terminal

---

### Post by Zotick on 2008-05-03
I tried that, and I got this syntax error:


 bash: syntax error near unexpected token `newline'

---

### Post by macaholic on 2008-05-03
Well that's because you left the "<>" remove them, I use those to show that you have to enter soemthing specific. Sorry for the confusion.

---

### Post by tjwoosta on 2008-05-03
```

cd .local/share/Trash/files

``` 
then

```
 
sudo rm -rf filename

```

---

### Post by macaholic on 2008-05-03
> **tjwoosta said:**
> ```

cd .local/share/Trash/files

``` 
then

```
 
sudo rm -rf filename

```
That will only work if he was logged in as root, in which case he wouldn't have this problem. He would need to be in ~/.local/share/Trash/files, just as I said in my posts.

---

### Post by Zotick on 2008-05-03
Stupid of me, I cant delete it because I named the file as [ Area ] 

When I put the command in the terminal it says it cant find the file. Is there anyway I can rename it on my trash?

---

### Post by armitage1337 on 2008-05-03
That's because the terminal doesn't recognize the characters "[", "]", or " " unless you prepend them with a "\", since those are control characters in the terminal. You would do ```
rm \[\ Area\ \]
``` to remove it.

---

### Post by tacutu on 2008-05-03
Try this:
rm -rf \[\ Area\ \]

---

### Post by Zotick on 2008-05-03
I tried it and it doesnt work:

[IMG]http://i27.tinypic.com/scqsz6.png[/IMG]

---

### Post by Zotick on 2008-05-03
Do you know what the problem is?

---

### Post by tjwoosta on 2008-05-04
ok do this exaclty like this
```

cd ~/.local/share/Trash/files

```

then **while in the directory named ~/.local/share/Trash/files** do this

```

sudo rm -rf \[\ Area\ \]

```

i noticed that in the above images you are still in the ~/ directory, if you were to run the rm -rf command there it would delete the wrong one!

---

### Post by Zotick on 2008-05-04
Thank you!

---

### Post by macaholic on 2008-05-04
Just an explanation for why it complains when you tried to remove the directory with jsut rm, rm by itself is just for files, you have to add the -r option (recursive) to have it remove directories.

---


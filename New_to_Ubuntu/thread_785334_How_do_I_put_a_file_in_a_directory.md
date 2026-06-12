---
title: "How do I put a file in a directory?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Carnivorum on 2008-05-07
Bs'd

I have 2 files on my desktop, and I want to put them into a directory. 

How do I do that?

I already made the directory, I only don't know how to move the files to there.

---

### Post by TeoBigusGeekus on 2008-05-07
Right click them->Cut 
and then Paste them in the directory you wanna put them.

---

### Post by Carnivorum on 2008-05-07
Bs'd

As far as I know, that directory only exists in the console.  So how can I paste something into the console?

---

### Post by glennric on 2008-05-07
From the terminal you can type
```
mv filename path/to/newlocation
```

Although, any files that exist are available both from the terminal and nautilus.

---

### Post by Joeb454 on 2008-05-07
Do this in a terminal ```
cd ~/Desktop
mv ./<filename> ~/<directory>
```

Where <filename> is the name of the file, and <directory> is the name of the directory you want to move it to (assuming it's in your home folder).

Also remember that Linux is case sensitive :)

---

### Post by TeoBigusGeekus on 2008-05-07
> **Carnivorum said:**
> Bs'd

As far as I know, that directory only exists in the console.  So how can I paste something into the console?

Could  you be a bit more descriptive regarding your problem?

---

### Post by Carnivorum on 2008-05-07
Bs'd

I'm making progress.  I'm now in that directory, together with those 2 audio files

I connected them together, it were 2 parts of large song which couldn't be sent in one shot by email. 

Now I want the song out of that directory, back to my desktop, so I can put it in amerok and other things. 

How do I do that?

---

### Post by TeoBigusGeekus on 2008-05-07
```
mv filename ~/Desktop
```

---

### Post by Carnivorum on 2008-05-07
Bs'd

I'm now in the directory poetpendulum.

When I do there "ls", I get:  

Poet.mp3aa  Poet.mp3ab  The Poet And The Pendulum.mp3

Then I do:  mv The Poet And The Pendulum ~/Desktop, and then he tells me:  

`The': No such file or directory

---

### Post by AndrewTheArt on 2008-05-07
> **Carnivorum said:**
> Bs'd

I'm now in the directory poetpendulum.

When I do there "ls", I get:  

Poet.mp3aa  Poet.mp3ab  The Poet And The Pendulum.mp3

Then I do:  mv The Poet And The Pendulum ~/Desktop, and then he tells me:  

`The': No such file or directory
When referring to filenames with spaces on the terminal, you need to put it it quotes. Otherwise, it takes each individual space separated word as a different argument. 

Try - 

```
mv "The Poet And The Pendulum.mp3" ~/Desktop
```

---

### Post by Carnivorum on 2008-05-07
Bs'd

Somebody told me to put the "poet and the pendulum" between inverted comma's, and now it worked. 

Thanks everybody for your help.

---

### Post by muteXe on 2008-05-07
What does "Bs'd" mean?

---

### Post by TeoBigusGeekus on 2008-05-07
Try
mv "The Poet And The Pendulum".mp3 ~/Desktop

---

### Post by Joeb454 on 2008-05-07
You don't **have** to use quotes. You can also se a backslash followed by a space (i.e. "\ " though without quotes ;))

Just letting you know the other options available :p

---

### Post by Joeb454 on 2008-05-07
> **muteXe said:**
> What does "Bs'd" mean?

I was also wondering this ;)

---

### Post by tetsuc on 2008-05-07
apparently it means "with the help of heaven". who knew... learn something new every day :)

(referred to here: [http://yeshuaministries.tripod.com/BS-D.htm](http://yeshuaministries.tripod.com/BS-D.htm))

---

### Post by Carnivorum on 2008-05-07
Bs'd

The above is an abbreviation of the Aramaic expression: Ba siata desmaya, and that means: With the help of heaven.

---

### Post by AndrewTheArt on 2008-05-07
> **Joeb454 said:**
> You don't **have** to use quotes. You can also se a backslash followed by a space (i.e. "\ " though without quotes ;))

Just letting you know the other options available :p
But that's highly annoying :)

---

### Post by t0p on 2008-05-07
> **AndrewTheArt said:**
> When referring to filenames with spaces on the terminal, you need to put it it quotes. Otherwise, it takes each individual space separated word as a different argument. 

Try - 

```
mv "The Poet And The Pendulum.mp3" ~/Desktop
```

**Or** you can use the "escape character", \, like this:
```
mv The\ Poet\ And\ The\ Pendulum.mp3 ~/Desktop
```

Incidentally, earlier you said that a particular directory *only exists in the console* and not in Nautilus.  This is incorrect.  In the console, input the command
```
ls
```
and you'll get a list of directories and files in your Home directory, right?  Now, click on **Places > Home Folder** and the gui will show you the contents of your Home directory.  Compare this to the list you got in console - they're the same, yeah?

Well they *should* be the same anyway...

---

### Post by xzero1 on 2008-05-07
There are some tuturial videos you may be interested in.
See [http://screencasts.ubuntu.com/]("http://screencasts.ubuntu.com/")

---


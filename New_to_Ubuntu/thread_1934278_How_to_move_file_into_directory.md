---
title: "How to move file into directory?"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by jrw93 on 2012-03-01
Hello All,

I just took the plunge today and installed ubuntu, and am learning how to use the terminal. I have some basic commands down such as moving directories and copy/pasting and opening files/documents.

I, however, do not understand the mv command. I thought this was supposed to mv your document to a particular directory?

For instance, I have a file called text on my desktop, and a directory called Onetime

If I enter mv text Onetime, it just renames my text to Onetime. What is the line to move text INTO Onetime, not just rename it? I've tried researching it.. can't really find a answer.

Please help me in my transition from Windows to Ubuntu a little easier! Thanks!!!

---

### Post by papibe on 2012-03-01
Hi jrw93.

If the second argument does not exists 'mv' acts as rename.

I have a couple of guesses why is not working for you:

[LIST=1]
[*]Onetime is not located in the same directory where you are running the 'mv' command. If that is the case, you may need to address Onetime using either a relative path (like ../Desktop/Onetime) or an absolute path (like /home/youruser/Desktop/Onetime).
[*]Another reason could be that the actual name is not Onetime, but something similar, and you are missing it by just a bit.
[/LIST]
In any case, the best tool you can use is autocompletion, start writing the destination and press tab, so it is complete your sentence. It may require several letters to be type before the autocompletion works, but it works not only with files, but with paths too.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by CidNight on 2012-03-01
> **papibe said:**
>  the best tool you can use is autocompletion, start writing the destination and press tab, so it is complete your sentence. It may require several letters to be type before the autocompletion works, but it works not only with files, but with paths too.


Wow, thanks for that tip - autocompletion is awesome!

---

### Post by jrw93 on 2012-03-01
Humm.. I think I'm in the right directory. Here is what I am typing. Both Onetime and Test are in my Desktop directory.

jack@jack-laptop:~$ cd Desktop
jack@jack-laptop:~/Desktop$ ls
Onetime  Test
jack@jack-laptop:~/Desktop$ mv Test ~/Onetime
jack@jack-laptop:~/Desktop$ 

However, the document Test gets renamed to Onetime and sent to my Home directory. I have NO idea how this is happening, any ideas?

---

### Post by athampan on 2012-03-01
The tilde specifies home directory.  So if your home directory is /home/user, your file Test lives in /home/user/Desktop and when you issue your command, it moves the file to /home/user/Onetime.

You command should be:

```
cd Desktop
mv Test ./Onetime

```

The "." specifies current directory

---

### Post by lswb on 2012-03-01
> **athampan said:**
> The tilde specifies home directory.  So if your home directory is /home/user, your file Test lives in /home/user/Desktop and when you issue your command, it moves the file to /home/user/Onetime.

You command should be:

```
cd Desktop
mv Test ./Onetime

```

The "." specifies current directory
In this instance the "./" is not necessary. "mv Test Onetime" will work provided both the file "Test" and the directory "Onetime" are in the current directory.

---

### Post by jerome1232 on 2012-03-01
> **jrw93 said:**
> Humm.. I think I'm in the right directory. Here is what I am typing. Both Onetime and Test are in my Desktop directory.

jack@jack-laptop:~$ cd Desktop
jack@jack-laptop:~/Desktop$ ls
Onetime  Test
jack@jack-laptop:~/Desktop$ mv Test ~/Onetime
jack@jack-laptop:~/Desktop$ 

However, the document Test gets renamed to Onetime and sent to my Home directory. I have NO idea how this is happening, any ideas?

that's because ~/Onetime means /home/yourusername/Onetime, if you wanted it to goto your desktop you would either do it as athampan said or use ~/Desktop/Onetime

---

### Post by jrw93 on 2012-03-02
Thanks for your help guys! It worked!

I was in my Desktop directory, and entered:

mv Test Onetime 

And that automatically moved my Test filed into the directory Onetime!

However -- I tried moving Test file from the directory Onetime to Desktop again.. but it just renamed it to desktop. I'm not sure what is going on here, as I am sure I am in the onetime directory.

When inside the Onetime directory, I entered mk Test Desktop

Does anyone know why this is happening?

---

### Post by Derek Karpinski on 2012-03-02
You're using relative paths instead of absolute paths.

Type:
```
pwd
```

to find your current directory.

[http://www.youtube.com/watch?v=M3JirqAPg9g](http://www.youtube.com/watch?v=M3JirqAPg9g)

[http://www.linuxquestions.org/questions/linux-general-1/absolute-and-relative-paths-256350/#post1300222](http://www.linuxquestions.org/questions/linux-general-1/absolute-and-relative-paths-256350/#post1300222)

---

### Post by jerome1232 on 2012-03-02
edit: misread post ignore

---


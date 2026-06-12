---
title: "ubuntu can't recognize javac command"
date: 2006-09-17
forum: Programming Talk
---

### Post by raul_ on 2006-09-17
Hi there. 
I installed the latest SDK (6) on my computer via the .bin file on the official page. everythinh went ok, i extracted the .bin file into the /usr/local directory, and it created a jdk1.6 dir (or something like that). I did a simple hello world to test the java compiler, and then i typed "javac file.java"   but the javac command wasn't recognized. I did man java but the only thing that popped up was something about "gij". Anyway, can any1 help me with that? i know the compiler comes with the SDK

---

### Post by kidders on 2006-09-17
Hi there,

If **whereis javac** doesn't show it up for you, then it's not installed (or at least, not in the right place!). Check that you've installed the right thing, that the install was error-free and then close and re-open your terminal window, just to be sure.

By the way, how come you didn't use Ubuntu's java packages? Do you *really* need version 6?

---

### Post by raul_ on 2006-09-17
Hey thanks for your reply =)
Here's what came  up
```

root@raul:/home/raul # whereis javac
javac:

```

And my answer: yes i do...actually i need 1.5 because that's what i'm using in college, but i chose to install this one.

---

### Post by kidders on 2006-09-17
Hmm, well javac wasn't installed anywhere sensible by the installer :-( you can, of course, go looking for it... **updatedb && slocate javac** or something like that, maybe.

It's been a long time since I downloaded Java directly from Sun ... is their installer debian-friendly?

---

### Post by raul_ on 2006-09-17
it's a bin file...i did what u said:
```

root@raul:/home/raul # updatedb && slocate javac[CODE]
```
/usr/share/vim/vim63/syntax/javacc.vim
/usr/share/vim/vim63/compiler/javac.vim
/usr/local/jdk1.6.0/bin/javac
/usr/local/jdk1.6.0/man/man1/javac.1
/usr/local/jdk1.6.0/man/ja_JP.eucJP/man1/javac.1
/windows/Os meus documentos/Fac/Java/tutorial/figures/getStarted/javac-mac.gif
/windows/Os meus documentos/Fac/Java/tutorial/figures/getStarted/javac1.gif
/windows/Os meus documentos/Fac/Java/tutorial/figures/getStarted/javac2.gif
/windows/Os meus documentos/Fac/Java/tutorial/figures/getStarted/javacicon-mac.gif
root@raul:/home/raul #
[/CODE]

---

### Post by raul_ on 2006-09-17
Hey man...i'm sorry i must be very slow (hey it's 1 AM give me a break =)   )
so what u're saying is for me to create an alias to the location where javac is located? i'll try that anyway =) thanks man u rock

EDIT: editing the ~/bashrc file worked. just one more thing...do i have to edit ALL the commands? because when i type "java something.class" it works, but i don't know if it's using the latest application, or the old one =\ if so...is it safe to remove the old one? (by aptitude or something)
And without using an alias, how can i make my "javac" command the DEFAULT one? (without having to modify the bashrc file)
I hope i'm not being a pain in the a** #-o

---

### Post by kidders on 2006-09-18
Yep, I guess you could try that. I'm not 100% certain it would work though, since all the files your installer put on your system are probably in non-standard locations.

```
ln -s /usr/local/jdk1.6.0/bin/javac /usr/bin/javac
```

The other possible approach would be, like you said, to edit your .bashrc, adding some additional locations to your search paths.

> i don't know if it's using the latest application, or the old one

Having more than one version of Java on your computer at the same time can get confusing, if you don't completely understand how both it and your system go about looking for class libraries, etc. If you take off Ubuntu's JRE though, you might have to reconfigure your web browsers, etc. to cooperate with your funny new install.

---

### Post by hod139 on 2006-09-18
Mu guess is that you want to do something like this (untested):
```

sudo ln -sf /usr/local/jdk1.6.0/jre/bin/java_vm /usr/bin/java_vm
sudo update-alternatives --install /usr/bin/java java6 /usr/local/jdk1.6.0/bin/java 1

``` This should hopefully add this version of java to the update alternatives list (as java6):
```
update-java-alternatives -l
``` If it is there, you should then be able to do:
```
sudo update-java-alternatives -s java6 
```

Again, this is untested and may not be 100% correct, but it is the basic idea anyway.

---

### Post by raul_ on 2006-09-18
First of all thanks for ur replies =)

That's something my professors would like (interesting solutions i mean) but i think it's just easier to remove ir and reinstall it on the place it's supposed to be installed (again, that's just what i think). the problem is...i don't know what the path is =\  help me out in this:
download the .bin file from the sun homepage, put the file in the dir i want to install it (extract it) and do it, and luckily, if i do it in the right place, i won't have problems. the only that's missing is the dir where i'm suppose to install it. 

Another thing, i checker my packages and i think that my "java" command uses the Java Runtime with GIJ. I think it's safe to remove it right?

---


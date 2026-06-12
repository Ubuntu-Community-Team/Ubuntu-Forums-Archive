---
title: "Problem with Ruby Eclipse"
date: 2007-05-23
forum: Programming Talk
---

### Post by BigDH01 on 2007-05-23
So I just installed the ruby plugin for eclipse as per these instructions:

[Here]("http://beans.seartipy.com/2006/08/12/develop-ruby-applications-using-eclipse-ide/")

It appears to be working, I can create a Ruby project and run a .rb file as a Ruby application.  However, nothing works. Even doing something as simple as puts "hello world" won't show anything on the eclipse console.  I went to a Konsole and ran ruby testfile.rb which is also very simple and I get nothing on the console.

Here are the results of a ruby -v:

ruby 1.8.4 (2005-12-24) [i486-linux]

I need to get this working for work.  I appreciate any help!!

---

### Post by finer recliner on 2007-05-24
i appear to have a later version of ruby installed. i'm running feisty. see if you can upgrade.

```

$ ruby -v
ruby 1.8.5 (2006-08-25) [i486-linux]


```

---

### Post by Ubuntist on 2007-05-24
finer recliner (or anybody else), are you able to us Eclipse's debug feature on Ruby code?  Whenever I try, I get an error message saying
> Specified executable rdebug-ide does not exist for usr

---

### Post by finer recliner on 2007-05-25
sorry i dont use eclipse. i just do:

```

$ruby filename.rb

```

and all is well (until i get my first runtime error :-P )

---

### Post by Ubuntist on 2007-05-30
Thanks for the reply, finer recliner.

FWIW, I think I've solved my problem: see  [_this thread_.]("http://ubuntuforums.org/showthread.php?t=428477")

---


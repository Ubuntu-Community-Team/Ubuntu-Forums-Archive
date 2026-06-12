---
title: "[SOLVED] Rails 1.2.6 on Ubuntu 8.10 : my nightmare..."
date: 2009-01-01
forum: Programming Talk
---

### Post by skaboss on 2009-01-01
Hello,

I installed ruby and rubygems via aptitude.
Everything seems ok.
I need rails 1.2.6, so i can't install it via aptitude (it would install rails 2.0).
I typed ```
 sudo gem install rails -v 1.2.6
```
and got the resulting 
```
Successfully installed rails-1.2.6
1 gem installed

```

But if i want to run rails, here is what i get : 
```
$ rails testproject
bash: /usr/bin/rails: No such file or directory

```

Can someone help me please ?

---

### Post by skaboss on 2009-01-01
My apologies : i got the answer on the rails site : 

I just had to do 

```
 export PATH=$PATH:/var/lib/gems/1.8/bin

```

---


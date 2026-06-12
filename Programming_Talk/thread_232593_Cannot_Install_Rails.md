---
title: "Cannot Install Rails"
date: 2006-08-08
forum: Programming Talk
---

### Post by PeopleEater on 2006-08-08
I've been trying to install Ruby on Rails through Rubygems but it will not work, it says that it cannot find a dependency and I'm stuck. I would really apreciate if someone could tell me how to either fix this problem or install another way.

```
garrett@ubuntu:~$ sudo gem install rails
Install required dependency activesupport? [Yn]  y
ERROR:  While executing gem ... (Gem::GemNotFoundException)
    Could not find activesupport (= 1.3.1) in the repository

```

---

### Post by PeopleEater on 2006-08-08
Of coarse 5 minutes after I make this post the exact command runs perfectly. It never fails... :o

---

### Post by giacomolg on 2006-08-09
My problem at the moment is this

> giacomo@ubuntu:~/Downloads/rubygems-0.9.0$ sudo gem install rails
Install required dependency actionpack? [Yn]
ERROR:  While executing gem ... (Gem::GemNotFoundException)
    Could not find actionpack (= 1.12.4) in the repository


Even on rubyforge the newest actionpack's version is  [1.12.1]("http://rubyforge.org/frs/?group_id=249&release_id=4816")

Anyone experiencing the same issue?

Bye

---

### Post by asimon on 2006-08-09
> **giacomolg said:**
> 
Anyone experiencing the same issue?

Yes, the same here and several people at the [Rails mailing list](http://www.ruby-forum.com/topic/76584#new) expierience the same. Probably something fishy the the gem index.

---

### Post by giacomolg on 2006-08-09
> **asimon said:**
> Yes, the same here and several people at the [Rails mailing list](http://www.ruby-forum.com/topic/76584#new) expierience the same. Probably something fishy the the gem index.
Oh, I see. Not with much surprise, now I get another error again:

giacomo@ubuntu:~$ sudo gem install rails
Install required dependency actionpack? [Yn]  y
[I]ERROR:  While executing gem ... (OpenURI::HTTPError)
    404 Not Found[/I]

Is there any alternative way of installing RoR on Ubuntu Dapper?

ThanX:D

---

### Post by boredandblogging.com on 2006-08-10
> **giacomolg said:**
> Oh, I see. Not with much surprise, now I get another error again:

giacomo@ubuntu:~$ sudo gem install rails
Install required dependency actionpack? [Yn]  y
[I]ERROR:  While executing gem ... (OpenURI::HTTPError)
    404 Not Found[/I]

Is there any alternative way of installing RoR on Ubuntu Dapper?

ThanX:D

I think there is an apt-get package called rails that you can install that should do the trick.

---

### Post by asimon on 2006-08-10
> **boredandblogging.com said:**
> I think there is an apt-get package called rails that you can install that should do the trick.
The gem installation should work now, the problems were fixed.

If you use Rails in a production environment you better install version 1.1.5 though gem and don't use the debian package because the Dapper (and Edgy) version has a critical security issue:
[Bug #55811](https://launchpad.net/bugs/55811).

---


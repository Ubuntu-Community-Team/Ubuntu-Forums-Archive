---
title: "Help, I have encountered a problem installing RVM"
date: 2010-10-24
forum: Programming Talk
---

### Post by FamousAmos on 2010-10-24
Hi, I'm trying to install RVM so that I can install Ruby and Ruby on Rails.  I followed the instructions [here]("http://rvm.beginrescueend.com/rvm/install/").  I installed from the GitHub Repository as was recommended and edited my home directory's .bashrc and .profile files as directed on that page.  However, when I run:

```
type rvm | head -n1
```

I do not get the output of 

```
rvm is a function
```

as it says I should.  Instead I get:

```
rvm is /usr/local/bin/rvm
```

As far as I can tell from that page, I have done everything as directed, and yet my installation of RVM is not sourcing correctly(apparently).  Can anyone help me with this?

Thanks in advance.

---

### Post by FamousAmos on 2010-10-25
Just a little bump to see if anyone can help me with this.  Thanks.

---

### Post by FamousAmos on 2010-10-27
Hi, I solved my problem.  I didn't quite follow the instructions exactly, I installed using sudo, so things didn't work properly.  I ran the following and I was able to install RVM properly:

```
sudo rm -rf /etc/rmvrc /usr/local/rvm /usr/local/bin/rvm* /usr/local/lib/rvm* $HOME/.rvm
 < <( curl http://rvm.beginrescueend.com/releases/rvm-install-head ) #  http://rvm.beginrescueend.com/rvm/install/ 

```

And everything worked properly.  So if any of you run into this issue in the future, I hope this will help you :)


Cheers.

---


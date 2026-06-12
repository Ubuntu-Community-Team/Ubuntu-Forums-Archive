---
title: "Ruby-Build failed using rbenv installation"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by vigneshwaran2 on 2016-01-12
I am trying install ruby2.2.3 using rbenv method in my ubuntu 14.04, so I tried all the below codes.
```
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev

cd
git clone git://github.com/sstephenson/rbenv.git .rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/sstephenson/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash
```
But When I tried the next step of code
```
rbenv install 2.2.3
```
I Got the Following error.
```
$ rbenv install 2.2.3
Downloading ruby-2.2.3.tar.bz2...
-> https://cache.ruby-lang.org/pub/ruby/2.2/ruby-2.2.3.tar.bz2
error: failed to download ruby-2.2.3.tar.bz2

BUILD FAILED (Ubuntu 14.04 using ruby-build 20160111)

Inspect or clean up the working tree at /tmp/ruby-build.20160112104557.13429
Results logged to /tmp/ruby-build.20160112104557.13429.log

Last 10 log lines:
/tmp/ruby-build.20160112104557.13429 ~
curl: (18) transfer closed with 2798902 bytes remaining to read


```
Please help me to install ruby2.2.3 and what is the reason for this error.
Thank you.

---

### Post by vigneshwaran2 on 2016-01-12
I tried this
```
mount | grep tmp
df -h | grep tmp
sudo mount -o remount,size=300M,noatime /tmp
```
But I got the following error.
```
mount: /tmp not mounted or bad option
```
Then I tried this```
 curl -fsSL https://gist.github.com/mislav/a18b9d7f0dc5b9efc162.txt | rbenv install --patch 2.2.3
```
but it asked to install rbenv. So I installed rbenv by ```
apt-get install rbenv
```
Then I didn't try the above code, I repeated by ```
rbenv install 2.2.3
```.
It worked now for me.):P
But I dont know what is the cause of this error. If anyone can point out  the reason for the error. It will be very useful. Thank You.

---


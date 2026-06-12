---
title: "Ubuntu, or browsercms broken?"
date: 2012-02-19
forum: Programming Talk
---

### Post by locosway on 2012-02-19
I can't get browsercms to install no matter what I try. Running Ubuntu Server 11.10.

root@ubuntu:~# ruby -v
ruby 1.9.2p290 (2011-07-09 revision 32553) [x86_64-linux]


root@ubuntu:~# gem list
abstract (1.0.0)
actionmailer (3.0.11)
actionpack (3.0.11)
activemodel (3.0.11)
activerecord (3.0.11)
activeresource (3.0.11)
activesupport (3.0.11)
ancestry (1.2.4)
arel (2.0.10)
builder (2.1.2)
bundler (1.0.22)
erubis (2.6.6)
i18n (0.5.0)
json (1.6.5)
mail (2.2.19)
mime-types (1.17.2)
polyglot (0.3.3)
rack (1.2.5)
rack-mount (0.6.14)
rack-test (0.5.7)
rails (3.0.11)
railties (3.0.11)
rake (0.9.2.2)
rdoc (3.12)
thor (0.14.6)
treetop (1.4.10)
tzinfo (0.3.31)


greg@ubuntu:~$ sudo gem install browsercms
[sudo] password for greg:
ERROR:  Error installing browsercms:
       browsercms requires Ruby version >= 1.9.2.

---


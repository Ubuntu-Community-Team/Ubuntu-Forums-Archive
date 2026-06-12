---
title: "Noob help with Ruby on Rails"
date: 2009-11-11
forum: Programming Talk
---

### Post by caradeporra on 2009-11-11
I am sure there are plenty of people who are going to gawk at this question, but i am a complete newbie on this.  I have been trying to setup a simple site through ruby.  I have restful authentication setup and I am trying to add several other features like simple captcha.  

a lot of these other script/plugins use the git feature.  So here comes the stupid question...  How do i add the repositories, or set up ruby to be able to install from git?

---

### Post by yerhot on 2009-11-25
install Git.

```
sudo apt-get install git-core

```
now you can install via Git.  For instance, to install Will Paginate as a Rails Plugin simply
```
script/plugin install git://github.com/mislav/will_paginate.git 
```

For info on adding sources to Gem check out the manual. [http://docs.rubygems.org/read/book/1](http://docs.rubygems.org/read/book/1)

---


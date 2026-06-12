---
title: "how do i install ruby 1.9.2"
date: 2010-08-24
forum: Programming Talk
---

### Post by pythonsyntax on 2010-08-24
How do i  compile and install ruby 1.9.2 on ubuntu?

---

### Post by trigsenior on 2010-08-27
Hello,



get the latest stable version from [http://www.ruby-lang.org/en/downloads/](http://www.ruby-lang.org/en/downloads/)


```

wget ftp://ftp.ruby-lang.org//pub/ruby/1.9/ruby-1.9.2-p0.tar.gz

```

lets extract it

```

tar -xvvf ruby-1.9.2-p0.tar.gz

```

enter the Freshly extracted file
```
 
cd ruby-*

```

Now look for a file called README or INSTALL and read it for install instructions. 

In my case i had to run this..

```

./configure
make
install 
sudo make install 

```

PS: When i did it i ran into dependency hell with zlib and gems however i'm running jaunty on an _unconventional_ system. So tell me if you get the same problem (or any others) and I'll try and help you fix it.

---

### Post by kyonides on 2010-08-31
Thanks for the info, even if I didn't start this thread, but how can I install it in a different folder than ruby 1.9.1?

---

### Post by sharpdust on 2010-09-01
> **kyonides said:**
> Thanks for the info, even if I didn't start this thread, but how can I install it in a different folder than ruby 1.9.1?

```
./configure --prefix=/YOUR/NEW/DIRECTORY
```

Might I also suggest that in the ruby community, using [rvm]("http://rvm.beginrescueend.com/rvm/install/") is the preferred way of installing ruby.

---

### Post by PicklePumpers on 2010-09-03
> **sharpdust said:**
> ```
./configure --prefix=/YOUR/NEW/DIRECTORY
```

Might I also suggest that in the ruby community, using [rvm]("http://rvm.beginrescueend.com/rvm/install/") is the preferred way of installing ruby.

While I greatly appreciate all the hard work that's gone into RVM it's never worked for me. I tried it on OS X and it randomly lost connection to what version it was on. This happened not once but three times. 

I always assume I did something wrong when something stops working on my computer because, you know, I'm the one doing stuff, but in the most obvious case of RVM-WTF-itus all I did was run a simple ruby script that was nothing more than setting some local variables and puts'ing them out to the console; one second it worked then literally the next second it didn't. Ruby page faulted and wouldn't even run anymore. I thought, "Wow, did I do something in my script?" But no, it was just a demo from a website tutorial showing how to use arrays and hashes. Nothing fancy or system mucking about-ish.

Now I've just tried using it on Ubuntu 10.04 server. I wanted to install ruby 1.9.2 and rails 3.0.0 but when it was all installed rails couldn't be found even though it was listed in "gem list". I've given up on RVM for now and am just going to try installing everything myself manually.

I guess the whole point of my long winded rant is to point out saying, "Use RVM" is a bit like saying "Can't see? Rub camel dung in your eye, that always helps me." Plus I don't live near any camels, the dragons ate them all.

---

### Post by tgalati4 on 2010-09-03
Camel dung is actually a good remedy for panther pis s in your eyes.  And if the panther was close enough to only pis s in your eyes--consider yourself lucky.

RVM worked for me under Hardy.  Haven't tried it under Jaunty.

---

### Post by roberto.tomas on 2010-09-07
(note: I am on 10.04) I wrote this guide to remind me how, from back when I was testing the 1_9_3dev branch (now defunct)
```

how to install a new ruby manually:

bash
    export BV=1.9.3dev
    autoconf
    ./configure --with-ruby-version=$BV --prefix=/usr --program-suffix=$BV
    make
    sudo make install

    sudo update-alternatives \
        --install /usr/bin/ruby ruby /usr/bin/ruby$BV ${BV//./""} \
        --slave   /usr/bin/erb  erb  /usr/bin/erb$BV \
        --slave   /usr/bin/irb  irb  /usr/bin/irb$BV \
        --slave   /usr/bin/rdoc rdoc /usr/bin/rdoc$BV \
        --slave   /usr/bin/ri   ri   /usr/bin/ri$BV
    sudo update-alternatives --install /usr/bin/gem gem /usr/bin/gem$BV ${BV//./""}
    sudo update-alternatives --config ruby
    sudo update-alternatives --config gem
exit

if you have troubles with --program-suffix and sub programs (ri, gem, etc), try replacing relevant lines with:
    ./configure --with-ruby-version=$BV --prefix=/usr
    make
    sudo make install
    sudo ruby -e 'Dir.glob("bin/*") do |fh| %x(mv #{fh} /usr/bin/#{fh}#{ENV["BV"]}); end'
    sudo mv /usr/bin/ruby /usr/bin/ruby$BV
```

---

### Post by kyonides on 2010-09-15
> **sharpdust said:**
> ```
./configure --prefix=/YOUR/NEW/DIRECTORY
```

Might I also suggest that in the ruby community, using [rvm]("http://rvm.beginrescueend.com/rvm/install/") is the preferred way of installing ruby.
I'm sorry but it didn't help me since it still installed a lot of the components in the following folders...

> installing binary commands:   /usr/lib/ruby/1.9.2/bin
installing base libraries:    /usr/lib/ruby/1.9.2/lib
installing arch files:        /usr/lib/ruby/1.9.2/lib/ruby/1.9.1/i686-linux
installing extension objects: /usr/lib/ruby/1.9.2/lib/ruby/1.9.1/i686-linux
installing extension objects: /usr/lib/ruby/1.9.2/lib/ruby/site_ruby/1.9.1/i686-linux
installing extension objects: /usr/lib/ruby/1.9.2/lib/ruby/vendor_ruby/1.9.1/i686-linux
installing extension headers: /usr/lib/ruby/1.9.2/include/ruby-1.9.1/i686-linux
installing extension scripts: /usr/lib/ruby/1.9.2/lib/ruby/1.9.1
installing extension scripts: /usr/lib/ruby/1.9.2/lib/ruby/site_ruby/1.9.1
installing extension scripts: /usr/lib/ruby/1.9.2/lib/ruby/vendor_ruby/1.9.1
installing extension headers: /usr/lib/ruby/1.9.2/include/ruby-1.9.1/ruby
installing rdoc:              /usr/lib/ruby/1.9.2/share/ri/1.9.1/system
installing capi-docs:         /usr/lib/ruby/1.9.2/share/doc/ruby
installing command scripts:   /usr/lib/ruby/1.9.2/bin
installing library scripts:   /usr/lib/ruby/1.9.2/lib/ruby/1.9.1
installing common headers:    /usr/lib/ruby/1.9.2/include/ruby-1.9.1
installing manpages:          /usr/lib/ruby/1.9.2/share/man/man1
installing default gems:      /usr/lib/ruby/1.9.2/lib/ruby/gems/1.9.1 (cache, doc, gems, specifications)

which wasn't what I tried to do here...

---

### Post by sharpdust on 2010-09-16
> **kyonides said:**
> I'm sorry but it didn't help me since it still installed a lot of the components in the following folders...



which wasn't what I tried to do here...

Where are you intending to install it? The 1.9.1 stuff exist there for comparability reasons, see the FAQ on this [page]("http://www.ruby-lang.org/en/news/2010/08/18/ruby-1-9-2-is-released/").

---


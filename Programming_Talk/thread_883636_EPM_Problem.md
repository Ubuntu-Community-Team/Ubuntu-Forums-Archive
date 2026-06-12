---
title: "EPM Problem"
date: 2008-08-08
forum: Programming Talk
---

### Post by ruairidh on 2008-08-08
Hi,

I'm creating a simple package for my ruby script so that you can type in (blah) and the command specified in the script is parsed.

For example:

```
Talk = puts "Hi there"
```

My code works perfectly in console on it's own and I decided to package it for ease of use. I'm putting the file script.rb into /usr/bin as "script".

I decided to use epm because it made package building so simple and I've used it before.

The package is built successfully and installs without error but it appears that my script won't run when I try to type the command in the console.

The contents of my program.list file are as follows:

```

%product Moo Make
%copyright 2008 Ruairidh 
%vendor Ruairidh 
%description Ruby clone of the popular unix program cowsay. Usage: moomake <text>
%version 0.1
%readme README
%license LICENSE
%requires ruby

f 755 root sys /usr/bin/moomake moomake.rb

```

Any ideas?

EDIT:

Fixed the issue, problem lay with me giving the wrong path in #!/usr/bin/ruby changed it to #!/usr/bin/env ruby and reinstalled the package.

---


---
title: "Installing Mongrel on Feisty"
date: 2007-05-22
forum: Programming Talk
---

### Post by Cryption on 2007-05-22
I am new to Ubuntu.  I have used Red Hat for years.  I installed Build-Essential, Ruby and RubyGems through Synaptic, which worked great.  Then I installed "mongrel" through the CLI using the following command:

sudo gem install mongrel --include-dependencies

This placed some bins in /var/lib/gems/1.8 among other files.

On Fedora those two files are placed in /usr/lib/ruby/gems/1.8 which is part of my path.

The tutorial sites I have found have not mentioned having to do anything special to be able to run the command mongrel_rails from the CLI.  Though I would expect that I need to add /var/lib to my PATH to be able to do that in this case on Ubuntu.

Could anyone shed some light on this situation?

---

### Post by TheOtherShoe on 2007-05-25
You are correct; you will want to add /var/lib/gems/1.8/bin to your path. To do so, add this line to .bashrc in your home directory:
```
PATH=$PATH:/var/lib/gems/1.8/bin
```

---


---
title: "Ruby - setting up vim in irb"
date: 2010-07-30
forum: Programming Talk
---

### Post by styracosaurus on 2010-07-30
Hi,

I'm trying to set up editing within irb using vim as described in this vimcast: [http://vimcasts.org/episodes/running-vim-within-irb/](http://vimcasts.org/episodes/running-vim-within-irb/)

I did the gem install interactive_editor and it seemed to install the gem to /home/me/.gems/ruby/1.9.1/gem/interactive_editor, and I also edited my .irbrc file and added:

require 'rubygems'
require 'interactive_editor'

but when I try to run vi from irb I get this:

NameError: undefined local variable or method `vi’ for main:Object
from (irb):1

I am very new to Ruby/gems etc... I don't even know where to begin.  Googling this error didn't really help, I only found a few people with the same issue and no answers.

I'm on Ubuntu 10.04, I have Ruby 1.9.1 installed... not sure about the versions for irb or rubygems.

Thanks a lot!

---

### Post by lindsay_keir on 2010-08-02
Maybe you haven't installed everything 1.9? I just put in a new topic called **How-To Install Ruby 1.9 and Ruby Gems into Ubuntu** which may help.

---


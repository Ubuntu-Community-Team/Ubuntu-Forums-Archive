---
title: "Cucumber installation help needed"
date: 2013-10-16
forum: Programming Talk
---

### Post by Laura_Kuhner on 2013-10-16
Hi All,

I am a newbee in ubuntu and I’m trying to learn cucumber.
 
I have OS X 10.8.5 and have ruby 1.9.3p392 installed.
 
Trying to install cucumber, I get the following error:
 
$ sudo gem install cucumber
Building native extensions.  This could take a while...
ERROR:  Error installing cucumber:
            ERROR: Failed to build gem native extension.
 
        /usr/local/rvm/rubies/ruby-1.9.3-p392/bin/ruby extconf.rb
checking for main() in -lc... *** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.
 
Provided configuration options:
            --with-opt-dir
            --without-opt-dir
            --with-opt-include
            --without-opt-include=${opt-dir}/include
            --with-opt-lib
            --without-opt-lib=${opt-dir}/lib
            --with-make-prog
            --without-make-prog
            --srcdir=.
            --curdir
            --ruby=/usr/local/rvm/rubies/ruby-1.9.3-p392/bin/ruby
            --with-gherkin_lexer_ar-dir
            --without-gherkin_lexer_ar-dir
            --with-gherkin_lexer_ar-include
            --without-gherkin_lexer_ar-include=${gherkin_lexer_ar-dir}/include
            --with-gherkin_lexer_ar-lib
            --without-gherkin_lexer_ar-lib=${gherkin_lexer_ar-dir}/lib
            --with-clib
            --without-clib
/usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:381:in `try_do': The compiler failed to generate an executable file. (RuntimeError)
You have to install development tools first.
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:461:in `try_link0'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:476:in `try_link'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:619:in `try_func'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:845:in `block in have_library'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:790:in `block in checking_for'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:284:in `block (2 levels) in postpone'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:254:in `open'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:284:in `block in postpone'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:254:in `open'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:280:in `postpone'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:789:in `checking_for'
            from /usr/local/rvm/rubies/ruby-1.9.3-p392/lib/ruby/1.9.1/mkmf.rb:840:in `have_library'
            from extconf.rb:5:in `<main>'
 
 
Gem files will remain installed in /usr/local/rvm/gems/ruby-1.9.3-p392/gems/gherkin-2.12.2 for inspection.
Results logged to /usr/local/rvm/gems/ruby-1.9.3-p392/gems/gherkin-2.12.2/ext/gherkin_lexer_ar/gem_make.out
 
 
I have searched google and tried various options, but nothing is working.
 
Any help would be greatly appreciated.
 
Thanks,
Laura

---

### Post by dwhitney67 on 2013-10-17
You have OS X 10.8.5?  I thought you were using Ubuntu?

Anyhow, these errors (see below) are probably telling you that you need to install development tools (gcc, make, etc) on to your system.
```

Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers. Check the mkmf.log file for more
details. You may need configuration options.

```
To install the development tools, do this:
```

$ sudo apt-get install build-essential

```
Then repeat the 'cucumber' configuration process.

---


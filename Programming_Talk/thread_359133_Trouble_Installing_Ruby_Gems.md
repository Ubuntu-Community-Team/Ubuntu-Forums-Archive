---
title: "Trouble Installing Ruby Gems"
date: 2007-02-11
forum: Programming Talk
---

### Post by infernon on 2007-02-11
Hello, 

I am attempting to install Ruby Gems with the intention of installing Rails afterwards.

I have extracted the files from the tarball and am attempting to run setup.rb (this is the Gems tarball, sorry), but I receive the following error message:

<--- lib
/usr/local/lib/ruby/site_ruby/1.8/rubygems/remote_fetcher.rb:4:in `require': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/remote_fetcher.rb:4
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:8:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/source_index.rb:8
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:501:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:501
        from /home/infernon/Desktop/rubygems-0.9.2/./post-install.rb:81:in `require'
        from /home/infernon/Desktop/rubygems-0.9.2/./post-install.rb:81:in `install_sources'
        from /home/infernon/Desktop/rubygems-0.9.2/./post-install.rb:116:in `try_run_hook'
        from setup.rb:584:in `run_hook'
        from setup.rb:1322:in `exec_task_traverse'
        from setup.rb:1175:in `exec_install'
        from setup.rb:894:in `exec_install'
        from setup.rb:712:in `invoke'
        from setup.rb:681:in `invoke'
        from setup.rb:1359

I have verified that zlib for Ruby is installed so I am not very sure of where to go from here.  Any help that anyone could provide would be great.  I am a bit new to Linux as well, so you'll have to excuse me if I'm a bit slow on the uptake:)

---

### Post by infernon on 2007-02-11
As a follow up, i needed some libraries:

zliblg
zliblg-dev

Just in case anyone else runs into this...

---

### Post by justinwr on 2007-02-26
> **infernon said:**
> As a follow up, i needed some libraries:

zliblg
zliblg-dev

Just in case anyone else runs into this...

actually they are spelled zlib**1**g (number one) and i have installed both as you have suggested, with no luck! maybe this is a rubygems-0.9.2 issue, since i know i have had 0.9.0 working in ubuntu in a past installation.

hopefully i will find some luck.... thanks,
justin-

---

### Post by justinwr on 2007-02-26
actually did a Google search and found this blurb in Japanese that, thankfully, Google could interpret ;)

```
% cd ./ruby-1.8.5-p12/ext/zlib
% ruby extconf.rb --with-zlib-include=/usr/include --with-zlib-lib=/usr/lib 
% make 
% sudo make install 
% cd ../rubygems-0.9.1 
% ruby setup.rb config 
% ruby setup.rb setup 
% sudo ruby setup.rb install [abbreviation] <--- lib Successfully built RubyGem Name:...................
```

completely solved this problem, hope that helps anyone else if inferno's tip doesn't work!

happy hacking,
justin-

---

### Post by Geoffaz on 2007-03-30
Building gems from source wasn't working for me.  However, I did get everything up and running after this command:

```
sudo apt-get install --reinstall libgems-ruby1.8
```

From here: [http://railsforum.com/viewtopic.php?pid=15770#p15770]("http://railsforum.com/viewtopic.php?pid=15770#p15770")

---

### Post by michwill on 2007-04-14
Just FYI, this might prove a helpful tutorial:

[http://blog.mondragon.cc/articles/2007/02/03/compiling-ruby-1-8-5-w-openssl-on-debian-etch-testing-and-freebsd-in-home](http://blog.mondragon.cc/articles/2007/02/03/compiling-ruby-1-8-5-w-openssl-on-debian-etch-testing-and-freebsd-in-home)

---

### Post by jmvbxx on 2007-04-25
I had the exact same problem and ended up just compiling the ruby-zlib from source.

I downloaded the file from:

[HTML]http://raa.ruby-lang.org/project/ruby-zlib[/HTML]

Then:

sudo ruby extconf.rb
make
make install

Once I did this I was able to run 'sudo ruby setup.rb' without problem from my gems dir.

---


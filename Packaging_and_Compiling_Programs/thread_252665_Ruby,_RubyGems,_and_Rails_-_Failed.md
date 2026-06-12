---
title: "Ruby, RubyGems, and Rails - Failed?"
date: 2006-09-07
forum: Packaging and Compiling Programs
---

### Post by Raavea on 2006-09-07
Hey there, I tried once before to get Ruby on Rails to work on my Ubuntu Breezy Badger system, but failed miserably due to being a general newb forging ahead of myself recklessly.

 Well, now I've got Dapper Drake, and I'm drooling at the prospect of exploring this awesome sounding thing called Ruby on Rails again.

 However, I don't think RubyGems and Rails have installed. This looks like a big mess of stuff I don't really understand, but parts of it scream ERROR at my poor brain, so if anyone could tell me if this means it succeeded or failed, I'd be greatly appreciative.
```
raavea@bernard:~/rubygems-0.9.0$ sudo ruby setup.rb
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/local/bin/
install gem /usr/local/bin/
install gem_mirror /usr/local/bin/
install gem_server /usr/local/bin/
install gemlock /usr/local/bin/
install gemri /usr/local/bin/
install gemwhich /usr/local/bin/
install index_gem_repository.rb /usr/local/bin/
install update_rubygems /usr/local/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/ruby/site_ruby/1.8/
install rubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
install ubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
---> lib/rbconfig
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rbconfig
install datadir.rb /usr/local/lib/ruby/site_ruby/1.8/rbconfig
<--- lib/rbconfig
---> lib/rubygems
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install cmd_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install incremental_fetcher.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install loadpath_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
<--- lib/rubygems
<--- lib

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original _require': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:7
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:93:in `manage_gems'
        from /home/raavea/rubygems-0.9.0/./post-install.rb:70:in `install_source s'
        from /home/raavea/rubygems-0.9.0/./post-install.rb:81:in `try_run_hook'
        from setup.rb:577:in `run_hook'
        from setup.rb:1315:in `exec_task_traverse'
        from setup.rb:1168:in `exec_install'
        from setup.rb:887:in `exec_install'
        from setup.rb:705:in `invoke'
        from setup.rb:674:in `invoke'
        from setup.rb:1352
raavea@bernard:~$ cd ..
raavea@bernard:~$ cd rubygems-0.9.0
raavea@bernard:~/rubygems-0.9.0$ sudo gem install rails --include-dependencies
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/builder.rb:7
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:93:in `manage_gems'
        from /usr/local/bin/gem:10

```PS: Also, if it failed.. How do I fix it? x.x


I've seen [this thread]("http://www.ubuntuforums.org/showthread.php?t=169891"), but it's for Breezy so I'm not sure if it's safe to use any of the stuff in there. If you know what I mean..

---

### Post by Blacktalon on 2006-10-31
Hello,

Great to hear you are interested in ruby on rails, it's a fun one to play with.

Well about your problem first I must ask some question cause I am afraid Im not a guru at this yet.

Question 1: did you do (in terminal) sudo apt-get install ruby irb rdoc
Question 2: Have you tried (in terminal) sudo gem update
Question 3: Have you done (in Terminal) sudo gem install rails

:cool:

---


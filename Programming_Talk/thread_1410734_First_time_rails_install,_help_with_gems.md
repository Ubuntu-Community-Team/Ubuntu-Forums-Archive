---
title: "First time rails install, help with gems"
date: 2010-02-19
forum: Programming Talk
---

### Post by woodsonoversoul on 2010-02-19
Hello all,
    I just installed ruby enterprise edition with rails. I down loaded the latest version of gems and ran ```
dan@dev:~/initial_install/rubygems-1.3.5$ sudo ruby setup.rb
``` Which returned:
```

RubyGems 1.3.5 installed                                    
./lib/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- rdoc/rdoc (LoadError)
        from ./lib/rubygems/custom_require.rb:31:in `require'                                               
        from ./lib/rubygems/commands/setup_command.rb:352:in `run_rdoc'                                     
        from ./lib/rubygems/commands/setup_command.rb:247:in `install_rdoc'                                 
        from ./lib/rubygems/commands/setup_command.rb:120:in `execute'                                      
        from ./lib/rubygems/command.rb:257:in `invoke'                                                      
        from ./lib/rubygems/command_manager.rb:132:in `process_args'                                        
        from ./lib/rubygems/command_manager.rb:102:in `run'                                                 
        from ./lib/rubygems/gem_runner.rb:58:in `run'                                                       
        from setup.rb:35                    
```

Then I tried to install the mysql gem and  got the following out put:
```
dan@dev:~/initial_install/rubygems-1.3.5$ gem install mysql
WARNING:  Installing to ~/.gem since /usr/lib/ruby/gems/1.8 and
          /usr/bin aren't both writable.                       
WARNING:  You don't have /home/dan/.gem/ruby/1.8/bin in your PATH,
          gem executables will not run.                           
Building native extensions.  This could take a while...           
ERROR:  Error installing mysql:                                   
        ERROR: Failed to build gem native extension.              

/usr/bin/ruby1.8 extconf.rb
extconf.rb:10:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:10                                          


Gem files will remain installed in /home/dan/.gem/ruby/1.8/gems/mysql-2.8.1 for inspection.
Results logged to /home/dan/.gem/ruby/1.8/gems/mysql-2.8.1/ext/mysql_api/gem_make.out      
```

What an I missing here?

---

### Post by BbUiDgZ on 2010-02-19
> **woodsonoversoul said:**
> Hello all,
    I just installed ruby enterprise edition with rails. I down loaded the latest version of gems and ran ```
dan@dev:~/initial_install/rubygems-1.3.5$ sudo ruby setup.rb
``` Which returned:
```

RubyGems 1.3.5 installed                                    
./lib/rubygems/custom_require.rb:31:in `gem_original_require': no such file to load -- rdoc/rdoc (LoadError)
        from ./lib/rubygems/custom_require.rb:31:in `require'                                               
        from ./lib/rubygems/commands/setup_command.rb:352:in `run_rdoc'                                     
        from ./lib/rubygems/commands/setup_command.rb:247:in `install_rdoc'                                 
        from ./lib/rubygems/commands/setup_command.rb:120:in `execute'                                      
        from ./lib/rubygems/command.rb:257:in `invoke'                                                      
        from ./lib/rubygems/command_manager.rb:132:in `process_args'                                        
        from ./lib/rubygems/command_manager.rb:102:in `run'                                                 
        from ./lib/rubygems/gem_runner.rb:58:in `run'                                                       
        from setup.rb:35                    
```

Then I tried to install the mysql gem and  got the following out put:
```
dan@dev:~/initial_install/rubygems-1.3.5$ gem install mysql
WARNING:  Installing to ~/.gem since /usr/lib/ruby/gems/1.8 and
          /usr/bin aren't both writable.                       
WARNING:  You don't have /home/dan/.gem/ruby/1.8/bin in your PATH,
          gem executables will not run.                           
Building native extensions.  This could take a while...           
ERROR:  Error installing mysql:                                   
        ERROR: Failed to build gem native extension.              

/usr/bin/ruby1.8 extconf.rb
extconf.rb:10:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:10                                          


Gem files will remain installed in /home/dan/.gem/ruby/1.8/gems/mysql-2.8.1 for inspection.
Results logged to /home/dan/.gem/ruby/1.8/gems/mysql-2.8.1/ext/mysql_api/gem_make.out      
```

What an I missing here?

use sudo

---


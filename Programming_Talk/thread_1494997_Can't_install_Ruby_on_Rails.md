---
title: "Can't install Ruby on Rails"
date: 2010-05-27
forum: Programming Talk
---

### Post by nxhoaf on 2010-05-27
To day, I installed Ruby on Rails
Here is the step : ;
1. Dowload Ruby source code and install it 
   ( [Ruby  1.9.1-p376]("ftp://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.1-p376.tar.gz") (md5:  ebb20550a11e7f1a2fbd6fdec2a3e0a3)  from [http://www.ruby-](http://www.ruby-)  lang.org/en/downloads/

   $ ./configure; make; sudo make install
    Here is the result : 
   ```

    nxhoaf@NeverGiveUp:/usr/local/bin$ ruby -v
    ruby 1.9.1p376 (2009-12-07 revision 26041) [i686-linux]
   
```2. Dowload Ruby gem and install it ([rubygems-1.3.7.tgz]("http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz") from [http://rubyforge.org](http://rubyforge.org) /frs/?group_id=126)
  nxhoaf@NeverGiveUp:~/Downloads/rubygems-1.3.7$ ruby setup.rb 
 ..............
  RubyGems installed the following executables:
    /usr/local/bin/gem
 and the result : 
 ```

  nxhoaf@NeverGiveUp:/usr/local/bin$ gem -v
   1.3.7
 
```3. But when i try to execute the folowing command, an error occured : 
```

 nxhoaf@NeverGiveUp:/usr/local/bin$ sudo gem install rails --include-dependenciesERROR:  Loading command: install (LoadError)
    no such file to load -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::InstallCommand
nxhoaf@NeverGiveUp:/usr/local/bin$ 

```and when i tried to update gem, it seem not to work
```

nxhoaf@NeverGiveUp:/usr/local/bin$ sudo gem update
ERROR:  Loading command: update (LoadError)
    no such file to load -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::UpdateCommand
nxhoaf@NeverGiveUp:/usr/local/bin$ 


```

I didn't know why i got that error
 anyone can help me !!!!!!

---

### Post by twisted_steel on 2010-05-27
Is there a specific reason you are installing ruby and rubygems from source?  It looks like almost everything you need is available via the repositories as long as you have a relatively recent version of Ubuntu.

See this page for more information: [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails).

Otherwise, I am not sure about that error.

---

### Post by nxhoaf on 2010-05-29
I followed it and it still not working . Btw, can anyone tell me how to create a ruby on rails project on netbeans. I read this tutor but in the migration database step, it doesn't work, too :((
[http://netbeans.org/kb/docs/ruby/rapid-ruby-weblog.html](http://netbeans.org/kb/docs/ruby/rapid-ruby-weblog.html)

---

### Post by b1nar10 on 2010-09-01
Hey all!, same problem :(

```

me@mypc:~$ ruby -v
ruby 1.9.2p0 (2010-08-18 revision 29036) [i686-linux]
me@mypc:~$ gem -v
1.3.7

```

then I try:

```

me@mypc:~$ gem install rails
ERROR:  Loading command: install (LoadError)
    no such file to load -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::InstallCommand

```

:confused:

I've installed zlib* from apt-get, but it doesn't help.
Thanks in advance for your help!.

---

### Post by sharpdust on 2010-09-02
To the original poster: Rails is not compatible with ruby 1.9.1, you have to use 1.9.2 or 1.8.7.

Try installing libzlib-ruby from apt-get.

If that doesn't work, then install with [rvm]("http://rvm.beginrescueend.com/rvm/install/") which is the preferred way to install ruby. They even have a section that addresses the [zlib]("http://rvm.beginrescueend.com/packages/zlib/") problem.

---

### Post by MMCX on 2010-10-19
> **b1nar10 said:**
> Hey all!, same problem :(

```

me@mypc:~$ ruby -v
ruby 1.9.2p0 (2010-08-18 revision 29036) [i686-linux]
me@mypc:~$ gem -v
1.3.7

```then I try:

```

me@mypc:~$ gem install rails
ERROR:  Loading command: install (LoadError)
    no such file to load -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::InstallCommand

```:confused:

I've installed zlib* from apt-get, but it doesn't help.
Thanks in advance for your help!.

Hi,

I had the exact problem. So i thought i'd leave a note on how i managed to finally fix this.

Even you install zlib after installing ruby via RVM, things do not work well. And yes you get that ' no such file to load -- zlib' error when you use the 'gem' command. e.g. 'gem list'
[FONT=Verdana]
So here's what I did
- First remove your rvm ruby installation:
rvm remove ruby-x.x.x # put your ruby version here

- T[/FONT][FONT=Verdana]hen install zlib via rvm
 rvm package install zlib

- Finally install ruby again
rvm install ruby-x.x.x
[/FONT]
--Fixed! --

All the credit goes to '[JasonOng]("http://stackoverflow.com/users/6048/jasonong")' response below:
[http://stackoverflow.com/questions/2441248/rvm-ruby-1-9-1-troubles](http://stackoverflow.com/questions/2441248/rvm-ruby-1-9-1-troubles)

'JasonOng' mentioned that you better use :
rvm install 1.9.1 -C --with-zlib-dir=$rvm_path/usr

..but i didn't have use the '-C --with..' part

Anyway this problem did not occur when I followed this great tute which tells you to install zlib and the other required packages before using rvm to install ruby:
[http://rbjl.net/19-rubybuntu-1-installing-ruby-and-rails-on-ubuntu](http://rbjl.net/19-rubybuntu-1-installing-ruby-and-rails-on-ubuntu)

Hope this helps to anyone searching for a fix.

---

### Post by brezenix on 2010-11-09
> **nxhoaf said:**
> 
and when i tried to update gem, it seem not to work
```

nxhoaf@NeverGiveUp:/usr/local/bin$ sudo gem update
ERROR:  Loading command: update (LoadError)
    no such file to load -- zlib
ERROR:  While executing gem ... (NameError)
    uninitialized constant Gem::Commands::UpdateCommand
nxhoaf@NeverGiveUp:/usr/local/bin$ 

```

I didn't know why i got that error
 anyone can help me !!!!!!

PS : sorry for my english :)

Before you install Ruby, you need to install some libraries:

```
sudo aptitude install build-essential libssl-dev libreadline5 libreadline5-dev zlib1g zlib1g-dev
```

---

### Post by krazyd on 2010-11-09
> **MMCX said:**
> installing ruby via RVM
Don't use RVM.
[http://www.lucas-nussbaum.net/blog/?p=550](http://www.lucas-nussbaum.net/blog/?p=550)

brezenix has the right idea.

---

### Post by schuft on 2011-02-24
This is probably obvious to most people, but it tripped me up: when brezenix says you need to install those libraries before installing ruby, he means you need to install them before *compiling* ruby.  Being new to linux, it took me a few minutes to realize that.

---

### Post by Free Hugs on 2011-10-17
Hey guys, this is easier to resolve than you think. Basically, if the zlib library isn't there at the time you compile ruby, you just have to go back and install the library and then re-compile that module. Here are the steps:

```
sudo apt-get install zlib1g-dev
cd /ruby-source-files/ext/zlib
ruby extconf.rb
make
sudo make install
```

Now you have zlib enabled  :-)

---

### Post by beaknit@gmail.com on 2011-10-21
Also - rvm makes solving this (and almost every other ruby problem) much, much easier:

[https://rvm.beginrescueend.com/packages/zlib/](https://rvm.beginrescueend.com/packages/zlib/)

---

### Post by trivialpackets on 2011-10-21
[http://www.rubypluspl.us/2011/10/quick-and-dirty-rails-dev-box-on-ubuntu.html](http://www.rubypluspl.us/2011/10/quick-and-dirty-rails-dev-box-on-ubuntu.html)

I've yet to have this fail and used just about the exact same process in 11.04.  I would advise making your own decision regarding the use of RVM.  For a development environment, I enjoy it very much, because I don't know what environment I may need at any given time.  I wouldn't use it in a deployment, but that's really not its purpose.

---

### Post by I_hate_isNaN on 2012-01-03
Concur about RVM. I'm a ruby on rails developer and find it invaluable. I feel strongly that you should offer up solutions to the original poster's problem. Not opinions.

Inside railstutorial.org, a site is mentioned which has complete install instructions for ruby on rails using RVM. It's here: [http://toranbillups.com/blog/archive/2010/09/01/How-to-install-Rails-3.0-and-Ruby-1.9.2-on-Ubuntu](http://toranbillups.com/blog/archive/2010/09/01/How-to-install-Rails-3.0-and-Ruby-1.9.2-on-Ubuntu)

I'm sure this is an old-ish issue, but hopefully that link helps.

---

### Post by glunder on 2012-01-29
Probably this problem is solved.  
 Here is what I did, that worked for me:
 I have Ubuntu 11.10
 I use my rails app with mysql. Got mysql server from the program center in ubuntu (v. 5.1.5)
 

 - sudo apt-get install ruby1.9.1
 - sudo gem install sinatra
 - sudo gem install haml
 [FONT=Liberation Serif, Times New Roman, serif]- sudo [/FONT][FONT=Liberation Serif, Times New Roman, serif]apt-get[/FONT][FONT=Liberation Serif, Times New Roman, serif]install[/FONT][FONT=Liberation Serif, Times New Roman, serif]libmysqlclient-dev[/FONT][FONT=Liberation Serif, Times New Roman, serif]libmysql-ruby1.9[/FONT][FONT=Liberation Serif, Times New Roman, serif]ruby1.9.1-dev[/FONT]
 -sudo gem install rails
  (version 3.1.3 was installed)
 - sudo gem uninstall rack
 (choose the 1.4 version for uninstall)
 - sudo gem install therubyracer
 (for the rake command to function therubyracer must be used )
 Put [FONT=Bitstream Charter, serif]"gem[/FONT][FONT=Bitstream Charter, serif]'therubyracer',[/FONT][FONT=Bitstream Charter, serif]platforms[/FONT][FONT=Bitstream Charter, serif]=>[/FONT][FONT=Bitstream Charter, serif]:ruby" in the Gemfile[/FONT]
 [FONT=Bitstream Charter, serif]- bundle install[/FONT]
 After this my rails application do function well at my site.  
 

 Good luck.
 Gjermund,

---

### Post by chandanjc1 on 2012-06-14
^Thanks for your help. That got it running for me.

---

### Post by RealHector on 2012-07-24
> **chandanjc1 said:**
> ^Thanks for your help. That got it running for me.
which solution help you?

---

### Post by raja.genupula on 2012-07-24
@RealHector  , solution mentioned at post #14

---

### Post by RealHector on 2012-07-24
I find the solution:

[LEFT][FONT=Arial]$ rvm pkg install zlib
$ rvm remove 1.9.3(your version)
$ rvm install 1.9.3[/FONT][FONT=Arial](your version)[/FONT]
[FONT=Arial]$ rvm --default 1.9.3[/FONT][FONT=Arial](your version)[/FONT][/LEFT]
 [LEFT][FONT=Arial]$ gem install rails[/FONT]

[FONT=Arial][/FONT]
[FONT=Arial]I hope can help somebody
  [/FONT][/LEFT]

---

### Post by nokors on 2012-12-01
For zlib package this issue will fix problem.
No need to remove ruby,install zlib1g package from terminal by - apt-get install zlib1g , and after that reboot PC ;-)

---


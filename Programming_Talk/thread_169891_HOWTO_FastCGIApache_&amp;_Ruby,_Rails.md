---
title: "HOWTO: FastCGI/Apache &amp; Ruby, Rails"
date: 2006-05-03
forum: Programming Talk
---

### Post by TheDracle on 2006-05-03
**_Installing RAILS on Ubuntu Breezy Badger_**

**Get ruby:**

**The package below apparently installs an incompatible 1.8.3 version of the ruby interpreter.**
```

sudo apt-get install ruby1.8

```
**On Breezy, try using the source package below, or perhaps obtain a 1.8.2 deb package?**

You can instead get a .tar.gz package, and compile it from source:

```

wget http://rubyforge.org/frs/download.php/2338/ruby-1.8.2.tar.gz
cd ruby-1.8.2
./configure
make
make test
sudo make install 

```

**Get ruby gems:**

**Go to:**

[RubyGEMS]("http://rubyforge.org/projects/rubygems/")

And download the latest version, OR use the following wget command:

```

wget http://rubyforge.org/frs/download.php/5207/rubygems-0.8.11.tgz

```

Then:

```

tar -xzf rubygems-0.8.11.tgz
cd rubygems-0.8.11 
sudo ruby setup.rb

```

**Install RAILS with Ruby Gems: **

```

sudo gem install rails

```

For now, do &#8216;NOT&#8217; gem install mysql (Use the defaults if you plan to use mysql). I haven&#8217;t yet discovered a work around to a segfault problem that occurs. A future HOWTO to install the native mysql drivers is needed.

**_Fixing Ubuntu Console readline problem_**

You need to do this to run script/console for RAILS, or else you get the following error:

/usr/local/lib/ruby/1.8/irb/completion.rb:10:in `require&#8217;: no such file to load&#8212;readline (LoadError)

**Install curses and readline**

```

apt-get install libncurses5-dev libreadline5-dev

```

**Manually make and install readline**

```

cd ext/readline

ruby extconf.rb

make

sudo make install

```

**_Setup with FastCGI/Apache:_**

**Check out:**
[Rails WIKI]("http://wiki.rubyonrails.com/rails/pages/HowtoSetupApacheWithFastCGIAndRubyBindings")

      First, get libfcgi-dev (fcgi headers) and install the fcgi gem:

```

sudo apt-get install libfcgi-dev
sudo gem install fcgi

```

**Configure apache httpd.conf**

```

Alias /namefromroot/ /home/jason/public_html/railsap/public
    <Directory /home/jason/public_html/railsap/public>
        Options ExecCGI
        AddHandler cgi-script .cgi
        AddHandler fastcgi-script .fcgi .fcg .fpl
        AllowOverride all
        Order allow,deny
        Allow from all
    </Directory>

```

And make a softlink to your public directory:

```

ln -s railsap/public /home/jason/public_html/railsap

```

In the above configuration, I&#8217;m making a softlink to my rails project&#8217;s public directory, to my public_html directory. I then set an alias, namefromroot, to make it easier for people to access the root of my application.

**Add fastcgi to modules.conf**

Open modules.conf (/etc/apache/modules.conf on my system) with your favorite editor, and add the following line:

```

LoadModule fastcgi_module /usr/lib/apache/1.3/mod_fastcgi.so

```

If you use Alias in httpd.conf for your rails directory, be sure to fix it!

Edit public/.htaccess under your project, and add RewriteBase:

```

RewriteBase /namefromroot

```

This will make it so that it redirects to the apropriate base directory.

Also, change

```

RewriteRule ^(.*)$ dispatch.cgi [QSA,L]
to "RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]

```

All Directories need a+r permissions, log directory needs write permissions &#8220;0666,&#8221; and all directories under tmp/ need write permissions to store session data, etc with.

```

chmod -R a+r app

cd app/log/

chmod a+w *
or
chmod 0666 *


```

**If you get an Rails application failed to start properly&#8221; Error**

Make sure there are no &#8220;puts&#8221; statements in your controllers!

If it isn&#8217;t working after this:

Clear out the session data from tmp/session, and make sure it&#8217;s writable. Also, clear the cookies in your browser, so it will try to make new session data.

---

### Post by skeeterbug on 2006-05-03
There is one problem with this post. Breezy will isntall ruby 1.8.3 which IS NOT comptable with Rails 1.1. Dapper has ruby 1.8.4 and is comptable. 

ruby -v will spit out what version you are using.

---

### Post by TheDracle on 2006-05-03
Perhaps it's a bit outdated--- my ruby version shows 1.8.2, on Breezy Badger. Must be out of date, I'll see if I can ammend it to get the right ruby version :) Thanks!


From the RAILS website:

We recommend Ruby 1.8.4 for use with Rails. Ruby 1.8.2 is fine too, but version 1.8.3 is not. 

-Jason Thomas.

---

### Post by skeeterbug on 2006-05-03
[QUOTE=TheDracle]Perhaps it's a bit outdated--- my ruby version shows 1.8.2, on Breezy Badger. Must be out of date, I'll see if I can ammend it to get the right ruby version :) Thanks!


From the RAILS website:

We recommend Ruby 1.8.4 for use with Rails. Ruby 1.8.2 is fine too, but version 1.8.3 is not. 

-Jason Thomas.[/QUOTE]

No problem :cool: 

I know I ran into this problem installing it just last week. Version 1.8.3 kept getting installed for me. I didn't realize at first that 1.8.3 wouldn't work **AT ALL**. I spent a lot of time banging my head on the wall re-reading all the howto's trying to figure out what I missed!

---

### Post by pstreck on 2006-05-04
is there a clean way to install ruby 1.8.2 or 1.8.4 on breezy? By clean I mean by using a package. I hate to manually install stuff as it tends to break future updates.

---

### Post by TheDracle on 2006-05-04
[QUOTE=pstreck]is there a clean way to install ruby 1.8.2 or 1.8.4 on breezy? By clean I mean by using a package. I hate to manually install stuff as it tends to break future updates.[/QUOTE]

I agree completely--- using a source tarball isn't a very good work around. I'd like to look into some work around using a 1.8.2 deb package maybe? Does anyone out there have some information relating to this?

---

### Post by hotani on 2006-05-05
What about Dapper/apache2/fcgid?

Documentation I've read so far has said to use fcgi instead of fastCGI on Apache 2, so that is how I've attempted to set it up.

It looked like all the necessary items were available in Synaptic, so I installed them. However, although the ruby html test page comes up in my test app, rails doesn't seem to be working correctly. I tried adding a controller and got "page not found." Seems like something wrong with my configuration but I can't figure out what. Could someone post up/link to a sample .htaccess or something?

EDIT: Found it! Near the bottom of [this page](http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable) is a great explanation of a virtual host setup, fcgi and the .htaccess file, as well as an example.

---

### Post by chris.olsen on 2006-06-07
For some reason  the when I try to start the apache server with:
/usr/local/apache2/bin/apachectl start

I get an error message ( line 412 of the apache httpd.conf file) that the mod_fcgi.so file does not exist, and when I check, sure enough it is not there.

Everything seemed to go good up to this point, including the install of the fastcgi.  I am not sure if something got missed or what.

Thanks for any help

---

### Post by bob_the_d on 2006-07-08
Here's a question I have about it though.  I follow you up to the editing the httpd.conf file, but when you set up the aliases, I start to worry.

The thing is that I planned on setting this up on a multi-user system and wanted to have all users to be able to deploy rails code.  But the alias seems to point the rails code from a specific user.  Any way to get around this one?

---

### Post by RadarListener on 2006-07-13
I'm trying to fcgid to work on LAMPP, but at the moment the dispatch.fcgi is showing as plain text.

[http://pastebin.ca/86813](http://pastebin.ca/86813) is my config.

---

### Post by G.Lindqvist on 2006-07-17
> **TheDracle said:**
> For now, do ‘NOT’ gem install mysql (Use the defaults if you plan to use mysql). I haven’t yet discovered a work around to a segfault problem that occurs. A future HOWTO to install the native mysql drivers is needed.


I got problem with installing the mysql gem. Anyone got a clue?

> ERROR:  While executing gem ... (Gem::GemNotFoundException)
    Could not find msyql (> 0) in the repository

---

### Post by HumanAnarchist on 2006-08-08
I can't make this work. I've done what's been said in the guide and read in the rails wiki, but I could not find anyone with the same problem...

```

sudo gem install fcgi

```

AND

```

sudo gem install fcgi -- --with-fcgi-include=/usr/include --with-fcgi-lib=/usr/lib Attempting local installation of 'fcgi'

```

```

Local gem file not found: fcgi*.gem
Attempting remote installation of 'fcgi'
Building native extensions.  This could take a while...
*** extconf.rb failed ***
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
        --ruby=/usr/bin/ruby1.8
        --with-fcgi-dir
        --without-fcgi-dir
        --with-fcgi-include=${fcgi-dir}/include
        --with-fcgi-lib=${fcgi-dir}/lib
ERROR:  While executing gem ... (RuntimeError)
    ERROR: Failed to build gem native extension.
Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.7 for inspection.
  ruby extconf.rb install fcgi -- --with-fcgi-include=/usr/include --with-fcgi-lib=/usr/lib\nchecking for fcgiapp.h... no
checking for fastcgi/fcgiapp.h... no


Results logged to /usr/lib/ruby/gems/1.8/gems/fcgi-0.8.7/ext/fcgi/gem_make.out

```

.ha-

---

### Post by skeeterbug on 2006-08-16
If speed isn't an issue, I would say use CGI with Apache. CGI is nice because you can update thins without restarting the server every time. Currenly im running FCGI on our produciton site, but I've also ran CGI fine too. This box is a windows machine, but I have a mock production server with lighty + fcgi bindings internally. 


[http://www.mission3.com](http://www.mission3.com)

---

### Post by jjjhead on 2006-08-18
To build Fastcgi with Apache 2.2.x, you need to modify the fcgi.h file. 

Here is the instruction: [http://hack.emilykwan.com/node/95]("http://hack.emilykwan.com/node/95")

---

### Post by jeffvc on 2006-10-08
> **HumanAnarchist said:**
> I can't make this work. I've done what's been said in the guide and read in the rails wiki, but I could not find anyone with the same problem...

I had the same problem under Dapper.

I went through quite a bit of pain trying to get the fcgi gem to install. I eventually managed to do it, but had to compile the fcgi dev libraries from scratch.  I did a bit more looking around and found these on the Ubuntu help site:

[LIST]
[*][Ubuntu Documentation RubyOnRails]("https://help.ubuntu.com/community/RubyOnRails")
[*][Ubuntu Documentation ApacheRailsFCGI]("https://help.ubuntu.com/community/ApacheRailsFCGI")
[/LIST]

I started again from scratch, and following these documents I had Rails up and running in no time.

---

### Post by danaildelev on 2006-10-13
It's just perfect

[http://www.bulgariancoastalproperties.com/](http://www.bulgariancoastalproperties.com/)

---

### Post by skeeterbug on 2006-10-27
If anyone is still using FastCGI and having problems, check out Mongrel + Apache.

[http://mongrel.rubyforge.org/docs/apache.html](http://mongrel.rubyforge.org/docs/apache.html)


I switched my companies website from fastCGI to this setup, and I will never look back! :-D

---

### Post by chris.olsen on 2006-11-07
This is what I get when trying to install rubygems.  After this when I then  try to install ruby on rails it hurls right away.
---------
 sudo ruby setup.rb
---> bin
<--- bin
---> lib
---> lib/rubygems
<--- lib/rubygems
<--- lib
---> bin
adjusting shebang: gem_mirror
<--- bin
---> lib
---> lib/rubygems
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/local/bin/
install gemwhich /usr/local/bin/
install gem /usr/local/bin/
install gem_server /usr/local/bin/
install generate_yaml_index.rb /usr/local/bin/
install update_rubygems /usr/local/bin/
install gem_mirror /usr/local/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/
install ubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
install rubygems.rb /usr/local/lib/ruby/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/ruby/site_ruby/1.8/
---> lib/rubygems
mkdir -p /usr/local/lib/ruby/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install cmd_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install loadpath_manager.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install deployment.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/ruby/site_ruby/1.8/rubygems
<--- lib/rubygems
<--- lib

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__': No such file to load -- syck (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/1.8/yaml/syck.rb:5
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/1.8/yaml.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require__'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:21:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:6
         ... 13 levels...
        from setup.rb:887:in `exec_install'
        from setup.rb:705:in `invoke'
        from setup.rb:674:in `invoke'
        from setup.rb:1352

---

### Post by maddog39 on 2006-11-25
> **hotani said:**
> What about Dapper/apache2/fcgid?

Documentation I've read so far has said to use fcgi instead of fastCGI on Apache 2, so that is how I've attempted to set it up.

It looked like all the necessary items were available in Synaptic, so I installed them. However, although the ruby html test page comes up in my test app, rails doesn't seem to be working correctly. I tried adding a controller and got "page not found." Seems like something wrong with my configuration but I can't figure out what. Could someone post up/link to a sample .htaccess or something?

EDIT: Found it! Near the bottom of [this page](http://wiki.rubyonrails.com/rails/pages/RailsOnUbuntuDebianTestingAndUnstable) is a great explanation of a virtual host setup, fcgi and the .htaccess file, as well as an example.
Ermm... fcgi is fastCGI, I know because my web host uses fastCGI and fcgi is the extension for fastCGI.

---

### Post by bribaetz on 2007-08-07
yay i got the first reply in months

---

### Post by mickeyWD on 2007-09-08
Hi all,
is this guide up to date?

I've setup ubuntu server 7.04 with rails
and script/console give me the prompt without errors.
Have I to install readline?

---

### Post by mickeyWD on 2007-09-10
mod_fcgid is better then mod_fastcgi.

I think this is a good start point for Ubuntu users:
[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by Keymone on 2007-09-17
i would recommend to use nginx + mongrel_cluster + ruby on rails instead of apache

---

### Post by iperez on 2007-09-20
I just created a deb package for it and a repository that can be added to your sources.list.

See it here [http://salomon.ls.fi.upm.es/proxectos/rails-deb.html](http://salomon.ls.fi.upm.es/proxectos/rails-deb.html).

The deb contains dependencies and a script that calls gem install fcgi if it cannot be found. Extract the files from the deb to see what it actually has, and please send me any suggestions you have.

I will create other package for mongrel (some help would be appreciated, I can add other people's packages to this tree), and I will also add some basic documentation in future versions of the packages.

Ivan.

---

### Post by iperez on 2007-09-20
I just created a deb package for it and a repository that can be added to your sources.list.

See it here [http://salomon.ls.fi.upm.es/proxectos/rails-deb.html](http://salomon.ls.fi.upm.es/proxectos/rails-deb.html).

The deb contains dependencies and a script that calls gem install fcgi if it cannot be found. Extract the files from the deb to see what it actually does, and please send me any suggestions you have.

I will create other package for mongrel (some help would be appreciated, I can add other people's packages to this tree), and I will also add some basic documentation in future versions of the packages.

Ivan.

---

### Post by Railsbuntu on 2007-12-29
> **Keymone said:**
> i would recommend to use nginx + mongrel_cluster + ruby on rails instead of apache

Do you have a good tutorial on how to install all this? I am stuck during the configuration of mongrel when issuing:
```
sudo mongrel_rails cluster::configuer -e production -p 8000 -N 3 -c /var/www/myrailsapp --user www-data --group www-data
```

I get:
```
!!! Path to config file not valid: config/mongrel_cluster.yml
cluster::configure reported an error. Use mongrel_rails cluster::configure -h to get help.

```
Which is not super helpful.


When I search the mongrel_cluster.yml file, it doesn't exist on my harddrive.

EDIT: FIXED!

You actually have to be inside your rails application directory.

---

### Post by davidomundo on 2008-02-04
I also recommend using nginx.
However, instead of mongrel, I would use thin, which is the new ruby server on the block.

Here are some comparison pages:

[http://www.wikivs.com/wiki/NGINX_vs_LigHTTPd]("http://www.wikivs.com/wiki/NGINX_vs_LigHTTPd")

[http://www.wikivs.com/wiki/Mongrel_vs_Thin]("http://www.wikivs.com/wiki/Mongrel_vs_Thin")

---


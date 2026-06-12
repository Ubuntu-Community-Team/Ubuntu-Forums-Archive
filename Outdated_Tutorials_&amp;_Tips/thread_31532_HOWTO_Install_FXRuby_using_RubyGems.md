---
title: "HOWTO: Install FXRuby using RubyGems"
date: 2005-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by redge on 2005-05-03
FXRuby is a Ruby extension module that provides an interface to the FOX GUI library.
During installation in Ubuntu, I ran into several small problems - that's why I will summarize the installation here, in case that anyone else gets stuck during installation.

First of all, you have to install all required Ruby libraries (using apt-get or aptitude or whatever):

Ruby itself:
[list]
[*]ruby
[*]libruby
[*]irb (Interactive RuBy, this is optional)
[/list] 

Additional libraries:
[list]
[*]build-essential
[*]xlibs-dev 
[*]libyaml-ruby 
[*]libzlib-ruby
[*]libwebrick-ruby (needed for gem_server)
[/list] 

You will also need the Fox Toolkit, of course. Since the repository only includes a binary for Fox 1.0, you will need to download and compile a newer Version yourself.
Get version 1.2 from here:
[http://www.fox-toolkit.org/ftp/fox-1.2.16.tar.gz](http://www.fox-toolkit.org/ftp/fox-1.2.16.tar.gz) 
I recommend version 1.2, since it is (as far as I know) the latest version which is supported by FXRuby. 

Now, you should be able to install it the usual way: 

```
tar -xvzf fox-1.2.16.tar.gz
cd fox-1.2.16
./configure
make
sudo make install
```

This has the disadvantage that this Fox version won't be listed in the apt-repository (which would be handy for a deinstallation).
So I recommend you install 'checkinstall' (which can be found in 'universe'). This tool will monitor the installation progress and will then create a package which will be listed in the apt-repository.

So, after installation of 'checkinstall', you should use the following command instead of the above:

```
tar -xvzf fox-1.2.16.tar.gz
cd fox-1.2.16
./configure
make
sudo checkinstall -D
```

And the rest will be done automatically. 
If the installation fails because some X header files are missing, you'll have to install the following package: xlibs-dev (it should be in the Ubuntu repositories).

If compilation succeeded, you have to make your system aware of the fox library, so that FXRuby can find the library later on. 
One way to do this is to modify the LD_LIBRARY_PATH environment variable to include the directory where libFOX-1.2.so is installed. For example, if libFOX-1.2.so is installed in /usr/local/lib (which will normally be the case), try setting:

```
export LD_LIBRARY_PATH=/usr/local/lib
```

If this works, you can of course permanently add the LD_LIBRARY_PATH setting to your login file(s) so that you don't have to remember to type it each time. Another approach that should work for Linux is to modify your /etc/ld.so.conf  file to include the installation directory (e.g. /usr/local/lib). If you'd like to do this instead, you'll need to (as root):

[list=1]
[*]Edit your /etc/ld.so.conf file and add the directory where libFOX.so is installed; and,
[*]At the shell prompt, type ldconfig to reload the linker configuration.
[/list] 

Now that the Fox Toolkit is installed, you have to install RubyGems, Ruby's packaging system. You could install FXRuby directly, but the Gems system makes it easier to upgrade your Ruby extensions, or to install several versions of one extension simultaneously. Unfortunately, RubyGems cannot be found in the Ubuntu repositories.

But you can get it from [http://rubygems.rubyforge.org](http://rubygems.rubyforge.org) and run (as root, if appropriate and necessary)

```
ruby setup.rb
```

That should suffice for RubyGems to work!

Now, finally, we are able to install FXRuby. Run the following command:

```
sudo gem install fxruby
```

You are then prompted for the version you would like to install -- choose the latest (at the time of this writing, this was fxruby 1.2.6).

Compilation will take several minutes. On my system, I received lots of warnings during compilation -- but as long as it does not stop with an error, you can ignore them.

If you installed irb at the beginning, you can now use it to test your FXRuby installation. Start irb and type in the following:

```

irb(main):001:0> require 'rubygems'
=> true
irb(main):002:0> require_gem 'fxruby'
=> true
irb(main):003:0> include Fox
=> Object

```

If it works that far, FXRuby should have been successfully installed -- congratulations!!

---

### Post by stoffe on 2005-07-08
My compilation failed due to missing dependencies, turns out I had to add another library (Xxf86vm) by hand to configure.in, line 128 (in that particular version of Fox anyways) before configure to make it build:
```
X_BASE_LIBS="-lXext -lX11 -lXxf86vm"
``` 
Managed to arrive at this solution by finding similar errors via Google. It seems to be related to X.org somehow, and it is possible that this library isn't installed by default either, but I had it installed.

I haven't really dug into to why's or anything, but if someone else gets stumped like me and need a quick black box-fix, this did it for me.

---

### Post by stoffe on 2005-07-08
Also, it is very common that you will want fxscintilla support too, make sure to download, build and install fxscintilla before running the gem install. You can grab it from here: [http://savannah.nongnu.org/download/fxscintilla/](http://savannah.nongnu.org/download/fxscintilla/) - just get the latest and do the configure, make, make/checkinstall dance as usual. The gem build will pick it up.

Furtermore, remember that applications needs to be changed from for instance: ```
require 'fox12'
``` to the appropriate ```
require 'rubygems'
require_gem 'fxruby'
```. 

My specific reason for installing this was to try out the editor [Mondrian](http://mondrian-ide.com/), which needs both fxscintilla and the "require"-change in the main file to work.

---

### Post by zaphy on 2007-07-23
I found that feisty does support fox without manually downloading source-files.

I did

aptitude install libfox-1.6-0 libfox-1.6-dev libfox-1.6-doc

And after these packages were installed a

gem install fxruby

did succeed.

FXRuby-version was 1.6.11

---

### Post by Flak Magnet on 2007-08-01
Errors to the effect of:
[I]
Building native extensions.  This could take a while...
extconf.rb:4:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:4

ERROR:  While executing gem ... (RuntimeError)
    ERROR: Failed to build gem native extension.
Gem files will remain installed in /var/lib/gems/1.8/gems/fxruby-1.6.11 for inspection.


Results logged to /var/lib/gems/1.8/gems/fxruby-1.6.11/ext/fox16/gem_make.out[/I]

Can be fixed with a quick:

*apt-get install ruby1.8-dev*

Perhaps that should be added to the list of pkgs in the how-to.

---

### Post by ilbs2005 on 2007-08-11
Ubuntu 7
Fox 1.7.11 (Installed by source)
FXRuby 1.6.11 (Installed by gem)
gcc 4.1.2
irb 0.9.5
ruby 1.8.5

irb(main):001:0> require 'rubygems'
=> true
irb(main):002:0> require_gem 'fxruby'
=> true
irb(main):003:0> include Fox
NameError: uninitialized constant Fox
       from (irb):3


What is this???

I have tried those commands but no success:
require 'fox14'
require 'fox15'
require 'fox16'
require 'fox17'
require_gem 'fox14'
require_gem 'fox15'
require_gem 'fox16'
require_gem 'fox17'


Thanks in advance

---

### Post by maxeem on 2007-11-09
Ububtu Feisty Fawn

sudo aptitude install libfox-1.6-dev

download [http://rubyforge.org/frs/download.php/26727/FXRuby-1.6.12.tar.gz](http://rubyforge.org/frs/download.php/26727/FXRuby-1.6.12.tar.gz)

tar -xvzf FXRuby-1.6.12.tar.gz
cd FXRuby-1.6.12
ruby install.rb config
ruby install.rb setup
sudo ruby install.rb install

checking...

irb(main):001:0> require 'fox16'
=> true
irb(main):002:0> include Fox
=> Object

works fine

---

### Post by jk.cheng on 2010-08-10
Ubuntu 10.04

```

require 'rubygems'
require 'fox16'

gem 'fxruby'

include Fox

```

This work fine on my box.

---


---
title: "What is 'gl' and where do I get it for Edgy?"
date: 2007-10-09
forum: Programming Talk
---

### Post by frisket on 2007-10-09
I wanted to play around with gl_tail, the graphical realtime logfile display from [http://www.fudgie.org/](http://www.fudgie.org/) so I installed Ruby and assorted other dependencies mentioned, using Synaptic, plus rubygems from hints on CoderSifu (there appears to be no such things as rubygems package for Edgy).

However, the app is missing 'gl'. The error message says:

$ ./gl_tail-0.04.rb 
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- gl (LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from ./gl_tail-0.04.rb:67
$

I assumed (in my naivety) that libopengl-ruby would have provided this, but apparently not. Does anyone know what plain unvarnished 'gl' is and where I can get it?

---

### Post by indecisive on 2007-10-09
Installing freegl, freeglut, or packages by that name (look in Synaptic) *might* help.

---

### Post by TomPreuss on 2007-10-09
> **frisket said:**
> I wanted to play around with gl_tail, the graphical realtime logfile display from [http://www.fudgie.org/](http://www.fudgie.org/) so I installed Ruby and assorted other dependencies mentioned, using Synaptic, plus rubygems from hints on CoderSifu (there appears to be no such things as rubygems package for Edgy).

However, the app is missing 'gl'. The error message says:

$ ./gl_tail-0.04.rb 
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- gl (LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from ./gl_tail-0.04.rb:67
$

I assumed (in my naivety) that libopengl-ruby would have provided this, but apparently not. Does anyone know what plain unvarnished 'gl' is and where I can get it?

I'm also attempting to get this same script to work (saw it [on Slashdot yesterday](http://developers.slashdot.org/article.pl?sid=07/10/07/1232245), eh?).  Have you done the following (from the instructions within the script)?

```
sudo apt-get install rubygems rake ruby1.8-dev libgl1-mesa-dev libglut3-dev
sudo gem install -y net-ssh ruby-opengl -r
```

All of those packages installed for me in Feisty, but I get this same exact error you do.  I'm going to try emailing Erlend and pointing him to this thread for some help.

---

### Post by Fbot1 on 2007-10-09
That's very strange. The only thing I can suggest is to reinstall rubygems.

---

### Post by sublimespot on 2007-10-10
Exact same problem. I emailed the author

---

### Post by Fudgie on 2007-10-10
Humm.. I've tried it on both Feisty and Gutsy, and something like this has worked fine both times:
```
  sudo apt-get install rubygems rake ruby1.8-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev build-essential
  sudo gem install -y net-ssh ruby-opengl -r

```

What happens if you install irb and type:
```
irb
require 'rubygems'
gem 'ruby-opengl'
require 'gl'
require 'glut'
gem 'net-ssh'

```

Does that work? If so, replace the require section of the script with that.

---

### Post by TomPreuss on 2007-10-10
> **Fudgie said:**
> Humm.. I've tried it on both Feisty and Gutsy, and something like this has worked fine both times:
```
  sudo apt-get install rubygems rake ruby1.8-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev build-essential
  sudo gem install -y net-ssh ruby-opengl -r

```
This looks okay:
```
$ sudo apt-get install rubygems rake ruby1.8-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rubygems is already the newest version.
rake is already the newest version.
ruby1.8-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libglu1-mesa-dev is already the newest version.
libglut3-dev is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

> **Fudgie said:**
> What happens if you install irb and type:
```
irb
require 'rubygems'
gem 'ruby-opengl'
require 'gl'
require 'glut'
gem 'net-ssh'

```

Does that work? If so, replace the require section of the script with that.
Here we go, this looks like something to work on:
```
$ irb
irb(main):001:0> require 'rubygems'
=> true
irb(main):002:0> gem 'ruby-opengl'
=> true
irb(main):003:0> require 'gl'
LoadError: no such file to load -- gl
        from /usr/lib/ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/lib/ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from (irb):3
irb(main):004:0> require 'glut'
=> true
irb(main):005:0> gem 'net-ssh'
=> true
irb(main):006:0> 

```

---

### Post by Fudgie on 2007-10-10
And the output of 
```
sudo gem install ruby-opengl
```
please?

(Select version 0.40.1 for your architecture, option 2, I think it is)

---

### Post by jgabrielygalan on 2007-10-10
Hi, I had the exact same problems, and after installing the required packages with apt-get (everything successful) installing the suggested gems says: 

$ sudo gem install -y net-ssh ruby-opengl -r
Successfully installed net-ssh-1.1.2
Installing ri documentation for net-ssh-1.1.2...
Installing RDoc documentation for net-ssh-1.1.2...
Select which gem to install for your platform (i486-linux)
 1. ruby-opengl 0.40.1 (i386-mswin32)
 2. ruby-opengl 0.40.1 (ruby)
 3. ruby-opengl 0.40.0 (ruby)
 4. ruby-opengl 0.33.0 (ruby)
 5. Cancel installation
> 2
Building native extensions.  This could take a while...
/usr/bin/ruby1.8 mkrf_conf.rb
rake
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-2.0.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.2.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-2.1.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.3.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.4.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.5.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-enums.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.0-1.1.c
gcc -shared  -L/usr/lib  -o gl.so gl.o gl-2.0.o gl-1.2.o gl-2.1.o gl-1.3.o gl-1.4.o gl-1.5.o gl-enums.o gl-1.0-1.1.o  -lpthread -ldl -lcrypt -lm -lGL -lruby1.8
cp ext/gl/gl.so lib
/usr/bin/ruby1.8 mkrf_conf.rb
rake
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c glu.c
glu.c: In function ‘free_tess’:
glu.c:512: warning: unused variable ‘call_key’
glu.c:511: warning: unused variable ‘id’
glu.c: In function ‘glu_TessVertex’:
glu.c:944: warning: unused variable ‘id’
glu.c:943: warning: unused variable ‘call_key’
glu.c: In function ‘glu_ErrorString’:
glu.c:1400: warning: pointer targets in passing argument 1 of ‘rb_str_new2’ differ in signedness
glu.c: In function ‘glu_GetString’:
glu.c:1414: warning: pointer targets in passing argument 1 of ‘rb_str_new2’ differ in signedness
gcc -shared  -L/usr/lib  -o glu.so glu.o  -lpthread -ldl -lcrypt -lm -lGLU -lGL -lruby1.8
cp ext/glu/glu.so lib
/usr/bin/ruby1.8 mkrf_conf.rb
rake
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c glut.c
glut.c: In function ‘glut_KeyboardFunc’:
glut.c:198: warning: passing argument 1 of ‘glutKeyboardFunc’ from incompatible pointer type
glut.c: In function ‘glut_AddMenuEntry’:
glut.c:581: warning: unused variable ‘value’
glut.c: In function ‘glut_ChangeToMenuEntry’:
glut.c:618: warning: unused variable ‘value’
glut.c: In function ‘glut_BitmapCharacterX’:
glut.c:1099: warning: unused variable ‘font’
glut.c: At top level:
glut.c:836: warning: ‘glut_MenuStateFunc’ defined but not used
gcc -shared  -L/usr/lib  -o glut.so glut.o  -lpthread -ldl -lcrypt -lm -lglut -lGLU -lGL -lruby1.8
cp ext/glut/glut.so lib
rm -r ext/gl/Rakefile
rm -r ext/glu/Rakefile
rm -r ext/glut/Rakefile
rm -r ext/gl/mkrf.log
rm -r ext/glu/mkrf.log
rm -r ext/glut/mkrf.log
rm -r ext/gl/gl.so
rm -r ext/glu/glu.so
rm -r ext/glut/glut.so
rm -r lib/gl.so
rm -r lib/glu.so
rm -r lib/glut.so
rm -r ext/gl/gl.o
rm -r ext/gl/gl-2.0.o
rm -r ext/gl/gl-1.2.o
rm -r ext/gl/gl-2.1.o
rm -r ext/gl/gl-1.3.o
rm -r ext/gl/gl-1.4.o
rm -r ext/gl/gl-1.5.o
rm -r ext/gl/gl-enums.o
rm -r ext/gl/gl-1.0-1.1.o
rm -r ext/glu/glu.o
rm -r ext/glut/glut.o
rm -r pkg
rake RUBYARCHDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1)
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/ext/gl)
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/ext/glu)
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/ext/glut)

rake RUBYARCHDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib install
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1)
rake aborted!
Don't know how to build task 'install'

(See full trace by running task with --trace)

rake RUBYARCHDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib clean
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1)
Successfully installed ruby-opengl-0.40.1

Hope this helps,

Jesus.

---

### Post by Fudgie on 2007-10-10
> **jgabrielygalan said:**
> 
rake RUBYARCHDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1/lib install
(in /usr/lib/ruby/gems/1.8/gems/ruby-opengl-0.40.1)
rake aborted!
Don't know how to build task 'install'


Here's your problem.

sudo gem update --system

should solve it. (ruby-opengl requires gems version 0.9.1+)

I'll be catching that problem and printing the fix in version 0.05 (along with other common installation problems).

---

### Post by jgabrielygalan on 2007-10-10
> **Fudgie said:**
> Here's your problem.

sudo gem update --system

should solve it. (ruby-opengl requires gems version 0.9.1+)

I'll be catching that problem and printing the fix in version 0.05 (along with other common installation problems).


Thanks, that worked like a charm. I'll be having some fun monitoring the logs now. Thanks for the program too, keep up the good work and the fun ideas.

Regards,

Jesus.

---

### Post by TomPreuss on 2007-10-10
> **Fudgie said:**
> And the output of 
```
sudo gem install ruby-opengl
```
please?

(Select version 0.40.1 for your architecture, option 2, I think it is)

Done.  Output:

```
$ sudo gem install ruby-opengl
Password:
Select which gem to install for your platform (i486-linux)
 1. ruby-opengl 0.40.1 (i386-mswin32)
 2. ruby-opengl 0.40.1 (ruby)
 3. ruby-opengl 0.40.0 (ruby)
 4. ruby-opengl 0.33.0 (ruby)
 5. Cancel installation
> 2
Building native extensions.  This could take a while...
/usr/bin/ruby1.8 mkrf_conf.rb
rake
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-2.0.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.2.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-2.1.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.3.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.4.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.5.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-enums.c
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c gl-1.0-1.1.c
gcc -shared  -L/usr/lib  -o gl.so gl.o gl-2.0.o gl-1.2.o gl-2.1.o gl-1.3.o gl-1.4.o gl-1.5.o gl-enums.o gl-1.0-1.1.o  -lpthread -ldl -lcrypt -lm -lGL -lruby1.8
cp ext/gl/gl.so lib
/usr/bin/ruby1.8 mkrf_conf.rb
rake
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c glu.c
glu.c: In function ‘free_tess’:
glu.c:512: warning: unused variable ‘call_key’
glu.c:511: warning: unused variable ‘id’
glu.c: In function ‘glu_TessVertex’:
glu.c:944: warning: unused variable ‘id’
glu.c:943: warning: unused variable ‘call_key’
glu.c: In function ‘glu_ErrorString’:
glu.c:1400: warning: pointer targets in passing argument 1 of ‘rb_str_new2’ differ in signedness
glu.c: In function ‘glu_GetString’:
glu.c:1414: warning: pointer targets in passing argument 1 of ‘rb_str_new2’ differ in signedness
gcc -shared  -L/usr/lib  -o glu.so glu.o  -lpthread -ldl -lcrypt -lm -lGLU -lGL -lruby1.8
cp ext/glu/glu.so lib
/usr/bin/ruby1.8 mkrf_conf.rb
rake
gcc  -fPIC -Wall -g -fno-strict-aliasing -O2  -fPIC   -I/usr/include -I/usr/lib/ruby/1.8/i486-linux -I/usr/local/lib/site_ruby/1.8 -I. -c glut.c
glut.c: In function ‘glut_KeyboardFunc’:
glut.c:198: warning: passing argument 1 of ‘glutKeyboardFunc’ from incompatible pointer type
glut.c: In function ‘glut_AddMenuEntry’:
glut.c:581: warning: unused variable ‘value’
glut.c: In function ‘glut_ChangeToMenuEntry’:
glut.c:618: warning: unused variable ‘value’
glut.c: In function ‘glut_BitmapCharacterX’:
glut.c:1099: warning: unused variable ‘font’
glut.c: At top level:
glut.c:836: warning: ‘glut_MenuStateFunc’ defined but not used
gcc -shared  -L/usr/lib  -o glut.so glut.o  -lpthread -ldl -lcrypt -lm -lglut -lGLU -lGL -lruby1.8
cp ext/glut/glut.so lib
rm -r ext/gl/Rakefile
rm -r ext/glu/Rakefile
rm -r ext/glut/Rakefile
rm -r ext/gl/mkrf.log
rm -r ext/glu/mkrf.log
rm -r ext/glut/mkrf.log
rm -r ext/gl/gl.so
rm -r ext/glu/glu.so
rm -r ext/glut/glut.so
rm -r lib/gl.so
rm -r lib/glu.so
rm -r lib/glut.so
rm -r ext/gl/gl.o
rm -r ext/gl/gl-2.0.o
rm -r ext/gl/gl-1.2.o
rm -r ext/gl/gl-2.1.o
rm -r ext/gl/gl-1.3.o
rm -r ext/gl/gl-1.4.o
rm -r ext/gl/gl-1.5.o
rm -r ext/gl/gl-enums.o
rm -r ext/gl/gl-1.0-1.1.o
rm -r ext/glu/glu.o
rm -r ext/glut/glut.o
rm -r pkg
rake RUBYARCHDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.40.1/lib
(in /var/lib/gems/1.8/gems/ruby-opengl-0.40.1)
(in /var/lib/gems/1.8/gems/ruby-opengl-0.40.1/ext/gl)
(in /var/lib/gems/1.8/gems/ruby-opengl-0.40.1/ext/glu)
(in /var/lib/gems/1.8/gems/ruby-opengl-0.40.1/ext/glut)

rake RUBYARCHDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.40.1/lib install
(in /var/lib/gems/1.8/gems/ruby-opengl-0.40.1)
rake aborted!
Don't know how to build task 'install'

(See full trace by running task with --trace)

rake RUBYARCHDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.40.1/lib RUBYLIBDIR=/var/lib/gems/1.8/gems/ruby-opengl-0.40.1/lib clean
(in /var/lib/gems/1.8/gems/ruby-opengl-0.40.1)
Successfully installed ruby-opengl-0.40.1

```

> **Fudgie said:**
> Here's your problem.

sudo gem update --system

should solve it. (ruby-opengl requires gems version 0.9.1+)

I'll be catching that problem and printing the fix in version 0.05 (along with other common installation problems).

Also done.  Output:

```
$ sudo gem update --system
Updating RubyGems...
Attempting remote update of rubygems-update
Successfully installed rubygems-update-0.9.4
Updating version of RubyGems to 0.9.4
Installing RubyGems 0.9.4
---> bin
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
---> lib/rubygems/commands
<--- lib/rubygems/commands
---> lib/rubygems/digest
<--- lib/rubygems/digest
<--- lib/rubygems
<--- lib
---> bin
updating shebang: gem
updating shebang: gem_mirror
updating shebang: gem_server
updating shebang: gemlock
updating shebang: gemri
updating shebang: gemwhich
updating shebang: index_gem_repository.rb
updating shebang: update_rubygems
<--- bin
---> lib
---> lib/rbconfig
<--- lib/rbconfig
---> lib/rubygems
---> lib/rubygems/commands
<--- lib/rubygems/commands
---> lib/rubygems/digest
<--- lib/rubygems/digest
<--- lib/rubygems
<--- lib
rm -f InstalledFiles
---> bin
mkdir -p /usr/bin/
install gem /usr/bin/
install gem_mirror /usr/bin/
install gem_server /usr/bin/
install gemlock /usr/bin/
install gemri /usr/bin/
install gemwhich /usr/bin/
install index_gem_repository.rb /usr/bin/
install update_rubygems /usr/bin/
<--- bin
---> lib
mkdir -p /usr/local/lib/site_ruby/1.8/
install gemconfigure.rb /usr/local/lib/site_ruby/1.8/
install rubygems.rb /usr/local/lib/site_ruby/1.8/
install ubygems.rb /usr/local/lib/site_ruby/1.8/
---> lib/rbconfig
mkdir -p /usr/local/lib/site_ruby/1.8/rbconfig
install datadir.rb /usr/local/lib/site_ruby/1.8/rbconfig
<--- lib/rbconfig
---> lib/rubygems
mkdir -p /usr/local/lib/site_ruby/1.8/rubygems
install builder.rb /usr/local/lib/site_ruby/1.8/rubygems
install command.rb /usr/local/lib/site_ruby/1.8/rubygems
install command_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install config_file.rb /usr/local/lib/site_ruby/1.8/rubygems
install custom_require.rb /usr/local/lib/site_ruby/1.8/rubygems
install dependency_list.rb /usr/local/lib/site_ruby/1.8/rubygems
install doc_manager.rb /usr/local/lib/site_ruby/1.8/rubygems
install format.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_commands.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_open_uri.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_openssl.rb /usr/local/lib/site_ruby/1.8/rubygems
install gem_runner.rb /usr/local/lib/site_ruby/1.8/rubygems
install installer.rb /usr/local/lib/site_ruby/1.8/rubygems
install old_format.rb /usr/local/lib/site_ruby/1.8/rubygems
install open-uri.rb /usr/local/lib/site_ruby/1.8/rubygems
install package.rb /usr/local/lib/site_ruby/1.8/rubygems
install remote_fetcher.rb /usr/local/lib/site_ruby/1.8/rubygems
install remote_installer.rb /usr/local/lib/site_ruby/1.8/rubygems
install rubygems_version.rb /usr/local/lib/site_ruby/1.8/rubygems
install security.rb /usr/local/lib/site_ruby/1.8/rubygems
install server.rb /usr/local/lib/site_ruby/1.8/rubygems
install source_index.rb /usr/local/lib/site_ruby/1.8/rubygems
install source_info_cache.rb /usr/local/lib/site_ruby/1.8/rubygems
install source_info_cache_entry.rb /usr/local/lib/site_ruby/1.8/rubygems
install specification.rb /usr/local/lib/site_ruby/1.8/rubygems
install timer.rb /usr/local/lib/site_ruby/1.8/rubygems
install user_interaction.rb /usr/local/lib/site_ruby/1.8/rubygems
install validator.rb /usr/local/lib/site_ruby/1.8/rubygems
install version.rb /usr/local/lib/site_ruby/1.8/rubygems
---> lib/rubygems/commands
mkdir -p /usr/local/lib/site_ruby/1.8/rubygems/commands
install build_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install cert_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install check_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install cleanup_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install contents_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install dependency_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install environment_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install help_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install install_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install list_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install outdated_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install pristine_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install query_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install rdoc_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install search_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install sources_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install specification_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install uninstall_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install unpack_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
install update_command.rb /usr/local/lib/site_ruby/1.8/rubygems/commands
<--- lib/rubygems/commands
---> lib/rubygems/digest
mkdir -p /usr/local/lib/site_ruby/1.8/rubygems/digest
install digest_adapter.rb /usr/local/lib/site_ruby/1.8/rubygems/digest
install md5.rb /usr/local/lib/site_ruby/1.8/rubygems/digest
install sha1.rb /usr/local/lib/site_ruby/1.8/rubygems/digest
install sha2.rb /usr/local/lib/site_ruby/1.8/rubygems/digest
<--- lib/rubygems/digest
<--- lib/rubygems
<--- lib
  Successfully built RubyGem
  Name: sources
  Version: 0.0.1
  File: sources-0.0.1.gem
Removing old RubyGems RDoc and ri...
Installing rubygems-0.9.4 ri...
Installing rubygems-0.9.4 rdoc...

As of RubyGems 0.8.0, library stubs are no longer needed.
Searching $LOAD_PATH for stubs to optionally delete (may take a while)...
...done.
No library stubs found.

RubyGems system software updated

```

Then I get this when trying to run the script: 

```
$ ruby gl_tail-0.05.rb 
Missing or outdated gem: ruby-opengl (>=0.40.1)
Ubuntu:
  sudo apt-get install rake ruby1.8-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev
  sudo gem install -y -r ruby-opengl

```

When I try those commands they return the following:
```
$ sudo apt-get install rake ruby1.8-dev libgl1-mesa-dev libglu1-mesa-dev libglut3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rake is already the newest version.
ruby1.8-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libglu1-mesa-dev is already the newest version.
libglut3-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
and
```
$ sudo gem install -y -r ruby-opengl
Bulk updating Gem source index for: http://gems.rubyforge.org
ERROR:  While executing gem ... (Gem::GemNotFoundException)
    Could not find ruby-opengl (> 0) in any repository

```
I don't get it, I thought I just made sure I had  ruby-opengl 0.40.1, but it says I don't.

Ideas?

---

### Post by Fudgie on 2007-10-11
Try 
```
sudo gem install -y ruby-opengl -r
```
and make sure you pick version 0.40.1.

---

### Post by TomPreuss on 2007-10-11
> **Fudgie said:**
> Try 
```
sudo gem install -y ruby-opengl -r
```
and make sure you pick version 0.40.1.

Okay.  Output:

```
$ sudo gem install -y ruby-opengl -r
Password:
Bulk updating Gem source index for: http://gems.rubyforge.org
Select which gem to install for your platform (i486-linux)
 1. ruby-opengl 0.40.1 (i386-mswin32)
 2. ruby-opengl 0.40.1 (ruby)
 3. ruby-opengl 0.40.0 (ruby)
 4. ruby-opengl 0.33.0 (ruby)
 5. Skip this gem
 6. Cancel installation
> 2
Building native extensions.  This could take a while...
Successfully installed ruby-opengl-0.40.1
Successfully installed mkrf-0.2.2
Successfully installed rake-0.7.3
Installing ri documentation for mkrf-0.2.2...
Installing ri documentation for rake-0.7.3...
Installing RDoc documentation for mkrf-0.2.2...
Installing RDoc documentation for rake-0.7.3...

```

Then I get

```
$ ruby gl_tail-0.05.rb Missing gem net-ssh.
Ubuntu:
  sudo gem install -y -r net-ssh
```

So then:

```
$ sudo gem install -y -r net-ssh
Successfully installed net-ssh-1.1.2
Successfully installed needle-1.3.0
Installing ri documentation for net-ssh-1.1.2...
Installing ri documentation for needle-1.3.0...
Installing RDoc documentation for net-ssh-1.1.2...
Installing RDoc documentation for needle-1.3.0...

```

Now the glTail window opens when I run the script and I get

```
1 frames in 16.890 seconds =  0.059 FPS
Elements[0], Activities[0]
373 frames in  5.008 seconds = 74.481 FPS
Elements[0], Activities[0]
375 frames in  5.012 seconds = 74.820 FPS
Elements[0], Activities[0]
224 frames in  5.027 seconds = 44.559 FPS
Elements[0], Activities[0]
369 frames in  5.010 seconds = 73.653 FPS
Elements[0], Activities[0]
372 frames in  5.020 seconds = 74.104 FPS
Elements[0], Activities[0]
370 frames in  5.007 seconds = 73.897 FPS
Elements[0], Activities[0]
353 frames in  5.011 seconds = 70.445 FPS
Elements[0], Activities[0]

``` in the console, but the glTail window is blank.

---

### Post by Fudgie on 2007-10-11
Then you've either got the wrong login information, the wrong path to the file, or the file in a wrong format. Try enabling the
```
#session_options[:verbose] = :debug 
```
line near the bottom to see the SSH output in the console.

---

### Post by TomPreuss on 2007-10-11
> **Fudgie said:**
> Then you've either got the wrong login information, the wrong path to the file, or the file in a wrong format. Try enabling the
```
#session_options[:verbose] = :debug 
```
line near the bottom to see the SSH output in the console.

You got it, typo in the path to file.

Thanks heaps!

---


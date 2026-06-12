---
title: "Eclipse: Trouble with Ruby Debugger"
date: 2007-04-30
forum: Programming Talk
---

### Post by Ubuntist on 2007-04-30
I'd like to debug Ruby code in the Eclipse IDE under Ubuntu Feisty.

In its preferences window, Eclipse says that "In order to use ruby-debug you have to install the gem ruby-debug-ide...."  OK, in Synaptic I install Ruby Gems and then try to install the right gem:
```

/usr/bin$ sudo gem install ruby-debug-ide
Install required dependency ruby-debug-base? [Yn]  y
Select which gem to install for your platform (i486-linux)
 1. ruby-debug-base 0.9.2 (ruby)
 2. ruby-debug-base 0.9.2 (mswin32)
 3. Cancel installation
> 1
Building native extensions.  This could take a while...
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
        from extconf.rb:1

ERROR:  While executing gem ... (RuntimeError)
    ERROR: Failed to build gem native extension.
Gem files will remain installed in /var/lib/gems/1.8/gems/ruby-debug-base-0.9.2 for inspection.
  

Results logged to /var/lib/gems/1.8/gems/ruby-debug-base-0.9.2/ext/gem_make.out

```That's obviously not good.  The file gem_make.out is empty.

Anybody have any suggestions?

---

### Post by chamstar on 2007-04-30
Have you tried RadRails at all, I know it is Rails focused but it is based around the Ruby Eclipse plugin...

---

### Post by Ubuntist on 2007-05-01
I dunno about RadRails, but using Synaptic I have definitely installed rails.

---

### Post by chamstar on 2007-05-03
RadRails is an IDE based on Eclipse so in runs on JVM which is no problem in Ububtu. Just download it - by the way if you do it is now developed by another company and you want RadRails classic as there new version which is merged with another product does not work on my install.

I installed ruby, irb, rdoc and ir using Synaptic but ruby gems would not work - it appeared to work but did not install any gems. So I had to download gem from the gem website and install it the normal way by running setup.rb, then I installed Rails using gem ie. gem install rails

So I have an up and running Rails install now, I remember from last time there where a couple of other things I had to do, these included installing the mysql bindings and in database.yml I had to put a reference to a socket file.

---

### Post by Ubuntist on 2007-05-29
The problem seems to be solved, at last.

I was able to install the gem ruby-debug-ide after installing ruby-pkg-tools with Synaptic.

Inside Eclipse, I still couldn't get the debugger to run: it still complained that it couldn't find rdebug-ide.  The solution was to go to Window -> Preferences -> Ruby -> Debugger and uncheck "Use ruby-debug library".  Perhaps unchecking this box means that I'm not getting the debugger's full functionality, but basic debugging functionality is available.

---

### Post by cebartling on 2007-12-23
I solved this problem by installing ruby1.8-dev, like so:

**[COLOR="Blue"] sudo apt-get install ruby1.8-dev[/COLOR]**

You will also need build-essentials installed.  All of my native extension build problems ceased once ruby1.8-dev was installed.

---


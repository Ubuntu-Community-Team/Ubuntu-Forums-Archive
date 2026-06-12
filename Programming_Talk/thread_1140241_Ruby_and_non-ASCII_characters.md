---
title: "Ruby and non-ASCII characters"
date: 2009-04-27
forum: Programming Talk
---

### Post by xyzt on 2009-04-27
I'm trying out Ruby. So far it seems fine, but I have a serious problem here on my system: several string methods don't work with characters other than ASCII. For instance:

[COLOR="RoyalBlue"][FONT="Fixedsys"]puts "Olá José António!".reverse[/FONT][/COLOR]

and .upcase won't upcase, etc.

The input method doesn't matter. If the string is entered via [FONT="Fixedsys"]gets[/FONT], the same problem occurs.

What is going on? One is supposed to be able to use his own language? TIA.

---

### Post by Tibuda on 2009-04-27
See this:
[http://www.nabble.com/How-to-upcase-downcase-utf-8-chars--td19300474.html](http://www.nabble.com/How-to-upcase-downcase-utf-8-chars--td19300474.html)

---

### Post by xyzt on 2009-04-27
> **danielrmt said:**
> See this:
[http://www.nabble.com/How-to-upcase-downcase-utf-8-chars--td19300474.html](http://www.nabble.com/How-to-upcase-downcase-utf-8-chars--td19300474.html)

Almost there:

[SIZE="1"][FONT="Fixedsys"]jmccm@ubuntu-base:~$ [COLOR="SeaGreen"]irb -rrubygems -runicode[/COLOR]
/usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': [COLOR="RoyalBlue"]no such file to load -- unicode (LoadError)[/COLOR]
	from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from /usr/lib/ruby/1.8/irb/init.rb:252:in `load_modules'
	from /usr/lib/ruby/1.8/irb/init.rb:250:in `each'
	from /usr/lib/ruby/1.8/irb/init.rb:250:in `load_modules'
	from /usr/lib/ruby/1.8/irb/init.rb:21:in `setup'
	from /usr/lib/ruby/1.8/irb.rb:54:in `start'
	from /usr/bin/irb:13
jmccm@ubuntu-base:~$ [COLOR="SeaGreen"]irb -rrubygems -rUnicode[/COLOR]
/usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `gem_original_require': [COLOR="RoyalBlue"]no such file to load -- Unicode (LoadError)[/COLOR]
	from /usr/lib/ruby/1.8/rubygems/custom_require.rb:31:in `require'
	from /usr/lib/ruby/1.8/irb/init.rb:252:in `load_modules'
	from /usr/lib/ruby/1.8/irb/init.rb:250:in `each'
	from /usr/lib/ruby/1.8/irb/init.rb:250:in `load_modules'
	from /usr/lib/ruby/1.8/irb/init.rb:21:in `setup'
	from /usr/lib/ruby/1.8/irb.rb:54:in `start'
	from /usr/bin/irb:13
jmccm@ubuntu-base:~$ 
[/FONT]
[/SIZE]
The Unicode thing seems to be still missing?

---

### Post by Tibuda on 2009-04-27
Have you installed the unicode gem?
```
sudo aptitude install rubygems # if not installed
sudo gem install unicode
```

---

### Post by xyzt on 2009-04-29
> **danielrmt said:**
> Have you installed the unicode gem?
```
sudo aptitude install rubygems # if not installed
sudo gem install unicode
```

We're not quite there yet... :)

```
leader@toshiba-ubuntu:~$ [COLOR="Lime"]sudo gem install unicode[/COLOR]
Building native extensions.  This could take a while...
[COLOR="Orange"]ERROR:  Error installing unicode:
	ERROR: Failed to build gem native extension.[/COLOR]

/usr/bin/ruby1.8 extconf.rb install unicode
extconf.rb:1:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:1

Gem files will remain installed in /var/lib/gems/1.8/gems/unicode-0.1 for inspection.
Results logged to /var/lib/gems/1.8/gems/unicode-0.1/ext/gem_make.out
```

---

### Post by Tibuda on 2009-04-29
> **xyzt said:**
> We're not quite there yet... :)

mkmf... you need to install the ruby1.8-dev package from synaptic to install the gem. It was already installed on my PC (for other gems), so I didn't got that message when installing the unicode gem. Install build-essentials too, if not already installed.

---

### Post by xyzt on 2009-04-30
Now I'm really at a loss:

```
leader@toshiba-ubuntu:~$ [COLOR="Lime"]sudo gem install unicode[/COLOR]
Building native extensions.  This could take a while...
Successfully installed unicode-0.1
1 gem installed
leader@toshiba-ubuntu:~$ [COLOR="Lime"]irb -rrubygems -runicode[/COLOR]
irb(main):001:0> puts [COLOR="Orange"]"Olá José António!"[/COLOR].reverse
[COLOR="Orange"]!oin&#65533;&#65533;tnA &#65533;&#65533;soJ &#65533;&#65533;lO[/COLOR]
=> nil
irb(main):002:0> 
```

build-essential was already installed (for gcc), ruby1.8-dev was the one missing.

---


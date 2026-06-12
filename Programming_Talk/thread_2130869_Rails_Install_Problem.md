---
title: "Rails Install Problem"
date: 2013-03-30
forum: Programming Talk
---

### Post by TheodoreP on 2013-03-30
Hello, Hello! I am currently enrolled in an online course for ruby on rails programming and I have successfully installed ruby however am having a little trouble installing rails using the suggested method of [FONT=Arial][SIZE=2]
[FONT=Courier New]```
sudo gem install rails --include-dependencies
```

It always gives me the same e[SIZE=2][FONT=Arial]rror[SIZE=2] which I've pasted below.
```

[SIZE=2][SIZE=2]theodorerees@theodorerees-HP-Pavilion-g7-Notebook-PC:~$ sudo gem install rails --include-dependencies
[sudo] password for theodorerees: 
INFO:  `gem install -y` is now default and will be removed
INFO:  use --ignore-dependencies to install only the gems you list
Building native extensions.  This could take a while...
ERROR:  Error installing rails:
    ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
    from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
    from extconf.rb:1:in `<main>'


Gem files will remain installed in /var/lib/gems/1.9.1/gems/json-1.7.7 for inspection.
Results logged to /var/lib/gems/1.9.1/gems/json-1.7.7/ext/json/ext/generator/gem_make.out[/SIZE][/SIZE]
```[/SIZE][/FONT][/SIZE] [/FONT][/SIZE][/FONT]

---

### Post by tgalati4 on 2013-03-30
How did you fix it?

---

### Post by TheodoreP on 2013-04-26
I just wen to the software center and downloaded the railities, bundlerand anything else I needed. To be honest I really can't rememeber. I just know that all you need for ror in ubuntu is available in the software center.

---


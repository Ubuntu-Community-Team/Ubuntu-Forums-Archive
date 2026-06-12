---
title: "Problems Installing FXRuby"
date: 2008-03-02
forum: Programming Talk
---

### Post by GuttaMan on 2008-03-02
I'm trying to install FXRuby on my laptop, but I'm coming into some problems.

Now, I've first compiled and installed FOX successfully. I'm still a relative newbie to Linux, and I've been following exact instructions to install. But when I've tried to FXRuby, I get this:

> jr@TP:~/dls/FXRuby-1.6.13$ ruby install.rb config
install.rb: entering config phase...
---> lib
---> lib/fox16
<--- lib/fox16
<--- lib
---> ext
---> ext/fox16
/usr/bin/ruby1.8 /home/jr/dls/FXRuby-1.6.13/ext/fox16/extconf.rb 
/home/jr/dls/FXRuby-1.6.13/ext/fox16/extconf.rb:4:in `require': no such file to load -- mkmf (LoadError)
        from /home/jr/dls/FXRuby-1.6.13/ext/fox16/extconf.rb:4
config failed
'system /usr/bin/ruby1.8 /home/jr/dls/FXRuby-1.6.13/ext/fox16/extconf.rb ' failed
Try 'ruby install.rb --help' for detailed usage.

Can anybody help me out with this.  Much Thanx

GM

---

### Post by dynnamitt on 2008-05-03
[Hardy 8.04]
Install 'libfox-1.6-dev' . I think that is far quicker and easier than to download the fox-toolkit src files.

'sudo apt-get install libfox-1.6-dev'

(See [http://ubuntuforums.org/showthread.php?t=31532](http://ubuntuforums.org/showthread.php?t=31532))

When I installed the above lib and did 'ruby install.rb config' from the fxruby-src-folder I did not get any errors....

BUT THEN when running 'ruby install.rb setup' It started to complain' about xrandr, so I fugured some extra *-dev lib was needed: 

'sudo apt-get install libxrandr-dev'


(fxruby version 1.16.14)

---


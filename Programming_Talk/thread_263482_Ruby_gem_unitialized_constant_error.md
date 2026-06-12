---
title: "Ruby gem unitialized constant error"
date: 2006-09-23
forum: Programming Talk
---

### Post by mistermax on 2006-09-23
I recently got the excellent Ruby cookbook and scanning through quickly seized upon the Blinkenlights examples.

However I'm seeing something like this:
 ./blinkenlights.rb
./blinkenlights.rb:7: uninitialized constant BlinkenLights (NameError)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from ./blinkenlights.rb:4


whenever I try to execute the script
#!/usr/bin/ruby

require 'rubygems'
require 'blinkenlights'

#Turn individual lights on and off
BlinkenLights.open do |lights|
    lights.left     = true
    lights.middle   = true
    lights.right    = true

    lights.scr = false
    lights.cap = false
    lights.num = false
end

#Dislay a light show
BlinkenLights.open do |lights|
    lights.left_to_right
    10.times{ lights.random }
    lights.right_to_left
end



I'm on 6.06 and I have the gem installed, I used sudo gem install blinkenlights and can list my local gems and see it.

So why do I get this error?

---


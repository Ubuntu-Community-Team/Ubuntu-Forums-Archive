---
title: "Ruby Socket Woes"
date: 2009-12-25
forum: Programming Talk
---

### Post by qalimas on 2009-12-25
```

Thread.new do |server|
  socket = TCPSocket.open('localhost', 6789)
    
  loop do

    #var = socket.gets
    command = socket.gets
    
    
    var = command.split
    puts var.inspect
    @glade["layout1"].move(@glade.get_widget("image2"), var[0], var[1])

  end
end

```


If I comment out the glade line, everything works fine, but the problem is that I want the socket to take the incoming data, and move an image in my application to the specified coordinates.

The data is being transfered, and all works well without that line.  With teh line not-commented, anytime data is sent through the server, it will print the first piece of data sent, then hang and print nothing else, as if it were stuck on the glade function.



Any ideas? :'(

---

### Post by qalimas on 2009-12-25
Edit: Ignore this post

---

### Post by qalimas on 2009-12-26
This is continuing to confuse me.

The first two conditions, when met, so what is expected of them.  The third however, locks the socket up, and the first two conditions no longer respon, even when met.  The test telnet connection to the same port as the application can still recieve data from the program, but the program can no longer recieve data from anything D=


```
def dowith_me(var)
  scommand = var.split
  
  if scommand[0] == "show"
    $o.glade["image2"].visible = true
  elsif scommand[0] == "hide"
    $o.glade["image2"].visible = false
  elsif scommand[0] == "move"
    $o.glade.move($o.glade.get_widget("image2"), 48, 48)
  end
  
  #puts scommand.inspect
  #move_image(scommand[0].to_i, scommand[1].to_i)
end
```

The code that calls the function:
```
#!/usr/bin/env ruby
## This file is part of Game of Trace
require 'rubygems'
require 'eventmachine'
require 'socket'


Thread.new do |server|

  socket = TCPSocket.open('localhost', 6789)
    
  while line = socket.gets
    dowith_me(line.chop)
  end
  
  socket.close

end
```


I'm **really** trying here, but this is damned weird..

Edit: I forgot to mention, `$o.glade.move($o.glade.get_widget("image2"), 48, 48)` called normally (not done through a thread) works perfectly fine...

---

### Post by qalimas on 2010-01-01
Bump :(

---


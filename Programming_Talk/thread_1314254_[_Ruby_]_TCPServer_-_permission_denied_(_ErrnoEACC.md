---
title: "[ Ruby ] TCPServer - permission denied ( Errno::EACCES )"
date: 2009-11-04
forum: Programming Talk
---

### Post by liquidbee on 2009-11-04
What's wrong with this code ? Why I keep getting [COLOR=Red]Permission denied[/COLOR] when creating a new [COLOR=Blue]TCPServer[/COLOR] object ?

```
require 'socket'

port = (ARGV[0] || 80).to_i
server = TCPServer.new("localhost", port)

```

```
./httpserver.rb:6:in `initialize': Permission denied - bind(2) (Errno::EACCES)
    from ./httpserver.rb:6:in `new'
    from ./httpserver.rb:6
```

---

### Post by dwhitney67 on 2009-11-04
You need root-permissions to bind to a port that is less than 1024.  I cannot tell from the snippet that you provided if you are attempting to use port 80 or some other port number within argv[0].

---

### Post by liquidbee on 2009-11-04
> **dwhitney67 said:**
> You need root-permissions to bind to a port that is less than 1024.  I cannot tell from the snippet that you provided if you are attempting to use port 80 or some other port number within argv[0].

Thank you very much - seems to be the case. Upon changing ( passing an argument ) the port to 3080 ( just an example ), everything works as excepted :)

---


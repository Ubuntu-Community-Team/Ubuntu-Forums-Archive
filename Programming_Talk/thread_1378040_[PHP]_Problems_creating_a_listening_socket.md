---
title: "[PHP] Problems creating a listening socket"
date: 2010-01-10
forum: Programming Talk
---

### Post by Vunutus on 2010-01-10
I'm attempting to code a fairly basic script to serve up messages to a few clients via sockets.

I've been stopped in my tracks very early on, however. When I try to call socket_create_listen(), I get the following error:

PHP Fatal error:  Call to undefined function socket_create_listen()

My code:
```

<?php
$socket = socket_create_listen("4050");

if(!$socket)
{
  print "Failed to create socket!\n";
  exit;
}

while (true)
{
  $player = socket_accept($socket);
  
  while(true)
  {
    $input = trim(socket_read($player, 256));
    if(trim($input) == "CHAT:Vunutus")
      socket_write($player, "YES:TinTin");
  }
  socket_close($player);
}

socket_close($socket);
?>
```

Not sure what I'm doing wrong here. I've never used PHP sockets before. I didn't have any problems using fsockopen()...

---

### Post by CyberJack on 2010-01-11
Can you check if sockets are enabled? because it seems like your php version is compiled without socket support.
You can do this by looking at phpinfo() and check if there is a part called "sockets". The line below should say "Sockets Support: enabled"

From the php manual page about sockets:
> The socket functions described here are part of an extension to PHP which must be enabled at compile time by giving the --enable-sockets option to configure.

---

### Post by Vunutus on 2010-01-11
> **CyberJack said:**
> Can you check if sockets are enabled? because it seems like your php version is compiled without socket support.
You can do this by looking at phpinfo() and check if there is a part called "sockets". The line below should say "Sockets Support: enabled"

From the php manual page about sockets:

That appears to be the problem. I've never run across something I needed to do in PHP that required recompilation. I'm currently in the process of compling php on my home system (a rather lengthy process) for testing purposes of my script.

Eventually when I finish this code and want to move it to my Ubuntu Server, I assume I'll need to compile PHP for it as well. Is there any fancy Ubuntu way of doing this? I assume if I'm using my own custom compiled version, apt will not manage the package. Is there perhaps any way to still enjoy package management options and keep my socket support?

---

### Post by CyberJack on 2010-01-12
How did you install your current php version? Because the version I installed from the normal repositories has sockets support enabled.

---

### Post by worseisworser on 2010-01-12
```

aptitude search php | grep socket
aptitude show php-net-socket
aptitude install php-net-socket

```

---


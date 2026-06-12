---
title: "VIM + Xdebug"
date: 2009-02-19
forum: Programming Talk
---

### Post by thale on 2009-02-19
Hey guys,

I'm a PHP developer and I've started using vim recently. I can get around pretty quick but I'm not a total pro yet.

My issue is I followed this tutorial: [http://www.apaddedcell.com/easy-php-debugging-ubuntu-using-xdebug-and-vim](http://www.apaddedcell.com/easy-php-debugging-ubuntu-using-xdebug-and-vim)

for hooking xdebug up to vim for debugging local php. It seemed to work with out a hitch until I actually try and step through or run to a break point then I receive this error and it drops the connection:
```
response xmlns:xdebug=http://xdebug.org/dbgp/xdebug xmlns=urn:debugger_protocol_v1 command=stack_get transaction_id=6
error code=5 : Command not available (Is used for async commands. For instance if the engine is in state "run" than only "break
message
command is not available
```

It seems like there is a possible version miss match or I possibly missed something when I set it up. Any insight would be appreciated.

---


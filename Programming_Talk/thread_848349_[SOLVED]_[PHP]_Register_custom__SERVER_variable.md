---
title: "[SOLVED] [PHP] Register custom _SERVER variable?"
date: 2008-07-03
forum: Programming Talk
---

### Post by altonbr on 2008-07-03
I have this odd problem of synchronicity between a shared environment and a new dedicated server.

In the comparison of the two phpinfo() files, there is a server variable on the shared server environment that is not in the dedicated environment. The dedicated environment is running Ubuntu 8.04 and is pretty much the default install besides a couple libraries here and there.

The variable is called 'PHP_SELF'

> PHP_SELF 
array1: /phpinfo.php 
array2:  


which seams to mimick '_SERVER["PHP_SELF"]' as seen here:
> 
_SERVER["PHP_SELF"]
array1: /phpinfo.php
array2: /phpinfo.php


Since this company's software seem to use PHP_SELF religiously, is there a way I can create that PHP environment on the dedicated?

Due to the complexity of their scripts, I don't want to run sed.

---

### Post by mssever on 2008-07-03
It looks like they've got register_globals turned on. You can do likewise, but beware the security implications: [http://us3.php.net/register_globals](http://us3.php.net/register_globals)

In my opinion, register_globals is evil. Aside from the security implications, it causes further namespace pollution, and PHP's namespace is polluted enough as it is. It's also why I don't use $_REQUEST: The values I use should only come from an expected source. If I'm expecting data to come in via $_GET, I don't want to get something from $_POST or $_COOKIE instead.

---

### Post by altonbr on 2008-07-03
> **mssever said:**
> It looks like they've got register_globals turned on. You can do likewise, but beware the security implications: [http://us3.php.net/register_globals](http://us3.php.net/register_globals)

In my opinion, register_globals is evil. Aside from the security implications, it causes further namespace pollution, and PHP's namespace is polluted enough as it is. It's also why I don't use $_REQUEST: The values I use should only come from an expected source. If I'm expecting data to come in via $_GET, I don't want to get something from $_POST or $_COOKIE instead.

Exactly.

Right now, my job is to move them to the dedicated machine and have it "just work" and then we'll work on making it more secure. To do this, I have to pretty much re-engineer their work, but that's okay.

I've made them aware of the security implementations of having register_globals 'On', but its cheaper for them to have it 'just work' and worry about it later.

Businesses I guess, but I'll turn it off ASAP, don't worry.

Thanks for the tips. Turns out I just needed to reboot Apache to make the changes. Didn't think turning on global_variables would create PHP_INFO, my apologies for jumping the gun.

---


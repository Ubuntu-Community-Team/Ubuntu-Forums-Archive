---
title: "Don't show warning messages on PHP?"
date: 2009-07-21
forum: Programming Talk
---

### Post by Fixman on 2009-07-21
I have a no-ip account that points to my computer, and works perfectly. Of course, it doesn't work when my computer is off, so my idea was to do a PHP script (hosted somewhere else) to check if my no-ip page was up, and then redirect to it, else show me a few files I have backed up in that other host.

It works smoothly, but the only problem is that I use fsockopen() to check if my no-ip page is up, and if it fails it prints an ugly big warning message.

Is there any way to not show some warning message in PHP? I googled some time for it and didn't find anything.

By the way, if you want to check it my page (in the other server) is [http://martinfixman.com.ar](http://martinfixman.com.ar), and I currently stopped my apache connection (so the no-ip account will be down).

---

### Post by Mirge on 2009-07-21
If you put '@' before a function, it suppresses warnings/errors.

You can also use the error_reporting() function, specifying 0 for the parameter if you want to disable all errors.

```

ini_set('display_errors', 'Off');
ini_set('display_startup_errors', 'Off');
error_reporting(0);

```

Would suppress all errors.

See: [http://us3.php.net/manual/en/function.error-reporting.php](http://us3.php.net/manual/en/function.error-reporting.php)

---


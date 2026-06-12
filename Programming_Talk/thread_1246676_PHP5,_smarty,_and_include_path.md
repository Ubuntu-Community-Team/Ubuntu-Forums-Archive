---
title: "PHP5, smarty, and include_path"
date: 2009-08-22
forum: Programming Talk
---

### Post by linfidel on 2009-08-22
I have PHP5 installed, and it works so far.

I downloaded smarty, and the install instructions say to" copy the files under the libs/ directory to a directory that is in your PHP include_path."  So, I looked at my php.ini file, and the include path line is commented out; but, if I do phpinfo, or php -i, it has an include path, but it doesn't exist (it says php instead of php5).  
[FONT=Courier New][SIZE=2]include_path => .:/usr/share/php:/usr/share/pear => .:/usr/share/php:/usr/share/pear[/SIZE][/FONT]

I have no idea where this is being set.  I'd really like to know how it gets set.

I created a smarty.ini file in the folder /etc/php5/conf.d, saying:
[Smarty]
include_path = ${include_path} ":/usr/share/php5/Smarty"

But now, if I type php -i, the include_path only says:
[FONT=Courier New][SIZE=2]include_path => :/usr/share/php5/Smarty => :/usr/share/php5/Smarty[/SIZE][/FONT]
and the former path is gone.

Can anyone shed light on what is going on here?  Not so much how to change it, but why it's doing this, so I can figure out the best way to set it up.

Thanks,

---


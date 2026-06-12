---
title: "php extensions"
date: 2007-03-29
forum: Programming Talk
---

### Post by rjfioravanti on 2007-03-29
I am trying to add a PHP extension

if i go to a webpage and echo phpinfo(), it tells me somewhere that extension_dir  is /usr/lib/php5/20060613+lfs


my php.ini file used to have the extension_dir line commented out

i changed it to be this

```

extension_dir = /usr/lib/php5/extensions

```

but when i refresh the phpinfo() it still tells me extension_dir is /usr/lib/php5/20060613+lfs

How can I change extension_dir to be something more intuitive... or am I stuck with that

I am using php version 5.2.1, and apache2

---

### Post by Mirrorball on 2007-03-29
Did you restart Apache?

---

### Post by rjfioravanti on 2007-03-29
ahhhhh Thank you!

I thought the php.ini was read every time there was a php script

I didn't know that apache had anything to do with it

---


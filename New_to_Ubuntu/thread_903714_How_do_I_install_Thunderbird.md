---
title: "How do I install Thunderbird"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by fawzley on 2008-08-28
How do I install Thunderbird?

I used the menus in Applications add & install and picked Thunderbird from the list.  
After the install when I run T-bird I get an error message 'application is running but not responding'... I am at a loss of how to make things work on Linux.

HELP.....

Fawzley

---

### Post by imagenius on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Cheesehead on 2008-08-28
As described, you did install it. It's simply not working.

Did you get any error messages during the install?
Do you have a menu item for it?

Open System -> Administration -> System Monitor:
Is a Thunderbird process running? If so, kill it ('end process' button).
Then try starting Thunderbird again.

Can you start it from the command line? (Open Accessories -> Terminal and type the command 'thunderbird'<enter>) What error does it give?

---

### Post by stunningman on 2008-08-28
uninstall previous thunderbird installation
then,
reinstall from command prompt
sudo apt-get install thunderbird

now restart your system or relogin press ctrl+alt+backspace

use it hope this works

---


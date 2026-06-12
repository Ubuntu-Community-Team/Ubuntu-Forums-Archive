---
title: "Ruby and crobtab execution"
date: 2006-06-06
forum: Programming Talk
---

### Post by sig_UVa on 2006-06-06
So I have a ruby script that works when I run ruby auto_sync.rb from the /var/www/quickbase/sae_sync/ directory


I want to run this as a cron so I use crontab -e and add the text below:

*/5 * * * * /var/www/quickbase/sae_sync/ruby auto_sync.rb

I get

/bin/sh: /var/www/quickbase/sae_sync/ruby: No Such File or Directory

If I remove the ruby command and do:

*/5 * * * * /var/www/quickbase/sae_sync/auto_sync.rb

I get

/bin/sh: /var/www/quickbase/sae_sync/auto_sync.rb: Permission Denied

in my log.

Any ideas? I appreciate the help!

---

### Post by Mike Douglas on 2006-06-07
*/5 * * * * /var/www/quickbase/sae_sync/ruby auto_sync.rb

Notice in this line that you are executing /var/www/quickbase/sae_sync/ruby on a file called auto_sync.rb in the current directory. When you run `ruby` in the terminal, what actually happening is the shell searching all the folders in $PATH (`echo $PATH` to see them) for a binary called ruby (which can be found in /usr/bin). What you want to do is run `ruby /var/www/quickbase/sae_sync/auto_sync.rb`.

*/5 * * * * /var/www/quickbase/sae_sync/auto_sync.rb

Here you are executing the file directly. Notice how the error is permission denied, this usually means the file isn't executable. To make a file executable: `chmod +x /var/www/quickbase/sae_sync/auto_sync.rb`. One thing to note is that when a text file is executed, the shell depends on something called a shebang which looks like: #!/usr/bin/env ruby. /usr/bin/env is just a program that searches $PATH for a program called ruby and provides the filename (/usr/bin/ruby). You can use /usr/bin/ruby directly, but it is good practise to use env.

Hopefully one of these solutions will provide you with the answer you need.

---

### Post by sig_UVa on 2006-06-07
Your first suggestion worked marvelously.  Thank you for your help!

---


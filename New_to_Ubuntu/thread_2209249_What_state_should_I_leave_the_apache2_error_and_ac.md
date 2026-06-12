---
title: "What state should I leave the apache2 error and access log files in"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by Weedy101 on 2014-03-04
I am a noob with Ubuntu, my hobby is learning all things web and I experiment with websites that I build in php5 using eclipse.

Because I do make many mistakes the log files get rather long very quickly, so for easy of use I am using 'per site loggin'. Once I have solved an issue I would like to empty the log file out ready for a clean start on the next issue which I know won't be long.

Do I need to leave at least a blank log file, or can I simply delete the existing file and let apache2 start a new one?

(See I told you I'm a noob ;) )

---

### Post by SeijiSensei on 2014-03-05
If you delete the files, then restart Apache, they will be recreated as empty.

Another option is to use "sudo cat /dev/null > /var/log/apache2/somesite-error.log" which will reset the file to zero length.

---


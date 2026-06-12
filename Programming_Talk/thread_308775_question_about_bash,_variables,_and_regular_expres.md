---
title: "question about bash, variables, and regular expressions"
date: 2006-11-28
forum: Programming Talk
---

### Post by c2483 on 2006-11-28
how can I use a bash variable in a regular expression
my expressions looks something like this
path="something"
s/.\//$path/

I want to replace ./ with something but it replaces it with the string $path

thanks in advance

---

### Post by eeGhoong0ais on 2006-11-28
Can you give the full command you're using, rather than just the regular expression? It sounds like a quoting problem of some sort, but it's impossible to tell without seeing the context.

---

### Post by c2483 on 2006-11-28
php=`locate mysql.so | grep php5`       this get a path
sudo sed -i 's/.\//$php/' /etc/php5/apache2/php.ini

but it just makes the line
extension_dir = "./"
into
extension_dir = "$php"

---

### Post by eeGhoong0ais on 2006-11-29
It is a quoting problem, then - the shell doesn't touch anything inside single quotes. If you use double quotes instead - ```
sudo sed -i "s/.\//${php}/" /etc/php5/apache2/php.ini
``` - bash will be able to see and expand the variable.

The braces I also added aren't necessary in this case, but they're a good habit to get into.

---


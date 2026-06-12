---
title: "Opening .php files in browser"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by Votlon on 2014-02-07
Whenever I open a .php file on linux (ie: index.php), it does not render the code onto the webpage. It downloads the file instead and puts the .php file in my downloads folder. 
What should I do to fix?

---

### Post by SeijiSensei on 2014-02-07
If you're accessing the file with a file:// URL, that is the correct behavior.  To view the page with the script intepreted you need to install a web server like Apache and connect to that with HTTP.

As a starting point, read [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you already have Apache installed, make sure you have also installed the **libapache2-mod-php5** package from the repositories.  It provides the code that tells Apache to use PHP when delivering objects with the .php extension.

---

### Post by Votlon on 2014-02-07
tyvm it worked!

---


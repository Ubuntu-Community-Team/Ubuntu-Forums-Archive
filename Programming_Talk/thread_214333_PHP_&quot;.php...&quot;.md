---
title: "PHP: &quot;.php?...&quot;"
date: 2006-07-12
forum: Programming Talk
---

### Post by Ubuntuud on 2006-07-12
Hi, I found a tutorial on PHP, works fine. But one subject isn't covered.
Sometimes I see (on this forum for example) php variables stored in the addressbar, like this:

[http://www.ubuntuforums.org/newthread.php?do=newthread&f=39](http://www.ubuntuforums.org/newthread.php?do=newthread&f=39)

How do you access that variable? As GLOBAL['do']? Thanks in advance!

---

### Post by ifokkema on 2006-07-12
> **Ubuntuud said:**
> Hi, I found a tutorial on PHP, works fine. But one subject isn't covered.
Sometimes I see (on this forum for example) php variables stored in the addressbar, like this:

[http://www.ubuntuforums.org/newthread.php?do=newthread&f=39](http://www.ubuntuforums.org/newthread.php?do=newthread&f=39)

How do you access that variable? As GLOBAL['do']? Thanks in advance!

If they're in the URL, you need $_GET['do']. If sent using a form with method=post, it's in $_POST['varname']. Then you have $_COOKIE['varname'] and $_SESSION['varname'], etc. See [http://www.php.net/manual/en/language.variables.predefined.php](http://www.php.net/manual/en/language.variables.predefined.php).

---

### Post by Ubuntuud on 2006-07-12
OK. Thank you very much!

---


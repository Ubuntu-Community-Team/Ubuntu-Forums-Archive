---
title: "phpmyadmin installation error"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by stupidquestion on 2012-06-25
I installed Ubuntu Server 12.04 and did "sudo apt-get install phpmyadmin" to install phpmyadmin, but eventually got this error:

```
â&#8221;&#338;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;ââ&#8221;&#8218; 
An error occurred while installing the database:                                                                  â&#8221;&#8218;â&#8221;&#8218;                                                                           
                                        â&#8221;&#8218;â&#8221;&#8218; ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)                               â&#8221;&#8218;â&#8221;&#8218;     
                                                                                                              â&#8221;&#8218;â&#8221;&#8218; If at this point you choose "retry", you will be prompted with all the 
configuration questions once more and      â&#8221;&#8218;â&#8221;&#8218; another attempt will be made at performing the operation. "retry (skip questions)" will immediately 
attempt the   â&#8221;&#8218;â&#8221;&#8218; operation again, skipping all questions.  If you choose "abort", the operation will fail and you will need to     â&#8221;&#8218;â&#8221;&#8218; downgrade, 
reinstall, reconfigure this package, or otherwise manually intervene to continue using it.  If you     â&#8221;&#8218;â&#8221;&#8218; choose "ignore", the operation will continue, 
ignoring further errors from dbconfig-common.                       â&#8221;&#8218;â&#8221;&#8218;                                                                                                                   
â&#8221;&#8218;â&#8221;&#8218; Next step for database installation:                                                                              â&#8221;&#8218;â&#8221;&#8218;                                                                         
                                          â&#8221;&#8218;â&#8221;&#8218;                                              abort                                                                â&#8221;&#8218;â&#8221;&#8218;                                         
     retry                                                                â&#8221;&#8218;â&#8221;&#8218;                                              retry (skip questions)                                               â&#8221;&#8218;â&#8221;&#8218;   
                                           ignore                            

```

I retried and it gave the same error. I had to press abort a few times too.

But despite the error message, I could still access phpmyadmin in my web browser after the setup. 

Why am I getting the error?

(The weird characters are from Putty, which doesn't display the menu correctly, and the texts are not visible unless I select them with mouse first)

---

### Post by cariboo on 2012-06-26
Did you setup a password, when you installed mysql? The password has to be different from the one you setup for root.

---

### Post by stupidquestion on 2012-06-26
> **cariboo907 said:**
> Did you setup a password, when you installed mysql? The password has to be different from the one you setup for root.

Which user's password do you mean? I did set the password for the mysql root, but I don't recall whether there was another one. How do I check?

---


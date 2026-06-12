---
title: "Load instructions only file file exists in Apache2 vhosts"
date: 2011-08-24
forum: Programming Talk
---

### Post by juliovedovatto on 2011-08-24
I want to load some specific configs into my virtualhost  blocks only if apache finds the file in vhost directory. There's a way  to to this?
  I tried with  but did not work.



```

  <VirtualHost 127.0.0.1:80>     
ServerName sites.foo     
DocumentRoot DIR/OF/SITE     
SetEnv APPLICATION_ENV "development"     
<Directory DIR/OF/SITE>         
DirectoryIndex index.php         
AllowOverride All         
Order allow,deny         
Allow from all     
</Directory>     
#Inside of VHost block     
<Files foo.xyz> #my specific conditions to check file and load instructions     
#Some instructions here     
</Files> 
</VirtualHost>
```But  only work if I enter the file into url directly.
  One of my vhost have a file that I need to put specific instructions.  I want to make this more flexible, like in the future I need to use it  again without editing another block. I want more conditional.

---

### Post by dazman19 on 2011-08-25
You could generate the vhosts file with a program or bash script before you start the apache service.

I cant imagine you wanting to restart the server service too often, unless it was not a production machine.

---


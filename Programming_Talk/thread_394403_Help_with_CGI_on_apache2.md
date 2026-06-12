---
title: "Help with CGI on apache2"
date: 2007-03-26
forum: Programming Talk
---

### Post by Wybiral on 2007-03-26
Hi! I've installed apache2 and have been playing around with PHP, but I'd like to enable CGI so I can try that out.

I've been looking for tutorials on the subject and haven't found much... Can someone explain what libraries I need and how to configure my apache2 installation to accept CGI?

Thanks.

PS:

I'm a total newb at server/web programming so any info would be great.

---

### Post by pmasiar on 2007-03-26
If your goal is to play with CGI, you don't have to use Apache for that. 9 lines of Python code gives you simple (and simple to configure) CGI server. See [http://learnpydia.pbwiki.com/WebApplication](http://learnpydia.pbwiki.com/WebApplication) - also 2 simple CGI apps

---

### Post by Wybiral on 2007-03-26
I might have to play around with that... Sounds interesting.

But for now, I would still really like to be able to do this with apache2.

---

### Post by lnostdal on 2007-03-27
Using a fresh Apache2 install(#1), I've enabled userdir as confirmed by doing this:


```

root@nostdal:/etc/apache2/mods-enabled# file userdir.conf 
userdir.conf: symbolic link to `/etc/apache2/mods-available/userdir.conf'
root@nostdal:/etc/apache2/mods-enabled# file userdir.load 
userdir.load: symbolic link to `/etc/apache2/mods-available/userdir.load'

```

..then I've added something to the original userdir.conf, here:

```

root@nostdal:/etc/apache2/mods-enabled# cat userdir.conf 
<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride FileInfo AuthConfig Limit
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>

        <Directory /home/*/public_html/cgi-bin>
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                SetHandler cgi-script
                Order allow,deny
                Allow from all
        </Directory>
</IfModule>

```

..do a restart of apache ( /etc/init.d/apache2 force-reload )

..then I do the following (just create the public_html/cgi-bin dirs if you haven't already):

```

lars@nostdal:~$ whoami
lars
lars@nostdal:~$ cd public_html/cgi-bin/
lars@nostdal:~/public_html/cgi-bin$ cat test.c
#include <stdio.h>

int main(){
  printf("Content-type: text/html\n\r\n\r");
  printf("Hello World!\n");
  return 0;
}
lars@nostdal:~/public_html/cgi-bin$ gcc -g -Wall -o test test.c
lars@nostdal:~/public_html/cgi-bin$ ./test
Content-type: text/html

Hello World!
lars@nostdal:~/public_html/cgi-bin$ 

```

..and you can see the result here: [http://nostdal.org/~lars/cgi-bin/test](http://nostdal.org/~lars/cgi-bin/test)

For further info, see: [http://www.jmarshall.com/easy/cgi/](http://www.jmarshall.com/easy/cgi/)

btw. you will soon discover that doing this stuff with plain CGI and C/C++ is a bad idea.


#1: I saw you mentioned something about a messed up apache-setup in the IRC-channel (stupid time-zones). To fix that you have got to purge every package that has "apache" in its name. apache-common .. etc.etc.

---

### Post by Wybiral on 2007-03-27
That worked great, thanks lnostdal.

---

### Post by Frosty Cold Drink on 2007-03-27
> **lnostdal said:**
> btw. you will soon discover that doing this stuff with plain CGI and C/C++ is a bad idea.

Plain CGI with anything is often bad. Although C or C++ CGI apps work just fine on low-volume servers  or with FastCGI. For tiny apps the lack of an interpreted languages overhead is great.

---

### Post by Wybiral on 2007-03-27
> **Frosty Cold Drink said:**
> Plain CGI with anything is often bad. Although C or C++ CGI apps work just fine on low-volume servers  or with FastCGI. For tiny apps the lack of an interpreted languages overhead is great.

Yeah, I've been told. I'm not making a professional site or anything, I'm just testing some things out and assembly/C are really the best for the kind of stuff I'm wanting to do.

Nice avatar BTW, master shake rules!

---


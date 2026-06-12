---
title: "Odd Apache CGI Problem"
date: 2007-09-13
forum: Programming Talk
---

### Post by SuperMike on 2007-09-13
I'm having an odd Apache2 problem where I can't add my own CGI language.

Okay, through Apache2, I can get my Perl scripts to run just fine from /var/www/test with their .pl extensions, but I had to do this:

1. sudo vi /etc/apache2/sites-enabled/000-default

I commented out with # the 'AllowOverride None' lines. Argh, cruel bastards be they.

2. sudo vi /var/www/test/.htaccess

I added these lines:

```
Options +ExecCGI
AddHandler cgi-script .pl
```

3. sudo /etc/init.d/apache2 restart

4. sudo chmod 755 /var/www/test/index.pl

5. I ensured the index.pl started with the following as the topmost line:

```
#!/usr/bin/perl
```


Okay, great, but now I wrote a new language called Polar and it has files that execute with .pol. The directive at the top of those scripts read:

#!/usr/lib/polar/polar

In the /usr/lib/polar directory is a Bash script called 'polar' that pre-processes the script and converts it from the "Polar" langauge I invented and into Javascript that can run through 'ngs-js' (an ELF binary that runs Javascript).

I then did all the numbered steps again but also changed step 2 to:

```
Options +ExecCGI
AddHandler cgi-script .pl .pol
```

If I do 'polar index.pol', it runs. If I do './index.pol', it does not run. If I try to hit the index.pol page in the browser, it reports an error:

500 Internal Server Error

However, if I make a .js file and call ngs-js directly with this technique, it works just fine. So what's the catch in making Apache2 know to run /usr/lib/polar/polar as the interpreter to my script?

---

### Post by SuperMike on 2007-09-13
I figured it out. The trick was:

1. Use this sort of .htaccess file:

```
Options +ExecCGI
AddHandler cgi-script .pol
```

2. Inside my Polar script file, I had this directive as the first line:

```
#!/usr/bin/polar
```

3. Now this was a symlink pointing to /usr/lib/polar/polar, but that was a Bash script. Apache2 gets cranky about that and won't let that run. I had to make a backup of that Bash script, and then use the command 'shc' to convert the Bash script to a binary ELF executable file in order to fool Apache2. This outputs polar.x. I rename polar.x as 'polar' in the /usr/lib/polar directory. That way, /usr/bin/polar, which was a symlink, would point directly to a so-called binary file and Apache2 would be happy again.

4. Note I also had another stumbling block. My 'polar' Bash script interacted with /tmp and would create a directory there called 'polar' for storing its stuff. It was not created, however, by 'root'. (It was because of something I had done previously.) Therefore, when I ran my scripts through Apache2, it would try to get into that /tmp/polar directory, not have the permissions, and would bomb out. Once I did...

```
sudo chown root.root /tmp/polar
```

...the scripts had permissions and could run fine.

This obscure bit of info might actually help .002% of the people on Earth, so I might as well post this, right?

---


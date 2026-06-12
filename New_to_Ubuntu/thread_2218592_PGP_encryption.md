---
title: "PGP encryption"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by lovewizard on 2014-04-21
Hi,

I installed the software on ubunty to encrypt my text with a PGP key.

But the result of the encryption is weird. I don't know if this is normal or ubuntu is missing a set of characters.


When i open the file with the encrypted text with the software geedit I get this:

> [I]
\85\A0\F9\DC\D5Z\82R[\FD\AA\97\AD&#1837;S\87=\FD\84H=L\90!\FAyQ\BB    \AC\BE\BA&#40107;8\ED\C23\86\EBu\A3X\F5\8A\DD\E1&#1773;\B6M\86\D0(\9F\8D>!"2+it&#383;\BCI\9F\D0Rf\81\B8l>F%_\FA/Î\9B\CE    A&\D7c\B9:U\BC\FB=\E8:\9DM&#31782;_\EE\D0\D3T\E3é\A8&#1702;Ni\DE    \EC\88\F57G\B8\BDmbM\C8\E5\AFaQ\CB&#1196;\D8<\E3\A9&#934;\BB<En\EE\BFV    \C1\83\93\93[\B7\F5&#702;\AD\D9\D1+\97\A4svB\FC-\89\9D$\B6\EF\B2M\8B2\D7\00\AD4up\91\CEVd'/\F8\97\B8\E5\94\B6\A5\A2\E9;\8B\81\A5\86\94J\FA\869'\838N\A9V\9F\8AW\A0\A9\D6tR\8Bs \D9\F01\EAn\80T\858
\93\F3\C4\EF\FD&#1921;Ax\B4
\CB\CDH\F0\A6\87T&#760;\C5    &#1804;Y\ED"\C1\85\F5&#1411;AbbV\8A\D8bC\D7t\FD&#1307;\84&#1286;\AC\B2{\8FH\C3H$\9F\AD}\AD\B7\00\C7O[/ \DE\D4}\99\8E\E8B0#\E0\B6\DE\FE.\F7\B8@&#1547;\91Aq[^\E6\91\F4\81P.ER/\CBx
\D6T\F1{\C1\878\90\E5\B4&\EA\D52\E2Z\B7c4F\C2Z\C1\E9\C3>CHL\A2.\829\C1'\CDS\D1&#2014;u\FA\99\9B\EF\87D\D5\E6\EBGS7=\DB\D5\DB\F7\91u\B7\CEVX\8F\F7w\9Cn\BC\CE?HE\8Avj\D47NM\BD&#59683;(\F9&#279;\91ZD\C7<`\84W+V\8F\F9\E0@\C3n{\E9\BCG\ED%\A8l\B2\A8\FBCI\F2mm4\9E\96&#1171;\E4%\943\D71S\FB\B7-BO\EBk\F7    \E4O\96\E40\86\B3\92\FC=\C9\DD\FB\F1&#1797;<+\99\89\87\DBl w\DAO6P\C3\D7v\BD\DB\D4\C0j~\FD\BB\F2\B07QqO-\E8\89\BFE\B2\AF\A9\8E\F66&#1552;s;\DE>\E8%5W&#814;/\C2\F55&#1710;B_8\ED\E3\B4L\C9Z\8D\80\A7\8C&#1927;_\AA\B4Hw\95
\B3\8A\B1\92
jo\D8\FE:w\DER'=\BFMd\D1[/I]


When I open the file with the terminal by typing: cat filename.pgp, I get this:

> &#65533;
  &#65533;&#65533;&#65533;&#65533;Z&#65533;R[&#65533;&#65533;&#65533;&#65533;&#1837;S&#65533;=&#65533;&#65533;H=L&#65533;!&#65533;yQ&#65533;    &#65533;&#65533;&#65533;&#40107;8&#65533;&#65533;3&#65533;&#65533;u&#65533;X&#65533;&#65533;&#65533;&#65533;&#1773;&#65533;M&#65533;&#65533;(&#65533;&#65533;>!
                                                                   "2+it&#383;&#65533;I&#65533;&#65533;Rf&#65533;&#65533;l>F%_&#65533;/Î&#65533;&#65533;    A&&#65533;c&#65533;:U&#65533;&#65533;=&#65533;:&#65533;M
                                &#31782;_&#65533;&#65533;&#65533;T&#65533;é&#65533;&#1702;Ni&#65533;    &#65533;&#65533;&#65533;7G&#65533;&#65533;mbM&#65533;&#65533;&#65533;Q&#65533;&#1196;&#65533;<&#65533;&#934;&#65533;<En&#65533;&#65533;V    &#65533;&#65533;&#65533;&#65533;[&#65533;&#65533;&#702;&#65533;&#65533;&#65533;+&#65533;&#65533;svB&#65533;-&#65533;&#65533;$&#65533;&#65533;&#65533;M&#65533;2&#65533;&#65533;4up&#65533;&#65533;Vd'/&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;9'&#65533;8N&#65533;V
                                                                              &#65533;&#65533;&#65533;&#65533;1n&#65533;T&#65533;s
         8
&#65533;&#65533;&#65533;&#65533;&#1921;Ax&#65533;
&#65533;&#65533;}&#65533;B0#&#65533;&#65533;&#65533;&#65533;.&#65533;&#65533;@&#1547;&#65533;Aq[^&#65533;&#65533;&#65533;&#65533;P.ER/&#65533;x&#65533;&#1307;&#65533;&#1286;&#65533;&#65533;{&#65533;H$&#65533;&#65533;}&#65533;&#65533;&#65533;O[/
&#65533;T&#65533;{&#65533;&#65533;8&#65533;&#65533;&#65533;&&#65533;&#65533;2&#65533;Z&#65533;c4F&#65533;Z&#65533;&#65533;&#65533;>CHL&#65533;.&#65533;9&#65533;'&#65533;S&#65533;&#2014;u&#65533;&#65533;&#65533;&#65533;&#65533;D&#65533;&#65533;&#65533;GS7=&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;VXw&#65533;n&#65533;&#65533;?HE&#65533;vj&#65533;
 7NM&#65533;&#59683;(&#65533;&#279;&#65533;ZD&#65533;<`&#65533;W+V&#65533;@&#65533;n{&#65533;&#65533;G&#65533;%&#65533;l&#65533;&#65533;
                                      &#65533;CI&#65533;mm4&#65533;&#65533;&#1171;&#65533;%&#65533;3&#65533;1S&#65533;&#65533;-BO&#65533;k&#65533;    &#65533;O&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;&#1797;<+&#65533;&#65533;&#65533;&#65533;l w&#65533;O6P&#65533;&#65533;v&#65533;&#65533;&#65533;&#65533;j~&#65533;&#65533;&#65533;&#65533;7QqO-&#65533;&#65533;&#65533;E&#65533;&#65533;&#65533;6&#1552;s;&#65533;>&#65533;%5W&#814;/&#65533;&#65533;5&#1710;B_8&#65533;&#65533;&#65533;L&#65533;Z&#65533;&#65533;&#65533;&#65533;&#1927;_&#65533;&#65533;Hw&#65533;
&#65533;&#65533;&#65533;&#65533;

jo&#65533;&#65533;:w&#65533;R'=&#65533;Mdr

---

### Post by jdeca57 on 2014-04-21
The idea of encryption is to make a file unreadable and from your post I see that is a success. ;-) Of course there is the matter of decryption in order to get to the contents. The public/private key concept is explained in, for example [http://www.pgpi.org/doc/pgpintro/](http://www.pgpi.org/doc/pgpintro/) ...

---

### Post by Impavidus on 2014-04-21
The encrypted file is a binary file. It no longer makes sense as a text file. Gedit deals with binary files by listing escape codes, whereas the terminal shows question marks. Your result is entirely expected.

---

### Post by Dennis N on 2014-04-21
You can encrypt to ascii characters only if you use the --armor (-a) option.

Example:

Encoding a document secret.txt:

[B][FONT=Courier New]dmn@Roxanne:~$ gpg -a -r [email]recipient@gmail.com[/email] -e secret.txt
[/FONT][/B]
The output looks like this:

```
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQEMA2DdJvNF8gfdAQgAgZUeiR0SZiuRg8mkRzy9ICISDHMg0vGn4c1an5UcZWWK
q4hbfDQ1FkzZ7rPKiVsGWBGNiAzsgHs1mczSdA5u5n05mA6idViKU/4okmV+pjt/
g+x+G0lNBbEe619NN9juLth5Gt0ezCx7XVuUjpU409fCcTKAvJhm8JymLZ1QDCp4
SEX6WXfgTpdyMYQ/2lu8mbHItCbH6c3KLjVUpsRjaupNwfdwpMnveGnbpxQxdpFe
BJVSk7uMQV/S74iiNyabkzQtCCjlRzpyYhdzRm6I8n4vDku4s6tCmYUhqUHweYCv
eYG08Sc5spvgTFSUMzpU9CpgZn0Xqp0o3aa3LcAo19JvARejJYBbfCKVZnGdF+Va
+S1JDzWKztFZ0EH9QWVOGqfXRY628mG9i4J/NJJ5uoLdIwh4E9du4C6/PRpwD2Sz
IES2QJkPQHI0Nc/neEv2LGONegMAjXjF0jMG+zgQSlZ2p5GP3emNH3FKIQEc8eIi
=hepi
-----END PGP MESSAGE-----
```

You can put this in the body of a standard email. and the recipient can decrypt with his private key.

---

### Post by lovewizard on 2014-04-21
> **Dennis N said:**
> You can encrypt to ascii characters only if you use the --armor (-a) option.

Example:

Encoding a document secret.txt:

[B][FONT=Courier New]dmn@Roxanne:~$ gpg -a -r [EMAIL="recipient@gmail.com"]recipient@gmail.com[/EMAIL] -e secret.txt
[/FONT][/B]
The output looks like this:

```
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.11 (GNU/Linux)

hQEMA2DdJvNF8gfdAQgAgZUeiR0SZiuRg8mkRzy9ICISDHMg0vGn4c1an5UcZWWK
q4hbfDQ1FkzZ7rPKiVsGWBGNiAzsgHs1mczSdA5u5n05mA6idViKU/4okmV+pjt/
g+x+G0lNBbEe619NN9juLth5Gt0ezCx7XVuUjpU409fCcTKAvJhm8JymLZ1QDCp4
SEX6WXfgTpdyMYQ/2lu8mbHItCbH6c3KLjVUpsRjaupNwfdwpMnveGnbpxQxdpFe
BJVSk7uMQV/S74iiNyabkzQtCCjlRzpyYhdzRm6I8n4vDku4s6tCmYUhqUHweYCv
eYG08Sc5spvgTFSUMzpU9CpgZn0Xqp0o3aa3LcAo19JvARejJYBbfCKVZnGdF+Va
+S1JDzWKztFZ0EH9QWVOGqfXRY628mG9i4J/NJJ5uoLdIwh4E9du4C6/PRpwD2Sz
IES2QJkPQHI0Nc/neEv2LGONegMAjXjF0jMG+zgQSlZ2p5GP3emNH3FKIQEc8eIi
=hepi
-----END PGP MESSAGE-----
```

You can put this in the body of a standard email. and the recipient can decrypt with his private key.


thank you
i finally did it
i was completly in the dark about how the results looks like 
now i finally did it

---


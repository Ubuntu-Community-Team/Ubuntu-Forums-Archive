---
title: "A bit complex doubt....."
date: 2009-07-23
forum: Programming Talk
---

### Post by veda87 on 2009-07-23
i found that the last login details are been kept at**/var/log/lastlogin**.... when I opened it using vi editor... i found something like this```
¸<92>hJtty1^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@×        p¡ö·PÞ× ^@^@^@^@^@^@^@^@^Tûç·^E^@^@^@^A^@^@^@^@^@^@     p¡ö·p¡ö·8Þ×     ^@^@^@^@xØ×     @¡ö·^D^@^@^@ø\Ú¿e(è·@¡ö·^]^@^@^@@¡ö·ô<8f>ö·ôÏ÷·XÞ×      xØ×     ^X]Ú¿Ø}÷·XÞ×    xØ×     ^@^@^@^@ô<8f>ö·@¡ö·xØ×  8]Ú¿V^Dè·@¡ö·xØ×        pØ× 
```

and when I login into my virutal console using root... it gives me my last login detail as ```
Last login: thu Jul 23 18:00:32 IST 2009 on tty1
``` I could figure out the console tty1 but not the date and time...I knew the **/var/log/lastlogin** is hard coded...

Can anyone help to know how the system interprets it.. How can I see this hard coded file in an user understandable format..

---

### Post by Martin Witte on 2009-07-23
When I run **lastlog**, the program designed to read file */var/log/lastlog*, see **man lastlog** for more information,  it seems to be not working:
```
martin@sony:~$ lastlog -u martin
Username         Port     From             Latest
martin                                     **Never logged in**
martin@sony:~$ 

```

I can find this information with
```
martin@sony:~$ last martin|head 
martin   pts/0        :0.0             Thu Jul 23 20:23   still logged in   
martin   pts/0        :0.0             Thu Jul 23 19:55 - 19:55  (00:00)    
martin   tty7         :0               Thu Jul 23 19:30   still logged in   
martin   pts/0        :0.0             Tue Jul 21 21:19 - 21:20  (00:00)    
martin   tty7         :0               Tue Jul 21 21:19 - down   (00:59)    
martin   tty7         :0               Mon Jul 20 21:52 - down   (00:07)    
martin   tty7         :0               Mon Jul 20 19:35 - down   (02:07)    
martin   tty7         :0               Sat Jul 18 23:38 - down   (01:37)    
martin   pts/0        :0.0             Thu Jul 16 21:08 - 21:26  (00:18)    
martin   pts/0        :0.0             Thu Jul 16 20:22 - 20:28  (00:06)    
martin@sony:~$ 

```

---


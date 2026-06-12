---
title: "lynx, links does not work on https://ubuntu.com/security/notices?order=newest"
date: 2022-11-16
forum: New to Ubuntu
---

### Post by maketopsite on 2022-11-16
```
$ links https://ubuntu.com/security/notices?order=newest&release=focal[6] 148598
$ 
$ lynx https://ubuntu.com/security/notices?order=newest&release=focal
[7] 148781
$



```

Is it please possible use these browsers on [https://ubuntu.com/security/notices?order=newest](https://ubuntu.com/security/notices?order=newest)      ?

---

### Post by Holger_Gehrke on 2022-11-16
The (main) problem is the '&' in the URL. In the shell a '&' means 'this is the end of the command, run it in the background'. You can bring lynx (or links) back to the foreground with the command 'fg' optionally with the job number(the number in the brackets) as an argument. Or you can put the URL in single quotes
```

lynx 'https://ubuntu.com/security/notices?order=newest&release=focal&details='

```

Holger

---

### Post by maketopsite on 2022-11-16
> **Holger_Gehrke said:**
> The (main) problem is the '&' in the URL. In the shell a '&' means 'this is the end of the command, run it in the background'. You can bring lynx (or links) back to the foreground with the command 'fg' optionally with the job number(the number in the brackets) as an argument. Or you can put the URL in single quotes
```

lynx 'https://ubuntu.com/security/notices?order=newest&release=focal&details='

```

Holger
thank you it works with lynx. But 
```

links 'https://ubuntu.com/security/notices?order=newest&release=focal&details='

``` still does not work

---


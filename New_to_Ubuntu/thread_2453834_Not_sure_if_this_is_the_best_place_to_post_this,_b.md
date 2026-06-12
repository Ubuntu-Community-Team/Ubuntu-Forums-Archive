---
title: "Not sure if this is the best place to post this, but extremely new and getting errors"
date: 2020-11-17
forum: New to Ubuntu
---

### Post by nyoorspace on 2020-11-17
I was attempting to run a 100% moral node.js script on digital studio code when i got the following error:
```
    if (err) throw new Error(err);             ^


Error: Error: wlan0     Interface doesn't support scanning.




    at /home/alex/app.js:9:20
    at /home/alex/node_modules/intruder/lib/index.js:59:21
    at ChildProcess.handleClose (/home/alex/node_modules/network-scanner/lib/index.js:72:14)
    at ChildProcess.emit (node:events:329:20)
    at maybeClose (node:internal/child_process:1055:16)
    at Socket.<anonymous> (node:internal/child_process:441:11)
    at Socket.emit (node:events:329:20)
    at Pipe.<anonymous> (node:net:655:12)



```

The script I was attempting to run was 

```
[COLOR=#569CD6][FONT=&quot]var[/FONT][/COLOR][COLOR=#D4D4D4][FONT=&quot] [/FONT][/COLOR][COLOR=#4EC9B0][FONT=&quot]Intruder[/FONT][/COLOR][COLOR=#D4D4D4][FONT=&quot] = [/FONT][/COLOR][COLOR=#DCDCAA][FONT=&quot]require[/FONT][/COLOR][COLOR=#D4D4D4][FONT=&quot]([/FONT][/COLOR][COLOR=#CE9178][FONT=&quot]'intruder'[/FONT][/COLOR][COLOR=#D4D4D4][FONT=&quot]);[/FONT][/COLOR][COLOR=#D4D4D4][FONT=&quot]
[COLOR=#4ec9b0]Intruder[/COLOR]()
  .[COLOR=#dcdcaa]on[/COLOR]([COLOR=#ce9178]'attempt'[/COLOR], [COLOR=#569cd6]function[/COLOR]([COLOR=#9cdcfe]ivs[/COLOR]) {
    [COLOR=#9cdcfe]console[/COLOR].[COLOR=#dcdcaa]log[/COLOR]([COLOR=#9cdcfe]ivs[/COLOR]);
  })
  .[COLOR=#dcdcaa]crack[/COLOR]([COLOR=#ce9178]'~Censored for privacy~'[/COLOR], [COLOR=#569cd6]function[/COLOR]([COLOR=#9cdcfe]err[/COLOR], [COLOR=#9cdcfe]key[/COLOR]) {
    [COLOR=#c586c0]if[/COLOR] ([COLOR=#9cdcfe]err[/COLOR]) [COLOR=#c586c0]throw[/COLOR] [COLOR=#569cd6]new[/COLOR] [COLOR=#4ec9b0]Error[/COLOR]([COLOR=#9cdcfe]err[/COLOR]);
    [COLOR=#9cdcfe]console[/COLOR].[COLOR=#dcdcaa]log[/COLOR]([COLOR=#9cdcfe]key[/COLOR]);
[/FONT][/COLOR]
[COLOR=#D4D4D4][FONT=&quot]  });[/FONT][/COLOR]
```

I went on the issues section on github and saw that several other users had gotten a similar error on linux, so I figured it was related to the operating system. Does anyone know how to fix wlan0?

For the record, I wasn't trying to crack someone else's wifi. I was just testing the script on my own.

---

### Post by wildmanne39 on 2020-11-17
Hello nyoorspace, from the forum rules:
> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.
While we believe that you do not have nefarious intentions this thread will be viewable on the internet by anyone with internet access and many of those users will not have as honorable intentions as you do, so please understand we do not allow this type of discussion on the forum as stated in the quoted text above.

Complete forum rules are located here:

[https://ubuntuforums.org/misc.php?do=showrules](https://ubuntuforums.org/misc.php?do=showrules)

Hope you get this issue resolved in another venue.

---


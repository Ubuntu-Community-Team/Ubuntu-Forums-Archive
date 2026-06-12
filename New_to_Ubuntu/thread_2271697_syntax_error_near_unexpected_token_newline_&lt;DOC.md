---
title: "syntax error near unexpected token newline &lt;DOCTYPE html&gt; while installing zpanel"
date: 2015-03-31
forum: New to Ubuntu
---

### Post by salim5 on 2015-03-31
I am new to **ubuntu**, trying to install **zpanel** on my VPS server.I have followed this answer,

[http://askubuntu.com/questions/430231/how-to-install-zpanel-10-1-1-for-ubuntu-server-12-04-lts](http://askubuntu.com/questions/430231/how-to-install-zpanel-10-1-1-for-ubuntu-server-12-04-lts)

[COLOR=#333333][FONT=UbuntuRegular]first download the script[/FONT][/COLOR]
wget [https://raw.github.com/zpanel/installers/master/install/Ubuntu-12_04/10_1_1.sh](https://raw.github.com/zpanel/installers/master/install/Ubuntu-12_04/10_1_1.sh)
[COLOR=#333333][FONT=UbuntuRegular]Then make the script executable[/FONT][/COLOR]
chmod +x 10_1_1.sh
[COLOR=#333333][FONT=UbuntuRegular]Then run the script[/FONT][/COLOR]
sudo ./10_1_1.sh


and it worked till I run the script.After executing the script,when I run it,I get this error on my putty

*./10_1_1.sh: line 4: syntax error near unexpected token `newline'*
[I]./10_1_1.sh: line 4: `<!DOCTYPE html>'


[/I]How can I get rid of this problem?Please help.

Thank you

---

### Post by sandyd on 2015-03-31
> **salim5 said:**
> I am new to **ubuntu**, trying to install **zpanel** on my VPS server.I have followed this answer,

[http://askubuntu.com/questions/430231/how-to-install-zpanel-10-1-1-for-ubuntu-server-12-04-lts](http://askubuntu.com/questions/430231/how-to-install-zpanel-10-1-1-for-ubuntu-server-12-04-lts)

[COLOR=#333333][FONT=UbuntuRegular]first download the script[/FONT][/COLOR]
wget [https://raw.github.com/zpanel/installers/master/install/Ubuntu-12_04/10_1_1.sh](https://raw.github.com/zpanel/installers/master/install/Ubuntu-12_04/10_1_1.sh)
[COLOR=#333333][FONT=UbuntuRegular]Then make the script executable[/FONT][/COLOR]
chmod +x 10_1_1.sh
[COLOR=#333333][FONT=UbuntuRegular]Then run the script[/FONT][/COLOR]
sudo ./10_1_1.sh


and it worked till I run the script.After executing the script,when I run it,I get this error on my putty

*./10_1_1.sh: line 4: syntax error near unexpected token `newline'*
[I]./10_1_1.sh: line 4: `<!DOCTYPE html>'


[/I]How can I get rid of this problem?Please help.

Thank you

Try
```

rm 10_1_1.sh
wget https://raw.githubusercontent.com/zpanel/installers/master/install/Ubuntu-12_04/10_1_1.sh
bash 10_1_1.sh

```

---

### Post by salim5 on 2015-03-31
Thanks for your reply.
Did you mean to use 

    [COLOR=#000000][FONT=Ubuntu Mono]bash 10_1_1.sh

[/FONT][/COLOR]instead of

     [COLOR=#000000]*chmod +x 10_1_1.sh*[/COLOR]
[COLOR=#000000][I]     sudo ./10_1_1.sh

[/I][/COLOR]If yes,then it is still giving me same error

---

### Post by sandyd on 2015-04-01
Whats the output of
```

cat 10_1_1.sh
```

---

### Post by salim5 on 2015-04-01
When you edited the first answer,I applied that.And IT WORKED!!!!
Thanks a loooooooooooooooooooooooooooooooooot.
Hats off.
I love ubuntu forum.

---

### Post by sandyd on 2015-04-01
Hi, please mark this thread as solved if you have found a solution by going to Thread Tools -> Mark Thread as Solved.

Thanks!

---


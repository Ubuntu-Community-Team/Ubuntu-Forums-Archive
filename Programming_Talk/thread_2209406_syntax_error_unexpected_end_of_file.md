---
title: "syntax error: unexpected end of file"
date: 2014-03-05
forum: Programming Talk
---

### Post by nico13 on 2014-03-05
Hello everyone,

I started writing a script which stop rtorrent, start vpn connection and restart rtorrent if my public ip is 123.456.789.000 (like below)

Each time I test the script, I get this error 

```
xbmc@xbmc:~/Scripts$ sudo bash checkip.sh
checkip.sh: line 14: syntax error: unexpected end of file
```

so this is my script, can you help me please ?

```
#!/bin/sh

if [ $curl ifconfig.me/ip == 123.456.789.000 ] && if [ $curl ifconfig.me/host == abc13-3-123-456-789-000.fbx.proxad.net ]; then
sudo service rtorrent-init stop;
wait
cd /etc/openvpn && sudo openvpn "my file.ovpn";
wait
sudo service rtorrent-init start;
fi
```

---

### Post by Vaphell on 2014-03-05
```
if [ $curl ifconfig.me/ip == 123.456.789.000 ] && [COLOR="#FF0000"]if[/COLOR] [ $curl ifconfig.me/host == abc13-3-123-456-789-000.fbx.proxad.net ]; then
```
remove it

$curl looks undefined and will expand to nothing. Is this how it's supposed to look?

and if you want to use bash, don't define sh as default
```
#!/bin/**bash**
```

also single commands don't require termination with ;, you need ; only when cramming more into a single line
```
cmd1
cmd2
cmd1; cmd2
```
some indentation would be nice so that *then* block is visible at a glance

---

### Post by nico13 on 2014-03-05
ok so I removed : the second if, the semi columns and the second "=" in the variables

I changed "[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/[/FONT][/COLOR]**sh" in "**[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/[/FONT][/COLOR][B]bash"

when I run the script, I got no error message but it doesn't work [/B]

---

### Post by Vaphell on 2014-03-05
I mentioned undefined $curl variable.

$curl calls a variable that is not defined anywhere so the conditions are bad and won't work.
i assume the script you copied some bits from had $curl defined as* curl=/usr/bin/curl* or something like that but here it expands to nothing. Strip $ sign to call curl directly and be done with it.

 also you don't even try to capture the output so even with $curl variable defined it still wouldn't work
```
if [ "[COLOR="#0000CD"]$([/COLOR] curl ifconfig.me/ip[COLOR="#0000CD"] )[/COLOR]" = "123.456.789.000" ] && [ "[COLOR="#0000CD"]$([/COLOR] curl ifconfig.me/host [COLOR="#0000CD"])[/COLOR]" = "abc13-3-123-456-789-000.fbx.proxad.net" ]
```

---


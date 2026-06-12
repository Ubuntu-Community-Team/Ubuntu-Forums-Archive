---
title: "Alias in the .bashrc file"
date: 2024-08-29
forum: New to Ubuntu
---

### Post by jmkmx on 2024-08-29
Hello my good people,

I have a question regarding the creation of alias in the .bashrc file.

So I tried adding a new alias for me to use to check ip info but is not working, I used the following line: [FONT=courier new]**alias ipinfo='ip a --color=auto'**[/FONT] but if I do alias[FONT=courier new]** ip='ip a --color=auto'**[/FONT] it works... So my question would be, do I need to use a real command, or it is possible to use a random word as an alias?

Thanks in advance!

---

### Post by Holger_Gehrke on 2024-08-29
The first thing I see which is a problem is that options come before commands and objects with 'ip'. So 'ip a --color=auto' produces an error while 'ip --color=auto a' works. When defining an alias, I usually give the full path to the command called by the alias to make sure that the right command is getting called and to avoid unintentional recursion. If i have 'alias ipinfo=ip --colour=auto a' and alias ip=ip --colour=auto a' defined, then ipinfo would get expanded twice and end up being an invalid command ('ip --color=auto a --color=auto a'). Using '/usr/sbin/ip' as part of the definition stops further expansion, as 'man bash' states in the section on aliases.

Holger

---

### Post by jmkmx on 2024-08-29
So how would I do this? I tried the following but it didn't work for me;

alias ipinfo='/usr/sbin/ip --color=auto a'

Can you please show me the proper way?

---

### Post by currentshaft on 2024-08-29
That is the right way to make an alias and it works fine for me.

---

### Post by &amp;KyT$0P# on 2024-08-29
jmkmx, what does "not working" and "didn't work" mean?  What is the full command you're entering in the interactive bash shell when you're trying to use the alias, and what actually happens instead of it working the way you want?

---

### Post by jmkmx on 2024-08-29
If I use a random word I get a command not found error, but if I use ip it does work :(
I'll stick with ip for now until I get more knowledge on how this works as I am relatively knew to using Linux/Ubuntu.

Thanks for your help!

---

### Post by &amp;KyT$0P# on 2024-08-29
> **jmkmx said:**
> If I use a random word I get a command not found error, 

Again, what is the full command you're entering in the interactive shell to get this result?

If, when the [FONT=monospace]ipinfo[/FONT] alias is set up, you run
```
type ipinfo
```
it should return something like
```
ipinfo is aliased to `/usr/sbin/ip --color=auto a'
```

If it doesn't, please post the full contents of your [FONT=monospace]~/.bashrc[/FONT]

---

### Post by Holger_Gehrke on 2024-08-29
Just putting the alias in the ~/.bashrc won't do anything until you start a new shell. bash only reads that file during startup. So you can either exit the terminal and open a new one or you can tell bash to re-read the file with '. ~/.bashrc' (that's a period and a space followed by the filename; alternatively you can use the 'source' command).

Holger

---

### Post by stephan4 on 2024-08-30
I tried it here on a Xubuntu 22.04 system and a Rocky-9 server, and run into issues with your approach:

```
[B][COLOR=#ff0000]
#1   #3   #2
[/COLOR][/B][FONT=courier new]
[COLOR=#ff0000]"**ip  a   --color=auto"**[/COLOR][/FONT]
[FONT=courier new]
**The ip help menu shows what is wrong:**
       **[COLOR=#008000]#1.     [/COLOR][COLOR=#ff8c00]#2      [/COLOR][COLOR=#0000ff]#3[/COLOR]**
Usage: [COLOR=#008000]**ip**[/COLOR] [ [COLOR=#ff8c00]**OPTIONS**[/COLOR] ] **[COLOR=#0000ff]OBJECT[/COLOR]** { COMMAND | help }
       ip [ -force ] -batch filename
where  [COLOR=#0000ff]**OBJECT**[/COLOR] := { [COLOR=#0000ff]**address**[/COLOR] | addrlabel | amt | fou | help | ila | ioam | l2tp |
                   link | macsec | maddress | monitor | mptcp | mroute | mrule |
                   neighbor | neighbour | netconf | netns | nexthop | ntable |
                   ntbl | route | rule | sr | tap | tcpmetrics |
                   token | tunnel | tuntap | vrf | xfrm }
       [COLOR=#ff8c00]**OPTIONS**[/COLOR] := { -V[ersion] | -s[tatistics] | -d[etails] | -r[esolve] |
                    **[COLOR=#ff8c00]-h[uman-readable[/COLOR]**] | -iec | -j[son] | -p[retty] |
                    -f[amily] { inet | inet6 | mpls | bridge | link } |
                    -4 | -6 | -M | -B | -0 |
                    -l[oops] { maximum-addr-flush-attempts } | -br[ief] |
                    -o[neline] | -t[imestamp] | -ts[hort] | -b[atch] [filename] |
                    -rc[vbuf] [size] | -n[etns] name | -N[umeric] | -a[ll] |
                    **[COLOR=#ff8c00]-c[olor][/COLOR]**}[/FONT]
```



The sort order of the arguments is important and also that you use a single dash instead of two (later may work with two too, but the help depicts 1 dash)
Long story short, this works:

[SIZE=4][FONT=courier new]**alias testme=**[/FONT][COLOR=#0000ff][FONT=courier new]**"**[/FONT][/COLOR][COLOR=#008000][FONT=courier new]**ip**[/FONT][/COLOR][COLOR=#ff8c00][FONT=courier new]** -human-readable -color=auto**[/FONT][/COLOR][COLOR=#0000ff][FONT=courier new]** address"**[/FONT][/COLOR][/SIZE]


Hint: -human-readable turns the subnet mask into CIDR notation.

---

### Post by jmkmx on 2024-09-04
This suggestion resolved my issue :o

After making changes in the bashrc file and exiting nano I used: ```
exec bash
```

Thank you for your help!

---


---
title: "Empty network file"
date: 2015-01-12
forum: New to Ubuntu
---

### Post by Mayte on 2015-01-12
Hi,

I'm new to ubuntu just install server 13.10 few days ago and it seems I made a mistake setting static IP because when I try to open now the network file using "sudo vi /etc/networking/interfaces" it doesn't show anything only "etc/networking/interfaces" [New DIRECTORY] in the left corner at the bottom of the screen.

How can I get back my file? Please 

Thanks

Myt

---

### Post by steeldriver on 2015-01-12
The file should be called 

```

/etc/**network**/interfaces

```

(no -ing) - vi thinks you are trying to create a new file (in a new directory /etc/networking)

---

### Post by Holger_Gehrke on 2015-01-12
A small tip to avoid mistakes like that **and** speed up command entry: the bash has command and file name completion. If you hit the tabulator key during entry, the bash will fill in as much as it can. Example: 'ls /e<tab>'  becomes 'ls /etc/'. If there is more than one way to complete the file name, a second press on the tabulator will show all possible completions; so
```

ls /etc/net<tab><tab>
```
will yield
```

netconfig      netscsid.conf  network/       networks
```

---


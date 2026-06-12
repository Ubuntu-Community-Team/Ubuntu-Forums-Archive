---
title: "How to show name and flag of a country that I'm currenty connected through Tor?"
date: 2023-06-20
forum: New to Ubuntu
---

### Post by desatir73162 on 2023-06-20
Hi there
I want to show the flag and name of the country that I'm currenty connected through Tor network in the right of top bar.
tried to use conky but I counldn't.
currently using ubuntu 22.04

thanks in advanced.

---

### Post by ActionParsnip on 2023-06-20
If you run:
```

sudo apt -y install whois

```

Then run:
```

whois `wget -qO- telnetmyip.com | grep comment | awk {'print $7'}` | grep -iE ^country

```
You will need to tell wget to use the SOCKS proxy that Tor uses. You can then get the country name you are in. You can then do something graphical with the output. Here is an example:
```

$ whois `wget -qO- telnetmyip.com | grep comment | awk {'print $7'}` | grep -iE ^country
country:        GB

```

---


---
title: "Conky wget stopped working"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2012-06-23
I have a conky that uses wget in a couple of places.
Everything worked fine until I booted up today and then my weather script and the part of the conky that pulls the exchange rate both stopped working.

When I ran the weather script in a terminal I noticed this right after starting the script:

```
wget: no process found
```

Does anyone know how I can get wget to work again?

---

### Post by Gone fishing on 2012-06-23
I think the problem is the wget part of your conky script has an error and wget cant download anything. Have a look at this and it might help [https://bbs.archlinux.org/viewtopic.php?id=139962](https://bbs.archlinux.org/viewtopic.php?id=139962)

---

### Post by GrouchyGaijin on 2012-06-23
> **Gone fishing said:**
> I think the problem is the wget part of your conky script has an error and wget cant download anything. Have a look at this and it might help [https://bbs.archlinux.org/viewtopic.php?id=139962](https://bbs.archlinux.org/viewtopic.php?id=139962)

Thanks,

I'm using a version of Teo's weather script that Sec11 modified and the other conky that uses wget calls the exchange rates from a web page.

The thing is that this happened all of a sudden.  I didn't make any changes to the conkys.
On one machine the weather conky still loads but the update is stuck at last night.
On the second machine the weather conky will not load anymore.

I think there is something in a recent round of Ubuntu updates that did it.  I haven't even opened a conkyrc file for months.

---

### Post by Gone fishing on 2012-06-24
I'm doubtful that its an update - I wonder if the URL has changed? Might be worth a check?

---

### Post by GrouchyGaijin on 2012-06-24
If for example I run 
```

${execi 3600 wget -q -O -  ["http://www.google.com/finance/converter?a=1000&from=JPY&to=USD"]("http://www.google.com/finance/converter?a=1000&from=JPY&to=USD")|grep  "<div id=currency_converter_result>"|sed 's/<[^>]*>//g'} 
```

in the conky I get zilch.  If I run 

```
wget -q -O -  ["http://www.google.com/finance/converter?a=1000&from=JPY&to=USD"]("http://www.google.com/finance/converter?a=1000&from=JPY&to=USD")|grep  "<div id=currency_converter_result>"|sed 's/<[^>]*>//g' 
```
in the terminal, it returns 

1000 JPY = 12.4000 USD

I checked the version of Conky in synaptic and it is still locked down at the same version I was using when everything worked.

---

### Post by stinkeye on 2012-06-24
Don't know if you had a copy/paste error but this works for me.
```
${execi 3600 wget -q -O - "http://www.google.com/finance/converter?a=1000&from=JPY&to=USD" | grep "<div id=currency_converter_result>" | sed 's/<[^>]*>//g'}
```
Ubuntu 12.04
conky --version 1.9.0-2


As far as I know it's only version 1.8.1-6 in the default 12.04 repo with problems.

---

### Post by GrouchyGaijin on 2012-06-24
> **stinkeye said:**
> Don't know if you had a copy/paste error but this works for me.
```
${execi 3600 wget -q -O - "http://www.google.com/finance/converter?a=1000&from=JPY&to=USD" | grep "<div id=currency_converter_result>" | sed 's/<[^>]*>//g'}
```Ubuntu 12.04
conky --version 1.9.0-2


As far as I know it's only version 1.8.1-6 in the default 12.04 repo with problems.

The thing is that I didn't change anything in the conkyrc.  I have had 1.8.1-6 locked for months now.

---

### Post by GrouchyGaijin on 2012-06-25
I installed Conky 1.9 from [http://packages.debian.org/testing/utils/conky-all](http://packages.debian.org/testing/utils/conky-all)
and now everything works as it should again.

---


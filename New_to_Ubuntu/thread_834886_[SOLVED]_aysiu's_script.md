---
title: "[SOLVED] aysiu's script"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by DrMilo on 2008-06-19
I used aysiu's script 

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

to force an install of Firefox 3 in Dapper. Since then I have upgraded to Hardy. Now Firefox crashes whenever I try to start it. I have tried removing all Firefox files through synaptic but it still happens after I reinstall. I think I need a way to totally purge Firefox. Or any suggestions would be welcomed, thanks.

---

### Post by Dynaflow on 2008-06-19
You can completely get rid of Mozilla's version, according the the page to which you linked, by doing these commands:

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

[As the tutorial says, be very, *very* careful with that last command.]

Then I suppose you would just reinstall from Add/Remove Programs or Synaptic.

---

### Post by DrMilo on 2008-06-19
> **Dynaflow said:**
> You can completely get rid of Mozilla's version, according the the page to which you linked, by doing these commands:

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

[As the tutorial says, be very, *very* careful with that last command.]

Then I suppose you would just reinstall from Add/Remove Programs or Synaptic.


My apologies, this day is rendering me stupid.

---


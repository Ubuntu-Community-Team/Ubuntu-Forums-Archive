---
title: "Boot with Guarddog, Surf with Firestarter"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Freedom Of Mountains on 2008-08-05
My problem is this: I installed Guarddog to my system, but before that I had Firestarter -I tried GD. only, after I tried I uninstalled it, and I kept Firestarter to default iptables gui. When sytem boots up, Firestarter can't be loaded (I get red 'failed' text, not the 'OK' at boot), instead system loads Guarddog succesfully(!), but I wonder about how can it be, because Guarddog IS NOT INSTALLED on my system, after all, how can be one program what I do not have (Guarddog) is switching on at boot?
And the second interesting thing is: I do not have internet connection until I start Firestarter, when I start it, then my internet connection 'gets the power', and I can surf, with big wondering eyes... Sorry about my English, it is not my mother tongue, but I hope someone may understand what I wrote, and help me to find out what can I do with the boot and the internet problems. Thanks.

---

### Post by bodhi.zazen on 2008-08-05
Remove all that and go with UFW :twisted:

```
sudo apt-get purge guarddog firestarter
```

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

I have not tried gufw ....

---

### Post by Freedom Of Mountains on 2008-08-05
Thank You, I think i will do this.. ;)

---


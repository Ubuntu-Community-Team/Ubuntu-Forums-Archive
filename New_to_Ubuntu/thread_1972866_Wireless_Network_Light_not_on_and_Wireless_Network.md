---
title: "Wireless Network Light not on and Wireless Network not working"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by CheesyFries on 2012-05-04
Hello. This is my first time using Ubuntu and I have a wireless problem. So, whenever I start up Windows OS the wireless light lights up showing some life onto the wireless connection. Unlike Windows, on Ubuntu the light doesn't light up and the wireless connection doesn't work. No matter how many times I turn it off and on the light won't light up. Either it's broken or something's going on.

Please help me. :)

---

### Post by carl4926 on 2012-05-04
Boot ubuntu
Open a terminal
Post result of

```
lspci -nnk
```

---

### Post by Segofam on 2012-05-04
Started my own thread...

---

### Post by grahammechanical on 2012-05-04
What wireless light? Is this a laptop?

If there is a key combination to switch the wireless adapter on, then switch the wireless adapter on before you boot into Ubuntu.

If you switch the wireless adapter off when in Windows, then it will say off when in Ubuntu. You need to leave the wireless adapter on when in Windows.

You also need to set up a connection to the wireless router/modem in Ubuntu.

We do this by clicking on the Network manager icon and selecting our wireless network from the list and then putting in the wireless authorisation pass phrase (not our log in password).

If you cannot see any wireless networks in that list, then your wireless adapter is

a) not switched on, See, comment made above & make sure that Enable Networking and Enable Wireless is ticked. Or,

b) not recognised by Ubuntu and you need to install a driver.

Please use this information to provide more detail as to the situation. Then you can be given advice.

Regards.

---


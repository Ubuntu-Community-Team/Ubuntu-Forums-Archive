---
title: "3G struglles"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by M@xil on 2011-11-05
Good morning 

I tried to install my vodafone huawei pocket wifi through a usb connection but failed, I have tried sakis3g but when going through the setup in the end it says " did not report GSm capabilities You can skip this by adding -noprobe command line switch" 

how do i do this? I am running ubuntu 11.10 on a dual boot with windows 7, the windows is 64bit so i believe that ubuntu would also be. 

did the following commands as well " killall modem-manager" and " modprob usbserial vendor=0x12d1 product=0x1506" no joy 

Any suggestions would be highly appreciated

regards
M

---

### Post by gandaran on 2011-11-06
what is the huawei brand model? maybe the device is so brand new it's not yet supported by usb-modeswitch!
using the network manager mobile setup wizard should get the modem working, you just have to be careful with the connection details are 100% correct, the APN being the most important for a successful connection.
and you can also try the vodafone mobile connect software. 
[https://forge.betavine.net/frs/?group_id=76](https://forge.betavine.net/frs/?group_id=76)

---

### Post by M@xil on 2011-11-06
It is a hauwei E585 model it came out last year.  Thanks will try the vodafone link

regards
M

---

### Post by gandaran on 2011-11-06
> **M@xil said:**
> It is a hauwei E585 model it came out last year.  Thanks will try the vodafone link

regards
M
does look new! could be the problem!
just another question, about the modem internet plan, is it a contract or one of those UK vodafone top up and go?
if it is the top up and go then you are going to have problems unless you know the connection details needed as not all use the same APN
the best way to get details is from the modem installed vodafone software on windows PC check the properties/preferences window.

---

### Post by M@xil on 2011-11-06
HI there 
 
It is a prepaid contract here in australia, will check the details on my windows machine and go from there. Running on ubuntu 11.10 if that helps. thanks for the help so far
 
regards
M

---

### Post by M@xil on 2011-11-09
Solved this problem by buying a netgear usb wireless adapter product code wg111v3, thanks to all who replied to this post.

regards
M

---


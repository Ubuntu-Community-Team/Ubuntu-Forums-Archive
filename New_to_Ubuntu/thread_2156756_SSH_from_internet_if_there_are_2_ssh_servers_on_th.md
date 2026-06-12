---
title: "SSH from internet if there are 2 ssh servers on the particular network?"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by Aphexlog on 2013-06-23
This I'm sure this is very noobish but I shall proceed. what would happen if you were to attempt to log in vie ssh from outside the net work (from the Internetz) and you had two ssh servers on the network? --you have one external IP so would it screw things up oorrr? -- how would it depict what server on that network to use? would you then have to use some sort of extension kind of like you would with an addon or sub domain? or am I over looking something simple? :confused:

---

### Post by Hadaka on 2013-06-23
Hi, the easy way would be to port forward from the router..

ssh -p2200 [EMAIL="server1@router.ip"]server1@router.ip[/EMAIL]-----------router portforward 2200 to server1.ip
ssh -p2201 [EMAIL="server2@router.ip"]server2@router.ip[/EMAIL]-----------router portforward 2201 to server2.ip
to the outside world..each machine within your lan...with its unique ip address
is the same as a separate network. Once attached of course it should have access
to the entire network...depending on how that network is configured.
that help?

---


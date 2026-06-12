---
title: "DHCP Server Side Config with Option 82"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by unagaraj on 2012-03-26
Could someone provide some tips on what the dhcpd.conf file should look like if I want to use DHCP option 82 to provide clients with IP addresses? 

Specifically, the clients need to get addresses in a particular range, but the relay agent can have an address that is not in this range. Can this be accomplished using Option 82 parameters?

Here's an example:
Comp1 is connected to a router on a VLAN that does not have an IP interface. The router has another VLAN that has an IP interface and connectivity to a DHCP server. Can the IP address of the VLAN that has connectivity to the DHCP server be used in the giaddr field of the DHCP packet? The option 82 fields will have Comp1's data encoded (mac address, port etc), so the DHCP replies can be properly forwarded out to the client.

Here's the crux though, the IP address that the DHCP server should give out should not be dependent on the GIADDR field. However, the server's reply should be sent to the relay agent address (that's in the giaddr).

Please let me know if I am not explaining myself clearly enough!

And thanks in advance for any replies!

Regards,
-Uday

---

### Post by unagaraj on 2012-03-26
C'mon guys! This shouldn't be such a hard one! Anything I can do to clarify my question?

Thanks,
-Uday

---

### Post by unagaraj on 2012-03-27
I am surprised and disappointed that no one has bothered to make even some suggestions! I was under the impression that Ubuntu server would be quite widely used and that the DHCP server functionality would be very widely used. Am I wrong? Do I need to bank on the Microsoft DHCP servers to provide me with this functionality?

Seem rather strange.

-Uday

---

### Post by Doug S on 2012-03-27
Your question is pretty advanced, and might have received more attention over on the server platforms forum. (Maybe a moderator could move it?)
 
Myself, I do not know the answer to your question. I do have something similar in my setup, but different enough (I think) that I am unable to provide help for you.

---

### Post by unagaraj on 2012-03-27
Thanks Doug. I'll post my question there too.

Regards,
-Uday

---

### Post by Doug S on 2012-03-27
I was going to say "NO", but I see that you posted there already. You are not supposed to multiple post the same thing (which I should have mentioned before).

---

### Post by unagaraj on 2012-03-27
Oops! I hope I haven't offended anyone!

---


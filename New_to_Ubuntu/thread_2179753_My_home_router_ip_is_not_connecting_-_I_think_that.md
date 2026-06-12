---
title: "My home router ip is not connecting - I think thats what its called"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by julia3 on 2013-10-09
I just marked my other two threads as solved. As I thought I should. Since becasue of you guys were solved. But yet another problem. I did something and now I'm kicking myself over it. And I do not know how to fix it. 
julia@julia-OptiPlex-745:~$ netstat -nat | grep 22 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 IP        Ip adress           ESTABLISHED
tcp        0      0 Ip           Ip      ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     
I replaced my ip adress which is correct with ip for my own protection. I do not know if people could get my ip and then hack it or not. I think this is my problem. The first 0.0.0.0 is suppose to be my home ip server. 10.0.0.11
Which I think is everyones airpot server ip. Well I type it into the firefox url bar. It says....
Unable to connect
 Firefox can't establish a connection to the server at 10.0.0.11.
   The site could be temporarily unavailable or too busy. Try again in a few
    moments.
  If you are unable to load any pages, check your computer's network
    connection.
  If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.
So I can;t login to my routers ip adress. Which is making me very fusturated. 
What did I do? I installed...
sudo apt-get install openssh-server openssh-client

---

### Post by MikeEvans on 2013-10-09
Hi Julia3,

I think you are trying to connect to your airport's http interface.  You need to determine the IP address of the airport.  I do not have an airport but I think I can help.  If your airport is your primary router then it should be both your gateway and your DHCP host.  

To find the address of your gateway run "route - n".  The first line should show your primary gateway.  This should be the address of your airport.  Try that address in firefox.

If that didn't work you can try to get the address of you DHCP host, which should be your airport.  Run "cat /var/lib/dhcp/dhclient.leases".  Look for "option dhcp-server-identifier x.x.x.x".

---

### Post by julia3 on 2013-10-09
Thanks for the speedy reply. I do the ip of my router. Its 10.0.0.1. 
When I type that in however it does not load. 
And I did route - n
It did not even display.

---

### Post by julia3 on 2013-10-09
Solved. How I solved it. Was I reset my router for thirty seconds.

---


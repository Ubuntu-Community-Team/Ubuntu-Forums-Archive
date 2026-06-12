---
title: "SSH tunnelling and Remote Desktop"
date: 2018-09-17
forum: New to Ubuntu
---

### Post by ndnd on 2018-09-17
Hello, 
I recently setup my MAC to access ubuntu server with tightvnc. For that I setup ssh tunnel (with key based authentication) using the command 

```
ssh -i /home/xxx/key -L 5900:localhost:5900  abc@100.100.100.10
```


I was able to use the tightvnc java viewer to connect. However, I am not able to understand even after closing the above terminal window I am still able to connect to the ubuntu server. Even from another PC ? The key based authentication has become ineffective ? 

I am not very familiar with ssh connections and if someone could guide be as to what to do to correct this? 

I want it to work like this 

```
Step1: Setup SSH tunnel to the specific port for tightvnc
Step 2: Use Tightvnc for remote desktop access
Step3: without SSH tunnel (key based authentication) no remote desktop access
```

---

### Post by steeldriver on 2018-09-17
Did you remember to disallow non-tunneled connections on the server side (by firewalling port 5900 and/or configuring the VNC server to listen only on the loopback interface)?

---

### Post by ndnd on 2018-09-17
Thanks for the quick reply. Could you tell me how to go about doing this or checking. I had set this up long time back for to connect from Windows using Putty. Only recently I saw this so I don't even remember how I set it up. 

What is safer measure ?   if I have 3-4 users using windows/MAC using few ports lets say 59xx 59yy 


Option 1: Do I have to firewall 
 
Or 

Option 2: Configure tightVNC server to listen only on the loopback interface (by that you mean 127.0.0.1::port right?)  

Sorry some details might be needed for a newbie like me :)

If option 2 or 1 is better any more idea on how to go about doing that would be of great help!

---

### Post by steeldriver on 2018-09-17
I think tightvncserver should support a -localhost option (not directly - but it should pass it to the underlying Xvnc process) however it may be easier/more reliable to use your firewall (since you likely want to enable that anyway, especially if the server is internet facing)

For example with UFW, make sure you have added a rule to allow SSH and then apply the "default deny" policy for everything else

---

### Post by ndnd on 2018-09-17
I was able to check and solve the problem but I want to make sure 

I did the 'localhost' option while starting the VNC server. 

However, while searching I used the nestat -ntlup command and saw there are bunch of ports open (including the tightvnc and xvmc which I believe would be ok now) 

>  Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:5901          0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:5902          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:5678            0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:5903          0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:6002            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:6003            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
udp        0      0 0.0.0.0:65045           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 10.240.166.170:123      0.0.0.0:*                           -               
udp        0      0 127.0.0.1:123           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:123             0.0.0.0:*                           -               
udp6       0      0 :::47440                :::*                                -               
udp6       0      0 :::123                  :::*                                -     

The only access I am doing is through SSH but I don't which ones to keep open/close ? Is there a red flag here ?

---


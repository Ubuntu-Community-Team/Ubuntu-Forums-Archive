---
title: "Wifi"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by R_T_WALLER on 2008-10-26
I started using the remix version but might switch back becuase for some reason my WIFI isnt working. When I hit F2 to turn it on it turns on for 3 seconds then turns off. I succesful used wifi with the original os so I dont know whats going on. I have also tried the standard version andI cant remember if I ever got to try using wifi, but one problem is that many of the windows that open for preferences etc. are to large to fit on the screen and then when I click on something it just shifts the box so that I can see the bottom but it never lets me click on anything. I think I'd prefer to use the standard over the remix but I would still like to solve the wifi problem.

Thanks

---

### Post by R_T_WALLER on 2008-10-26
also i can connect to th internet through a wire in my room but when I go to another building I am no geting internet through the wire. I had the remix workwith both cords before but that was before i changed os's a couple times

---

### Post by Crafty Kisses on 2008-10-26
What are the results of this command?
```
lshw -C network
```

---

### Post by R_T_WALLER on 2008-10-26
robert@robert-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:22:15:5c:c5:0e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl2 driverversion=2.0.5 firmware=L2 ip=149.159.49.49 latency=0 module=atl2 multicast=yes
robert@robert-laptop:~$

---

### Post by R_T_WALLER on 2008-10-26
With out my ethernet cord in it said this

robert@robert-laptop:~$ robert@robert-laptop:~$ lshw -C network
bash: robert@robert-laptop:~$: command not found
robert@robert-laptop:~$ WARNING: you should run this program as super-user.
bash: WARNING:: command not found
robert@robert-laptop:~$   *-network               
bash: *-network: command not found
robert@robert-laptop:~$        description: Ethernet interface
bash: description:: command not found
robert@robert-laptop:~$        product: L2 100 Mbit Ethernet Adapter
bash: product:: command not found
robert@robert-laptop:~$        vendor: Attansic Technology Corp.
bash: vendor:: command not found
robert@robert-laptop:~$        physical id: 0
bash: physical: command not found
robert@robert-laptop:~$        bus info: pci@0000:03:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
bash: bus: command not found
robert@robert-laptop:~$        logical name: eth0
bash: logical: command not found
robert@robert-laptop:~$        version: a0
bash: version:: command not found
robert@robert-laptop:~$        serial: 00:22:15:5c:c5:0e
bash: serial:: command not found
robert@robert-laptop:~$        width: 64 bits
bash: width:: command not found
robert@robert-laptop:~$        clock: 33MHz
bash: clock:: command not found
robert@robert-laptop:~$        capabilities: bus_master cap_list ethernet physical
bash: capabilities:: command not found
robert@robert-laptop:~$        configuration: broadcast=yes driver=atl2 driverversion=2.0.5 firmware=L2 ip=149.159.49.49 latency=0 module=atl2 multicast=yes
bash: configuration:: command not found
robert@robert-laptop:~$ robert@robert-laptop:~$ 
bash: robert@robert-laptop:~$: command not found
robert@robert-laptop:~$

---


---
title: "Losing Internet Connectivity"
date: 2022-08-20
forum: New to Ubuntu
---

### Post by dmacpeak on 2022-08-20
I'm losing internet connectivity regularly. This seems to have started when the VPN was installed which was ivpn from the snap package, however I installed the VPN so soon after beginning to use some Bluetooth it's hard to say if that is the issue.

After I turned off the VPN I was able to connect to the internet for a little while and prior to that I wasn't able to connect to the VPN and didn't have access to the internet. Now I have access to the VPN and can turn on ivpn but I have no internet connection and I've never had both at the same time.

I've tried pinging Mozilla on Google turning off the firewall and a host of things but if there's some sort of command that can help me connect to the internet through the terminal I would be most appreciative

---

### Post by bobunderwood99 on 2022-08-20
Hello,

Did you create an account with IVPN? [https://www.ivpn.net/](https://www.ivpn.net/) 

[https://www.techradar.com/vpn/virtual-private-networks](https://www.techradar.com/vpn/virtual-private-networks)

---

### Post by dmacpeak on 2022-08-20
Yes, I have an IVPN account.  I went through all the terminal entries after which I realized it was redundant bc I had the snap package downloaded.

The IVPN worked right away, but the Mozilla died soon after. I was then able to connect to Mozilla w the VPN off and connected to the VPN successfully after. They both worked for a short period.....

Now only the VPN will work and I can't connect to Mozilla regardless of IVPN on or off.

I will read the link you sent, thank you!

---

### Post by bobunderwood99 on 2022-08-21
The IVPN website states: [https://www.ivpn.net/apps-linux/](https://www.ivpn.net/apps-linux/) 

"Uninstall prior versions (DEB, RPM, etc.) of the IVPN App before switching to the snap release channel and vice versa."

At this point I would purge both versions then reinstall one version only.

---

### Post by ActionParsnip on 2022-08-21
I'm betting you can't hit DNS when the VPN is up. Once you connect, run
```

echo "nameserver 8.8.8.8"  | sudo tee /etc/resolv.conf > /dev/null

```
I have this with Surfshark via Openvpn client

---

### Post by SeijiSensei on 2022-08-21
If it matters, the "correct" way to fix your default DNS servers on recent Ubuntu systems using systemd is to edit /etc/systemd/resolved.conf and add the nameserver IPs to the DNS and FallbackDNS lines. Then restart the resolver with "sudo systemctl restart systemd-resolved".

---

### Post by ActionParsnip on 2022-08-21
> **SeijiSensei said:**
> If it matters, the "correct" way to fix your default DNS servers on recent Ubuntu systems using systemd is to edit /etc/systemd/resolved.conf and add the nameserver IPs to the DNS and FallbackDNS lines. Then restart the resolver with "sudo systemctl restart systemd-resolved".

Indeed but my command allows us to test. I think the VPN lacks split tunnelling so the DNS on the LAN will not be reachable

---

### Post by dmacpeak on 2022-08-22
It turns out the enabling of UFW was blocking the connection. After I disabled the firewall I could connect....

I guess I'll have to fly naked as to firewall if I want to use the net.

PS. I had a guy who originally worked at Red Hat prior to the acquisition by IBM helping me last night. He said UFW was not a real necessity unless I was running a server. He thought I'd be fine on a single machine without it.  He thought I was in much better security position w Ubuntu 20.04 than I would be with IOS, and light years safer than windows.

---

### Post by ActionParsnip on 2022-08-22
You don't have to fly naked. Just allow port 80,443 and 53 in and out of the firewall and you'll have Internet access

---

### Post by dmacpeak on 2022-08-24
How do I allow ports 80,443 and 53. Is it a command line thing or done from settings?

---

### Post by ActionParsnip on 2022-08-24
Ufw has a GUI but yes you can do it in the terminal if you like. Lots of guides online

---

### Post by ActionParsnip on 2022-08-25
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---


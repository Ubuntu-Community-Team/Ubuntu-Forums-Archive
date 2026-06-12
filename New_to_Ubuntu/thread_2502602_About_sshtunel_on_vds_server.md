---
title: "About sshtunel on vds server"
date: 2024-11-21
forum: New to Ubuntu
---

### Post by megaster on 2024-11-21
Friends, I use my vds server as sshtunel, now I want to use the ubuntu server that I installed on vmware as sshtunel, but I couldn't access the outside world. I did some research, there is something called reverse bridging, I couldn't understand this table, can someone who understands help me? It confused me a bit, when I do what is in this table, a vds account is opened on my virtual server, but I couldn't direct the port


[https://iximiuz.com/en/posts/ssh-tunnels/](https://iximiuz.com/en/posts/ssh-tunnels/)


[[IMG]https://i.hizliresim.com/4j5i4ni.jpg[/IMG]]("https://hizliresim.com/4j5i4ni")

---

### Post by TheFu on 2024-11-22
I'm confused.  Do you have a public IP, not private IP, on the internet from your ISP?
With VMware (or any hypervisor), just be certain to place the virtual machine setup in bridge mode and the VM will have the same access to the internet that the host has.  If you set it to be NAT, that's likely the issue.  No need for ssh-tunneling.

BTW, ssh tunnels only work for TCP traffic, not UDP.  That can cause privacy issues.  Tunnels are usually best when UDP is used, like a VPN would provide (aka wireguard).

What's a "vds server"?  I've used VPS, but never heard of VDS.

And before you go too far with VMware anything, perhaps you'd rather use a F/LOSS hypervisor that performs better or are easier to use without the proprietary software?  Since VMware was bought by Broadcom, they've not be too nice towards their customers. Should we reward that behavior?
[https://arstechnica.com/information-technology/2024/10/broadcom-tried-to-jack-vmware-prices-by-1050-percent-att-claims/](https://arstechnica.com/information-technology/2024/10/broadcom-tried-to-jack-vmware-prices-by-1050-percent-att-claims/)
[https://www.businessinsider.com/vmware-customers-price-hike-late-fees-broadcom-acquisition-2024-10](https://www.businessinsider.com/vmware-customers-price-hike-late-fees-broadcom-acquisition-2024-10)
[https://www.cio.com/article/2513389/vmware-licensing-and-pricing-hikes-what-options-do-you-have.html](https://www.cio.com/article/2513389/vmware-licensing-and-pricing-hikes-what-options-do-you-have.html)
Beware.

---


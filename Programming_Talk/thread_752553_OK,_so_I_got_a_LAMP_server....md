---
title: "OK, so I got a LAMP server..."
date: 2008-04-11
forum: Programming Talk
---

### Post by Fixman on 2008-04-11
But how do I access it from other computers? I can enter with [http://localhost](http://localhost), and with [http://127.0.0.1](http://127.0.0.1), but I can't by putting my public IP. (My IP is 201.235.222.57). Can you try entering (by pasting my IP into the address bar) or giving some advice of how can I publish my site by IP address? (because I'm just too lazy to get a DNS address).

---

### Post by LaRoza on 2008-04-11
> **Fixman said:**
> But how do I access it from other computers? I can enter with [http://localhost](http://localhost), and with [http://127.0.0.1](http://127.0.0.1), but I can't by putting my public IP. (My IP is 201.235.222.57). Can you try entering (by pasting my IP into the address bar) or giving some advice of how can I publish my site by IP address? (because I'm just too lazy to get a DNS address).

Does your ISP allow you to run a server on your plan?

---

### Post by Fixman on 2008-04-11
> **LaRoza said:**
> Does your ISP allow you to run a server on your plan?

Yes, it does.

But anyway, I have a router connecting to the internet. May that be a problem?

---

### Post by LaRoza on 2008-04-11
> **Fixman said:**
> Yes, it does.

But anyway, I have a router connecting to the internet. May that be a problem?

You would have to set it to forward the ports.

---

### Post by ruy_lopez on 2008-04-11
> **Fixman said:**
> Yes, it does.
But anyway, I have a router connecting to the internet. May that be a problem?

The simplest method is to enable port forwarding on your router (point port 80 at the private IP of the LAMP system). Then you need a dynamic dns name. No-ip and dyndns offer free dynamic addresses. Google them.

Just make sure you have everything locked down before going public.

---

### Post by Fixman on 2008-04-11
Dear LaRoza and ruy_lopez, would you marry me?

---

### Post by LaRoza on 2008-04-11
> **Fixman said:**
> Dear LaRoza and ruy_lopez, would you marry me?

No, I already have a Thinkpad (which I consider to be a sentient entity and deserving of all my earthly love)

---


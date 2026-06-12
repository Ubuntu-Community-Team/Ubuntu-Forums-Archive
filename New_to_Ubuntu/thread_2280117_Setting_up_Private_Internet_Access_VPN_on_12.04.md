---
title: "Setting up Private Internet Access VPN on 12.04"
date: 2015-05-28
forum: New to Ubuntu
---

### Post by neil_williams on 2015-05-28
Hi All,

Extreme noob here.  When trying to set up my VPN, I am entering the following:

**sudo openvpn UK Southampton.ovpn**

to connect to the southampton VPN.  But I keep getting the following error message:

[B]Options error: I'm trying to parse "UK" as an --option parameter but I don't see a leading '--'

[/B]
Any advice would be gratefully received!

NW

---

### Post by corti-nico on 2015-05-28
> **neil_williams said:**
> Hi All,

Extreme noob here.  When trying to set up my VPN, I am entering the following:

**sudo openvpn UK Southampton.ovpn**

to connect to the southampton VPN.  But I keep getting the following error message:

[B]Options error: I'm trying to parse "UK" as an --option parameter but I don't see a leading '--'

[/B]
Any advice would be gratefully received!

NW
Can you try with
```

sudo openvpn "UK Southampton.ovpn"

```
I think that there is a space that makes you trouble ;)

---

### Post by matt_symes on 2015-05-28
Hi

> sudo openvpn UK Southhampton.ovpn

Are you sure you need the "UK" in there ?

Last time i set up a VPN to allow my friend to view his house cameras whilst on holiday, i just passed the ovpn file directly to openvpn while i was testing it. I then set up a VPN client on his phone.

I'm pretty sure i didn't need to use sudo either, but i may be mistaken as it was a while ago.

Kind regards

---

### Post by neil_williams on 2015-05-28
thanks both;  I eventually ended up using their beta applet to get it set up.  Result.

---

### Post by tristan16 on 2015-05-28
If you install network-manager-openvpn, you can create the VPN connection in the NetworkManager, just like a normal WiFi connection.

---

### Post by sandyd on 2015-05-29
> **neil_williams said:**
> Hi All,

Extreme noob here.  When trying to set up my VPN, I am entering the following:

**sudo openvpn UK Southampton.ovpn**

to connect to the southampton VPN.  But I keep getting the following error message:

[B]Options error: I'm trying to parse "UK" as an --option parameter but I don't see a leading '--'

[/B]
Any advice would be gratefully received!

NW

Try (Replacing *filenamehere* with configuration file)
```

sudo openvpn --config "*filenamehere*"
```

As mentioned, it can also be used with networkmanager
```

sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome
```

You should then be able to create a new openvpn connection.

---


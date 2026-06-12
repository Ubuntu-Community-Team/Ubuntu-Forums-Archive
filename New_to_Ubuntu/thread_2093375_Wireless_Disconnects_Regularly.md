---
title: "Wireless Disconnects Regularly"
date: 2012-12-10
forum: New to Ubuntu
---

### Post by Cuencano on 2012-12-10
I have an older Sony Vaio VGN SZ650N running Ubuntu 12.04 LTS. Every 10 minutes or so it will disconnect from the router and then automatically reconnect. At the same time, other computers on the network also get disconnected, so it seems like the router is being reset.

I've collected some system information using a script I found on the forum - see attachment.

I'd be grateful for any advice on how to stop this behavior.

Roger

---

### Post by Cuencano on 2012-12-10
I just want to clarify that this behavior only happens when the Sony is connected by WiFi to the router. If the Sony is connected by LAN or is turned off, the network is stable with the remaining computers.

So this does not seem to be a problem with the router per se, but rather the interaction between the router and the Sony via WiFi.

---

### Post by Jmackxxx on 2012-12-10
I sounds Like a internal problem with your Router. Try changing the Security encryption on your Router even if its just temporary and see if it changes. I believe its a handshake issue

---

### Post by agxryt on 2012-12-10
> **Cuencano said:**
> I have an older Sony Vaio VGN SZ650N running Ubuntu 12.04 LTS. Every 10 minutes or so it will disconnect from the router and then automatically reconnect. At the same time, other computers on the network also get disconnected, so it seems like the router is being reset.

I've collected some system information using a script I found on the forum - see attachment.

I'd be grateful for any advice on how to stop this behavior.

Roger

From the output:

```
[ 6378.039642] wlan0: authenticate with <MAC address removed> (try 1)
[ 6378.041984] wlan0: authenticated
[ 6378.042322] wlan0: associate with <MAC address removed> (try 1)
[COLOR=Blue]*[ 6378.056691] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=12 aid=1)*[/COLOR]
[COLOR=Blue][ 6378.056696] *wlan0: <MAC address removed> denied association (code=12)*[/COLOR]
[ 6378.076459] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
```Looks like your router (the one who the request is being made to) is denying the connection to your PC. 

I'm not really sure what code 12 means, BUT I found a couple of posts mentioning trying wicd instead of network manager. 

You'd have to install wicd, THEN stop network manager. The problem is, if wicd doesn't work, you'll lose internet connection. haha! So don't uninstall network-manager just yet.

From what I've read, wicd should just take over. If not, try starting it manually in terminal.

```
sudo apt-get install wicd
```Once that has correctly installed,

```
sudo stop network-manager && wicd
```Should stop the network manager process, and start up the wicd daemon.

If this doesn't work, just restart the network-manager process.

```
sudo start network-manager
```

---

### Post by Cuencano on 2012-12-11
Changing from network manager to wicd seems to have solved this problem.

Thanks.

---


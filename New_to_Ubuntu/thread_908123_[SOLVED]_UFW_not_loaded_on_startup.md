---
title: "[SOLVED] UFW not loaded on startup"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Stefanie on 2008-09-02
I'm using Ubuntu Hardy and ufw is not enabled on startup, I have to run sudo ufw enable after boot. This is the output of cat /etc/ufw/ufw.conf:

```
# /etc/ufw/ufw.conf
# 

# set to yes to start on boot
ENABLED=yes
```

Does anyone know how to fix this?

---

### Post by gn2 on 2008-09-02
ufw is for modifying firewall settings.
The firewall is iptables.
You don't need ufw running at startup.

This may be helpful: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Stefanie on 2008-09-02
i need ufw running at startup because i use it to open a port for the connection with my mobile phone.

---

### Post by brian_p on 2008-09-02
> **Stefanie said:**
> i need ufw running at startup because i use it to open a port for the connection with my mobile phone.

Having the port open all the time seems the sensible thing.

---

### Post by lovinglinux on 2008-09-02
> **Stefanie said:**
> i need ufw running at startup because i use it to open a port for the connection with my mobile phone.

Once you open the port you can close the firewall. Next time you reboot the port will still be open. You only need to open the firewall interface when you need to modify the rules. That is how iptables work. I use Firestarter and open it when I login just because I want to monitor the connections, but I don't need it running to keep me safe. Once the firewall rules are created they don't change and they don't need the GUI to be running to be effective.

---

### Post by Stefanie on 2008-09-02
After startup I can't sync my mobile phone, but after running "sudo ufw enable" I can. So I guess I need ufw enabled on startup, and for the moment it isn't.

---

### Post by billgoldberg on 2008-09-02
> **Stefanie said:**
> After startup I can't sync my mobile phone, but after running "sudo ufw enable" I can. So I guess I need ufw enabled on startup, and for the moment it isn't.

That shouldn't be the case.

Are you sure you "did it right"?

You can configure UFW with GUFW (gui tool, google it). 

Or try firestarter to configure iptables for you.

---

### Post by brian_p on 2008-09-02
> **Stefanie said:**
> After startup I can't sync my mobile phone, but after running "sudo ufw enable" I can. So I guess I need ufw enabled on startup, and for the moment it isn't.

A little experiment to test ufw's involvement.

Remove ufw from the system.

```
sudo apt-get remove --purge ufw
```

Reboot and check mobile phone's ability to sync. Return to the original configuration with

```
sudo apt-get install ufw
```

Check phone again.

---

### Post by Stefanie on 2008-09-03
UFW was not loaded on startup, the output of "sudo ufw status" was "firewall disabled" (or something like that) and I couldn't sync my phone. After running "sudo ufw enable", however, I could, and "sudo ufw status" confirmed that the port was open. I am sure I set the rules correctly, and syncing really only works with ufw enabled, I double-checked everything.  

I found a solution, but it's a bit weird. I figured I don't need firestarter since I use ufw, so I uninstalled firestarter and now ufw is always enabled after startup, no need to run ufw enable anymore. Does anyone know how firestarter can be related to ufw? Apparently this guy had exactly the same issue so I'm not the only one :-) [http://ge.ubuntuforums.com/showthread.php?p=5582270](http://ge.ubuntuforums.com/showthread.php?p=5582270)

Thanks for the tip about GUFW, I'll check it out.

---

### Post by lovinglinux on 2008-09-03
> **Stefanie said:**
> I found a solution, but it's a bit weird. I figured I don't need firestarter since I use ufw, so I uninstalled firestarter and now ufw is always enabled after startup, no need to run ufw enable anymore. Does anyone know how firestarter can be related to ufw?

They are related because both are just GUI's to easily edit iptables. The real firewall is the iptables. To avoid problems you should have only one firewall GUI like now, unless you know what you are doing. Probably Firestarter was configured to load on login and hadn't rules for your phone port. So when you was logging in, Firestarter was silently rewriting the iptables. When you launch Gufw, it overwrite the iptables again with new rules, including the one for your phone port.

---

### Post by hyper_ch on 2008-09-03
why do you even modify the default firewalls settings? In most cases nothing is required to be changed.

---

### Post by Stefanie on 2008-09-03
> **lovinglinux said:**
> They are related because both are just GUI's to easily edit iptables. The real firewall is the iptables. To avoid problems you should have only one firewall GUI like now, unless you know what you are doing. Probably Firestarter was configured to load on login and hadn't rules for your phone port. So when you was logging in, Firestarter was silently rewriting the iptables. When you launch Gufw, it overwrite the iptables again with new rules, including the one for your phone port.

thanks for this explanation, now I understand what was happening. 

@hyper_ch: please read everything carefully before posting. Like I said, I need to add a rule because I want to sync my phone, as is explained here: [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

---

### Post by hyper_ch on 2008-09-03
> **Stefanie said:**
> @hyper_ch: please read everything carefully before posting. Like I said, I need to add a rule because I want to sync my phone, as is explained here: [http://www.synce.org/moin/SynceWithUbuntu](http://www.synce.org/moin/SynceWithUbuntu)

I did and that post says nothing about altering the default rules. You know, the default rules are: There are none

That means nothing is being blocked ;) and that is good so because for most people there is nothing that needs to be blocked. All that howto says is that if you have blocked all your stuff, you need to open that one connection. By default you don't ahve to do that ;)

---

### Post by Stefanie on 2008-09-03
i thought all ports were closed by default in ubuntu...

---

### Post by hyper_ch on 2008-09-03
you thought wrong. Why should all ports be closed?

- there are by default no servers running that open ports (unlike some other OS)
- by installing OSS you don't get all those programs that "phone home" (unlike some other OS)

So there is no need to have ports closed.

---

### Post by Stefanie on 2008-09-03
And what about security threads, eg attacks from the internet? When i was using firestarter i sometimes got a warning about a thai/vietnamese/chinese etc computer being blocked - apparently some people do try to break into your system?

---

### Post by hyper_ch on 2008-09-03
if you have no servers running then that does not do anything...

---


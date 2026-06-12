---
title: "Help with Script, please"
date: 2008-04-18
forum: Programming Talk
---

### Post by Amorget on 2008-04-18
I am having some issues with a basic script I set up to use a given ip address and subnet mask.  It is for setting up wireless routing for a VirtualBox.

Here it is:

```
#! /bin/bash
sysctl net.ipv4.ip_forward=1

X="VBoxTunctl -b -u username"

echo $X

ip link set ${X} up
ip addr add ${1}/${2} dev ${X}

parprouted eth1 ${X}

```

Here is the output I get when I run:

sudo ./TapUp.sh 192.168.0.111 24

```
net.ipv4.ip_forward = 1
VBoxTunctl -b -u amorget
Error: either "dev" is duplicate, or "-b" is a garbage.

```

Any help?

Also, would anyone happen to know if there is a way to use DHCP and "request" an ip address?  I'd like it if instead of having to input the ip address if it would grab one from the DHCP server.

Thanks,
Douglas

---

### Post by mssever on 2008-04-18
> **Amorget said:**
> I am having some issues with a basic script I set up to use a given ip address and subnet mask.  It is for setting up wireless routing for a VirtualBox.

Here it is:

```
#! /bin/bash
sysctl net.ipv4.ip_forward=1

X="VBoxTunctl -b -u username"

echo $X

ip link set ${X} up
ip addr add ${1}/${2} dev ${X}

parprouted eth1 ${X}

```Here is the output I get when I run:

sudo ./TapUp.sh 192.168.0.111 24

```
net.ipv4.ip_forward = 1
VBoxTunctl -b -u amorget
Error: either "dev" is duplicate, or "-b" is a garbage.

```Any help?

Also, would anyone happen to know if there is a way to use DHCP and "request" an ip address?  I'd like it if instead of having to input the ip address if it would grab one from the DHCP server.

Thanks,
Douglas

I'm not too familiar with network config, but it appears that your problem is due to your unquoted variable expansions. See if this works (noticing the double quotes): ```
#! /bin/bash
sysctl net.ipv4.ip_forward=1

X="VBoxTunctl -b -u username"

echo "$X"

ip link set "$X" up
ip addr add "$1/$2" dev "$X"

parprouted eth1 "$X"
```

---

### Post by Amorget on 2008-04-18
That helps!  One problem I am running into, I wanted X to be the output of the line "VBoxTunctl -b -u username", but it is being set to "VBoxTunctl -b -u username".  It should be coming back as tap0 (or something of the sort).

Any idea in how I can do that?

---

### Post by mssever on 2008-04-18
> **Amorget said:**
> That helps!  One problem I am running into, I wanted X to be the output of the line "VBoxTunctl -b -u username", but it is being set to "VBoxTunctl -b -u username".  It should be coming back as tap0 (or something of the sort).

Any idea in how I can do that?

OK, use command substitution: ```
X="$(VBoxTunctl -b -u username)"
```
Note that you'll sometimes see command substitution in `backquotes` instead of $(this way) but the $() way is much more flexible.

---

### Post by stroyan on 2008-04-18
> **Amorget said:**
> Also, would anyone happen to know if there is a way to use DHCP and "request" an ip address?  I'd like it if instead of having to input the ip address if it would grab one from the DHCP server.

You should look at the dhclient command.
It is what normally makes DHCP requests and configures interfaces with the results.

---

### Post by Joeb454 on 2008-04-18
Or if the above doesn't work you could try this ```
X=`VBoxTunctl -b -u username`
```

That _*should*_ assign X to the output of that VBox command :)

---

### Post by mssever on 2008-04-19
> **Joeb454 said:**
> ```
X=`VBoxTunctl -b -u username`
```

This code is inferior for two reasons:
[LIST=1]
[*]The $() notation is more flexible than ``. For example, you can nest them.
[*]Since you didn't surround your assignment with double quotes, you could end up with errors if the output of VBoxTunctl contains whitespace.[/LIST]

---


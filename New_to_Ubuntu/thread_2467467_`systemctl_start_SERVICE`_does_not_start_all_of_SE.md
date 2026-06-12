---
title: "`systemctl start SERVICE` does not start all of SERVICE@*"
date: 2021-09-27
forum: New to Ubuntu
---

### Post by 90v45mfsdhbgsd on 2021-09-27
When I run `systemctl start openvpn` the `openvpn@server_tap` starts.

But I created another server config `/etc/openvpn/server_tun` and another service `/etc/systemd/system/multi-user.target.wants/openvpn@server_tun.service` (copied from `openvpn@server_tap.service`) and this service does not start with `systemctl start openvpn`. I start it manually with `systemctl start openvpn@server_tun`.

But when I run `systemctl stop openvpn`, both of them stop!

I am not very familiar with systemd.
Did not `openvpn.service` start all of `openvpn@*.service` variants created from me?
What is wrong?
How can I do this?

---

### Post by The Cog on 2021-09-27
I have a feeling there is some other file that says which config files openvpn should start by default. Maybe /etc/default/openvpn? 
I could be wrong, it's over ten years since I configured OpenVPN, but it may be worth checking out.

---

### Post by 90v45mfsdhbgsd on 2021-09-30
Execute
systemctl daemon-reload
then
systemctl restart openvpn

---


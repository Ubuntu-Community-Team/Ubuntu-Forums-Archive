---
title: "Get active tcp connections and disconnect someone"
date: 2011-07-22
forum: Programming Talk
---

### Post by Hilgert on 2011-07-22
Hi all,

I have a problem when i port my app from win to unix, i write on C#(Mono), i cant find any information how to get all active server TCP connections and disconnect someone. Connections dont belongs to app.

On windows i use 2 packages iphlpapi, wsock32 but they dont available on unix

Thanks!

Sorry my english

---

### Post by Hilgert on 2011-07-22
nobody knows?

---

### Post by Zugzwang on 2011-07-23
Look into the "/proc/net" filesystem. Perhaps the "virtual" file "/proc/net/tcp" lists the connections you are interested in?

---

### Post by hakermania on 2011-07-23
also bumping only after at least 24 hours please

---

### Post by Hilgert on 2011-07-23
Thanks, for yours answers, i find "cutter" and TcpConnectionInformation for this.

---


---
title: "Kernel 3.0 cifs mount issues"
date: 2011-06-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-17
I have a new D-Link DNS-320 so trying to learn how sharing and how mount points works. There is a chance I am doing something wrong is so please help me get on the correct track. 

I tried the following mount command with 3.0-0 and 3.0-1 and got a crash but when I used 2.6.39-3 found success and got my home copied to the DNS. Any ideas?

```

bill@billsim-1110-64:~$ sudo mount -t cifs -o guest //XXX.XXX.X.XXX/Volume_1/game-1110-64home/bill/ /media/bills-dns-game-1110-64home

```

Thanks Bill

---

### Post by sparker256 on 2011-06-24
> **sparker256 said:**
> I have a new D-Link DNS-320 so trying to learn how sharing and how mount points works. There is a chance I am doing something wrong is so please help me get on the correct track. 

I tried the following mount command with 3.0-0 and 3.0-1 and got a crash but when I used 2.6.39-3 found success and got my home copied to the DNS. Any ideas?

```

bill@billsim-1110-64:~$ sudo mount -t cifs -o guest //XXX.XXX.X.XXX/Volume_1/game-1110-64home/bill/ /media/bills-dns-game-1110-64home

```

Thanks Bill
I have found that the guest option does not work with kernel 3.0-0, 3.0-1 and 3.0-rc4 and have reported my findings to the linux-cifs mailing list. When I use the following command mounting works correctly which is the way I wanted to us it going forward.
```

bill@billsim-1110-64:~$ sudo mount -t cifs -o credentials=/media/.creds //XXX.XXX.X.XXX/Volume_1/test/ /media/bills-dns-game-1110-64test

```

Bill

---

### Post by sparker256 on 2011-06-29
> **sparker256 said:**
> I have found that the guest option does not work with kernel 3.0-0, 3.0-1 and 3.0-rc4 and have reported my findings to the linux-cifs mailing list. When I use the following command mounting works correctly which is the way I wanted to us it going forward.
```

bill@billsim-1110-64:~$ sudo mount -t cifs -o credentials=/media/.creds //XXX.XXX.X.XXX/Volume_1/test/ /media/bills-dns-game-1110-64test

```

Bill

With the release of 3.0.0-0300rc5 this issue has been solved. I will report to the linux-cifs mailing list.

Bill

---

